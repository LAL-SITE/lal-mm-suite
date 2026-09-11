# Firm-Wide Operating Conventions

**Every Core Foundation skill points at this file.** It is the single shared statement of how
skills behave toward the person running them. A skill author can comply with everything below
without reading any other document, with one exception that is named and linked in § 6.

Six conventions. They are not style preferences. Each one exists because the opposite behaviour
was observed to break a real matter: a skill that redirected a user to a different tool, a skill
that told an approving attorney to get attorney approval, a skill that refused to start because
a prior stage was unlogged, a skill that reported a document missing that was sitting in the
matter file under a wrong name, a skill that demanded an audio recording, and a skill that
completed work nothing else could see.

---

## 1. ENVIRONMENT-FLEXIBLE

**Complete the task in the environment you are running in.** Never block on the environment.
Never redirect the user somewhere else to do the work.

If a different environment would be materially better for this task, say so in **one line**, then
keep working:

> One line, then continue. Nothing after it changes.
>
> *"A browser session with live rule lookup would let me verify the current text of this rule;
> proceeding here and flagging the citation for verification."*

Forbidden, in every skill, without exception:

- "This task is outside the scope of this environment."
- "Take this to <other tool> instead."
- "Open the matter project and describe the task there."
- Producing nothing and pointing at a different surface.

**Degraded is not blocked.** If a capability is genuinely unavailable — no web access, no
connector, no installed suite — do the part you can do, name the part you could not do, and hand
the user a specific next action. See § 7 on graceful degradation.

**Corollary for storage.** Reach files only through the file connector abstraction. A skill that
cannot reach the connector still runs: it works from whatever the user has pasted or uploaded,
says plainly that it could not read the matter file, and never claims a file is absent on the
basis of a failed read.

---

## 2. IDENTITY OVER LANES

**Role assignments are defaults, not gates.** Anyone may run any skill.

The role tokens — `{{ROLE_DRAFTER}}`, `{{ROLE_REVIEWER}}`, `{{ROLE_APPROVER}}`, `{{ROLE_INTAKE}}`
— describe *who owns an output by default in a typical install*. They do not describe who is
permitted to invoke a skill. A firm of one person maps all four tokens to that person. A firm of
forty maps them to four groups. Both are correct installs.

**The self-approval rule.** Where the person running the skill holds `{{ROLE_APPROVER}}`, that
person **self-approves**. Do not tell them to seek attorney approval. Do not route an output to
them and then wait for them to approve it to themselves. Record the approval and continue.

- Ask once, plainly, at the top of a session or the first time approval is reached:
  *"Are you the approving attorney on this matter?"*
- If yes — approval gates are satisfied by their confirmation, recorded as such, and the skill
  continues to a finished output.
- If no — the gate stands, and the output routes to `{{ROLE_APPROVER}}` with the specific
  question that needs answering.
- If unknown — ask. Do not assume the more restrictive answer and stall.

**What this does not relax.** An approval gate that exists for a reason other than seniority
still holds. Three examples, and they are the only kind:

| Gate | Why it survives self-approval |
|---|---|
| A missing attorney-supplied compliance block | The text does not exist. No role can approve absent text into existence. |
| A figure the client has not authorized in writing | The authorization is the client's, not the firm's. |
| A rule, statute, or authority whose current text has not been checked | Verification is an act, not a permission. |

Everything else — "route to the attorney," "escalate for review," "get sign-off" — is satisfied
when the approving attorney is the one asking.

**Never state a job title.** Buyer org charts differ and a title asserted in an output is wrong
somewhere. Write `{{ROLE_DRAFTER}}`, not a title. This applies to generated documents, signature
blocks, and the skill's own conversational output.

---

## 3. JUST-RUN-IT

**Prerequisite stages are soft checks.** A skill that depends on earlier work checks for it,
notes what it found, and proceeds on the best available basis.

Pause for exactly one reason: **a physically necessary input is absent and cannot be inferred,
substituted, or worked around.** When that happens, ask for the specific missing item.

