# Lane Selection Matrix

**Loaded by `lal-correspondence.SKILL.md` § 2.** Maps a trigger to a lane, a spec, a sub-type, a
signer, and a provenance class.

`P` column: **M** = matter-sourced, language recovered from sent correspondence · **T** =
template-sourced only, no sent instance exists anywhere in the corpus · **M/T** = mixed, structure
or some blocks sourced and others template-only · **NONE** = no source at all; **do not produce**.

Read the `P` column before drafting and tell the user what it says. See the skill § 3.

---

## 1. LANE BY RECIPIENT

| Recipient | Lane |
|---|---|
| The firm's own client | client |
| A lawyer for the other side | opposing counsel |
| The other side, **unrepresented** | opposing counsel — **unrepresented sub-lane, never the counsel-facing version** |
| Judge or judicial assistant | bench |
| Everyone else — custodian, provider, school, employer, neutral, platform | third party |

Confirm current representation status before choosing. Sending a counsel-facing letter to an
unrepresented party, or omitting the mandatory disclaimer, is the highest-risk error in the
opposing-counsel lane.

Where the firm acts as a **court-appointed neutral** rather than as counsel, the lane is third
party and the role is carried in the signature. Neutral and advocate roles never blend.

---

## 2. CLIENT LANE

### 2.1 Onboarding

| Trigger | Spec | Sub-type | Signer | P |
|---|---|---|---|---|
| Retainer countersigned **and** initial payment deposited to trust | retainer-transmittal | Retainer transmittal under firm cover, executed copy attached | attorney | **T** |
| Matter opened and active | client-welcome-engagement | Welcome / engagement | `{{ROLE_DRAFTER}}` | M/T |
| Portal and upload tooling provisioned | client-welcome-engagement | Portal and upload setup, sent as companion | attorney | M/T |
| Intake call scheduled | client-welcome-engagement | Intake-call preparation | attorney | T |

**Sequence and timing are load-bearing.** Transmittal within four hours of countersignature and
trust deposit; welcome within twenty-four hours; portal setup within forty-eight; intake prep
within twenty-four hours of the call being scheduled. The transmittal is attorney-signed and the
welcome is signed by `{{ROLE_DRAFTER}}` — that split is deliberate.

**Never send the welcome with unprovisioned or placeholder upload links.** Named in the source as
the single most common onboarding error. Confirm intake forms are provisioned before the welcome
goes out, and **received** before intake-call prep goes out.

**If the retainer is not yet signed** when intake prep is sent, write *your matter*, not *your
case*, and state that the retainer must be signed before substantive case work begins.

**No welcome or transmittal variant exists** for limited-scope, unbundled-coaching, flat-fee-only,
mediation-only, or court-appointed-neutral engagements; for post-judgment or modification matters
opened on an existing relationship; for a co-petitioner in an uncontested matter; for a retainer
signed by someone other than the client; for a partially funded or payment-plan engagement; for
transmitting a mid-matter scope addendum; or in any language other than English. The source
acknowledges these need different sequences and does not write them.

### 2.2 Status and strategy

| Trigger | Spec | Sub-type | Signer | P |
|---|---|---|---|---|
| Fixed monthly cadence | client-status-update | Monthly status | attorney reviews; `{{ROLE_DRAFTER}}` may draft | **T** |
| An offer or counter lands and the client must decide | client-status-update | Settlement posture update | **attorney only** | M/T |
| Notice of hearing received | client-status-update | Hearing / court-date confirmation | attorney | **T** |
| A client production has been reviewed and items remain outstanding | client-status-update **or** billing-deadline | Document-status / outstanding-items update | `{{ROLE_DRAFTER}}` under attorney review | **M** |
| Financial and document review complete; per-issue authorization needed | client-status-update | Settlement recommendation with per-issue Yes/No decision checklist | **attorney only** | **M** |

The last two are live sub-types the masters do not describe. The document-status update is the most
frequently sent status document in the harvest, appearing in five matters. The decision checklist
is the strongest single artifact in the client lane: it converts a strategy memo into an
authorization record.

**The monthly status email is never the vehicle for bad news or substantive strategy.** Those get a
separate dedicated message — and the corpus contains **no bad-news or adverse-ruling language at
all**, so the document the master points to does not exist. Also absent: trial-setting,
discovery-deadline-slipping, case-management-conference, dormant-matter, client-non-responsiveness
escalation, and post-judgment or enforcement status variants; and any cadence alternative other
than monthly.

