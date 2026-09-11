# Command Center Schema

Field-by-field definition of the per-matter state file. Version `1.0.0`.

Read this with `write-contract.md` — this file says what the fields *are*; that file says who
may write them.

**Conventions used below.**

- **Req** — `Y` required, `N` optional, `C` conditionally required (condition stated).
- A required field that is unknown is written as `null` **and** carries an open flag. `null`
  plus a flag is a task. A guessed value is a defect.
- All dates are `YYYY-MM-DD`. All timestamps are `YYYY-MM-DDTHH:MM` local, no timezone
  arithmetic performed by this skill.
- All `id` values are stable strings, never reused, never renumbered.
- Arrays are **append-only**. Removing or reordering an element is a schema violation.

---

## 0. TOP LEVEL

```json
{
  "schemaVersion": "1.0.0",
  "matter":   { },
  "scope":    { },
  "position": { },
  "deadlines": [ ],
  "ledger":    [ ],
  "flags":     [ ],
  "redFlags":  "",
  "provenance": { }
}
```

| Field | Type | Req | Meaning |
|---|---|---|---|
| `schemaVersion` | string, semver | Y | Schema this file conforms to. A reader that does not recognize the MAJOR version reads only, and flags. |
| `matter` | object | Y | Identity of the matter. § 1 |
| `scope` | object | Y | Scope of representation. § 2 |
| `position` | object | Y | Where the matter is. § 3 |
| `deadlines` | array of object | Y (may be empty) | Deadline register. § 4 |
| `ledger` | array of object | Y (min 1) | Append-only history. § 5 |
| `flags` | array of object | Y (may be empty) | Attorney flags. § 6 |
| `redFlags` | string | N | **Legacy compatibility only.** A free-text summary of urgent items, carried forward from the earlier roadmap context block. Readers may read it; writers must write `flags[]` instead. Never the only record of a flag. Deprecated — removed at schema `2.0.0`. |
| `provenance` | object | Y | Who created the file and with what. § 7 |

---

## 1. `matter`

| Field | Type | Req | Allowed values / format | Meaning |
|---|---|---|---|---|
| `client` | string | Y | — | Client name as it appears on the engagement document. Rendered as `{{CLIENT_NAME}}` in any generated document. |
| `caseNo` | string \| null | C | — | Required once a case exists. `null` pre-filing. Rendered as `{{CASE_NO}}`. |
| `matterType` | enum | Y | see below | The legal vehicle. |
| `matterPosture` | enum | N | `contested` · `uncontested` · `unknown` | Split out from `matterType` so the type enum stays stable. See Conflicts § A. |
| `clientRole` | enum | Y | `petitioner` · `respondent` · `movant` · `respondent-to-motion` · `intervenor` · `neutral` · `non-party-client` · `unknown` | Procedural posture of the client. Use the procedural role, not a party descriptor such as mother or father — those are facts about the case, not positions in it, and belong in the case file rather than the state schema. |
| `county` | string \| null | C | — | Filing county. Rendered as `{{COUNTY}}`. |
| `circuit` | string \| null | C | — | Judicial circuit. Rendered as `{{CIRCUIT}}`. |
| `division` | string \| null | N | — | Assigned division. `[CONFIRM LOCALLY: division practice and standing orders, with {{ROLE_APPROVER}}]` |
| `judge` | string \| null | N | — | Assigned judge or magistrate. Rendered as `{{JUDGE}}`. |
| `opposingCounsel` | string \| null | N | — | Or `"pro se"`. Rendered as `{{OPPOSING_COUNSEL}}`. |
| `minorChildren` | integer \| null | N | ≥ 0 | Count only. Names and dates of birth do not belong in the state file. |

**`matterType` allowed values** (ported unchanged from the earlier roadmap context block so
existing readers do not break):

`dissolution` · `paternity` · `modification` · `contempt` · `namechange` · `adoption` ·
`751` · `relocation` · `gal` · `injunction`

Two values are **added** because the earlier enum could not express them and the lifecycle
vocabulary requires them:

`mediation-neutral` — the firm is the mediator, not counsel for a party.
`advisory-only` — the engagement is coaching or document preparation with no matter vehicle of
the firm's own.

Anything not on this list is `null` plus a flag. Do not invent a value.

