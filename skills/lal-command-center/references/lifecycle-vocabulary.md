# Lifecycle Vocabulary

The canonical, firm-neutral phase, stage, and scope vocabulary for `position.*` and `scope.*`.
Sourced from the neutralized case-lifecycle-and-scope module of the Florida family law reference.

**Stage ids are contract.** Other suites match on them. Do not rename, do not invent, do not
localize. A stage that does not appear here is not a stage — raise a flag describing the work
instead.

**Roles are functional, never titles.** A buying firm's org chart is not the source firm's org
chart, so a job title is as wrong as a person's name. Four role tokens, mapped to real people
once, at install:

| Token | Function |
|---|---|
| `{{ROLE_INTAKE}}` | First contact and screening |
| `{{ROLE_DRAFTER}}` | Prepares work product |
| `{{ROLE_REVIEWER}}` | Reviews before it reaches the attorney |
| `{{ROLE_APPROVER}}` | Signs, files, appears, decides |

---

## 1. PHASES

Five operational phases. **Every service model runs through all five** — what changes between
models is the *content* of phase 3, not the existence of the phases.

| id | Label | Covers |
|---|---|---|
| `p1` | Inquiry, screening and intake | First contact through conflict clearance |
| `p2` | Case setup and initial strategy | Engagement, matter opening, assessment, initial pleadings |
| `p3` | Active case work | Service, responsive pleadings, temporary relief, disclosure, discovery, case management, experts |
| `p4` | Resolution | Mediation, pretrial, trial, final judgment |
| `p5` | Finalization and closing | Post-judgment compliance and file closing |

`position.currentPhase` is derived by the command center from `position.currentStage`, not
written independently. See § 2 for the mapping.

The same arc read as **legal posture** rather than workflow: intake determines posture → initial
filings establish subject-matter jurisdiction and start the clock → service creates personal
jurisdiction → disclosure and discovery drive money outcomes and credibility → motion practice
clears what is blocking progress → case management → mediation → hearings → trial → final
judgment with required statutory findings → post-judgment enforcement and appeals. Use the
posture view to see what must legally happen next; use the phase view to know which workflow is
live.

---

## 2. STAGES

Seventeen stages. `owner` is the role that owns the stage, not the only role that touches it.
`gate` is what must be true before the matter advances past it.

