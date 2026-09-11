# Stage Evidence Map

How a matter that is **already underway** joins without losing context.

This is the table that makes a mid-stream matter usable. Without it, a matter opened halfway
through disclosure looks identical to a matter opened yesterday, and every downstream skill
starts from the wrong place.

---

## THE THREE RULES OF INFERENCE

Read these before using the table. They are what keep inferred state honestly weaker than
witnessed state.

**1. Presence proves; absence proves nothing.** A missing document may mean the stage did not
happen, or it may mean the file is incomplete. Infer completion from presence only. Where a
stage that logically should have occurred has no evidence at all, raise a flag at severity
`attorney-review` — do not infer in either direction.

**2. A scheduled event is not a completed stage.** A notice that something is set means it is
set. Only the record of the thing happening means it happened.

**3. Every inferred completion is labelled as inferred.** The ledger `trigger` is the exact
string `inferred-from-file-scan` — not a paraphrase — and
`position.stageEvidence["<stageId>"]` names the specific file or folder. A reader must be able
to tell circumstantial evidence from a witnessed event without asking.

**Stage ids are contract.** Use only ids from `lifecycle-vocabulary.md` § 2. If work is
evidenced that no stage id covers, record it as a flag describing the work. Never invent a
stage id, and never localize one.

---

## TABLE A — PRIMARY EVIDENCE MAP

Slot names are functional slots from the file connector's taxonomy, never folder names.

| # | Evidence found | Slot | Effect on `position` | `stageEvidence` string to record |
|---|---|---|---|---|
| 1 | Signed engagement or scope document | `engagement` | `engagement-scope` **complete** | name of the signed document and its date |
| 2 | Intake questionnaire or client information forms | `intake` | `intake-conflict-check` **complete only if** a documented conflict check is also present; otherwise no completion + flag | the intake document, and the conflict-check document if present |
| 3 | Documented conflict check | `intake` or `notes` | `intake-conflict-check` **complete** | the conflict-check record |
| 4 | Case assessment or strategy memorandum | `work-product-output` or `notes` | `case-assessment` **complete** | the memorandum |
| 5 | Filed petition, or filed answer where the client is the respondent | `filed-client` | `initial-pleadings` **complete** | the filed pleading |
| 6 | Return of service, affidavit of service, or filed waiver of service | `filed-client` | `service` **complete** | the return, affidavit, or waiver |
| 7 | Answer, affirmative defenses, or counterpetition on file (either party) | `filed-client` / `filed-opposing` | `responsive-pleadings` **complete** | the responsive pleading and which party filed it |
| 8 | Organized production documents present for the client | `disclosure-client` | `mandatory-disclosure` **in progress — no completion** | the slot and an approximate document count |
| 9 | Disclosure or production tracker | `notes` | `mandatory-disclosure` **in progress — no completion** | the tracker file |
| 10 | Client financial affidavit | `disclosure-client` or `filed-client` | `mandatory-disclosure` **in progress — no completion** | the affidavit and its date |
| 11 | Financial-affidavit cross-check or reconciliation work product | `work-product-output` | `mandatory-disclosure` **in progress — no completion** | the cross-check document |
| 12 | Income analysis work product | `work-product-output` | `mandatory-disclosure` **in progress — no completion** | the analysis document |
| 13 | Opposing party financial affidavit | `disclosure-opposing` | `mandatory-disclosure` **in progress** — records that the other side produced; **no completion** | the affidavit and its date |
| 14 | Review of the opposing party's production | `work-product-output` | `discovery` **in progress — no completion** | the review document |
| 15 | **Filed certificate of compliance** | `filed-client` | `mandatory-disclosure` **complete** | the filed certificate and its filing date |
| 16 | Served interrogatories, requests to produce, subpoenas, or a discovery gap analysis | `discovery-served` or `work-product-output` | `discovery` **in progress — no completion** | what was served, on whom, and when |
| 17 | Asset-and-liability schedule or distribution chart work product | `work-product-output` | **No stage completion.** Informational only | the chart, recorded as a note |
| 18 | Support-guideline worksheet work product | `work-product-output` | **No stage completion.** Informational only | the worksheet, recorded as a note |
| 19 | Executed settlement agreement, full or partial | `orders-agreements-reports` | `mediation` **complete**, with the resolution recorded. An unsigned draft is **no completion** | the agreement, whether executed, and whether full or partial |
| 20 | Signed final judgment | `orders-agreements-reports` or `filed-client` | `final-judgment` **complete** | the judgment and its entry date |

Rows 17 and 18 are deliberately non-advancing. Analytical work product proves someone did
analysis; it does not prove a lifecycle stage closed. Recording it as a completion would
overstate the file's position, which is the exact failure this table exists to prevent.

---

## TABLE B — REMAINING LIFECYCLE ROWS

Sourced from `lifecycle-vocabulary.md` § 6 and reproduced here so a scan covers all seventeen
stages. Where the two files ever disagree, `lifecycle-vocabulary.md` controls.

| Evidence found | Effect |
|---|---|
| Filed motion for temporary relief, or an order on one | `temporary-relief` **complete** |
| Case management order | `case-management-conference` **complete** |
| Expert engagement, evaluation order, or social investigation order | `experts-evaluations` **complete** |
| Notice of mediation | `mediation` **scheduled — no completion** |
| Neutral's report of outcome | `mediation` **complete** |
| Pretrial stipulation, witness list, or exhibit list | `pretrial` **complete** |
| Trial order with a set date | `pretrial` **in progress.** Do **not** infer `trial` |
| Retirement order, executed deed, or income deduction order | `post-judgment-compliance` **in progress** |
| Approved closing letter | `file-closing` **complete** |

---

## WHICH STAGE IS LIVE

Exactly one stage is `position.currentStage`, and it must not also appear in
`completedStages`.

```
1. Take the highest-ordered completed stage from lifecycle-vocabulary.md § 2.
2. currentStage is the next stage in that order that is NOT in
   scope.outOfScopeStages.
3. If any row produced an "in progress" result for a stage that is not complete,
   that stage is currentStage instead — in-progress evidence beats sequence order.
4. If nothing at all was inferred, currentStage is intake-conflict-check.
5. If two in-progress stages compete, do not choose. Set currentStage to the
   earlier one and raise a flag at severity attorney-review naming both, with the
   evidence for each.
```

Stages are not strictly linear. Disclosure reopens; temporary relief recurs. Where a stage
resumes after being marked complete, that is a `stage-reopened` ledger entry — never a removal
from `completedStages`.

---

## OUT-OF-SCOPE STAGES

If an inferred stage appears in `scope.outOfScopeStages`, **do not record the completion.**
Raise a flag at severity `attorney-review` describing the out-of-scope work found in the file
instead. Silently recording out-of-scope work as completed blurs whether an attorney-client
relationship exists for that task, which is precisely what documented scope exists to prevent.

⚠️ VERIFY: confirm rule and current text before relying on this. This map infers workflow
position from documents present in a file. It does not verify that any document is sufficient,
timely, or correct — those are `{{ROLE_APPROVER}}` questions.