### 2.3 Documents and money

| Trigger | Spec | Sub-type | Signer | P |
|---|---|---|---|---|
| A production is partly complete and a specific item is missing | billing-deadline | Document chase | attorney, or `{{ROLE_DRAFTER}}` under review | **M** |
| An item appears in production that is not on the affidavit; or a payment stream cannot be characterized | billing-deadline | Explanation request on a specific transaction or account | attorney | **M** |
| A certificate, form, or class completion is outstanding | billing-deadline | Deliverable chase | `{{ROLE_DRAFTER}}` | **T** |
| A balance merely has to be stated at closure | billing-deadline / closing | One-line balance or trust status | attorney | **T** |
| A balance must be reconciled against agreements and then disposed of | billing-deadline | Fee accounting and balance disposition | **attorney only** | **M** |
| A signature is outstanding | — | — | — | **NONE** |
| A court-ordered client deadline was missed | — | — | — | **NONE** |
| Mid-matter past due; trust replenishment; payment-plan default; any refund | — | — | — | **NONE** |

`[CONFIRM LOCALLY: who signs a document chase — attorney or {{ROLE_DRAFTER}} under review, with {{ROLE_APPROVER}}]`

**The document chase is deliberately deadline-free** and frames the consequence as positional
advantage lost. No source provides a stated deadline date, a second- or final-notice escalation, a
consequence for continued non-response, a work-suspension warning, a late fee, or an interest
statement. A buyer whose practice needs enforceable client deadlines will find this sub-type too
soft. Say so at install.
`[CONFIRM LOCALLY: response-deadline convention for client document requests, and the escalation ladder, with {{ROLE_APPROVER}}]`

**Fee accounting is the highest-liability sub-type in the client lane.** Entitlement before
concession: state what the client contractually owes, only then dispose of it — reversing the order
makes a waiver read as an admission the fee was unearned. Then fence the disposition: a waiver
creates no credit balance. Every figure and the disposition decision itself require attorney
sign-off; none of it is boilerplate and none goes out over a staff signature.

Two verification gates on this sub-type:

- **The earned-on-receipt recital is a recital of one firm's agreement.** If the buyer's own fee
  agreement does not say a flat fee is earned on receipt and non-refundable, the sentence is false
  and must not ship.
  `[CONFIRM LOCALLY: whether the firm's flat fee is in fact earned on receipt under its own fee agreement]`
- **The hourly-equivalent value comparison invites a fee dispute.** Attaching a constructed hourly
  invoice and asserting a savings figure hands the client an alternative valuation of the same work,
  in writing. Opt-in only; never estimate the hourly figure.
  `[CONFIRM LOCALLY: whether the firm wants an hourly-equivalent comparison in fee correspondence at all, with {{ROLE_APPROVER}}]`

A fee accounting **contains no post-judgment warnings.** If it is doubling as the closing letter,
merge the closing lane's orders-still-bind, modifiability, anti-retaliation, and records-retention
blocks into it.

### 2.4 Ending the representation — closing versus disengagement

Ask the question before opening either spec: **did the work finish, or did it stop early?**

| | Closing | Disengagement |
|---|---|---|
| Trigger | Work finished | Work stopped early |
| Cause | Final order, completed scope, completed task | Non-payment, breakdown, client direction, conflict, non-cooperation |
| Client posture | Served | Often unhappy, sometimes unreachable |
| Court status | Usually final | Usually **still pending** |
| Central risk | Client thinks the firm still owns future work | Client misses a live deadline while unrepresented |

**The closure reason controls the letter. The same letter is never used for every file.** Attorney
approval is required before closure; a matter is not closed because it looks quiet.

**Closing sub-types:**

| Sub-type | P | The risk the letter must neutralize |
|---|---|---|
| Full representation after final judgment or order | **M** | Client assumes ongoing obligations are the firm's |
| Short-form full representation | **M** | Same, compressed |
| Limited scope completed | **M/T** | Client assumes the firm still covers the rest of the case |
| Coaching / unbundled service completed | **T** | Client believes the firm appeared for them |
| Flat-fee task completed | **M/T** | Client assumes the fee covers future work |
| Substitution of counsel | **T** | Gap in who owns the next deadline |
| Withdrawal granted | **T** | Client misses a pending deadline while unrepresented |
| Administrative closure / dormant file | **T** | Client believes a deadline is tolled |
| Mediation engagement concluded | **T** | Agreement never gets papered and filed |
| Court-appointed-neutral appointment ended | **T** | Assumption the neutral remains available |