| id | Phase | Label | Owner | Gate to clear |
|---|---|---|---|---|
| `intake-conflict-check` | `p1` | Intake and conflict check | `{{ROLE_INTAKE}}` | Conflict check clear and documented; case type, jurisdiction, and venue answered |
| `engagement-scope` | `p2` | Engagement and scope definition | `{{ROLE_INTAKE}}` → `{{ROLE_APPROVER}}` | Signed scope document in the file; service model recorded on the matter |
| `case-assessment` | `p2` | Case assessment and issue spotting | `{{ROLE_APPROVER}}` decides, `{{ROLE_DRAFTER}}` assembles | Attorney has confirmed case type, service model, and whether emergency or temporary relief applies |
| `initial-pleadings` | `p2` | Initial pleadings and filing | `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}` → `{{ROLE_APPROVER}}` | Attorney review complete; jurisdictional facts pled with specificity; every remedy pled; required affidavits attached and internally consistent |
| `service` | `p3` | Service of process | `{{ROLE_DRAFTER}}` mechanics, `{{ROLE_APPROVER}}` method | Return of service filed and reviewed; response deadline calendared; 120-day outside date diaried |
| `responsive-pleadings` | `p3` | Responsive pleadings and counterpetition | `{{ROLE_APPROVER}}` content, `{{ROLE_DRAFTER}}` assembly | Jurisdictional defenses raised by pre-answer motion or in the answer, or they are waived |
| `temporary-relief` | `p3` | Temporary relief | `{{ROLE_APPROVER}}` | Relief is pled in the pleadings; evidentiary support assembled; hearing set on the evidentiary calendar |
| `mandatory-disclosure` | `p3` | Mandatory disclosure | `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}` → `{{ROLE_APPROVER}}` | Production served inside the rule period; certificate of compliance reviewed and signed by the attorney before filing |
| `discovery` | `p3` | Discovery | `{{ROLE_APPROVER}}` strategy, `{{ROLE_DRAFTER}}` production | Three-way audit complete — financial affidavit vs. mandatory disclosure vs. certificate of compliance; documented good-faith conferral before any motion to compel |
| `case-management-conference` | `p3` | Case management conference | `{{ROLE_APPROVER}}` | Counsel can state service status, disclosure status, outstanding discovery, mediation posture, and trial time estimate |
| `experts-evaluations` | `p3` | Experts and evaluations | `{{ROLE_APPROVER}}` | Court authorization obtained where the rule requires it; expert deadlines from the case management order calendared |
| `mediation` | `p4` | Mediation | `{{ROLE_APPROVER}}`, or the neutral where the firm is mediating | Mandatory disclosure complete and major unknowns resolved; client reality-tested on what a court can and cannot order |
| `pretrial` | `p4` | Pretrial | `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}` | Discovery substantially complete; mediation held or waived; preliminary motions resolved |
| `trial` | `p4` | Trial | `{{ROLE_APPROVER}}` | Client prepared to testify; exhibits exchanged per local requirements; proposed findings drafted in statutory language |
| `final-judgment` | `p4` | Final judgment | `{{ROLE_APPROVER}}` | Judgment contains every statutory finding the relief requires; ambiguity removed; all post-judgment obligations calendared |
| `post-judgment-compliance` | `p5` | Post-judgment compliance | `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}` | Rehearing/clarification window and appeal window addressed; transfers, retirement orders, and refinancing deadlines diaried |
| `file-closing` | `p5` | File closing | `{{ROLE_DRAFTER}}` assembles, `{{ROLE_APPROVER}}` approves the letter | Every item in § 5 is true |

**Not every stage occurs in every matter.** A stage that does not apply is recorded in
`scope.outOfScopeStages` or noted in `position.stageEvidence` as not applicable — never quietly
skipped, because a skipped stage and an inapplicable stage look identical in a completed-stage
list and only one of them is fine.

**Stages are not strictly linear.** Discovery reopens. Temporary relief recurs. Where a stage
resumes after being marked complete, write a `stage-reopened` ledger entry rather than removing
it from `completedStages` — removal is a schema violation and destroys the history of the first
pass.

---

## 3. SCOPE MODELS

Six models. The distinction that matters legally is **whether an attorney-client relationship
exists** and **whether an appearance was entered.** Fee structure is not a model — it lives in
`scope.billingBasis`.

| `serviceModel` | Attorney of record? | Core authorization | Ends by |
|---|---|---|---|
| `full-representation` | Yes | Everything in the matter | Final judgment plus closing, or court-approved withdrawal |
| `limited-scope` | Yes, for the named proceeding only | Only the proceeding or matter named in the notice | Filing the termination of limited appearance |
| `advice-and-counsel` | No | Education, strategy, review, preparation of the client | Completion of the purchased sessions or deliverable |
| `document-preparation` | No | Preparing documents the party files pro se | Delivery of the document, with the required certification |
| `neutral-mediator` | No — neutral | Facilitating resolution between the parties | The mediator's report of outcome |
| `neutral-gal` | No — court-appointed neutral | Investigation and recommendations to the court | Conclusion or discharge of the appointment |

**Notes that bear on the schema.**

- **`full-representation`** does not authorize work in a *different* matter — a separate
  injunction, dependency, or criminal case needs its own engagement and its own command center.
- **`limited-scope`** requires `scope.limitedPurpose` populated verbatim from the filed notice.
  The notice must be filed at the time of appearance and **signed by the party**; client consent
  is a filing requirement, not a courtesy. During the limited appearance, documents and hearing
  notices are served on both the attorney and the party. If notice arrives for a hearing outside
  the scope, the attorney must notify the court and the opposing party of non-attendance — write
  that as a deadline object with `ownerRole: {{ROLE_APPROVER}}`.