| Never say | Say instead |
|---|---|
| "Complete Stage 4 first." | "I don't have a served date for the production I'm measuring against — what date was it served?" |
| "Run the intake skill before this one." | "I don't see an opened matter. What's the matter name and county so I can proceed?" |
| "The tracker has not been updated." | *(Nothing. Proceed, and note the tracker gap in your output.)* |
| "This requires the discovery suite, which is not installed." | "Working from the documents in the matter file directly, since the discovery suite isn't installed." |

Three rules on pausing:

1. **Ask for the item, never for the stage.** "What is the hearing date?" not "complete the
   scheduling workflow."
2. **Ask once, and ask for everything at once.** Batch every missing input into a single numbered
   list. Do not interrogate turn by turn.
3. **Offer a provisional path.** If the user cannot supply the item now, say what you can produce
   without it and what will be marked unresolved. Then produce that.

**Missing state is never a stop.** If the command center does not exist, or exists and is stale,
use your own defaults, say plainly in your output that you did so, and raise a flag. Never stall
a task waiting on state.

---

## 4. READ FILES FIRST

**Search the whole matter file before you say anything is missing.** A skill that reports a
document absent when it is sitting in the file under a wrong name has produced a false negative,
and the user acts on it.

Before any statement of the form "we do not have X," "X is missing," or "X was never produced":

1. **List the whole matter file**, not the folder where X belongs. The single most common failure
   is a correctly named document in the wrong folder.
2. **Search by content, not only by filename.** Filename search is not sufficient. Bulk exports,
   scanner defaults, and portal downloads produce filenames that reveal nothing about contents. A
   name-search negative is **inconclusive**, never a finding.
3. **Check for misnamed variants** — abbreviations, party initials, date-first and date-last
   naming, version suffixes, and the buyer's prior naming convention alongside the current one.
4. **Check adjacent and nested locations** — an archive folder inside an open matter folder, a
   correspondence subfolder, a personal drive area, and any folder whose name suggests closure or
   staging. Nested archives inside unrelated matter folders are real and are easy to miss.
5. **Open the candidates.** A file whose name matches is not a finding until its contents are
   read. Filename and contents disagree often enough that the mismatch must be assumed.

Only after all five may a skill state that something is missing — and it states it as *not
located in the matter file*, with the locations searched named.

**Then offer the cleanup.** Whenever the search surfaces misnamed or misfoldered documents, say
so and offer a file-organizer pass:

> *"While searching I found four documents that are misnamed and two in the wrong folder. If the
> file-organizer skill is installed I can run a cleanup pass over the matter; if not, here is the
> list so you can move them."*

Offer it. Do not perform a rename or a move as a side effect of another task, and never move a
document between matters.

---

## 5. TRANSCRIPTS PREFERRED

**A typed memo or a set of notes always suffices.** Never require a recording, an audio file, or
a platform-generated transcript as a condition of doing the work.

Where a skill needs the content of a conversation — an intake call, a client meeting, a
collateral interview, a hearing, a mediation session — accept, in descending order of preference
and with no order being mandatory:

1. A verbatim or near-verbatim typed transcript.
2. A contemporaneous typed memo.
3. Handwritten notes, typed up or described.
4. The user's recollection, stated in the session.

Say which one you used and treat the lower-fidelity sources as lower-fidelity in the output — a
recollection is attributed as a recollection, not recorded as testimony. What you never do is
refuse to proceed, ask whether a recording exists, or suggest the conversation be redone with
recording enabled.

**Never ask for a recording.** Recording carries consent obligations that vary by state and by
participant, and it is not the skill's place to prompt for it.

---

## 6. COMMAND-CENTER WRITES

Skills write their results to the matter's command center: **stage completions, deadlines,
lifecycle moves, and attorney flags.** Work that is not recorded there is invisible to every
other suite.

**The write rules are not restated here.** They are governed by a single document, and a skill
author writing to the command center must read it:

> **the write contract** — `references/write-contract.md` **as it sits inside the command-center
> skill.** This conventions block is bundled into every skill as that skill's own
> `references/conventions.md`, so the write contract is **not** at a path relative to the skill you
> are running: it is a document belonging to the command-center skill, and it is read from there.

That contract is self-contained. It covers append-only behaviour, field ownership, re-reading
before writing, conflict reporting, flag handling, the nine mandatory deadline fields, stage
completion sequence, scope changes, what to do when the command center does not exist, storage
neutrality, and a nine-question self-check.

