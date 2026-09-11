---
name: lal-start-case
description: "First touch on a matter. Use on any new, transferred, or in-progress matter to scan the file, infer what already happened, and birth the command center. Runs once per matter, before other skills."
---

# Start Case — First-Touch Scan

## When to use this skill (full trigger reference)

First touch on a matter. Scans the matter file through the file connector, infers from the documents present what has already happened, and births the matter command center with that state — so a matter already halfway through disclosure joins without losing context. Runs once per matter, before any other skill works on it. Use IMMEDIATELY on: "new matter", "new client", "set up this matter", "start the case file", "open a case", "the matter folder is ready", "initialize this matter", "we're taking over this case", "this file came from another firm", "the case is already underway", "what's already been done on this file", "scan the file and tell me where we are", or any request to initialize, adopt, or take stock of a matter for the first time. Reads and writes only through the file connector. Writes state only through the command center write contract; never invents a field, never guesses a fact.

One job, and it ends cleanly: **scan the matter file, infer what is already done, birth the
command center. Stop there.**

The value is adoption. A matter that has been running for eight months, or that arrived from
another firm, or that predates the software, must be able to join at its real position — not
at the beginning. Everything in this skill exists to establish that position from evidence and
record it honestly.

This skill decides nothing legal. It reads documents, infers workflow position, and routes
every judgment call to `{{ROLE_APPROVER}}`.

**Fires once per matter.** Re-running it on a matter that already has a command center is a
reconciliation, not a birth — see § 7.

---

## STEP 1 — RESOLVE THE MATTER FILE

Call the file connector, Operation 1.

The connector handles the provider. This skill never learns which provider is bound, never
receives a path, and never prints a location into any document.

**If the connector resolves the matter root** — proceed to Step 2.

**If the connector reports more than one candidate** — the connector asks; wait for the answer.
Do not choose.

**If the connector reports zero candidates** — stop and report:

> I cannot find this matter's file in your storage. Confirm with `{{ROLE_INTAKE}}` that the
> matter has been opened in `{{PM_SYSTEM}}` and that its folder exists, or tell me where it
> lives and I will use that.

**If the connector is unbound or storage is unreachable** — do not stop. Ask the operator to
attach or paste what exists, and run the whole scan against that instead. Say once that the
scan covers only what was provided, and flag every conclusion drawn from a partial file.

Once resolved, ask the operator to record the location where the connector suggests, so future
sessions do not repeat the lookup.

---

## STEP 2 — FULL SCAN

Call the file connector, Operation 2, **Mode A (full scan)**. This is one of the few callers
entitled to a full scan.

Read the returned inventory carefully. **This inventory is the evidence base for everything
below.** Note in particular:

- Which functional slots are populated, which are empty, and which are unmapped.
- Whether the `work-product-output` slot already has files. If it does, this is **not** a new
  matter — it is a returning or migrated one.
- Whether any timestamps came back `unavailable`. If they did, recency-based conclusions are
  unavailable and must not be improvised.

---

## STEP 3 — EXTRACT CASE BASICS FROM THE FILE

**Read before you ask.** Every fact recoverable from the file is a question the operator does
not have to answer.

### What each slot tells you

| Slot | What its contents establish |
|---|---|
| `engagement` | Service model, fee basis, contracted scope, signature date |
| `intake` | Client details, opposing party, whether minor children exist, screening concerns |
| `identification` | Client identity confirmation |
| `filed-client` | What has been filed for the client — petition, answer, motions, certificates |
| `filed-opposing` | What the opposing party has filed — answer, counterpetition, motions |
| `orders-agreements-reports` | Entered orders, executed agreements, neutral and expert reports |
| `disclosure-client` | Whether the client's production exists, and how far along it is |
| `disclosure-opposing` | Whether the opposing party has produced |
| `discovery-served` | Whether formal discovery has been served, and by whom |
| `notices` | What is set — hearings, mediation, depositions |
| `hearings` | Past and upcoming hearing materials |
| `filed-pending` | Anything submitted but not accepted — a live loose end |
| `work-product-output` | Prior generated work. Non-empty means the matter is not new |