Every closing sub-type ends with a **scope fence** — some form of *unless a new written agreement
is signed*. It appears in every template in the corpus. Treat it as mandatory.

The known executed limited-scope closing is **one email** carrying the mechanic, the scope recital,
the opposing-counsel notification, and a rehire invitation. It contains no enumerated
not-responsible list, no deadline-ownership transfer, no no-tolling paragraph, no billing statement,
and no file-retention statement — on a case that was still pending. Use the template's structure
with that email's sentences, never that email alone.

**Disengagement sub-types:**

| Sub-type | P | Hard stop |
|---|---|---|
| Client-directed stop mid-matter, case still pending | **M** | No — client-initiated; attorney still reviews |
| Post-withdrawal confirmation, order already entered | **T** | **Yes** |
| Administrative / dormant closure | **T** | **Yes**, where the ground is non-payment or non-cooperation |
| Non-payment disengagement, firm-initiated pre-withdrawal | **NONE** | **Yes — absolute** |
| Intent-to-withdraw warning | **NONE** | **Yes — absolute** |
| Conflict / irreconcilable breakdown | **NONE** | **Yes — absolute** |
| Client non-cooperation with discovery | **NONE** | **Yes — absolute** |

See the skill § 6 for the hard stop. The four `NONE` rows are doubly blocked: the compliance block
is missing **and** the sub-type is unsourced. Neither is curable by drafting.

**Do not scaffold a firm-initiated disengagement from the client-directed sub-type.** That sub-type
is client-initiated and therefore omits every element that makes a firm-initiated exit defensible —
statement of cause, cure period, notice of intent, and the compliance basis.

**No review solicitation in any of these documents.** One executed source letter solicited a public
review in the same letter that announced a motion to withdraw.

**No estate-planning reference, and no practice-area cross-sell.** A closing letter is the worst
place for a cross-sell: it sits beside the sentence disclaiming responsibility for future work.

Named gaps in this pair: no file-retention period, destruction schedule, client collection
deadline, or originals-versus-copies rule anywhere in the corpus — one letter references a
"standard file retention policy" without stating a term of it. No approved email sign-off block for
a scope-ending communication. No statement of who may sign one; **default to attorney signature and
require an explicit override.** No refund letter. No surrender-of-papers language. No
steps-taken-to-avoid-prejudice language. No neutral, non-promotional close appropriate to an adverse
exit.

---

## 3. OPPOSING COUNSEL LANE

Every sub-type in this lane carries attorney approval as **required** in the source. There is no
staff-sendable opposing-counsel letter. A simple courtesy *confirmation* may go out over a staff
signature after the attorney has approved the underlying request.

| Trigger | Sub-type | P |
|---|---|---|
| Retained; notice of appearance filed | Initial contact, notice enclosed | **T** |
| Substitution order entered | Substitution of counsel | **T** |
| Mandatory disclosure production is materially incomplete | Disclosure deficiency / meet-and-confer | **T** |
| Discovery responses are materially incomplete | Discovery deficiency / meet-and-confer | **T** |
| A non-party subpoena is going out | Subpoena cover and objection-window notice | **T** |
| Coordinating availability before approaching the court | Scheduling / joint availability | **M** |
| An existing setting has moved | Re-notice / updated setting | **M** |
| Extension, planned absence, or a discrete reciprocal courtesy | Professional courtesy — **three options, exactly one ships** | **T** |
| Transmitting a package, a counter, or a final offer | Settlement package transmittal | **M** |
| Responding to a counter-proposal | Agreed / not-agreed split, reconciliation, one authorized number | **M** |
| Serving a statutory settlement proposal | Statutory proposal cover | **T** |
| Pre-service outreach, other side unrepresented | Plain-register outreach with **mandatory disclaimer** | **M** |
| Settlement offer to an unrepresented party | Options-not-ultimatum, with **mandatory disclaimer** | **M** |
| Responding to a bad-faith or unreasonable letter; cease-and-desist; sanctions demand outside the deficiency escalation; withdrawing or correcting an offer already served; any multi-party or intervenor variant | — | **NONE** |