Two things about it that matter at the level of these conventions:

- **The absence of a command center never blocks anything.** The contract specifies exactly what
  to do in each case, including the case where no file can be written at all.
- **Never fabricate a value to fill a required field.** An unknown required field is `null` plus a
  flag. A plausible guess is a defect every downstream suite inherits and nobody can detect.

---

## 7. THE STANDING RULES THAT APPLY TO EVERY SKILL

These are not conventions about user interaction. They are output rules, and they are absolute.

### 7.1 Tokens — curly for everything

Two classes, both curly. There are no bracket-style placeholders anywhere in any Core output.

**Install-time** — resolved once, when the buyer installs:

`{{FIRM_NAME}}` · `{{ATTORNEY_NAME}}` · `{{BAR_NO}}` · `{{FIRM_ADDRESS}}` · `{{FIRM_PHONE}}` ·
`{{FIRM_EMAIL}}` · `{{PM_SYSTEM}}` · `{{DMS}}` · `{{RESEARCH_PROVIDER}}` · `{{UPLOAD_PORTAL}}` ·
`{{PAYMENT_PROCESSOR}}` · `{{ESIGN_TOOL}}` · `{{ROLE_DRAFTER}}` · `{{ROLE_REVIEWER}}` ·
`{{ROLE_APPROVER}}` · `{{ROLE_INTAKE}}`

**Draft-time** — resolved per matter, per document. **Also curly. This is a deliberate ruling,
not an oversight:** a single token syntax means one lint rule catches every unresolved
placeholder, and a draft-time token left unfilled fails the same check as an install-time one.

`{{CLIENT_NAME}}` · `{{CASE_NO}}` · `{{JUDGE}}` · `{{OPPOSING_COUNSEL}}` · `{{COUNTY}}` ·
`{{CIRCUIT}}` · `{{DATE}}` · `{{AMOUNT}}`

Additional curly tokens appear in specific content specs — among them
`{{CLIENT_UPLOAD_TOOL}}`, `{{VIDEO_TOOL}}`, `{{THIRD_PARTY_NAME}}`, `{{DIVISION}}`. They follow
the same rules. A skill may use a spec's token vocabulary; it may not invent a new bracket syntax.

**Fill-in tokens for the standard output blocks.** The flag template, the out-of-scope routing
statement, and the neutral-options construction all carry fill-ins. Those fill-ins are **curly
tokens, not brackets**, and they are documented here so a lint rule can catch them:

| Token | Resolves to | Used in |
|---|---|---|
| `{{FLAG_SUBJECT}}` | The one issue a flag is about | Flag template |
| `{{TRIGGER_CLASS}}` | Exactly one trigger class from the enumerated set | Flag template |
| `{{FACTS_ON_HAND}}` | The facts and sources actually in the file, named with file names | Flag template |
| `{{MISSING_ITEM}}` | The specific missing item — never "more information" | Flag template |
| `{{STOP_BASIS}}` | The rule, duty, or risk making this an attorney call, with the verify warning | Flag template |
| `{{OPTION_A}}` · `{{OPTION_B}}` | Neutrally stated alternatives, with no recommendation | Flag template; any neutral-options block |
| `{{DOMAIN_NAME}}` | The out-of-scope domain being refused | Out-of-scope routing statement |
| `{{FILE_EVIDENCE}}` | Only what is actually in the matter file, named with file names | Out-of-scope routing statement |
| `{{REQUIREMENT_CLASS}}` | Exactly one of: attorney judgment · attorney-supplied policy · a purchased suite that covers it | Out-of-scope routing statement |

Every one of these resolves before the block is emitted. An unresolved one fails the same check as
an unresolved install-time token.

### 7.2 `[CONFIRM LOCALLY]` — the one permitted bracket construction

Where practice varies by **circuit, county, division, judge, or clerk**, emit:

```
[CONFIRM LOCALLY: <what to confirm>, with <whom to confirm it>]
```

It is an instruction to the user, not a defect and not a placeholder. It names the thing and the
person. `[CONFIRM LOCALLY: local continuance lead time, with {{ROLE_APPROVER}}]` is compliant.
`[CONFIRM LOCALLY: procedure]` is not — it names neither.

