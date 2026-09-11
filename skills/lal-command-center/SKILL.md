---
name: lal-command-center
description: "The per-matter state file every suite reads and writes. Use for case status, what's next, deadlines, stage logging, scope changes, and attorney flags. Fires at session open and after any stage."
---

# Command Center

## When to use this skill (full trigger reference)

The matter command center — the single per-matter state file that every other Legal Authority Lab suite reads before it works and writes to when it finishes. Holds matter position (phase, stage, completed stages), scope of representation, the deadline register with the authority and computation basis for every date, the append-only lifecycle ledger, and open attorney flags. Use IMMEDIATELY on: "where are we on this case", "what's the status", "what's next", "open the command center", "set up this matter", "log this stage", "what's due", "how was that date computed", "scope changed", "flag this for the attorney", "what changed since last session", or any request to read, record, or reconcile matter state. Also fires automatically at the open of any session on a matter and at the close of any skill that completes a stage, computes a deadline, changes scope, or raises a flag. Reads and writes through the file connector — never assumes a storage provider. Never overwrites; always appends.

The command center is the **write contract** for the whole product line. Every suite depends
on its schema. A silently dropped flag or a miscomputed jurisdictional deadline recorded
without its basis is the kind of defect that surfaces in front of a judge.

Three rules govern everything below.

1. **Append, never overwrite.** State fields are superseded by a new entry plus a ledger
   line, not by deletion. History is the product.
2. **Never drop a flag.** An open attorney flag stays open until a named resolving role
   closes it. No skill may resolve another skill's flag.
3. **Record how, not just what.** Every deadline carries its authority and computation
   basis. Every stage move carries its trigger and evidence.

This skill decides nothing legal. It records state, surfaces what is running, and routes
judgment calls to `{{ROLE_APPROVER}}`.

---

## WHERE IT LIVES

One file per matter, in the matter's working location:

```
COMMAND-CENTER.md
```

Read and write it through the file connector. Do not assume a provider — the same file must
work on a local folder, a project upload area, `{{DMS}}`, or any cloud drive the firm uses.
Resolve the matter root once per session; if the connector cannot resolve it, see
**Degradation** below.

The file has two halves that must agree:

- **A fenced `json` block** — the machine state. Other suites parse this.
- **A human mirror below it** — tables a person reads without parsing JSON.

When the two disagree, the JSON block is authoritative and the mirror is regenerated from it.
The mirror is the only part of the file that is ever rewritten wholesale.

---

## WHEN THIS SKILL FIRES

**Automatically, at session open.** Read the command center before any other work. Report,
in four lines: current phase and stage, deadlines due inside 30 days, open flags, and what
changed since the last recorded write.

**Automatically, at the close of any skill that:**
- completes or advances a stage
- computes, satisfies, extends, or misses a deadline
- changes scope of representation, service model, resolution path, or discovery level
- raises or resolves an attorney flag
- receives, serves, or files anything that starts or stops a clock

**On request.** Any of the trigger phrases in the description.

**Update triggers — the enumerated list.** Ported from the append-only tracker discipline and
extended for lifecycle and deadlines. Write on every one of these, not only at stage
completion:

| # | Event | What gets written |
|---|---|---|
| 1 | Matter opened / first session | Birth entry (see below) |
| 2 | Scope document signed, amended, or replaced | `scope` supersede + ledger `scope-change` |
| 3 | Stage begun | `position.currentStage` + ledger `stage-advance` |
| 4 | Stage completed and cleared review | `position.completedStages[]` + ledger `stage-complete` |
| 5 | Anything served, received, or filed | Ledger entry + any deadline it triggers or satisfies |
| 6 | A deadline is computed | New `deadlines[]` object with authority and basis |
| 7 | A deadline is satisfied, extended, waived, or missed | Deadline `status` supersede + ledger |
| 8 | An order setting a hearing or trial arrives | One deadline object per date in the order, plus the warning ladder |
| 9 | An attorney flag is raised | New `flags[]` object |
| 10 | A flag is resolved | Flag `resolvedAt` + `resolvingRole` + ledger |
| 11 | Resolution path, discovery level, or client role changes | State supersede + ledger |
| 12 | A prior entry is found to be wrong | **Correction entry**, never a silent edit (see below) |
| 13 | Matter closed | Ledger `closed` entry; file is retained, not deleted |

Do not wait for a stage to finish. The command center is a live log.

---

## BIRTHING A COMMAND CENTER

If `COMMAND-CENTER.md` does not exist, create it. Never refuse work because it is missing.

**Step 1 — Scan before asking.** Read what the matter folder already contains and infer state
from the documents present. Use the evidence table in `references/lifecycle-vocabulary.md`
(§ Evidence → Stage Inference). A matter that arrives mid-stream joins the ledger mid-stream:
record inferred stages with `trigger: "inferred-from-file-scan"` and
`evidence: "<filename or folder>"`, so it is visible that no one witnessed the event.

**Step 2 — Ask only for what the scan cannot answer.** One organized block, not one question
at a time. Typically missing from files: assigned `{{ROLE_APPROVER}}`, anticipated resolution
path, known deadlines with no notice yet on file, known risk items not yet documented.