### Documents to read in full

Call the connector, Operation 3, on:

1. The signed engagement or scope document.
2. The intake questionnaire.
3. The most recent filed pleading, either party.
4. Every entered order.
5. Any executed agreement.

Extract, and record where each came from:

- client name; procedural role; opposing party; whether opposing counsel appears or the party
  is unrepresented
- matter type; county; circuit; division; assigned judge or magistrate; case number
- service model; fee basis; contracted scope; whether court appearances are included; whether
  disclosure and discovery are included
- count of minor children
- what the orders require, and of whom
- any date any document states

**Never infer a fact the documents do not state.** An unknown is a gap. A gap is `null` plus a
flag — never a plausible-looking value. This is the single most consequential rule in this
skill: a guessed county, judge, or service date propagates into every downstream suite and
nobody can detect it later.

---

## STEP 4 — ASK ONLY FOR WHAT IS MISSING

Ask **once**, in one organized block. Not one question per turn.

Gaps the file usually cannot close:

- which person fills `{{ROLE_APPROVER}}` on this matter
- anticipated resolution path, where no pleading or order reveals it
- scope promised in conversation but absent from the signed document — a discrepancy to raise,
  not to resolve
- known concerns not yet documented anywhere in the file
- a deadline the operator knows about for which no document exists

For every gap the operator leaves unanswered: write `null` and raise a flag. Do not ask twice
and do not stall. **Nothing in this skill blocks on an unanswered question.**

If the file closed every gap, say so and move on:

> The matter file gave me everything I need. Proceeding to record position.

---

## STEP 5 — DETERMINE WHAT IS ALREADY COMPLETE

Apply `references/stage-evidence-map.md` to the inventory from Step 2.

That reference is the mechanism by which a mid-stream matter joins at its real position. It
carries the full evidence table, the three rules of inference, the rule for selecting which
stage is live, and the handling for out-of-scope stages. Follow it exactly.

Three points carry over into the write:

- **Stage ids come only from `lifecycle-vocabulary.md` § 2.** Never invent, never localize.
- **Every completion inferred here is written with `trigger: "inferred-from-file-scan"`** —
  that exact string, unparaphrased — and a matching `position.stageEvidence` entry naming the
  file or folder.
- **In-progress evidence does not complete a stage.** It selects `currentStage`.

---

## STEP 6 — BIRTH THE COMMAND CENTER

This is the deliverable. Comply with the command center write contract exactly.

### 6.1 Route by what is installed

| Situation | What to do |
|---|---|
| **`lal-command-center` is installed** | Invoke it and pass the state assembled above. It births the file and derives `position.currentPhase`. Do not write `position.currentPhase` yourself. |
| **Not installed, but the connector can write** | Create `COMMAND-CENTER.md` in the matter's working location with the minimum viable shape below. Derive `currentPhase` from `currentStage` per `lifecycle-vocabulary.md` § 2, state in the birth ledger entry that this skill derived it for schema validity, and raise an `informational` flag for reconciliation when the command center is installed. |
| **Not installed and the connector cannot write** | Emit the complete JSON block in your own output under the heading **`PENDING COMMAND CENTER WRITE`**, tell the operator exactly where to save it, and finish the task. Do not fail, and do not drop the content. |

### 6.2 The shape

Only fields defined in `schema.md`. **If a value you need has no field, it is not in the
schema — raise a flag describing what you needed and stop. Never add a field.**