It is **not** a substitute for content that should exist. A `[CONFIRM LOCALLY]` marker standing
in for text an attorney is required to supply is a defect; see § 7.6.

### 7.3 Never emit

- `Click here to enter text.` — an unfilled word-processor content control. It exists in real
  approved firm forms. Any output containing it fails.
- `XXXXXXXX` or any run of placeholder X's.
- An unresolved `{{TOKEN}}` in a document represented as ready to send.
- A bracket-style placeholder of any other shape.

Check for all four before output. A hard fail, not a warning.

### 7.4 Authority — no case law, ever

Rules, statutes, and Bar rules only. **No case law anywhere in any Core skill or reference** — no
case names, no reporter citations, no parentheticals, no "courts have held."

Every rule, statute, and Bar rule carries, at the point of citation:

> ⚠️ VERIFY: confirm rule and current text before relying on this.

Rule numbers used as trigger vocabulary in a skill description are not citations and do not carry
the warning; anything in a body, a reference, or a generated document does.

Official sources only where a source is named: `floridabar.org`, `flcourts.gov`,
`leg.state.fl.us`. No other URL appears in any output.

### 7.5 Graceful degradation

Every dependency on another suite is written as a two-branch instruction:

> *If the <X> suite is installed, do A. If not, do B.*

Branch B is always a real, useful path — not an apology and not a stop. State which branch you
took. A skill that names a dependency without naming the fallback is incomplete.

### 7.6 Never fabricate

An honestly named gap is a required output. Padded content is a defect the buyer discovers
mid-matter, which is the worst possible moment.

- Do not invent a rule, a period, a form number, a retention policy, or a local practice.
- Do not scaffold a document type from an adjacent one and present it as sourced.
- Do not fill an attorney-owned block with drafted text, and do not fill it with a
  `[CONFIRM LOCALLY]` marker either. Stop and say the block has not been supplied.
- Where a content spec labels an entry **template-sourced** rather than matter-sourced, say so to
  the user. Untested template language is legitimate to ship and illegitimate to misrepresent.
- Where a spec records that a document type has no source at all, do not produce that document
  type. Name the gap.

### 7.7 Zero source-firm identity

Core Foundation is white-labeled. No output — skill body, reference, or generated document —
contains: a source firm name or brand; any staff first name; **any staff job title** (use role
tokens); a named practice-management, e-signature, upload, or payment vendor (use the token); a
bar number as a literal; a billing rate; a tenant, site, drive letter, local path, or storage
provider name; or any URL except the three official Florida sources in § 7.4.

**No estate-planning reference anywhere.** The source library wrongly asserted the firm offered
it. A beneficiary-review reminder is permitted and must refer out rather than offer a service.

**No review-solicitation language in any representation-ending document.** A closing,
disengagement, withdrawal, substitution, or non-representation letter never asks for a public
review. One executed source letter solicited a review in the same document that announced a
motion to withdraw. That must not propagate.

---

## 8. AUTHOR SELF-CHECK

Ten questions. A `no` to any one means the skill is not compliant with these conventions.

1. Does the skill complete its task in whatever environment it is running in, with no redirect?
2. Can any role invoke it, and does an approving attorney self-approve without being told to seek
   approval?
3. Are prerequisite stages soft checks, with pauses only for named physically necessary inputs?
4. Does it search the whole matter file — by content, in nested locations, opening candidates —
   before calling anything missing, and does it then offer a cleanup pass?
5. Does it accept a typed memo or notes wherever conversation content is needed, and never ask for
   a recording?
6. Does it write stage completions, deadlines, lifecycle moves, and flags per the write contract,
   and continue when no command center exists?
7. Are all tokens curly, with `[CONFIRM LOCALLY: what, with whom]` the only bracket construction?
8. Is there zero case law, and does every rule, statute, and Bar rule carry the verification
   warning?
9. Is every cross-suite dependency written as installed-versus-not, with a real fallback?
10. Are all gaps named rather than filled, is template-sourced language labeled as such, and is
    there zero source-firm identity, zero estate planning, and zero review solicitation in any
    representation-ending document?
