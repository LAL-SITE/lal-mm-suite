# Provider Capability Matrix

What each supported provider can and cannot do, and **the fallback for every capability it
lacks.** No capability gap is allowed to become an error or a silent omission.

**Cloud storage is not a requirement of this product.** A firm working from a folder on its own
equipment, or from nothing but files uploaded into the conversation, is fully supported. The
only difference is which capabilities are live, and every reduction below has a stated
substitute.

**One provider is bound per install.** This matrix is what the operator is shown when more than
one is available, and what governs behaviour after binding.

---

## 1. CAPABILITIES

Nine capabilities. Everything the seven operations need reduces to these.

| Key | Capability | Used by |
|---|---|---|
| `search` | Find a folder or file by name | Operation 1 |
| `enumerate` | List a folder's contents, and its subfolders | Operation 2 |
| `timestamps` | Reliable per-file last-modified dates | Operations 2, 4 |
| `delta` | Detect what changed since a prior scan | Operations 2B, 6 |
| `read-text` | Return a file's text content | Operations 3, 5 |
| `write` | Create a new file | Operation 4 |
| `list-before-write` | Enumerate a target folder immediately before writing, to pick a version number | Operation 4 |
| `create-folder` | Create a missing folder | Operations 2, 4 |
| `locator` | Return a stable, re-openable reference to a saved file | Operation 4 |

---

## 2. THE MATRIX

`✔` full · `~` partial or conditional · `✘` unavailable

| Capability | Uploads | Local folder | SharePoint | OneDrive | Google Drive | Dropbox | Box |
|---|---|---|---|---|---|---|---|
| `search` | ✘ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| `enumerate` | ~ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| `timestamps` | ✘ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| `delta` | ✘ | ✔ | ~ | ~ | ~ | ~ | ~ |
| `read-text` | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ | ✔ |
| `write` | ✘ | ✔ | ~ | ~ | ~ | ~ | ~ |
| `list-before-write` | ✘ | ✔ | ~ | ~ | ~ | ~ | ~ |
| `create-folder` | ✘ | ✔ | ~ | ~ | ~ | ✔ | ✔ |
| `locator` | ✘ | ~ | ✔ | ✔ | ✔ | ✔ | ✔ |

**Read the `~` marks as "verify at install, then record the answer."** Cloud connectors differ
by the permissions granted to them, and two firms on the same provider may not have the same
write access. `~` means: probe it once during Operation 0, and record the result in
`capabilityOverrides`. Do not assume in either direction — an assumed write capability is a
lost document.

**`delta` is `~` on every cloud provider for one reason:** delta requires either a durable
change cursor or a reliable modified-since query. Where the connector exposes one, delta is
live. Where it exposes only per-file timestamps, delta is synthesized by comparing a stored
inventory (see § 4). Where it exposes neither, delta is off.

---

## 3. PER-PROVIDER NOTES

### Project / conversation uploads
The floor case, and a fully supported one. Files exist because someone attached them. There is
no folder tree, no search, no write-back, and no notion of "since last time." Everything the
connector does is read-and-report. Do not simulate a folder structure over uploads — report the
files that exist and ask for anything missing by name.

### Local or mounted folder
The most capable configuration, and the one with the fewest surprises: every capability is
genuinely available. `locator` is `~` only because a location on the operator's own equipment is
not a clickable reference for anyone else — report the folder and filename in words.

### SharePoint · OneDrive · Google Drive · Dropbox · Box
All five support search, enumeration, timestamps, text reads, and stable locators. All five vary
on **write, folder creation, and change cursors** depending on how the connector was authorized.
Probe once, record, and re-probe only on rebind.

Where a provider distinguishes a personal area from a shared or team area, bind the **shared**
area if the firm has one. A matter file in a personal area is invisible to everyone else and is
a continuity problem the moment that person is away.

---

## 4. FALLBACKS — ONE PER CAPABILITY

Every row is a behaviour, not an apology. None of them errors.

| Missing | Fallback |
|---|---|
| `search` | Skip Operation 1 Step 2. Go straight to asking the operator where the matter lives, and record the answer as `matterRootLocator` so the question is asked once per matter, not once per session. |
| `enumerate` | Operation 2 cannot build the inventory. Emit the empty inventory template and ask the operator to paste a directory listing or attach the relevant files. Parse what comes back into the standard format so downstream skills still receive the shape they expect. |
| `timestamps` | Print `unavailable` in every date column. **Never estimate a date.** Ordering by date is unavailable; order by name and say so. Any downstream skill that needs recency gets told it is unavailable rather than given a guess. |
| `delta` | Synthesize: store a lightweight inventory snapshot at the end of each session and diff filenames on the next open. If timestamps are also missing, delta reduces to added-and-removed only — report it as `delta: names only` so nobody reads "no changes" as "nothing was modified." If snapshots cannot be stored either, Operation 6 does nothing and says nothing, and Operation 2B reports `delta unavailable on this provider` once per session. |
| `read-text` | Not applicable — no supported provider lacks it. If a *specific file* cannot be read (image-only PDF, unsupported type), report the file as unread and name it. Never summarize a file you could not open. |
| `write` | Operation 4 emits the complete file content in the response, states the exact filename and target slot, and says plainly that the write is not persisted and someone must save it. Flag the session's writes as unpersisted. Never report a save that did not happen. |
| `list-before-write` | Consecutive versioning is impossible. Append a collision-proof suffix to the filename instead of `v<N>`, and tell the operator once that versions will be unique but not sequential. **Never** write a bare filename that could overwrite an existing file. |
| `create-folder` | Do not invent a location. Report the missing folder by its configured name, write nothing, and ask the operator to create it. Offer to write into an existing mapped slot as an interim, clearly labelled, only if the operator asks. |
| `locator` | Report the slot and filename in words. Every save still reports where it landed. |

---

## 5. WHAT THE OPERATOR IS TOLD, AND WHEN

- **At binding** — the chosen provider and, in one line each, any capability it lacks and what
  happens instead.
- **Once per session** — any reduction that changes what the session can promise:
  unpersisted writes, unavailable delta, non-sequential versions.
- **Never repeated turn after turn.** A capability gap stated once is information; stated five
  times it is noise, and the operator stops reading the line that matters.

---

## 6. WHAT THIS MATRIX DOES NOT DECIDE

It does not rank providers, and it does not recommend one. A firm's storage choice is driven by
its own confidentiality obligations, its retention policy, and its existing systems — none of
which are in scope here.

`[CONFIRM LOCALLY: which storage location satisfies the firm's client-confidentiality and file-retention obligations, with {{ROLE_APPROVER}}]`
