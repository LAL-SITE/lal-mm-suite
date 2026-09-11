---
name: lal-file-connector
description: "Storage abstraction - the one skill that touches files. Use for any read, write, scan, save, or template pull on a matter, and to connect or switch storage providers. Fires at session open."
---

# File Connector — Foundation Layer

## When to use this skill (full trigger reference)

The storage abstraction for the whole product line — the one skill that touches files, so no other skill names a storage provider. Detects and binds one provider at install (uploads, a local folder, SharePoint, OneDrive, Google Drive, Dropbox, or Box), then serves every suite through seven fixed operations: resolve the matter root, scan the matter folder, read a document, save output under a never-overwrite versioned filename, pull a template from the firm library, run a quiet delta scan at session open, and degrade gracefully when storage fails. Fires whenever any skill needs a file, and silently on the first turn of every session on a matter. Use IMMEDIATELY on: "find the matter folder", "scan the matter file", "what came in since last time", "read that document", "save it to the matter", "pull the template", "connect my storage", "switch storage providers", or any read, write, list, or search of a matter file. Cloud storage is not required — a local folder or plain uploads works.

This is the **single point of contact between the suites and storage.** Every other skill
calls this one when it needs to read, list, or write a file. No other skill talks to a
storage connector, and no other skill names a provider.

That is the whole value: when a firm changes storage, or a provider's API changes, or a
buyer arrives with nothing but chat uploads, **only this skill changes** — not the suites
that depend on it.

Three invariants:

1. **One provider per install, bound explicitly.** Never inferred mid-session, never silently
   switched.
2. **Never overwrite.** A file with the same date and title becomes the next version.
3. **Never guess between candidates.** Two plausible matter folders is a question for the
   operator, not a coin flip. Mismatched matter folders are how privileged content leaks
   between cases.

---

## OPERATION 0 — INSTALL-TIME PROVIDER DETECTION AND BINDING

Runs **once, at install**, and never again unless a rebind is explicitly requested. Until a
binding exists, every other operation runs in the degraded mode described at the end of this
section — it never errors and never silently omits.

### 0.1 Detection sequence

Probe in this fixed order. Order is deliberate: cheapest and most certain first, so a firm
with no cloud storage at all reaches a working binding without being asked about connectors
it does not have.

| # | Candidate | Probe | Classify as |
|---|---|---|---|
| 1 | **Project / conversation uploads** | Are there files readable in the session's own upload or knowledge area? Documents the client sent through `{{UPLOAD_PORTAL}}` usually reach a session this way | `available` if any readable file surface exists |
| 2 | **Local or mounted folder** | Is there a folder the session can both list and write? | `available` only if listing **and** writing both succeed |
| 3 | **`{{DMS}}` connector** | If `{{DMS}}` is configured at install, probe that connector by name first among the cloud candidates | `available` / `unauthorized` / `absent` |
| 4 | **SharePoint** | Connector present and a search or listing call returns without an auth error | `available` / `unauthorized` / `absent` |
| 5 | **OneDrive** | as above | as above |
| 6 | **Google Drive** | as above | as above |
| 7 | **Dropbox** | as above | as above |
| 8 | **Box** | as above | as above |

Three classifications, and the distinction matters:

- **`available`** — reachable and responding.
- **`unauthorized`** — the connector exists but is not authorized. This is **not** absent.
  Report it as a fixable condition and name it in the candidate list. Do not authorize
  anything yourself and do not ask for tokens, codes, or callback URLs.
- **`absent`** — no connector at all.

### 0.2 Resolving the result

| Detection result | What to do |
|---|---|
| **Exactly one `available`** | Bind it. Echo the binding back for confirmation before the first write. |
| **More than one `available`** | **Ask. Do not guess and do not rank silently.** List every available candidate with what it can and cannot do (from `references/provider-matrix.md`), and let the operator choose one. |
| **Zero `available`, one or more `unauthorized`** | Report which connectors exist but are unauthorized, and that authorization happens in the operator's own connector settings — not here. Bind `none-detected` and run degraded until they return. |
| **Zero of either** | Bind `none-detected`. Run degraded. Never error. |