- **`advice-and-counsel`** is the model most prone to drift. The litigant remains pro se and owns
  every deadline. Deadlines recorded on such a matter carry `ownerRole: "client"`, and that is
  not a formality — recording a client-owned deadline as firm-owned misstates who is responsible.
- **`document-preparation`** ends at delivery. Nothing is on the docket, so there is nothing to
  terminate; `appearanceType` is `none`.
- **Both neutral models**: a neutral engagement in a matter permanently forecloses representing
  either party in that matter. Screen at conflict-check time, not later. Where the firm is the
  mediator there is no legal strategy in the matter at all — the file is administrative and
  neutral, and the command center records position and dates only.

`[CONFIRM LOCALLY: how the installing firm classifies its own service offerings, with
{{ROLE_APPROVER}}]` — the source module is explicit that its own sources split this taxonomy
differently and that each installing firm must decide before model-specific workflows are
applied.

---

## 4. SCOPE CHANGE AND CREEP

**Governing rule: if it is not written in the engagement, it is not in the engagement.**

Before performing any task, confirm it falls inside the engagement document. Log time regardless
of billing structure — time logging is the mechanism that makes creep visible before it becomes
free work.

**Creep signals that should produce a flag, not a favour:**

- Repeated "quick questions" outside the defined deliverable.
- A request to file or attend something not in the engagement.
- A client treating "prepare for mediation" as "attend mediation."
- The court setting a hearing outside the scope of a limited appearance.
- An advisory client beginning to treat the firm as counsel of record.

Do not answer the out-of-scope question "just this once." Beyond the workload problem, silently
performing out-of-scope legal work blurs whether an attorney-client relationship exists for that
task — which is precisely the ambiguity that documented scope and the appearance-notice mechanics
exist to prevent.

**Scope expansion is legitimate.** Moving a client from advisory to limited scope, from one
limited task to another, or from limited to full representation is normal. It requires a new
signed scope document, and if it changes the attorney's role on the docket, the corresponding
filed notice. In the schema that is a `scope-change` ledger entry plus, where the docket role
changes, a flag for `{{ROLE_APPROVER}}`.

---

## 5. CLOSING — WHAT MUST BE TRUE

A matter does not close because the hearing is over. `file-closing` completes only when all ten
are true. If any item is false, the matter stays open.

1. The matter is legally concluded — final judgment entered, case dismissed, settlement fully
   executed, the limited-scope proceeding completed, the deliverable delivered, the mediation
   reported, or the neutral appointment discharged.
2. The docket reflects the firm's exit — no pending matters or a court order permitting
   withdrawal; for limited scope, the termination of limited appearance is filed; for advisory and
   document-preparation models, confirm no appearance was ever entered by mistake.
3. All final orders are in the file — entered, conformed, saved.
4. Post-judgment obligations are transferred or completed — retirement orders prepared or
   expressly excluded from scope; deeds and titles transferred; support start dates, refinancing
   deadlines, and transfer deadlines either done or handed to the client in writing.
5. No deadline is still running against the client — the rehearing/clarification and appeal
   windows have expired, or been consciously waived by the client with attorney advice.
6. Discovery and disclosure obligations are resolved — nothing outstanding, no unserved
   certificate, no undelivered supplemental production.
7. Billing is final — final invoice issued, trust balance reconciled and refunded or applied, no
   unrecorded time.
8. A closing letter has been drafted and **approved by `{{ROLE_APPROVER}}` before it goes out.**
   It states that the representation has ended, what was and was not done, what the client must
   now do and by when, and what happens to the file.
9. The file is organized and archived per the firm's retention policy, and the client's original
   documents are returned or their disposition documented.
10. Matter status is updated in `{{PM_SYSTEM}}` so the file stops appearing as active.

`[CONFIRM LOCALLY: which role owns formal file closure, with {{ROLE_APPROVER}}]` — the source
module records two different allocations across its own sources and treats this as a firm
operational decision rather than a legal requirement. The attorney-approval gate on the closing
letter is preserved either way.

---

## 6. EVIDENCE → STAGE INFERENCE