---

## 2. `scope`

Reconciled between the earlier retainer-driven list and the lifecycle vocabulary. See
Conflicts § B for the mapping.

| Field | Type | Req | Allowed values | Meaning |
|---|---|---|---|---|
| `serviceModel` | enum | Y | `full-representation` · `limited-scope` · `advice-and-counsel` · `document-preparation` · `neutral-mediator` · `neutral-gal` · `unknown` | The legally meaningful model. Determined by whether an attorney-client relationship exists and whether an appearance was entered — not by how the fee is structured. |
| `billingBasis` | enum | N | `hourly` · `flat` · `hybrid` · `not-recorded` | Fee structure. Orthogonal to `serviceModel`. Kept separate so a fee change does not read as a scope change. |
| `attorneyClientRelationship` | enum | Y | `yes` · `yes-advisory-only` · `no` · `unknown` | Whether an attorney-client relationship exists for this engagement. |
| `appearanceType` | enum | Y | `general` · `limited` · `none` · `unknown` | Whether an appearance was entered and of what kind. A limited appearance is a filed, party-signed notice — not an internal understanding. |
| `limitedPurpose` | string \| null | C | — | Required when `appearanceType` is `limited`. The proceeding or matter named in the notice, verbatim. |
| `scopeDocumentOnFile` | boolean | Y | — | Whether a signed scope document is in the file. `false` is a flag, always. |
| `scopeDocumentDate` | date \| null | C | — | Date of the operative signed scope document. |
| `courtAppearancesIncluded` | enum | Y | `yes` · `no` · `per-scope-document` · `unknown` | — |
| `discoveryIncluded` | enum | Y | `yes` · `no` · `partial` · `unknown` | — |
| `discoveryLevel` | enum | Y | `full` · `partial` · `minimal` · `none` · `unknown` | Ported unchanged. Planned depth, distinct from whether discovery is in scope. |
| `resolutionPath` | enum | Y | `litigation` · `mediation` · `uncontested` · `hybrid` · `tbd` | Ported; `hybrid` added because the source phase tables describe hybrid paths but the earlier enum had no value for one. |
| `outOfScopeStages` | array of string | N | stage ids | Stages consciously excluded. Populated for limited scope and advisory models. An empty array on a limited-scope matter is a flag. |

---

## 3. `position`

| Field | Type | Req | Allowed values | Meaning |
|---|---|---|---|---|
| `currentPhase` | enum | Y | `p1`…`p5` | Operational phase. See `lifecycle-vocabulary.md` § 1. Legacy `p1`/`p2`/`p3` files map forward per Conflicts § C. |
| `currentStage` | string | Y | a stage id from the canonical list | The one stage that is live. Exactly one. |
| `completedStages` | array of string | Y (may be empty) | stage ids | Append-only. A stage id appears at most once. |
| `stageEvidence` | object | N | `{ "<stageId>": "<evidence string>" }` | What confirms each completed stage. A stage completed by file-scan inference must have an entry here naming the file or folder. |
| `roadmapVersion` | string \| null | N | `vN` | Version of the external case plan this position was last reconciled against, if such a suite is installed. |
| `lastUpdated` | date | Y | — | Date of the most recent write of any kind. |
| `lastWrittenBy` | string | Y | skill name | Which skill performed the most recent write. |

`currentStage` **must not** appear in `completedStages`. If it does, that is a malformed write —
reconcile before any further writes.

---

## 4. `deadlines[]`

One object per deadline. This is the highest-consequence structure in the schema.