**Sequencing and verification gates:**

- Serve counsel before serving a records custodian. The rule sequence is not discretionary.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- A cure deadline must leave time to draft, file, and have heard a motion to compel before the
  milestone. The source specifies a two-week minimum buffer.
- Confirm a statutory settlement-proposal mechanism actually reaches the claim before serving one.
  The source is emphatic that it does not reach most equitable family-law claims and that the
  specificity requirements must be reviewed first.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- Substitution letters go out only after the order is entered, with the filed order attached, and
  only after prior counsel's file has been received or a transfer deadline set.
- Build a deficiency letter against the **actual production**, the filed certificate of compliance,
  and the filed financial affidavit. Generic deficiency complaints draw generic responses.
- Never state a settlement figure the client has not authorized in writing.
- Do not include a child's name, date of birth, or school in correspondence to an adverse party
  unless identification is legally necessary.

**Both deficiency sub-types ship as pure scaffolding.** No worked deficiency item exists anywhere
in the library — the two deficiency letters found in matter files were **incoming**, on another
firm's letterhead. What is sourced is the four-part item discipline: what is missing, what the rule
requires, where the inconsistency appears, and the specific supplemental item requested. No item
ships without all four.

**The settlement inadmissibility paragraph is verbatim and non-negotiable.**
`[CONFIRM LOCALLY: the controlling fee-shifting and settlement-inadmissibility authority in the buyer's jurisdiction]`

---

## 4. BENCH LANE

Attorney approval is **required** on all eight formal sub-types. No formal bench letter is
staff-sendable.

| Trigger | Sub-type | Addressed to | Register | P |
|---|---|---|---|---|
| Requesting a special-set hearing | Special-set request | assistant | either | **M** |
| Asking which calendar a motion belongs on | Calendar-placement inquiry | assistant | email | **M** |
| Taking or confirming a held date | Date-hold confirmation and notice follow-through | assistant | email | **M** |
| Transmitting an agreed proposed order | Agreed order cover | judge | formal | **T** |
| Transmitting an unopposed proposed order | Unopposed order cover | judge | formal | **T** |
| Transmitting an order after a ruling | After-hearing order cover — **three circulation states, exactly one ships** | judge | formal | **T** |
| Delivering a binder or PDF set before a hearing | Courtesy copy cover with tab index | judge | formal | **T** |
| Case is ready to be set | Status letter — ready | assistant | formal | **T** |
| Parties jointly holding the case | Status letter — abeyance | assistant | formal | **T** |
| Withdrawing a motion and releasing calendar time | Withdrawal and calendar release | assistant | formal | **T** |
| Emergency or genuinely ex parte cover; responding to a rejected order; resubmitting a corrected order; continuance to the bench; correcting a prior misstatement to the court; multi-judge or consolidated variant | — | — | — | **NONE** |

**The ex parte discipline is the load-bearing content of this lane.** Both sources are strict.

Always: `cc:` opposing counsel by full name and email on the face of the letter; confirm the other
side was advised *before* the letter went to the bench where the spec sequences it; state the other
side's position on the record of the letter — agreed, unopposed and affirmatively confirmed,
objected with a competing order enclosed, or served on a named date and unresponsive; deliver an
identical courtesy set to the other side and say so; confirm the other side's availability before
proposing dates, because listing unconfirmed dates manufactures a continuance dispute; where the
other side has not confirmed, say so plainly and ask for the date to be **held** rather than booked;
keep the other side on live email threads.

Never: argue the merits; argue a form dispute in a cover letter; characterize the other side or
their conduct; argue discovery deficiencies in a status letter; editorialize on why a motion is
being withdrawn; submit a proposed order that tracks the client's preference rather than the court's
ruling; treat silence as consent — **unopposed requires affirmative confirmation.**

The practical expression of the discipline, from an observed thread: **negotiate off-thread, report
on-thread.** Where the assistant instructs the parties to coordinate between themselves, comply and
report the result rather than continuing to negotiate in front of the court.

**Never state an abeyance with no update date** — open-ended abeyance invites dismissal for lack of
prosecution. Abeyance requires joint election; a unilateral request is a motion, not a letter.

**Check the other party's notice entitlement before accepting a date.** A date the firm cannot
properly notice is worse than no date.