**Step 3 — Write the birth entry.** `schemaVersion`, `matter`, `scope`, `position`, empty
`deadlines`, `flags`, and a single `ledger` entry of type `birth` recording who created it,
when, and from what evidence.

**Step 4 — Compute the deadlines the birth facts already imply.** If a service date is on
file, the clocks that run from it are already running. Create those deadline objects now,
each with its authority, and each carrying the verify warning. See
`references/deadline-authorities.md`.

**Step 5 — Flag what the scan could not resolve.** Missing scope document, unknown service
date, unresolved matter type, no assigned approver — each is a flag, not a shrug. Severity
`attorney-review` at minimum.

**Never fabricate to complete a field.** An unknown value is `null` with a flag, never a
plausible guess. `null` plus a flag is a task; a guessed value is a defect that propagates
to every suite that reads it.

---

## HOW IT READS

Reading is cheap and always allowed. Any skill, any role.

1. Resolve the matter root through the file connector.
2. Read `COMMAND-CENTER.md` and parse the JSON block.
3. If the JSON block is malformed or absent but the file exists: do **not** rewrite it. Read
   the human mirror, report what you could recover, raise a flag with severity
   `attorney-review` describing the corruption, and proceed read-only until a human confirms.
4. Filter to what your task needs. A drafting skill needs `matter`, `scope`, and open flags.
   A discovery skill needs `position` and the deadline register. Do not load the whole ledger
   to answer a one-field question.

**Reading is not endorsing.** A stage marked complete with
`trigger: "inferred-from-file-scan"` is weaker evidence than one with a witnessed trigger.
Say so when it matters.

---

## HOW IT WRITES

Every write is an append. There is no update-in-place operation in this schema.

**To change a state field** (anything under `matter`, `scope`, or `position`): write the new
value, and write a ledger entry recording `from`, `to`, `actorRole`, `trigger`, and
`evidence`. The old value survives in the ledger. A state change without a matching ledger
entry is a malformed write.

**To add a deadline, flag, or ledger entry:** append the object. Never renumber, never
compact, never remove.

**To correct an error:** append a ledger entry of type `correction` that names the entry being
corrected by `id`, states what was wrong, and states the corrected value. Then supersede the
state field. Do not delete the wrong entry — a deadline that was wrongly computed and then
fixed is exactly the history that has to survive.

**Field ownership.** Not every skill may write every field. The full matrix is in
`references/write-contract.md`. The short version: a skill writes the fields its own work
produces, and never the fields another skill owns. Nobody but `{{ROLE_APPROVER}}` closes a
flag of severity `urgent` or `jurisdictional-risk`.

**Conflict.** If the value you are about to write is already set to something different, and
you were not the skill that set it: do not overwrite. Write your value into a ledger entry of
type `conflict`, leave the existing state field alone, and raise a flag naming both values and
both sources. Two suites disagreeing about the current stage is information, not noise.

**Concurrency.** Re-read immediately before writing. If the file changed since your read,
re-base your append on the current content. Never write a whole file you assembled from a
stale read — that is how appends become overwrites.

---

## DEADLINES — THE PART THAT IS MALPRACTICE IF WRONG

A deadline object records **how the date was reached**, not only the date. A date with no
recorded basis cannot be audited, and an unauditable jurisdictional date is worse than no
date at all.

Required on every deadline: `id`, `label`, `authority`, `computedFrom` (the triggering event,
its date, and the service method), `computationBasis` (the counting rule actually applied),
`dueDate`, `jurisdictional`, `extendable`, `ownerRole`, `status`. Full definitions in
`references/schema.md`.

**Rules.**

- **No service date, no deadline.** If the triggering date is unknown, create the deadline with
  `dueDate: null`, `status: "uncomputable"`, and a flag. Do not estimate.
- **Record the counting rule you applied**, including whether the period was under 7 days,
  whether the last day rolled off a weekend or holiday, and whether days were added for the
  service method. Confirm the clerk's observed-holiday calendar locally —
  `[CONFIRM LOCALLY: clerk-observed closures and holiday calendar, with {{ROLE_INTAKE}}]`.
- **Every authority carries the verify warning.** Rules amend on independent cycles.
- **Jurisdictional and non-extendable dates are flagged on creation**, not on approach.
- **Order-created deadlines outrank rule defaults.** A date set by a trial or hearing order
  controls; record `authority` as the order itself and
  `[CONFIRM LOCALLY: assigned judge's written procedures, with {{ROLE_APPROVER}}]`.
- **Build the warning ladder.** For each hard date, populate `warnings` at T-14, T-7, and T-3.
  This is an internal control, not a rule requirement — say so when reporting it.
- **A missed deadline is never quietly restatused.** `status: "missed"` plus a flag of severity
  `urgent`, plus a ledger entry. Whether it can be cured is an attorney decision.

Nothing in this skill computes a deadline as legal advice. It records the computation so a
human can check it.

---

## ATTORNEY FLAGS

A flag is an object, not a sentence in prose. Objects survive; prose gets summarized away.