When asking, ask once, in one block, with the tradeoffs visible. A reasonable framing:

> I can see more than one place to keep matter files. Pick one and I will use it for
> everything:
>
> - **<candidate>** — <what it does well> · <what it cannot do, from the capability matrix>
> - **<candidate>** — …
>
> Cloud storage is not required. A folder on your own machine, or just uploading files into
> the conversation, both work — you lose automatic change detection with uploads, and I will
> tell you each time that matters.

If the operator declines to choose, leave the binding unset and run degraded. **Do not pick
for them.**

### 0.3 What the binding records

Write an install-time configuration block. These are the only settings other skills may rely
on, and none of them is a provider name exposed outside this skill:

```
providerBinding      one of: uploads | local | sharepoint | onedrive | google-drive |
                     dropbox | box | none-detected
matterRootLocator    provider-native locator for the matter root — a path, an item id, or a
                     link. Opaque to every other skill. Never printed into a document.
libraryLocator       locator of the firm template / clause library. Read-only, always.
outputSlot           functional slot that receives generated work product.
                     Default: work-product-output
taxonomyProfile      name of the folder taxonomy in force. Default: lal-default
                     (see references/folder-taxonomy-default.md)
capabilityOverrides  per-capability overrides where the operator knows better than the probe
```

### 0.4 Rebinding

Only on explicit request, or after a bound provider fails **twice in one session**. On the
second failure: report it, offer a rebind, and continue in degraded mode. **Never switch
providers on your own.** A silent switch means half a matter's files live somewhere nobody
was told about.

On rebind, state plainly that files already written under the previous binding do not move,
and that moving them is an operator task.

### 0.5 Degraded mode — `none-detected` or unbound

Never error. Never silently omit. For every operation:

- **Read** — work from whatever the operator pastes or uploads into the session, and say once
  per session that the session is the only source.
- **Scan** — report that no folder is reachable, and offer the inventory format so the
  operator can paste a directory listing instead.
- **Save** — emit the complete file content in the response, state the exact filename and the
  functional slot it belongs in, and say plainly that **this session's writes are not
  persisted.** A write believed to have succeeded and did not is worse than one reported as
  failed.
- **Delta scan** — skip silently. Say nothing at session open; delta is unavailable, not
  broken.

---

## THE ABSTRACTION — WHAT OTHER SKILLS CALL

Other skills call operations by number and describe what they want **functionally.** They
never name a provider, never pass a path, and never pass a folder name.

| A calling skill asks for | It passes | It gets back |
|---|---|---|
| The matter root | client identifier | an opaque root handle, or a stop |
| An inventory | `full` or `delta` | the fixed inventory format in Operation 2 |
| A document | a **functional slot** plus a filename or description | text content, plus a note if formatting was lost |
| A save | content, a document title, a file type, a target slot | filename assigned, version assigned, an opaque locator |
| A template | the template's name | text content, cached for the session |

**Functional slots, not folder names.** A slot is a contract; a folder name is
configuration. `disclosure-client` is a slot. Whatever folder that maps to is
`taxonomyProfile`'s business, and no other skill's. The slot list and the shipped default
mapping are in `references/folder-taxonomy-default.md`.

If a calling skill asks for a slot the taxonomy does not map, do not improvise a folder.
Report the unmapped slot, offer the default mapping for it, and ask.

---

## OPERATION 1 — RESOLVE THE MATTER ROOT

Runs at the start of every session on a matter. Goal: confirm the matter's location **before**
any skill reads or writes. Four steps, in order.

**Step 1 — Check the session's own configuration.** If a matter root locator has been recorded
for this matter (in project or session instructions, or in the connector configuration), use
it. Done.

