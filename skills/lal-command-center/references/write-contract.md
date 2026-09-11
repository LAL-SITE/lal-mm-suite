# The Command Center Write Contract

**Read this if you are authoring a skill that writes to the command center.** It is
self-contained: you can comply without reading `schema.md` end to end. Consult `schema.md`
only for the exact field list of an object you are creating.

The command center is the one place the whole product line agrees on state. Every suite reads
it and several write it. That only works if every writer obeys the same six rules.

---

## THE SIX RULES

### 1. Append. Never overwrite.

There is no update-in-place operation. To change a state value you write the new value **and**
append a ledger entry recording `from`, `to`, `actorRole`, `trigger`, and `evidence`. The prior
value survives in the ledger.

To add a deadline, flag, or ledger entry, append the object. Never renumber ids, never compact
arrays, never remove an element. A resolved flag keeps its object and gains three fields.

**A state change with no matching ledger entry is a malformed write.** If you cannot describe
the trigger and the evidence, you are not ready to write.

### 2. Write only the fields you own.

You write the fields your own work produces. You do not write fields another skill owns, even
when you can see they are wrong — for that, see rule 4.

| Field group | Written by |
|---|---|
| `matter.*` | Intake / matter-opening skills, and the command center at birth |
| `scope.*` | Engagement, scope, and closing skills. Nobody else, ever. A discovery or drafting skill that believes scope changed raises a flag; it does not edit `scope`. |
| `position.currentStage`, `position.completedStages`, `position.stageEvidence` | Whichever skill actually completed the work, or the command center on its behalf |
| `position.currentPhase` | The command center only, derived from the stage |
| `position.roadmapVersion` | A case-plan or roadmap skill, if installed |
| `deadlines[]` | Any skill that computes or discharges a deadline in its own lane |
| `deadlines[].status` → `waived` | `{{ROLE_APPROVER}}` decisions only |
| `deadlines[].authorityVerified` → `verified-by-role` | `{{ROLE_REVIEWER}}` or `{{ROLE_APPROVER}}` only |
| `ledger[]` | Every writer, on every write |
| `flags[]` — raising | Any skill |
| `flags[]` — resolving | Only per the severity table in rule 5 |
| `redFlags` | Nobody. Read-only legacy field. Write `flags[]`. |
| `provenance.*` | The command center only |

If your write needs a field not in this table, it is not in the schema. Do not add one. Raise a
flag describing what you needed and stop — an invented field is invisible to every other
reader and is a silent data loss.

### 3. Re-read immediately before you write.

The file may have changed since you read it at session open.

1. Re-read the file.
2. Re-base your append on the current content.
3. Write.

Never assemble a whole file from a stale read and save it. That is how an append becomes an
overwrite and how another suite's flag disappears.

### 4. On conflict, do not win. Report.

If a field you are about to write already holds a different value, and you were not the skill
that set it:

- **Leave the existing value alone.**
- Append a ledger entry of type `conflict` carrying your value, your evidence, and the existing
  value.
- Raise a flag naming both values, both sources, and which one your work assumed.

Two suites disagreeing about the current stage is information. Silently resolving it destroys
the information and leaves whichever suite was right operating on a value it did not write.

The one exception: you may overwrite a value **you** wrote earlier in the same session, and only
by way of a `correction` ledger entry naming the entry you are correcting.

### 5. Never drop a flag.

- Raise it the moment you find it, not at the end of your run.
- You may not close a flag you did not raise unless the severity table permits your role.
- You may not lower a severity you did not set. Propose the change in a ledger entry and leave
  the flag open.
- You may not close a flag as a side effect of unrelated work.

| Severity | May be closed by |
|---|---|
| `informational` | Any role |
| `attorney-review` | `{{ROLE_REVIEWER}}` may triage; `{{ROLE_APPROVER}}` closes |
| `urgent` | `{{ROLE_APPROVER}}` only |
| `jurisdictional-risk` | `{{ROLE_APPROVER}}` only |

Before you finish, compare the count of open flags at the start of your run against the count at
the end. If it dropped without matching `flag-resolved` ledger entries, stop and reconcile.

### 6. Never fabricate a value.

An unknown required field is `null` plus a flag. `null` plus a flag is a task someone will
complete. A plausible guess is a defect that every downstream suite inherits and nobody can
detect.

This applies hardest to dates. A deadline whose triggering date you do not know is written with
`dueDate: null` and `status: "uncomputable"`, plus a flag. It is never estimated.

---

## WRITING A DEADLINE — THE MINIMUM BAR

A deadline is the only object in this schema whose defect is potentially malpractice. Nine
fields are non-negotiable:

| Field | What it must contain |
|---|---|
| `id` | Stable, unique, never reused |
| `label` | What a person would call it on a calendar |
| `authority` | The rule, statute, or **order** that creates it — the instrument, not a paraphrase. Where an order sets the date, cite the order; the order controls over the rule default. |
| `computedFrom` | `event`, its `date`, the `serviceMethod`, and the document that establishes the date |
| `computationBasis` | The counting rule you actually applied, in enough detail to be re-checked by someone else |
| `dueDate` | The date, or `null` with `status: "uncomputable"` |
| `jurisdictional` | `yes` / `no` / `unknown` — and `unknown` requires a flag |
| `extendable` | `yes` / `no` / `only-before-expiry` / `unknown` |
| `ownerRole` | A role token. Never a person's name. |