Used when birthing a command center on a matter that is already underway. Every stage marked
complete this way is written with `trigger: "inferred-from-file-scan"` and an entry in
`position.stageEvidence` naming the file or folder. Inference is weaker than a witnessed event
and must stay visibly so.

| Evidence present in the matter | Stage inferred complete |
|---|---|
| Documented conflict check | `intake-conflict-check` |
| Signed engagement or scope document | `engagement-scope` |
| Intake questionnaire or client information forms | `intake-conflict-check` |
| Case assessment or strategy memo | `case-assessment` |
| Filed petition, or filed answer where the client is the respondent | `initial-pleadings` |
| Return of service, affidavit of service, or filed waiver | `service` |
| Answer, affirmative defenses, or counterpetition on file | `responsive-pleadings` |
| Filed motion for temporary relief, or an order on one | `temporary-relief` |
| Financial affidavit plus disclosure documents produced | `mandatory-disclosure` in progress |
| Filed certificate of compliance | `mandatory-disclosure` |
| Served interrogatories, requests to produce, or subpoenas | `discovery` in progress |
| Case management order | `case-management-conference` |
| Expert engagement, evaluation order, or social investigation order | `experts-evaluations` |
| Notice of mediation | `mediation` scheduled |
| Mediator's report | `mediation` |
| Executed settlement agreement, full or partial | `mediation` with resolution recorded |
| Pretrial stipulation, witness list, or exhibit list | `pretrial` |
| Trial order with a set date | `pretrial` in progress; do **not** infer `trial` |
| Signed final judgment | `final-judgment` |
| Retirement order, executed deed, or income deduction order | `post-judgment-compliance` in progress |
| Approved closing letter | `file-closing` |

**Two rules on inference.**

- **A scheduled event is not a completed stage.** A notice of mediation means mediation is
  scheduled; only the report means it happened. A trial order means pretrial is live; it never
  means trial occurred.
- **Absence proves nothing.** A missing document may mean the stage did not happen, or that the
  file is incomplete. Infer completion from presence only. Where a stage that should logically
  have occurred has no evidence, raise a flag at severity `attorney-review` — do not infer either
  way.

---

## 7. ISSUE COMPLETENESS CHECK

The source module's issue-spotting map for a dissolution, retained here because the command
center is where a missing issue becomes visible: **parenting; equitable distribution; alimony;
child support; and everything else** — fees, name change, deeds and transfers, and the remaining
cleanup items.

Run it as a completeness test at three moments: drafting the petition (is every live issue either
pled or consciously excluded?), building the discovery plan (does each live issue have a document
source?), and drafting the final judgment (does each live issue have an enforceable provision with
dates, amounts, and mechanics?).

**A paternity action is narrower** — parenting, child support, and the fee portion of the
remainder. Equitable distribution and alimony cannot be pled in a paternity action.

⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 8. ROUTE TO `{{ROLE_APPROVER}}` ON SIGHT

These are recorded in the command center as flags, never decided in it.

- Case type selection where the facts could support more than one vehicle.
- Any interstate or child-custody-jurisdiction question, including whether another state retains
  exclusive continuing jurisdiction.
- Whether long-arm jurisdiction applies.
- Choice of service method, especially any substitute or constructive service, and any
  avoiding-service situation.
- Whether to answer or attack jurisdiction first — the wrong reflex waives the defense.
- Whether a situation is a true emergency or temporary relief, and whether ex parte relief is
  appropriate.
- Any safety, domestic violence, firearms, substance-abuse, or dependency indicator, including
  whether mediation is contraindicated.
- Any conflict-of-interest question, including whether a conflict is waivable.
- Any scope change or scope-boundary dispute.
- Withdrawal or partial withdrawal.
- Whether to engage an expert, seek an evaluation of a minor child, or request a social
  investigation.
- Settlement authority, agreement terms, and merger versus incorporation into the final judgment.
- Selection of the post-judgment vehicle — rehearing, clarification, clerical correction, relief
  from judgment, modification, enforcement, or appeal. Choosing wrong can foreclose all options.
- Any certificate of compliance, closing letter, or filing — drafted by staff, signed and filed
  only by the attorney.
- Any assessment that a deadline has been missed.