**Step 2 — Search by client name.** Ask the provider to search for a matter folder using the
client identifier. Prefer folders whose name matches the firm's active-matter naming pattern
over folders matching the pre-engagement pattern. Both patterns are configuration
(`taxonomyProfile`), not fixed.

**Step 3 — More than one match: ask.** Show every match with its last-modified date and ask
which is correct. **Do not guess.** This is the do-not-guess stop, and it is not negotiable:
mismatched matter folders are how privileged content crosses between cases.

**Step 4 — Zero matches: stop.** Do not create a matter folder to get unblocked. Report:

> I cannot find a matter folder for this client in the bound storage. Either it has not been
> created yet, or it is named differently than the configured pattern. Confirm with
> `{{ROLE_INTAKE}}` that the matter has been opened in `{{PM_SYSTEM}}` and that its folder
> exists, or paste the folder's location and I will use it.

**Once resolved, the root locks for the session.** All operations run beneath it. This
connector never reads from one matter's folder while operating on another, and never resolves
a second root in the same session without an explicit instruction to switch matters.

---

## OPERATION 2 — SCAN THE MATTER FOLDER

Two modes. **Delta is the default** unless the calling skill asks for full.

### Mode A — Full scan

Requested by first-touch and rebuild skills only, or by an operator saying "rescan
everything." Walk every mapped slot and build the inventory in **exactly this format** —
downstream skills parse it, so the shape is contract:

```
MATTER ROOT: <client identifier>
TAXONOMY: <taxonomyProfile>   PROVIDER CAPABILITIES: <full | reduced: …>

<SLOT NAME> → <mapped folder name>   [N files | last modified: <date or unavailable>]
   <filename>   <last modified or unavailable>
   <filename>   <last modified or unavailable>
<SLOT NAME> → <mapped folder name>   [0 files]
<SLOT NAME> → UNMAPPED               [not present in this taxonomy]
<UNRECOGNIZED FOLDER: folder name>   [N files]

TOTALS: <N> files across <N> folders | slots mapped: <N> | slots missing: <N>
SCAN MODE: full | SCAN DATE: {{DATE}}
```

Rules for the inventory:

- **List every mapped slot, including empty ones.** An empty slot is information; an omitted
  slot is a gap a downstream skill will misread as absence of the whole category.
- **List unrecognized folders too**, under `UNRECOGNIZED FOLDER`. Do not silently ignore
  folders outside the taxonomy, and do not move or rename them.
- Where the provider cannot supply timestamps, print `unavailable` — never a guessed date.
- Never truncate a file list without saying so. If a slot has more files than can be printed,
  print the count and the most recent ones and label the list `truncated`.

### Mode B — Delta scan

Compare current state to the last scan recorded for this matter. Return only:

- **Added** since last scan — slot, filename, date
- **Modified** since last scan — slot, filename, date
- **Removed** since last scan — slot, filename

If nothing changed: `No new files since last scan on <date>.`

**Quiet by default.** A delta scan flags changes. It does not re-run analysis, does not
regenerate anything, and does not notify anyone. Decisions about what to re-run stay with the
operator.

**If the provider cannot do delta** (see the capability matrix), say so once per session and
fall back to the matrix's stated substitute — never present a full scan as if it were a
delta, and never claim nothing changed when you could not tell.

---

## OPERATION 3 — READ A DOCUMENT

1. Confirm the target is inside the resolved matter root or the read-only library. Nothing
   outside those two boundaries is read without explicit operator confirmation — privileged
   content protection.
2. Read through the bound provider.
3. Return text content to the calling skill.
4. If the file is a scanned image or an image-only PDF, say that text extraction may be
   incomplete and that OCR may be required. Do not paraphrase what you could not read.

### Known limitation — word-processing formatting does not survive a read