```json
{
  "schemaVersion": "1.0.0",
  "matter": {
    "client": "{{CLIENT_NAME}}",
    "caseNo": null,
    "matterType": null,
    "matterPosture": "unknown",
    "clientRole": "unknown",
    "county": null,
    "circuit": null,
    "division": null,
    "judge": null,
    "opposingCounsel": null,
    "minorChildren": null
  },
  "scope": {
    "serviceModel": "unknown",
    "billingBasis": "not-recorded",
    "attorneyClientRelationship": "unknown",
    "appearanceType": "unknown",
    "limitedPurpose": null,
    "scopeDocumentOnFile": false,
    "scopeDocumentDate": null,
    "courtAppearancesIncluded": "unknown",
    "discoveryIncluded": "unknown",
    "discoveryLevel": "unknown",
    "resolutionPath": "tbd",
    "outOfScopeStages": []
  },
  "position": {
    "currentPhase": "p1",
    "currentStage": "intake-conflict-check",
    "completedStages": [],
    "stageEvidence": {},
    "roadmapVersion": null,
    "lastUpdated": "{{DATE}}",
    "lastWrittenBy": "lal-start-case"
  },
  "deadlines": [],
  "ledger": [],
  "flags": [],
  "provenance": {
    "createdAt": "{{DATE}}T00:00",
    "createdBy": "lal-start-case",
    "createdFrom": "file-scan",
    "installedSuites": [],
    "storageBackend": "unknown"
  }
}
```

Every value above is the **unknown** state. Replace only what Steps 3 to 5 actually
established, and leave the rest as written — each remaining `null` or `unknown` gets a flag per
§ 6.5. Populate `provenance.storageBackend` from what the connector reports, and
`provenance.installedSuites` with the suites observed this session — best-effort, never
authoritative.

`redFlags` is not written. It is read-only legacy. Flags go in `flags[]`.

### 6.3 The birth ledger entry

One entry, always first:

```json
{
  "id": "led-0001",
  "timestamp": "{{DATE}}T00:00",
  "type": "birth",
  "field": null,
  "from": null,
  "to": null,
  "actorRole": "system",
  "trigger": "first-touch scan of the matter file",
  "evidence": "full inventory of <N> files across <N> folders",
  "writtenBy": "lal-start-case",
  "correctsEntry": null,
  "narrative": "Command center created from a first-touch file scan. Position inferred from documents present."
}
```

`actorRole: "system"` is permitted here and only here — automated inference at birth.

### 6.4 Stage completions

For every stage the evidence map marked complete:

```
1. Confirm the stage id exists in lifecycle-vocabulary.md § 2.
2. Append it to position.completedStages — once. Check it is not already there.
3. Add position.stageEvidence["<stageId>"] naming the file or folder.
4. Append TWO ledger entries: stage-complete for it, and stage-advance for the
   stage that becomes live.
5. trigger on every one of them is exactly: inferred-from-file-scan
6. Leave position.currentPhase to the command center where it is installed.
```

`currentStage` must never also appear in `completedStages`. Check before you finish.

### 6.5 Flags to raise at birth

Raise each the moment you find it, not at the end.

| Condition | Severity |
|---|---|
| Any required field written as `null` or `unknown` | `informational`, naming the field and who can supply it |
| `scope.scopeDocumentOnFile` is `false` | `attorney-review` — always. A matter running without a signed scope document in the file is a scope and fee exposure |
| A stage that logically should have occurred has no evidence either way | `attorney-review` |
| Two in-progress stages compete for `currentStage` | `attorney-review`, naming both and the evidence for each |
| Inferred work appears in `scope.outOfScopeStages` | `attorney-review`, describing the out-of-scope work. **Do not record the completion** |
| Anything in `filed-pending` | `attorney-review` — something was submitted and not accepted |
| A date appears in a document but this skill did not compute a deadline from it | `attorney-review`, quoting the date and its source document |
| Contracted scope in the signed document differs from what the operator described | `attorney-review` |
| Any safety, jurisdictional, or conflict indicator visible in the file | `urgent` — and route to `{{ROLE_APPROVER}}` on sight |

### 6.6 Deadlines — what this skill does not do

**`deadlines[]` is written empty.** Computing a deadline requires an authority, a
`computedFrom` event with its service method and source document, and a real
`computationBasis` — and a deadline is the one object in the schema whose defect is potentially
malpractice.

This skill records dates it *saw*, as flags quoting the date and naming the document. It does
not compute, does not estimate, and does not convert an observed date into a deadline object.
The command center or a calendaring lane owns that.

Every deadline anyone later derives from those flags carries, wherever displayed:

> ⚠️ VERIFY: confirm rule and current text before relying on this.