| Field | Type | Req | Allowed values / format | Meaning |
|---|---|---|---|---|
| `id` | string | Y | stable, unique | Never reused. |
| `label` | string | Y | — | Plain-language name a person recognizes on a calendar. |
| `authority` | string | Y | — | The rule, statute, or order that creates the deadline. Cite the instrument, not a summary of it. An order is cited as the order (title and date), not as the rule the order was entered under. |
| `authorityVerified` | enum | Y | `unverified` · `verified-by-role` | Starts `unverified`. Only `{{ROLE_REVIEWER}}` or `{{ROLE_APPROVER}}` may set `verified-by-role`, and only after reading current rule text. The verify warning is displayed regardless. |
| `computedFrom` | object | Y | § 4.1 | The triggering event. |
| `computationBasis` | string | Y | — | The counting rule actually applied, in enough detail to be re-checked: the stated period, whether it was under 7 days, how the last day was handled, and whether any days were added for the service method. Free text on purpose — a code cannot capture "last day fell on a clerk-observed closure." |
| `dueDate` | date \| null | Y | — | `null` only when `status` is `uncomputable`. |
| `internalDueDate` | date \| null | N | — | Firm-side working date, ordinarily earlier than `dueDate`. An internal control, not a legal date. Never substitute it for `dueDate`. |
| `jurisdictional` | enum | Y | `yes` · `no` · `unknown` | Whether missing it may forfeit a right, defense, or the court's ability to act. `unknown` requires a flag. |
| `extendable` | enum | Y | `yes` · `no` · `only-before-expiry` · `unknown` | Whether the period can be enlarged, and when. |
| `selfExecuting` | boolean | N | — | `true` where the consequence of missing it attaches automatically without any motion by the other side. Surfaces separately in reporting. |
| `ownerRole` | enum | Y | `{{ROLE_INTAKE}}` · `{{ROLE_DRAFTER}}` · `{{ROLE_REVIEWER}}` · `{{ROLE_APPROVER}}` · `client` | Role tokens only. Never a person. |
| `status` | enum | Y | `open` · `satisfied` · `extended` · `waived` · `missed` · `superseded` · `uncomputable` · `not-applicable` | See § 4.2. |
| `satisfiedBy` | string \| null | C | — | Required when `status` is `satisfied`. What discharged it, and its date. |
| `warnings` | array of date | N | — | The T-14 / T-7 / T-3 ladder. Internal control, not a rule requirement. |
| `mirroredTo` | string \| null | N | — | e.g. `"{{PM_SYSTEM}} on 2026-01-15"`. `null` means the date exists only in this file — report that. |
| `raisedBy` | string | Y | skill name | Which skill created the object. |
| `createdAt` | timestamp | Y | — | — |
| `notes` | string | N | — | Including any `[CONFIRM LOCALLY: …]` items that bear on the date. |

### 4.1 `computedFrom`

| Field | Type | Req | Meaning |
|---|---|---|---|
| `event` | string | Y | The triggering event, e.g. `"service of initial pleading on respondent"`. |
| `date` | date \| null | Y | Date of the triggering event. `null` forces `status: "uncomputable"`. |
| `serviceMethod` | enum \| null | C | `personal` · `portal-eservice` · `email` · `mail` · `hand-delivery` · `waiver` · `publication` · `not-applicable` · `unknown`. Required when the period runs from service, because the method can change the count. |
| `sourceDocument` | string \| null | N | The document that establishes the date — a return of service, a portal notification, an order. |

### 4.2 `status` semantics

| Value | Meaning | Required companion |
|---|---|---|
| `open` | Running. | — |
| `satisfied` | Discharged. | `satisfiedBy` |
| `extended` | A new period was granted. | A **new** deadline object; this one becomes `superseded` and the new one references it in `notes`. |
| `waived` | Consciously not pursued. | Ledger entry naming the deciding role. Only `{{ROLE_APPROVER}}` may set this. |
| `missed` | The date passed undischarged. | Flag at severity `urgent`, minimum. Never set silently. |
| `superseded` | Replaced by another deadline object. | `notes` naming the successor `id`. |
| `uncomputable` | Triggering date unknown. | Flag; `dueDate` is `null`. |
| `not-applicable` | Does not apply to this matter. | `notes` stating why. |

---

## 5. `ledger[]`

Append-only history of every state change. The ledger is the audit trail; if a state field
changed and the ledger does not say so, the write was malformed.