Confirmed by direct testing (2026-07-18), and it has not changed since: reading a `.docx`
through a storage connector returns **plain extracted text only** — no bold, no indentation,
no fonts, no margins, no styles. This holds whether the file is read live from the provider
or from a session upload area. In the same testing, `.pdf` and `.xlsx` read from an upload
area **did** retain their real binary structure.

**Practical effect, and the workaround:** no skill may promise to "pull the live template and
preserve formatting" when the source is a `.docx`. Where exact word-processor formatting
matters — anything filed, anything that must match a court's expectations pixel for pixel —
do two things instead:

1. Read the *formatting* from a PDF export of the source document, where real formatting
   survives.
2. Generate the output with a validated, code-based document builder, not by echoing a live
   re-read.

State this limitation to the operator the first time a `.docx` template is requested in a
session. Do not let a caller discover it in a filed document.

---

## OPERATION 4 — SAVE OUTPUT

Every skill that produces a deliverable saves through here.

### Filename format

```
{{DATE}} - {{CLIENT_NAME}} - <Document Title> - v<N>.<ext>
```

- `{{DATE}}` — today, in the firm's configured short date format.
- `{{CLIENT_NAME}}` — as configured for filenames. One form, used consistently.
- `<Document Title>` — short, title case, descriptive.
- `v<N>` — version. See below.

### Versioning — never overwrite

```
1. List the target slot for files matching:
      {{DATE}} - {{CLIENT_NAME}} - <Document Title> - v*.<ext>
2. If none match                → save as v1
3. If the highest match is vN   → save as v(N+1)
4. Never reuse a version number. Never overwrite. Never delete.
```

The point of versioning is that `{{ROLE_REVIEWER}}` and `{{ROLE_APPROVER}}` can see
iterations. An overwritten draft destroys the review record.

**If the provider cannot list before writing** — some cannot, reliably — the matrix's
fallback applies: generate a collision-proof suffix instead of a sequence, and tell the
operator that versions will not be consecutive. Never write a bare filename that could
clobber an existing file.

### Target

Default target is the `work-product-output` slot. A calling skill may name a different slot;
it may not name a folder. Never write into the library — the library is read-only, always.

### After saving, return to the caller

- the filename assigned
- the version assigned
- an opaque locator for the saved file

And tell the operator:

> Saved: `<filename>` → <slot, in plain words>
> <locator, where the provider supplies one>
> `{{ROLE_REVIEWER}}` review required before this leaves the firm.

Where the provider supplies a clickable locator, always include it. Where it does not, say
where the file is in words. Never report a save without saying where it landed.

---

## OPERATION 5 — PULL FROM THE LIBRARY

When a drafting skill needs a template, clause bank, or master document:

1. The caller names the document it wants.
2. Locate it under `libraryLocator`.
3. Read it (Operation 3).
4. Return text content to the caller.

**Session cache.** If the same library document is requested twice in one session, return the
copy from the first read. Library documents change rarely, and re-reading them wastes the
operator's time and the provider's rate limit. The cache is per session and never persists.

**Text only.** Per Operation 3, this returns words, not formatting. Fine for clause language,
boilerplate, and reference data. Not a substitute for real formatting — see the workaround.

**Read-only, without exception.** This connector never writes to the library. Templates live
there; outputs go to the matter.

---

## OPERATION 6 — SESSION-OPEN DELTA SCAN (SILENT)

Fires on the first turn of every session on a matter, before any other skill runs.

```
1. Resolve the matter root (Operation 1), using the recorded locator if there is one.
2. Run a delta scan (Operation 2, Mode B).
3. If there are changes, surface them in a few lines at the top of the first response.
4. If there are no changes, say nothing at all. Do not mention the scan. Go straight to
   what the operator asked for.
```

The change notice, when there is one:

> **New in the matter file since <date>:**
> - New: `<slot>` / `<filename>` (<date>)
> - New: `<slot>` / `<filename>` (<date>)
>
> Skills that read those slots will reflect them. No action required unless you want to
> re-run an earlier stage.