**`computationBasis` is the field people skip. Do not skip it.** "45 days" is not a
computation basis. What it must record: the stated period; whether the period was under seven
days (which changes whether intervening weekends and holidays count); how the last day was
handled if it fell on a weekend, a legal holiday, or a clerk-observed closure; and whether any
days were added for the service method. A date without a recorded basis cannot be audited, and
an unauditable jurisdictional date is worse than no date at all.

**Every deadline you write carries, wherever it is displayed:**

> ⚠️ VERIFY: confirm rule and current text before relying on this.

**Never restatus a deadline to `missed` silently.** `status: "missed"` requires a flag at
severity `urgent` or higher and a ledger entry. Whether it can be cured is an
`{{ROLE_APPROVER}}` decision, not yours.

---

## WRITING A STAGE COMPLETION

```
1. Confirm the stage id exists in lifecycle-vocabulary.md. Do not invent stage ids.
2. Append the id to position.completedStages (once — check it is not already there).
3. Add position.stageEvidence["<stageId>"] naming what confirms it.
4. Set position.currentStage to the next live stage.
5. Append TWO ledger entries: stage-complete for the finished stage,
   stage-advance for the new one.
6. Leave position.currentPhase alone — the command center derives it.
```

If you inferred the completion from a file scan rather than witnessing it, `trigger` must be the
exact string `inferred-from-file-scan`. That phrase is load-bearing; it is how a reader knows
the evidence is circumstantial. Do not paraphrase it.

If the stage you completed is listed in `scope.outOfScopeStages`, do not record the completion.
Raise a flag at severity `attorney-review` describing the out-of-scope work instead. Silently
performing out-of-scope work blurs whether an attorney-client relationship exists for that
task — which is exactly what documented scope exists to prevent.

---

## WRITING A SCOPE CHANGE

Only engagement, scope, and closing skills. If that is not you, raise a flag.

```
1. Supersede the affected scope.* fields.
2. Append a ledger entry of type scope-change.
3. In narrative, state (a) whether a new signed scope document exists, and
   (b) whether the change alters the attorney's role on the docket.
4. If (a) is no, or (b) is yes, raise a flag at severity attorney-review — a scope
   change that alters the docket role requires a corresponding filed notice, and that
   is an {{ROLE_APPROVER}} decision.
```

Scope expansion is legitimate and normal. It is done formally or not at all.

---

## IF THE COMMAND CENTER DOES NOT EXIST

This is the case authors get wrong most often. **Nothing ever blocks on the file's absence.**

| Your situation | What to do |
|---|---|
| The command center skill is installed | Invoke it. It births the file, then you write normally. |
| Not installed, but you can write files | Create `COMMAND-CENTER.md` in the matter's working location with the minimum viable shape: `schemaVersion`, `matter` (whatever you know, `null` elsewhere), `scope` (`unknown` values are legitimate here), `position`, empty `deadlines` and `flags`, one `ledger` entry of type `birth` with `createdFrom: "<your skill name>"`, and `provenance`. Flag every `null` required field. Then write your own entry. |
| Not installed and you cannot write files | Emit your intended entry in your own output as a fenced `json` fragment headed **`PENDING COMMAND CENTER WRITE`**, tell the operator where it should be saved, and continue your task. Do not fail, and do not drop the entry. |

Same principle in the other direction: if you need a value the command center does not have, use
your own defaults, say plainly in your output that you did so, and raise a flag. Never stall a
task waiting on state.

---

## STORAGE

Read and write through the file connector abstraction. Do not assume a provider. The same file
must work on a local folder, a project upload area, `{{DMS}}`, or any cloud drive. Never
hard-code a path, a drive, a site, or a URL.

If the connector cannot write, emit the complete updated JSON block in your response, tell the
operator exactly where to save it, and flag that the session's writes are unpersisted. A write
you believed succeeded and did not is worse than one you reported as failed.

---

## SELF-CHECK BEFORE YOU FINISH

Nine questions. A `no` to any of them means your write is not compliant.

1. Did every state change get a matching ledger entry with `from`, `to`, `actorRole`, `trigger`,
   and `evidence`?
2. Did I write only fields I own?
3. Did I re-read the file immediately before writing?
4. Is every array still append-only — no removals, no renumbering, no reordering?
5. Does every deadline I wrote carry its authority, its `computedFrom`, and a real
   `computationBasis`?
6. Is every date I wrote traceable to a source document, with nothing estimated?
7. Are all flags I found still open unless my role was permitted to close them, and is the open
   count reconciled?
8. Is every required field either populated or `null`-with-a-flag — with nothing guessed?
9. Did I report, in my own output, what I wrote and where?