### 6.7 Before you finish

Re-read the file immediately before writing, re-base on current content, then write. Then
check all nine:

1. Every state change has a matching ledger entry with `from`, `to`, `actorRole`, `trigger`,
   `evidence`.
2. Only fields this skill owns were written — `matter.*`, `scope.*` at birth, `position` stage
   fields, `ledger[]`, `flags[]`, `provenance` where the command center is not installed.
3. The file was re-read immediately before the write.
4. Every array is append-only.
5. `deadlines[]` is empty, or every object in it carries authority, `computedFrom`, and a real
   `computationBasis`.
6. Every date written traces to a source document. Nothing estimated.
7. Every flag raised is still open. Open count reconciled.
8. Every required field is populated or `null`-with-a-flag. Nothing guessed.
9. What was written, and where, is reported in your own output.

---

## STEP 7 — REPORT, AND STOP

Report in plain text — this is a status report, not a document:

```
MATTER FILE SCANNED — {{DATE}}
Files: <N> across <N> folders | Slots populated: <N> of <N> | Timestamps: available | unavailable

POSITION RECORDED
  Current stage:      <stage id> — <label>
  Completed stages:   <list, or "none inferred">
  All completions above were inferred from the file scan, not witnessed.

OPEN FLAGS RAISED
  <severity> — <description>
  …

GAPS LEFT OPEN
  <field> — needs <role token>
  …

COMMAND CENTER
  Written | Emitted for manual save | Handed to lal-command-center
  Deadlines: none computed by this skill. <N> observed dates raised as flags.
```

Then stop.

### Where this skill ends

Core's first touch ends at a birthed command center holding an evidence-backed position. That
is the deliverable, and it is complete on its own — every other Core skill can work from it
immediately.

Narrative case summaries, case plans, onboarding checklists, and generated instruction blocks
are **not part of Core** and are not produced here. If a suite that owns those is installed,
hand it the command center and let it take over. If none is installed, say plainly that the
command center is the deliverable and that nothing is missing from Core's side.

Either way: never error, never silently omit, and never produce a partial imitation of
something another suite owns.

### If the matter already has a command center

Do not birth a second one and do not overwrite. Read it, compare it to what the scan shows,
and:

- Where they agree — report agreement and stop.
- Where they differ — **leave the existing value alone.** Append a `conflict` ledger entry
  carrying your value, your evidence, and the existing value, and raise a flag naming both
  values, both sources, and which one your scan assumed. Two readings of the same file
  disagreeing is information; silently resolving it destroys the information.

---

## RULES THAT ALWAYS APPLY

- **Fires once per matter.** After that it reconciles, never re-births.
- **Read before you ask.** Then ask once, in one block.
- **Never fabricate.** `null` plus a flag is a task someone completes. A plausible guess is a
  defect every downstream suite inherits and nobody can detect.
- **Inference stays visibly weaker than observation.** `inferred-from-file-scan`, exactly.
- **Never invent a schema field or a stage id.**
- **No storage plumbing in any output.** No provider name, path, drive, site, tenant, or link
  is written into a document. Documents carry `{{CLIENT_NAME}}`, `{{CASE_NO}}`, `{{COUNTY}}`,
  `{{CIRCUIT}}`, `{{JUDGE}}`, `{{OPPOSING_COUNSEL}}`, `{{DATE}}`, and the firm's own install
  tokens.
- **No scope document in the file is always a flag.**
- **Route to `{{ROLE_APPROVER}}` on sight:** any safety, domestic violence, or dependency
  indicator; any jurisdictional or interstate question; any conflict question; any scope
  discrepancy; any assessment that a date may have been missed.
- **Nothing produced here is filed, served, or sent.** `{{ROLE_APPROVER}}` decides that.

`[CONFIRM LOCALLY: division practice, standing orders, and how the assigned division expects a newly adopted file to be presented, with {{ROLE_APPROVER}}]`

⚠️ VERIFY: confirm rule and current text before relying on this. This skill records where a
matter stands. It does not verify that anything in the file was timely, sufficient, or correct.