| Field | Type | Req | Allowed values | Meaning |
|---|---|---|---|---|
| `id` | string | Y | stable, unique | — |
| `timestamp` | timestamp | Y | — | When the entry was written. |
| `type` | enum | Y | `birth` · `stage-advance` · `stage-complete` · `stage-reopened` · `scope-change` · `deadline-added` · `deadline-status-change` · `flag-raised` · `flag-resolved` · `conflict` · `correction` · `note` · `closed` | — |
| `field` | string \| null | C | dotted path | The state field affected, e.g. `position.currentStage`. Required for any type that changes state. |
| `from` | string \| null | C | — | Prior value. `null` where none existed. Required for state changes. |
| `to` | string \| null | C | — | New value. Required for state changes. |
| `actorRole` | enum | Y | role token, or `system` | The role on whose authority the change was made. `system` only for automated inference at birth. |
| `trigger` | string | Y | — | What caused it. Use `inferred-from-file-scan` where nothing was witnessed — that phrase is load-bearing and must not be paraphrased. |
| `evidence` | string \| null | Y | — | The document, filing, order, or communication that supports it. `null` is permitted only for `note`, and only then. |
| `writtenBy` | string | Y | skill name | Which skill wrote the entry. `lal-command-center (on behalf)` where written for a suite that is not installed. |
| `correctsEntry` | string \| null | C | ledger id | Required for `correction`. |
| `narrative` | string | N | — | One or two sentences for a human. Never the only record of a change. |

`scope-change` entries additionally require, in `narrative`, whether a new signed scope
document exists and whether a docket notice is required — a scope change that alters the
attorney's role on the docket needs a corresponding filed notice, and that is an
`{{ROLE_APPROVER}}` decision.

---

## 6. `flags[]`

| Field | Type | Req | Allowed values | Meaning |
|---|---|---|---|---|
| `id` | string | Y | stable, unique | — |
| `raisedBySkill` | string | Y | skill name | Which skill raised it. Attribution matters — the raising skill knows why. |
| `severity` | enum | Y | `informational` · `attorney-review` · `urgent` · `jurisdictional-risk` | — |
| `description` | string | Y | — | What is wrong or undecided, specifically enough to act on without re-reading the file. |
| `requiredAction` | string | N | — | What must happen to clear it. |
| `blocksStage` | string \| null | N | stage id | The stage that must not advance while this is open. |
| `raisedAt` | timestamp | Y | — | — |
| `resolvedAt` | timestamp \| null | Y | — | `null` while open. |
| `resolvingRole` | enum \| null | C | role token | Required when `resolvedAt` is set. `urgent` and `jurisdictional-risk` may only carry `{{ROLE_APPROVER}}`. |
| `resolutionNote` | string \| null | C | — | Required when `resolvedAt` is set. What was decided or done. |
| `relatedDeadline` | string \| null | N | deadline id | — |

A flag object is never deleted. Resolution is the addition of three fields, not a removal.

---

## 7. `provenance`

| Field | Type | Req | Meaning |
|---|---|---|---|
| `createdAt` | timestamp | Y | When the file was born. |
| `createdBy` | string | Y | Skill that created it. |
| `createdFrom` | string | Y | What it was built from: `file-scan`, `operator-input`, `migrated`, or a combination. |
| `installedSuites` | array of string | N | Suites observed present at the most recent session. Used to explain degraded behaviour later. Best-effort, never authoritative. |
| `storageBackend` | enum | N | `local` · `project-upload` · `cloud-connector` · `unknown` | What the file connector resolved to. Recorded for troubleshooting only. No behaviour depends on it. |

---

## 8. CONFLICTS BETWEEN SOURCES — RESOLVED HERE

**A. Matter type granularity.** One source enumerated thirteen matter types including
contested/uncontested splits and a coaching type; the machine-readable context block in the
same source enumerated ten without those splits. Resolution: the ten-value enum is preserved
so existing readers do not break, contested/uncontested moves to `matterPosture`, and coaching
is expressed through `scope.serviceModel` rather than a matter type. Two values were added
(`mediation-neutral`, `advisory-only`) for engagements the ten-value enum could not express at
all.

**B. Service model taxonomy.** One source enumerated eight service models keyed to retainer
products, mixing legal model with fee structure (e.g. a flat-fee and an hourly variant of the
same limited-scope model appeared as two models). The lifecycle source enumerated six models
keyed to whether an attorney-client relationship exists and whether an appearance was entered,
and expressly flagged the taxonomy as unresolved between its own sources. Resolution: the
lifecycle taxonomy is canonical for `serviceModel`, and fee structure moves to `billingBasis`.
Mapping for anyone migrating a file written under the earlier list:

| Earlier value | `serviceModel` | `billingBasis` |
|---|---|---|
| Full Rep (Hourly) | `full-representation` | `hourly` |
| Limited Scope Flat | `limited-scope` | `flat` |
| Limited Scope Hourly | `limited-scope` | `hourly` |
| Coaching model | `advice-and-counsel` | as written |
| Non-attorney support services (flat or hourly) | `document-preparation` | as written |
| Single-document drafting, no review | `document-preparation` | `flat` |
| Single-document drafting with attorney review | `limited-scope` | `flat` |
| Single advisory session | `advice-and-counsel` | `flat` |
| Scope addendum | inherits from the original; write a `scope-change` ledger entry | inherits |

`[CONFIRM LOCALLY: how the installing firm classifies its own service offerings, with
{{ROLE_APPROVER}}]` — the lifecycle source is explicit that firms split this field differently
and that the installing firm must decide.

**C. Phase count.** One source used three phases; the lifecycle source described five
operational phases and, separately, a seventeen-stage table. Resolution: five phases are
canonical. Forward mapping for legacy files: `p1` → `p1`+`p2`, `p2` → `p3`, `p3` → `p4`+`p5`.
A migrated file records the mapping in a `correction` ledger entry rather than guessing which
half of a split phase it was in.

**D. Flags as string vs. objects.** The earlier context block carried a single `redFlags`
string. That cannot express severity, attribution, or resolution, and a string is trivially
lost in summarization. Resolution: `flags[]` objects are canonical; `redFlags` is retained
read-only for compatibility and is deprecated.

---

## 9. GAPS LEFT OPEN DELIBERATELY

These are recorded as gaps rather than filled with invented structure.

1. **No hearing or event calendar.** Deadlines are modelled; hearings, depositions, and
   mediation sessions are not. No source described a hearing object, and a deadline object is
   the wrong shape for an event that has a duration, a location, and attendees. A calendaring
   suite should own this. Until one exists, hearing dates are recorded as deadline objects
   whose `label` names the event, with `notes` carrying logistics.
2. **No party or contact records.** Only counts and procedural roles. Nothing in the sources
   supported a contact schema, and personal detail in a state file that many skills read is a
   confidentiality liability.
3. **No billing, trust, or time data.** `billingBasis` records the fee structure only. Amounts,
   balances, and time entries live in `{{PM_SYSTEM}}`.
4. **No document inventory.** Deliberately delegated. Where a discovery or disclosure suite is
   installed, its tracker owns document-level state and this file references it. Where one is
   not, only stage state and deadlines are recorded here — the gap is reported, not papered
   over with a half-built document log.
5. **No automated date arithmetic.** `computationBasis` is free text describing a computation a
   human performed or verified. The schema deliberately does not encode a computation engine;
   encoding one would imply the dates are calculated rather than recorded, and the counting
   rules turn on locally variable inputs such as clerk-observed closures.

---

## Pleading & Filing Log (added v1.1)

One row per FILED, SERVED, or RECEIVED court document — pleadings, notices, and
orders. **Drafts never appear here.** Per the filing-status rules (ambient), the
evidence of status is folder location, a file-stamp, or the user's statement —
the existence of a document in a drafts folder is not evidence of filing.

| Field | Type | Req | Notes |
|---|---|---|---|
| `date` | date | Y | Filing / service / entry date — never the draft date |
| `title` | string | Y | Document title as captioned |
| `type` | enum | Y | `pleading` · `motion` · `notice` · `order` · `judgment` · `discovery` · `other` |
| `direction` | enum | Y | `filed-by-us` · `filed-by-op` · `issued-by-court` · `served-on-us` · `served-by-us` · `received` |
| `status` | enum | Y | `submitted` · `accepted` · `served` · `entered` · `rejected` |
| `evidence` | string | Y | Folder location, stamp, portal confirmation, or "per [user]" |
| `responseDeadline` | date \| null | C | Computed from the correct trigger; flagged until attorney-confirmed |
| `linkedDeadlines` | list | N | IDs of deadline entries this document created |
| `notes` | string | N | Reserved rulings, partial grants, service method |

Write rules: order review and notice handling MUST write a row before their run
ends. Status transitions (`submitted` → `accepted` → `served`) update the row,
never duplicate it. A rejected filing keeps its row with status `rejected` and a
note — silence about rejections is how deadlines get missed.