**Tension the buyer must resolve deliberately:** the template library requires attorney signature on
everything to the bench; live practice has staff emailing the assistant directly on pure calendar
logistics. Both are defensible.
`[CONFIRM LOCALLY: whether staff may correspond with a judicial assistant without attorney signature, and where the boundary sits, with {{ROLE_APPROVER}}]`

**Run the buyer's judicial-procedures reference before every bench transmittal.** Format is
judge-specific. All of the following vary: word-processor format with or without electronic
signature, PDF only, portal-only submission, whether a courtesy email to the assistant is expected,
whether paper or PDF binders are accepted, whether a separate filed notice for trial is required,
whether a filed notice of withdrawal is required in addition to or instead of a letter, and how
special sets are reserved.

---

## 5. THIRD-PARTY LANE

A third-party letter fires where the firm's authority derives from a court appointment, an
anticipated-litigation preservation duty, or a pre-service overture.

| Trigger | Sub-type | Recipient | P |
|---|---|---|---|
| Court-appointed neutral must notify parents and counsel it will contact third parties | Collateral-contact notice | both parents / counsel | **M** |
| Litigation reasonably anticipated; relevant records sit with a third party | Preservation notice — custodian | bank, processor, employer, exchange, cloud or platform provider | **T** |
| Same, directed at the other side | Preservation notice — party or counsel | other side | **T** |
| Resolve before formal service; other side unrepresented | Pre-service outreach with **mandatory disclaimer** | unrepresented adverse party | **M** |
| A court order directs a provider to speak with the appointed neutral | Outreach to the collateral contact itself, on order authority | provider | **M** |
| A release is needed between neutral, consenting parent, and provider | Consent to release information — **instrument format** | provider, executed by the parent | **M** |
| Expert, evaluator, or mediator engagement; subpoena cover; records **production** request; school or non-clinical records request; process-server instructions; neutral's report transmittal; any third-party transmittal; fee terms for any neutral or expert | — | — | **NONE** |

**Gates:**

- **Never send provider outreach without the order actually attached.** The whole authority claim
  rests on the enclosure. And the assertion that the neutral need not submit questions in advance is
  an interpretation of one specific appointment order, not a general rule — confirm the order says so.
- **A confidentiality commitment to withhold collateral statements from parents must match the
  appointment order** in the specific case before it is sent.
- **Narrow a preservation scope deliberately.** As drafted it is broad enough to draw an overbreadth
  objection. Broaden later with formal process.
- **Do not request privileged material in a way that risks waiver.** Where privileged items are
  preserved, they are logged when produced.
- **A release clause authorizing onward disclosure to "any third parties" is extremely broad.**
  Narrow it to the actual providers in the matter unless the appointment order supports the wider
  grant. A release tied to the duration of an appointment requires a fresh instrument if the
  appointment ends and is later renewed.
- **Providers may insist on their own authorization form in addition.** Expect to execute both.
- **Any support figure in pre-service outreach must be tied to a current guidelines worksheet**, not
  to a prior estimate. Every number and the tone require attorney sign-off; the disclaimer is
  mandatory and is not sufficient on its own.
- **Telling a provider to consult its own counsel while discouraging delay** is a framing an attorney
  should confirm is acceptable in the division before use — a party's treating provider may hold
  privileges the parent has not waived.
- **Strip social handles and website links** from any generated version of provider outreach. The
  source email carried both.

Named source defects that must not propagate: a plural/singular verb mismatch in the release
instrument; and one source PDF named as a consents packet that actually contains a mixed bundle
including a blank release bearing a **different matter's** party name. Cross-matter content in a
single file is real. Filename would not have revealed any of it.

---

## 6. THE THREE DOCUMENTED CONTRADICTIONS

Surface each one rather than choosing silently.

| Contradiction | Master says | Live practice does |
|---|---|---|
| Deadlines on client document asks | Every ask carries a deadline | Deliberately deadline-free; consequence framed as positional advantage lost |
| Matter identifiers in subject lines | Prohibited | All-caps label plus party styling |
| Legal references in client letters | No rule, statutory, or case references in status correspondence | Florida law and guideline standards are referenced in plain language, without formal citation format |

The third has a hard limit regardless of which convention the buyer picks: **where a client letter
asserts a legal entitlement in plain language, the assertion is verified.** Plain language does not
lower the accuracy bar. ⚠️ VERIFY: confirm rule and current text before relying on this.