**What this scan does not do:** it does not re-run any analysis, does not regenerate any
deliverable, does not write anything, and does not notify `{{ROLE_APPROVER}}`. It is a
notification layer only.

If the provider cannot do delta scans, this operation does nothing and says nothing.

---

## OPERATION 7 — ERROR HANDLING

**Provider call fails.**

> I cannot reach the matter storage right now. Confirm the connector for the bound provider
> is enabled and authorized in your own settings — sometimes the authorization just needs to
> refresh. I will keep working from what is in this session and will tell you if anything
> I produce is unsaved.

Never ask for a token, a code, or a callback URL. Two failures in one session triggers the
rebind offer in § 0.4.

**A slot is empty when it seems like it should not be.** Do not assume. Report what you found
and ask whether the folder should have content. An empty slot is often legitimate — a new
matter, disclosure not yet requested — and inventing an explanation is worse than asking.

**A required slot's folder does not exist.** If the provider can create folders, create it
from the taxonomy's exact configured name before writing, and report that you did. If it
cannot, report the missing folder, write nowhere, and ask the operator to create it.

**A filename does not fit the firm's convention.** Do not reject it. Read it. Flag it:
"filename does not match the configured convention — recommend renaming before further
processing." Conventions are enforced at organize time, not read time.

**Two files have near-identical names.** Show both, with dates, and ask which is current.
**Never guess.** This is exactly how a superseded or privileged document gets used downstream.

**The operator names a file outside the matter root.** Stop and confirm before reading. State
which matter is resolved for the session.

---

## RULES THAT ALWAYS APPLY

- **The bound provider is the source of truth.** Files pasted in chat or uploaded into the
  session are reference copies unless uploads *is* the binding.
- **Versioned, never overwritten.** Same date plus same title equals the next version.
- **One matter per session.** The root resolves once and locks.
- **The library is read-only.**
- **Quiet by default.** Delta scans are one short block. Full scans run only when asked.
- **Every save reports where it landed.**
- **No provider name, locator, path, tenant, site, drive, or URL is ever written into a
  generated document.** Documents carry `{{CLIENT_NAME}}`, `{{CASE_NO}}`, and the firm's own
  tokens — never storage plumbing.
- **Never fabricate.** An unknown date is `unavailable`. An unreadable file is reported as
  unreadable. A gap is marked, not filled in.

---

## WHO DEPENDS ON THIS

Every suite reads and writes through this skill. Graceful degradation runs both ways: if a
caller is not installed, this skill simply is not called by it; if this skill is unbound, each
caller still completes its work in degraded mode.

| Caller | What it needs here |
|---|---|
| First-touch / matter-launch skill (`lal-start-case`) | Operation 1, Operation 2 Mode A, Operation 4 |
| Matter state file (`lal-command-center`) | Operation 3 and Operation 4 on the state file, every session |
| Ethics and verification skill (`lal-florida-ethics`) | Operation 3 on engagement and scope documents |
| Correspondence skills | Operation 3 on prior correspondence, Operation 5 for templates, Operation 4 to save |
| Any disclosure or discovery suite, if installed | Operation 2 on the disclosure slots, Operation 4 for trackers and logs |
| Any drafting suite, if installed | Operation 5 for masters, Operation 4 for drafts |
| Any review or QC skill, if installed | Operation 3 on the draft, Operation 4 for the review memo |
| Any case-plan or reporting suite, if installed | Operation 2, Operation 4 |

---

## REFERENCES

- `references/provider-matrix.md` — what each supported provider can and cannot do, and the
  fallback for every capability it lacks.
- `references/folder-taxonomy-default.md` — the functional slot contract and the **default**
  folder mapping. The mapping is configuration and is meant to be replaced.

⚠️ VERIFY: confirm rule and current text before relying on this. This skill moves files; it
decides nothing legal. Any question about what a document means, whether a date is
jurisdictional, or whether something may be sent goes to `{{ROLE_APPROVER}}`.