Required: `id`, `raisedBySkill`, `severity`, `description`, `raisedAt`. On close:
`resolvedAt`, `resolvingRole`, `resolutionNote`.

| Severity | Meaning | Who may resolve |
|---|---|---|
| `informational` | Recorded for context; no action gated on it | Any role |
| `attorney-review` | Work may continue; `{{ROLE_APPROVER}}` must see it before the affected item advances | `{{ROLE_REVIEWER}}` may triage; `{{ROLE_APPROVER}}` closes |
| `urgent` | Affected work stops until resolved | `{{ROLE_APPROVER}}` only |
| `jurisdictional-risk` | A right, defense, or deadline may already be at risk | `{{ROLE_APPROVER}}` only |

**Handling.**
- Raise on the spot. A flag deferred to the end of a session is a flag lost.
- Report every open flag at session open and session close, every time, even when the list is
  unchanged. Repetition is the feature.
- Never downgrade a severity you did not set. Propose the downgrade in a ledger entry and let
  the owning role decide.
- Never close a flag as a side effect of unrelated work.
- If the count of open flags at close is lower than at open with no matching resolution ledger
  entries, that is a defect — stop and reconcile before reporting.

Route to `{{ROLE_APPROVER}}` on sight: any question of case-type selection, jurisdiction or
venue, service method, scope change or scope-boundary dispute, whether a matter is a true
emergency, any safety indicator, any conflict question, and any assessment that a deadline has
been missed.

---

## DEGRADATION — ASSUME THE BUYER DOES NOT OWN EVERYTHING

Every cross-suite interaction degrades. It never errors and never silently omits.

| Situation | If installed | If not installed |
|---|---|---|
| A suite wants to record a stage completion | It writes `position` + ledger per the write contract | Command center writes on its behalf from what the suite reported, marking `writtenBy: "lal-command-center (on behalf)"` |
| A roadmap or case-plan skill exists | Read its stage vocabulary and mirror its phase labels | Use the canonical phase and stage list in `references/lifecycle-vocabulary.md` |
| A discovery or disclosure suite exists | Link its tracker by relative reference; do not duplicate its document log | Record only the disclosure **deadlines and stage state** here; note in the mirror that no document-level tracker is installed |
| A correspondence suite exists | Deadlines that require a letter get an owner and a ledger note pointing at it | Record the deadline and flag that the letter must be drafted outside the product |
| A calendaring integration to `{{PM_SYSTEM}}` exists | Note in each deadline that it was mirrored to `{{PM_SYSTEM}}`, with the date | Output a copy-paste deadline block for a human to enter, and flag that the dates live only in this file |
| The file connector cannot write | — | Emit the complete updated JSON block in the response, tell the operator exactly where to save it, and flag that the session's writes are unpersisted |
| The command center does not exist and the calling skill cannot create it | — | The calling skill emits its intended entry as a fenced JSON fragment labelled `PENDING COMMAND CENTER WRITE`, and proceeds. Nothing blocks on the file's absence |

An absent dependency is reported once, plainly, and then worked around. It is never the reason
a task fails.

---

## OUTPUT FORMAT

Two things, every time: the file write, and a short spoken report.

**The report — this shape, no longer than it needs to be:**

```
COMMAND CENTER — {{CLIENT_NAME}} | {{CASE_NO}} | as of {{DATE}}

POSITION
  Phase / Stage: [phase label] — [stage label]
  Scope:         [service model] · [billing basis] · attorney of record: [yes/no/limited]
  Path:          [resolution path] · discovery: [level]

DEADLINES — next 30 days
  [due date] · [label] · [authority] · owner [role] · [status]
  ⚠️ VERIFY: confirm rule and current text before relying on this.
  [jurisdictional / non-extendable dates called out explicitly]

OPEN FLAGS
  [severity] · [description] · raised [date] by [skill] · resolves with [role]

CHANGED THIS SESSION
  [one line per ledger entry written]

NOT INSTALLED
  [any suite whose absence changed how this ran — omit the section if none]
```

**Then state, in one line, what was written and where.** If nothing was written, say that too —
a session that changed state but wrote nothing is a defect.

---

## NON-NEGOTIABLES

- Appends only. No overwrite of any historical entry, ever.
- No fabricated field values. `null` plus a flag.
- No deadline without its authority and computation basis.
- No flag silently dropped, downgraded, or closed by a skill that did not raise it.
- No legal conclusion. This skill records; `{{ROLE_APPROVER}}` decides.
- No assumed storage provider. Everything through the file connector.
- Every rule and statute reference carries `⚠️ VERIFY: confirm rule and current text before
  relying on this.`
- No case law. Rules and statutes only.
- Log time for the session in `{{PM_SYSTEM}}` before closing. Unlogged work is invisible.

---

## REFERENCES

| File | Read it when |
|---|---|
| `references/schema.md` | You need field-by-field types, requiredness, and allowed values |
| `references/write-contract.md` | You are authoring another skill that writes here |
| `references/deadline-authorities.md` | You are creating a deadline object and need the authority and basis |
| `references/lifecycle-vocabulary.md` | You need the canonical phase, stage, and scope vocabulary |
