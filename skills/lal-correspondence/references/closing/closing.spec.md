# Closing Letter — Content Spec
lane: client
sources: 5 distinct matters (M01, M02, M03, M04, M10) + 1 firm-level closing system (T-CLOSE) + 3 approved form letters (T-FORM-A, T-FORM-B, T-FORM-C)
harvested: 2026-07-29

> **HARVEST INTEGRITY NOTE.** Target was 25–30 examples from distinct matters. Only
> **three** distinct matters yielded an executed closing letter. The bulk of the
> substance below comes from a single firm-level closing system document that contains
> a ten-category letter template bank. That document is genuine and substantive, but it
> is one source, not twenty-five. Buyers should be told this. See `## Coverage`.
>
> **ESTATE-PLANNING CONTAMINATION CONFIRMED AND STRIPPED.** The source closing system
> repeatedly asserts the firm offers estate planning services and contains a full
> `ESTATE PLANNING CLOSING LETTER TEMPLATE` plus a cross-sell sentence inside the master
> client letter. All of it has been omitted from this spec. See `## Attorney flags`.
>
> **SECOND CONTAMINATION CLASS FOUND AND STRIPPED — CROSS-PRACTICE MARKETING.** One of the
> approved form letters (T-FORM-C) contains a marketing paragraph promoting practice areas
> and affiliated businesses outside family law, and soliciting future non-family work. The
> firm this corpus is harvested from practices **Florida family law only**. That paragraph
> is omitted in full and is flagged as a defect class alongside estate planning. See
> `## Attorney flags`.

## When this fires

A closing letter fires when representation or a defined engagement has **completed** —
as distinct from being terminated early, which is the disengagement lane. The closure
reason controls the letter; the same letter is never used for every file.

Source rule, verbatim:
> Before preparing a closing letter, staff must identify why the matter is closing. The
> closure reason controls the letter language and workflow. Do not use the same letter
> for every file.

Confirmed closure triggers:
final judgment or order entered; settlement completed; flat-fee task completed;
limited-scope task completed; coaching/unbundled service completed; client terminated
representation; substitution of counsel; firm withdrawal; dormant / no communication;
unpaid matter closure; mediation completed; GAL appointment ended; administrative
duplicate or converted matter closure.

**Hard gate before drafting.** Attorney approval is required before closure. Staff must
not close a matter just because it appears quiet.

## Sub-types

| Code | Sub-type | Firm's role | Key risk the letter must neutralize |
|---|---|---|---|
| CL-1 | Full representation after final judgment/order | Counsel of record | Client assumes ongoing obligations are the firm's |
| CL-2 | Short-form full representation | Counsel of record | Same, compressed |
| CL-3 | Limited-scope completed | Limited-scope counsel | Client assumes firm still covers the rest of the case |
| CL-4 | Coaching / unbundled service completed | Not counsel of record | Client believes the firm appeared for them |
| CL-5 | Flat-fee task completed | Varies | Client assumes the fee covers future work |
| CL-6 | Substitution of counsel | Former counsel of record | Gap in who owns the next deadline |
| CL-7 | Withdrawal granted | Former counsel of record | Client misses a pending deadline while unrepresented |
| CL-8 | Administrative closure / dormant file | Varies or none | Client believes a deadline is tolled |
| CL-9 | Mediation engagement concluded | Mediator or party counsel | Agreement never gets reduced to writing and filed |
| CL-10 | GAL appointment ended | Court-appointed neutral | Assumption the GAL remains available |

**Omitted on instruction:** estate planning closing sub-type.

## Required structure per sub-type

**CL-1 (the master) — thirteen blocks, in order:**
1. Date; `Re: Closing of Your Family Law Matter`
2. Representation-concluded statement + final documents enclosed + keep-these instruction
3. Orders-still-bind paragraph (with the anti-side-agreement warning)
4. Modifiability paragraph, if support/parenting/ongoing obligations exist
5. Anti-retaliation paragraph, if enforcement risk exists
6. Reimbursement documentation paragraph, if shared expenses exist
7. Parenting plan paragraph, if children
8. Relocation paragraph, if children
9. Records/tax paragraph + tax disclaimer
10. Billing/trust paragraph
11. Scope-terminated confirmation (`we are not responsible for...`)
12. Warm close + future-work invitation + review request
13. Signature + `Attachments:` list

**CL-2:** blocks 1, 2, a merged orders+future-issues paragraph, 11, 10, 12, signature.

**CL-3 / CL-4 / CL-5:** scope definition must come *first* and be explicit. The
not-responsible list must be enumerated, not summarized.

**CL-6 / CL-7 / CL-8:** effective-date statement, then who owns deadlines now, then a
known-deadlines list or an express disclaimer of knowledge, then file transfer, then
billing.

**CL-9 / CL-10:** outcome statement, then residual-obligation statement, then
attachments.

## Opening paragraph bank

**Executed matter opener, warm variant (M01, M03):**
> Thank you for allowing me to represent you in your family law matter. I am hopeful
> that you are happy with your representation. Our representation of you is now
> concluded.

**Executed matter opener, feedback-inviting variant (M02, T-FORM-A, T-FORM-B):**
> Thank you for allowing our firm to represent you in your family law matter. I am
> hopeful that you are happy with your representation. If you are not for any reason,
> we would appreciate feedback as we strive to provide outstanding assistance during
> difficult times.

**Merged opener (T-FORM-C, round-2 find) — first person singular + feedback invitation.**
T-FORM-C combines the two variants above rather than choosing between them, and it is the
oldest approved form located. It confirms the merged form is firm-approved, not a drafting
accident:
> Thank you for allowing me to represent you in your family law matter. I am hopeful that
> you are happy with your representation. If you are not for any reason, we would
> appreciate feedback as we strive to provide outstanding assistance during difficult
> times. Our representation of you is now concluded.

> **T-FORM-C is a single-paragraph letter.** Opener, non-representation mechanic,
> address-currency instruction, free-notice offer, and new-retainer requirement are all
> run together into one block with no paragraph breaks. Structurally this is the weakest
> form in the corpus. Do not adopt its layout; adopt only its sentences.

**Late-closing acknowledgment variant (T-FORM-B) — the firm names the lateness:**
> This is a little late to send out your closing letter, but we would like to thank you
> for allowing our law firm to represent you in your family law matter.

**CL-1 system opener:**
> Our representation of you in this matter has now concluded. Attached are copies of the
> final documents you should keep for your records, including [CONFIRM LOCALLY: list
> final documents]. Please save these documents somewhere you can access them later. You
> may need to refer to them if questions come up about support, parenting, property,
> reimbursement, enforcement, modification, or future compliance.

**CL-3 opener:**
> The limited-scope service you retained {{FIRM_NAME}} to perform has been completed.
> Our work was limited to [CONFIRM LOCALLY: describe scope]. That limited scope is now
> finished.

**CL-3 opener, EXECUTED (M04) — round-2 find; this sub-type is no longer template-only.**
Sent as an email rather than a letter, on a **still-pending** case, by {{ROLE_DRAFTER}}
over {{ROLE_APPROVER}}'s copy. Note the structure: the mechanic comes first and the scope
recital is used as the *justification* for it, which is the reverse of the system
template's order:
> I am writing to inform you that we will be filing a Notice of Non-Representation with
> the court, as our limited retainer was specifically for representation at
> [CONFIRM LOCALLY: name the limited scope — e.g. mediation].

The firm's own scope recital formula, reusable verbatim with the scope swapped:
`our limited retainer was specifically for representation at {{SCOPE}}`.

**CL-4 opener:**
> This confirms that the coaching/unbundled legal service you retained us to provide has
> been completed. The service provided was [CONFIRM LOCALLY: coaching session, document
> review, form preparation, strategy session, procedural guidance].

**CL-5 opener:**
> The flat-fee service you retained us to complete has been finished. The completed
> service was [CONFIRM LOCALLY: describe service].

**CL-5 opener, EXECUTED (M10) — round-2 find; CL-5 is no longer template-only.**
A full closing letter delivered as a fee-accounting document. It carries a `RE:` line
naming the subject as an accounting rather than a closing, and the
representation-concluded statement is held back to the final block. Structurally this is
the inverse of CL-1:
> RE: CLARIFICATION OF FLAT FEE AGREEMENTS AND PAYMENTS
> Case {{CASE_NO}} | {{CLIENT_NAME}}
>
> Dear {{CLIENT_NAME}},
>
> I am writing to provide you with a clear accounting of the flat fee agreements you
> signed with our firm and the payments you made during your representation in your
> [CONFIRM LOCALLY: matter type] case.

> **M10 is the only executed closing in the corpus organized around money rather than
> around scope.** It runs: agreements recital → payments ledger → account summary →
> fee-decision → value justification → conclusion. The scope fence that every other
> closing leads with appears only in the last paragraph. Use its modules; do not adopt
> its ordering for a matter with live post-judgment obligations, because the
> orders-still-bind and modifiability warnings are entirely absent from it.

**CL-6 opener:**
> This confirms that {{FIRM_NAME}} no longer represents you in this matter because
> {{SUBSTITUTING_PARTY}} has substituted as counsel effective {{DATE}}.

`{{SUBSTITUTING_PARTY}}` resolves to the actual substituting actor — new counsel, opposing
counsel, or the client appearing pro se.

**CL-7 opener:**
> This confirms that {{FIRM_NAME}} no longer represents you in this matter. The Court
> entered an order allowing withdrawal on {{DATE}}.

Alternate second sentence where no order was entered:
> Our representation ended effective {{DATE}} pursuant to [CONFIRM LOCALLY: basis].

**CL-8 opener:**
> We are administratively closing your file at this time because [CONFIRM LOCALLY: the
> requested service was completed / we have not received the requested information /
> payment was not made / you advised you do not wish to proceed / there has been no
> activity or communication].

**CL-9 opener:**
> This confirms that the mediation engagement in this matter has concluded. Mediation
> occurred on {{DATE}} and resulted in {{MEDIATION_OUTCOME}}.

`{{MEDIATION_OUTCOME}}` resolves to full agreement, partial agreement, or impasse.

**CL-10 opener:**
> This confirms that the Guardian ad Litem appointment/file in this matter has concluded
> based on {{GAL_CONCLUSION_BASIS}}.

`{{GAL_CONCLUSION_BASIS}}` resolves to the court order, the final report, the final
hearing, or the discharge.

## Body modules

### MODULE `orders-still-bind` (CL-1)
> Even though our representation has ended, the orders entered in your case still matter.
> You are responsible for following the Final Judgment, Parenting Plan, Marital
> Settlement Agreement, support order, or any other court order that applies to you. Do
> not rely on verbal side agreements. If you and the other party decide to do something
> different, you should get legal advice before treating that change as enforceable.

### MODULE `notice-of-non-representation` (executed matters M02, M03, T-FORM-A, T-FORM-B)
This is the firm's distinctive real-world closing mechanic and does not appear in the
newer system document. Two variants:

*Non-representation variant:*
> We will be filing a Notice of Non-Representation in the Courts so that any future
> correspondence the Court may need to have with you goes directly to you. As such, it
> is important that you keep your contact and address information updated with the
> Courts. We would be happy to file a Notice of Updated Contact information for you in
> the future, free of charge if required. Simply contact our office and we will assist
> you.

*Withdrawal variant (M02):*
> Your case is currently pending, but you have requested us not to move it forward,
> thus, our representation in your matter has concluded. I will be filing a Motion to
> Withdraw in the Courts and any future correspondence the Court may need to have with
> you goes directly to you. As such, it is important that you keep your contact and
> address information updated with the Courts.

### MODULE `notify-opposing-counsel` (M04, executed) — **round-2 find; closes a structural hole**
Neither the executed letters harvested in round 1 nor the system templates said who tells
the other side. M04 does, and it is the only source in the corpus that does. Every
sub-type where the firm was counsel of record needs this block:
> We will notify opposing counsel that we are no longer the attorney of record in your
> matter.

### MODULE `future-correspondence-comes-to-you` (M04, executed)
The consequence sentence that follows the notification. It states the practical effect on
the client rather than the procedural fact:
> Please note that [CONFIRM LOCALLY: opposing counsel / the other party / the Court] will
> need to correspond with you directly regarding your case unless and until you decide to
> rehire us for further representation.

> **DEFECT IN SOURCE — DO NOT PROPAGATE.** M04's sentence reads `the attorney will need
> to correspond with you directly`. `The attorney` is ambiguous: on its face it can be
> read as the firm's own attorney. Context indicates opposing counsel. Any productized
> version must name the actor explicitly. This is a filename-innocent, contents-level
> defect: the document is titled as a routine notice and reads as clean until parsed.

### MODULE `rehire-invitation-on-limited-scope` (M04, executed)
Softer and shorter than the full-representation `new-retainer-required` module, and it
omits the new-contract requirement entirely — a divergence a buyer must resolve:
> Should you wish to engage our services again, we would be happy to assist you.

> **INCONSISTENCY, FLAGGED.** Every full-representation closing in the corpus states that
> further work requires a **new signed retainer contract**. The executed limited-scope
> closing does not. Pick one posture and hold it; the permissive version invites the
> client to assume the old engagement can simply resume.
> [CONFIRM LOCALLY: whether limited-scope re-engagement requires a new written agreement —
> with {{ROLE_APPROVER}}]

### MODULE `new-retainer-required` (executed matters — all)
> We are happy to assist you in the future should you require our services. In order to
> obtain further assistance from our firm, you would need to sign a new retainer
> contract.

### MODULE `civil-court-referral-out` (M01) — matter-specific but reusable
> Please keep in mind that if you and your ex have a jointly-titled property together,
> or any debts jointly-titled, you will need to seek remedies in civil court (not family
> court, since you are not legally married). If you have a joint credit card, for
> example, you will have to figure out an arrangement either between yourselves or with
> the credit card company (to either pay off, remove one person from the account, or
> close the account entirely). Otherwise, you will have to file a petition in civil court
> to have a judge decide what will happen. We can recommend attorneys that can assist
> with this. Since it is not family, we do not handle these types of cases.

### MODULE `future-questions-may-be-billable` (executed matters — all)
The firm's most consistently reused paragraph across every executed closing letter:
> While we are happy to answer any small questions that may come up, we have many
> clients and remembering the details of any one case after the passage of time can be
> difficult. Because of this, if we are required to pull your file, review the
> pleadings, agreements or judgments and advise you as to your rights and or options
> there could be a charge involved. Feel free to contact us and we will let you know
> whether we would require such a fee.

### MODULE `modifiability` (CL-1)
> If your case involves child support, alimony, time-sharing, parental responsibility,
> or other ongoing obligations, those issues may be modifiable only under the proper
> legal standard and only through the proper legal process. A change in income,
> expenses, parenting circumstances, relocation, health, employment, or the child's
> needs may or may not justify a modification. If something significant changes, do not
> wait until the problem becomes bigger. Get advice early.

### MODULE `anti-retaliation` (CL-1)
> If the other party violates the order, do not retaliate by violating the order
> yourself. Withholding support because time-sharing is being denied, or withholding
> time-sharing because support is unpaid, can create problems for you. Keep records,
> communicate in writing when appropriate, and seek legal advice about enforcement
> options.

### MODULE `reimbursement-proof` (CL-1)
> If your case involves child-related reimbursements, uncovered medical expenses,
> extracurricular expenses, school expenses, or other shared expenses, keep proof. Save
> invoices, receipts, proof of payment, and proof that you requested reimbursement from
> the other party. If the order does not provide a specific deadline, a written request
> with clear documentation is still important. If you ever need enforcement, the Court
> will want proof of what was paid, when reimbursement was requested, and whether
> payment was refused or ignored.

### MODULE `parenting-plan-compliance` (CL-1)
> If your case involves a Parenting Plan, follow both the letter and the spirit of the
> plan. Keep communication child-focused and documented. If safety issues arise, or if
> the other parent is not following the plan, get legal advice before making unilateral
> changes unless there is a true emergency.

### MODULE `relocation` (CL-1)
> If your case involves relocation, remember that Florida has strict rules about moving
> with a child. Do not assume you can move because the move seems reasonable or
> necessary. If you or the other parent may move more than fifty miles from the current
> residence for sixty consecutive days or more, you should get legal advice before
> taking action.

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `records-retention-financial` (CL-1)
> If your case involves alimony, child support, property division, retirement accounts,
> tax issues, sale of property, debt allocation, or transfer of assets, you should keep
> copies of all payment confirmations, transfer records, account statements, closing
> documents, receipts, titles, deeds, beneficiary forms, and related proof.

### MODULE `cl3-not-responsible` (CL-3)
> This means we are not responsible for any future filings, deadlines, hearings,
> discovery, service requirements, mediation preparation, trial preparation,
> enforcement, modification, appeal, rehearing deadline, or court communication unless a
> new written agreement is signed.
>
> Please review your documents and court notices carefully. If you have future
> deadlines, you are responsible for meeting them unless you hire us again under a new
> agreement. If you are unsure about what comes next, contact our office before the
> deadline passes.

### MODULE `cl4-not-counsel-of-record` (CL-4) — the single most important line in this sub-type
> {{FIRM_NAME}} did not become your attorney of record in court unless there is a
> separate written agreement and a Notice of Appearance filed by our office. You remain
> responsible for filing your documents, serving the other party, monitoring deadlines,
> attending hearings, complying with court orders, and taking the next steps in your
> case.

### MODULE `cl5-agreements-recital` (CL-5, M10) — round-2 find
Each flat-fee agreement gets its own named, dated heading, its fee, its scope sentence,
and a bulleted list of what the fee actually covered. The bullets are the deliverable
history, not the contract language.
> You entered into [CONFIRM LOCALLY: number] separate flat fee agreements with our firm:
>
> **AGREEMENT 1: [CONFIRM LOCALLY: scope name] (Signed {{DATE}})**
> Flat Fee Amount: {{AMOUNT}}
>
> This agreement covered our representation for [CONFIRM LOCALLY: scope] and related
> services through [CONFIRM LOCALLY: the terminating event]. This included:
> - [CONFIRM LOCALLY: enumerate the work actually performed under this agreement]

### MODULE `cl5-payments-ledger` (CL-5, M10)
A dated two-column ledger and an explicit total. The firm shows its arithmetic rather
than asserting a net.
> **PAYMENTS RECEIVED.** Our records show the following payments received from you:
>
> | Date | Amount |
> |---|---|
> | {{DATE}} | {{AMOUNT}} |
>
> TOTAL PAYMENTS: {{AMOUNT}}

### MODULE `cl5-account-summary` (CL-5, M10)
Per-agreement reconciliation, each ending in a status verdict. Credits are shown as
line items, not netted silently.
> **AGREEMENT 1: [CONFIRM LOCALLY: scope name]**
> - Flat fee owed: {{AMOUNT}}
> - Less: [CONFIRM LOCALLY: credit description] credit: ({{AMOUNT}})
> - Amount due: {{AMOUNT}}
> - Payment received ({{DATE}}): {{AMOUNT}}
> - STATUS: PAID IN FULL

### MODULE `cl5-flat-fee-earned-on-receipt` (CL-5, M10) — the contractual anchor
Stated before any waiver, so the waiver reads as a gift rather than a concession that the
fee was unearned:
> Per your [CONFIRM LOCALLY: agreement name] Agreement signed on {{DATE}}, you
> contractually owe the full flat fee of {{AMOUNT}}. The flat fee is earned upon receipt
> and is not refundable or reducible based on actual time spent or case outcome.

### MODULE `cl5-balance-waiver-and-no-credit` (CL-5, M10) — **highest-risk module in this spec**
Three moves in sequence: waive, characterize the waiver as a loss and a one-time
courtesy, then foreclose any future claim on it.
> However, as a professional courtesy and recognizing the circumstances of your case, we
> have decided to waive the outstanding balance of {{AMOUNT}}. Please understand that this
> waiver represents a significant financial loss to our firm and is offered as a one-time
> courtesy only.
>
> **Important:** This waiver does NOT create a credit balance with our firm that can be
> applied to future legal services. You have no credit balance. Should you require
> assistance with any modification or other legal matters in the future, we will provide a
> separate quote for those services, and any such quote will be independent of this prior
> matter.

### MODULE `cl5-flat-fee-value-comparison` (CL-5, M10)
An itemized hourly-equivalent invoice is attached and the delta is stated as client
savings. Kept because it is real firm language, but see Attorney flags before reuse.
> To illustrate the financial benefit of our flat fee arrangement, we have prepared an
> itemized summary of all work performed on your case (attached as
> [CONFIRM LOCALLY: invoice reference]). If we had billed you on an hourly basis for the
> same services actually provided, your fees would have totaled {{AMOUNT}}. Instead, by
> using our flat fee structure, you paid only {{AMOUNT}} in total fees — representing a
> savings of more than {{AMOUNT}} compared to hourly billing.
>
> The attached invoice demonstrates the substantial volume and scope of work performed on
> your behalf and reflects the true value of the legal services you received.

### MODULE `cl5-conclusion-and-file-availability` (CL-5, M10)
> Your representation on this matter is concluded. The final judgment was entered on
> {{DATE}}, and your case is now closed. All file materials will be made available to you
> per our standard file retention policy.
>
> If you have any questions about this accounting, please do not hesitate to reach out
> through the {{UPLOAD_PORTAL}}. We will be happy to clarify anything further.
>
> Thank you for allowing {{FIRM_NAME}} to assist you with your family law matter.

> **PARTIAL CLOSURE OF THE FILE-RETENTION GAP.** M10 is the only source that references a
> file-retention policy at all, and it references it without stating it. It still supplies
> no period and no destruction schedule.
> [CONFIRM LOCALLY: the actual retention period the phrase "our standard file retention
> policy" refers to — with {{ROLE_APPROVER}}]

### MODULE `cl5-scope-ceiling` (CL-5)
> Unless your written agreement says otherwise, this flat-fee service does not include
> future filings, hearings, amendments, negotiations, enforcement, modification, court
> appearances, or additional legal advice after completion of the task. If additional
> work is needed, we will need a new written agreement or approved scope expansion.

### MODULE `cl6-new-counsel-owns-it` (CL-6)
> Your new counsel is responsible for future filings, deadlines, hearings,
> communications, and case strategy. We are not responsible for future work in this
> matter unless a new written agreement is signed.

### MODULE `cl8-no-tolling` (CL-8) — critical
> This letter does not extend any court deadline or pause any requirement in your case.
> If you have a pending court case, you remain responsible for monitoring the docket,
> meeting deadlines, filing documents, attending hearings, and complying with all court
> orders unless you hire an attorney to handle those responsibilities.

### MODULE `cl9-agreement-must-be-papered` (CL-9)
> If an agreement was reached, the parties remain responsible for ensuring the agreement
> is reduced to the appropriate written documents, signed, filed, and implemented. If the
> matter impassed, the case will proceed according to the Court's deadlines and any
> further orders.

### MODULE `cl10-appointment-scope` (CL-10)
> The GAL's role was limited to the appointment and authority granted by the Court. Any
> future investigation, testimony, report, review, or involvement would require further
> Court authorization or a new appointment.

## Consequence / deadline language bank

**Scope-terminated confirmation (CL-1) — the operative sentence:**
> This letter confirms that our representation in this matter has concluded. We are not
> responsible for future filings, deadlines, hearings, enforcement issues,
> modifications, appeals, rehearing deadlines, compliance issues, or new disputes unless
> a new written agreement is signed.

**Short-form variant (CL-2):**
> This letter confirms that {{FIRM_NAME}} is no longer responsible for future filings,
> hearings, deadlines, or legal work in this matter unless we both sign a new agreement.

**Known-deadlines disclosure (CL-7) — must be one or the other, never blank:**
> You are responsible for all future deadlines, hearings, filings, discovery, court
> communications, and compliance with court orders unless and until another attorney
> appears for you. If there are pending deadlines or hearings, they are listed below
> based on the information currently available to us:
>
> {{DEADLINE_LIST}}
>
> Or, where there are none known, state instead: We are not aware of any currently
> scheduled hearings as of the date of this letter, but you are responsible for checking
> the court docket.

**Billing and trust bank (all sub-types):**

| Situation | Language |
|---|---|
| Final invoice attached | `Attached is your final invoice for services rendered.` |
| No balance due | `As of the date of this letter, your account does not reflect a balance due.` |
| Outstanding balance | `As of the date of this letter, your account reflects a balance of {{AMOUNT}}. Please contact our office to make payment arrangements.` |
| Refund pending | `Our records reflect a remaining trust/retainer balance of {{AMOUNT}}. The refund will be processed according to firm procedure after final reconciliation.` |
| Flat fee complete | `The flat-fee service has been completed and the fee has been earned according to the terms of your agreement.` |
| Payment plan continues | `Your file is being closed, but your payment obligation remains active. Please continue making payments according to the agreed payment arrangement unless the firm confirms otherwise in writing.` |

## Post-representation warning clause bank

Deploy only the clauses that apply. Source hard stop: *"Do not include relocation, child
support, alimony, or parenting warnings if they do not apply."*

**Modification:**
> Some family law orders can be modified later, but only if the legal standard is met
> and the proper legal process is followed. A substantial change in circumstances may
> include major changes in income, employment, expenses, child-related needs, health,
> parenting circumstances, or other legally relevant facts. Do not assume a change is
> automatic. Get legal advice before relying on an informal agreement.

**Enforcement and contempt:**
> If the other party does not comply with the order, keep records and seek legal advice.
> Do not retaliate by violating the order yourself. Your own noncompliance can hurt your
> ability to enforce the order later.

**Child support:**
> Child support must be paid as ordered unless and until the Court changes the order. If
> you lose your job, your income changes, the parenting schedule changes, or the child's
> needs change, get legal advice quickly. Waiting can create arrears or enforcement
> problems.

**Alimony:**
> Alimony obligations and rights depend on the specific language of the order or
> agreement. Remarriage, death, supportive relationships, retirement, income changes, or
> other events may affect alimony depending on the facts and the order. Speak with an
> attorney before stopping, reducing, or relying on a change.

**Parenting plan:**
> Follow the Parenting Plan unless a true emergency exists or the Court changes it. Keep
> communication focused on the child. Document issues. Do not use the child as
> messenger. Do not make unilateral changes simply because the other parent is
> difficult.

**Relocation:**
> Florida has specific relocation requirements when a parent wants to move more than
> fifty miles for sixty consecutive days or more. Do not move with a child, or agree to
> a move, without understanding the legal requirements.

⚠️ VERIFY: confirm rule and current text before relying on this.

**Reimbursement:**
> For reimbursements, keep proof of the expense, proof of payment, proof that the
> expense was shared or required, and proof that you requested reimbursement. If you
> only have verbal conversations, enforcement becomes harder.

**Beneficiary review — NARROWED.** The source clause bundled a beneficiary-review
reminder with an estate-planning cross-sell. The cross-sell is stripped. The retained
substance, which is jurisdiction-neutral and correct:
> After divorce, separation, or major family changes, review your will, trust, power of
> attorney, health care documents, life insurance, retirement beneficiaries,
> payable-on-death accounts, and emergency contacts. Court orders do not automatically
> clean up every beneficiary or estate planning issue.
>
> [CONFIRM LOCALLY: whether this firm offers estate planning. If not, this clause must
> refer the client out rather than offer the service.]

**Tax disclaimer:**
> {{FIRM_NAME}} does not provide tax advice. Speak with a qualified tax professional
> about the tax impact of support, property transfers, retirement division, sale of
> property, dependency exemptions, filing status, or settlement terms.

**Records and documentation:**
> Keep copies of orders, agreements, proof of payment, reimbursement requests, messages,
> receipts, account transfers, and compliance documents. If a dispute arises later,
> documentation matters.

## File retention and return-of-file language

Thin in source. What exists:

**CL-6 transfer:**
> We have provided or will provide your file materials as follows: [CONFIRM LOCALLY:
> describe transfer method]. If your new counsel needs additional documents, they may
> contact our office.

**CL-7 return:**
> Attached are documents from your file that you should keep for your records:
> [CONFIRM LOCALLY: list documents].

**CL-1 retention instruction:**
> Please save these documents somewhere you can access them later.

**Closing-packet composition (internal, from the closing workflow):**
> The closing packet should include final order/judgment, agreement, closing letter,
> final invoice or billing note, and any final deliverables. Any draft-only documents
> should remain clearly marked as drafts.

> **GAP.** No source states a document-retention *period*, a destruction schedule, a
> deadline for the client to request the file, or what happens to the file after that
> deadline. Do not invent one.
> [CONFIRM LOCALLY: file retention period and destruction policy — with {{ROLE_APPROVER}}]

## Closing bank

- `It was a pleasure working with you. If you need help in the future with a modification, enforcement issue, mediation, or another family law matter, please contact our office.`
- `Thank you for trusting us with your case. If you need assistance in the future, please contact us.`
- `Thank you for allowing us to assist you. If you need additional help, you may contact us about a new limited-scope service, coaching, mediation, full representation, or another appropriate service.`
- `Please give us a call if you have any questions or need legal services in the future. Thank you!`
- `We wish you the best moving forward.` (CL-6)
- `We sincerely hope that you and your family flourish as you move forward.` (M03, adapted — original named the child)
- Review request, tokenized: `We would also appreciate your review of our services here: [CONFIRM LOCALLY: firm review link].` Source added: *"This helps other prospective clients know the types of attorneys they would be hiring."*

## Signature block

```
Sincerely,

{{ATTORNEY_NAME}}
{{FIRM_NAME}}

Attachments: {{ATTACHMENT_LIST}}
```

Executed letters from the source firm used a fuller block, and where two attorneys had
appeared, **both** signed:

```
{{FIRM_NAME}}

By: ______________________________
{{ATTORNEY_NAME}}
Florida Bar No. {{BAR_NO}}
{{FIRM_ADDRESS}}
{{FIRM_PHONE}}
Service E-Mail: {{FIRM_EMAIL}}

and

By: ______________________________
{{ATTORNEY_NAME}}
Florida Bar No. {{BAR_NO}}
{{FIRM_ADDRESS}}
{{FIRM_PHONE}}
Service E-Mail: {{FIRM_EMAIL}}
```

Role-line variants: CL-9 signs as mediator; CL-10 signs as `Guardian ad Litem`.

**Round-2 signature findings.**

- **T-FORM-C carries a duplicated sign-off** — the word `Sincerely,` appears twice in
  sequence above the single attorney line. It is an uncorrected artifact sitting in a form
  the firm treats as approved. Treat as evidence that an approved-forms library is not
  automatically QC clean, and add a sign-off-duplication check to the closing QC step.
- **T-FORM-C is signed by one attorney only**, unlike the executed letters where both
  appearing attorneys signed. Both patterns are firm-approved; the count follows who
  appeared, not house style.
- **M04 was signed by {{ROLE_DRAFTER}}, not by an attorney.** The executed limited-scope
  end-of-representation notice went out over {{ROLE_DRAFTER}}'s name and title, with
  {{ROLE_APPROVER}} copied. This is the only representation-ending communication in the
  corpus not signed by a lawyer.
  > **FLAGGED FOR ATTORNEY DECISION.** A communication that announces the firm is ceasing
  > to be attorney of record is a scope-of-representation communication. Whether staff may
  > sign it is a judgment call, not a drafting one. The skill should default to attorney
  > signature and require an explicit override.
  > [CONFIRM LOCALLY: who may sign a notice that representation has ended — with
  > {{ROLE_APPROVER}}]
- **M04 used the email signature block, not a letter block** — no bar number, no `By:`
  line, no attachments list. If a sub-type is delivered by email, the signature bank above
  does not apply and a separate email block is needed.
  > **GAP.** No source provides an email-delivery signature block for a
  > representation-ending communication.
  > [CONFIRM LOCALLY: approved email sign-off block for scope-ending communications]

## Voice notes

- **Second person, imperative, unhedged.** `Do not rely on verbal side agreements.`
  `Get advice early.` `Keep records.` The firm gives instructions, not options.
- **Warnings are framed as consequences to the client, not as legal doctrine.** The
  anti-retaliation paragraph explains the practical harm before naming the rule.
- **The firm names the awkward thing out loud.** It says a closing letter is late. It
  says future questions may be billable. It says the file is closing because payment
  was not made. It does not soften these.
- **Warmth is bookended, never interleaved.** Thanks at the top, warmth at the bottom,
  and everything between is flat and operational.
- **Every sub-type ends with a scope fence.** Some version of `unless a new written
  agreement is signed` appears in every single template. Treat it as mandatory.
- Executed letters are more conversational than the system templates (`This is good
  news for you given the fact that...`). The system templates are tighter. A buyer
  installing this should pick a register and hold it.
- Enumerated not-responsible lists are long on purpose. Do not compress them.
- **In the money register (M10) the firm switches from imperative to declarative and adds
  typographic emphasis.** ALL-CAPS section heads, bold `Important:`, capitalized
  `STATUS: PAID IN FULL`, `does NOT create a credit balance`. This is the only executed
  closing that uses formatting to carry meaning, and the emphasis lands exclusively on
  the sentences that protect the firm.
- **The firm shows arithmetic rather than asserting a result.** Fees, credits, payments,
  and balances are each their own line. Nothing is netted silently.
- **Waivers are given and fenced in the same breath.** The courtesy is granted, priced as
  a loss to the firm, limited to one time, and stripped of any future credit value — all
  within one module. Consistent with the corpus-wide grant-then-close habit.

## Attorney flags

- **ESTATE PLANNING CONTAMINATION — CONFIRMED IN SOURCE, STRIPPED HERE.** The source
  closing system asserts in three places that the firm offers estate planning services,
  lists estate planning as a closing category, and contains a full estate planning
  closing letter template plus a cross-sell sentence inside the master client letter.
  All omitted. Any downstream build that reintroduces estate planning content is
  defective. If a purchasing firm *does* offer estate planning, that sub-type must be
  drafted from that firm's own material, not from this corpus.
- **CROSS-PRACTICE CROSS-SELL — CONFIRMED IN T-FORM-C, STRIPPED HERE.** Cross-practice or
  affiliated-business marketing language must not appear in a representation-ending letter.
  T-FORM-C contained such a paragraph; it is omitted in full. The source firm practices
  Florida family law only. This is a **second, independent contamination class** from
  estate planning, and it means the approved-forms library cannot be trusted to reflect
  current scope. Any downstream build that reintroduces a cross-sell of any kind is
  defective. A purchasing firm that genuinely offers other services must draft that
  paragraph itself.
  > Structural point for the skill: a closing letter is the worst possible place for a
  > cross-sell, because it sits directly beside the sentence disclaiming responsibility for
  > future work. The two paragraphs contradict each other.
- **`Click here to enter text.` CONFIRMED PRESENT IN AN APPROVED FORM.** T-FORM-C ships
  with unfilled Word content-control placeholders in the date, addressee, delivery-method,
  and salutation fields. The build rule against emitting that string is not hypothetical —
  it exists to prevent this exact form from being reproduced as-is. The skill must hard-fail
  on any residual `Click here to enter text.` before output.
- **Executed limited-scope closing (CL-3) now exists but is thin.** M04 is one email. It
  contains the mechanic, the scope recital, the opposing-counsel notification, and the
  rehire invitation. It contains **no** enumerated not-responsible list, **no** deadline
  ownership transfer, **no** no-tolling paragraph, **no** billing or trust statement, and
  **no** file-retention statement — on a case that was still pending. The system's CL-3
  template supplies all of those. A buyer must use the template's structure and M04's
  sentences, not M04 alone.
- **M10's fee-waiver module is the highest-liability text in this spec.** Waiving a
  contractual balance, characterizing the waiver as a firm loss, and denying any credit
  balance are all fee-agreement consequences. Every figure and the waiver decision itself
  require attorney sign-off; none of it may be generated as boilerplate. The
  `earned upon receipt and is not refundable` sentence is a recital of that firm's specific
  agreement and must be verified against the purchasing firm's own fee agreement before
  reuse — a flat fee that is not in fact earned on receipt under the local agreement makes
  this sentence false.
- **M10's hourly-comparison module invites a fee dispute.** Attaching a constructed
  hourly-equivalent invoice and asserting a savings figure puts an alternative valuation of
  the same work in the client's hands in writing. If the client later challenges the flat
  fee, the firm has supplied a competing number. Retained here because it is genuine firm
  language, but flagged: do not deploy without attorney direction, and never generate the
  hourly figure from an estimate.
  > [CONFIRM LOCALLY: whether the firm wants an hourly-equivalent comparison in closing
  > correspondence at all — with {{ROLE_APPROVER}}]
- **M10 omits every post-judgment warning** despite closing a matter with a final judgment
  and, by its own recital, child-related and financial-disclosure work. No
  orders-still-bind, no modifiability, no anti-retaliation, no records-retention paragraph.
  A fee-accounting closing must not replace a substantive closing; if the accounting letter
  is the closing letter, the CL-1 warning blocks have to be merged into it.
- **Live URLs in source.** Executed letters and the closing system carried live review
  links to three named platforms and a firm social page. All omitted; replaced with
  `[CONFIRM LOCALLY: firm review link]`. Never ship a hardcoded review URL.
- The CL-7 known-deadlines block must never go out blank or with placeholder text. It
  is either a real list or the express no-knowledge disclaimer.
- Do not send a closing letter that says representation ended if the firm is still
  counsel of record.
- Do not send a CL-4 letter that implies the firm represented the client in court.
- Do not close a matter with unresolved trust funds, refund issues, final invoice
  issues, or payment disputes without approval.
- Do not tell a client no deadlines remain unless the docket and attorney confirm it.
- Do not give tax advice.
- Do not advise the client to ignore or informally change a court order.
- Do not send post-judgment advice that conflicts with the final order.
- CL-1's modification/relocation/support/parenting clauses must be pruned to the
  matter. Sending a relocation warning in a no-child case is a defect.

## QC hard stops (verbatim from source, retained)

- Do not close the matter if attorney approval has not been received.
- Do not close a represented litigation matter without checking for pending hearings,
  deadlines, motions, proposed orders, or unresolved docket activity.
- Do not close a matter with unresolved trust funds, refund issues, final invoice
  issues, or payment disputes unless {{ROLE_APPROVER}} and [CONFIRM LOCALLY: which role
  handles trust and billing reconciliation at your firm] approve the plan.
- Do not leave final documents loose, mislabeled, or mixed with drafts.
- Do not mark a matter closed if there are unresolved tasks assigned to the firm.

## [CONFIRM LOCALLY] items

- [CONFIRM LOCALLY: file retention period and destruction policy — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: whether the firm offers estate planning; if not, the beneficiary clause must refer out]
- [CONFIRM LOCALLY: firm review link and which platforms to name]
- [CONFIRM LOCALLY: whether this circuit requires a Notice of Non-Representation, a Motion to Withdraw, or neither, when closing a still-pending case]
- [CONFIRM LOCALLY: whether the clerk in this county accepts a Notice of Updated Contact Information, and whether the firm files it without charge]
- [CONFIRM LOCALLY: trust refund reconciliation timeline — with the role that handles trust and billing reconciliation at your firm]
- [CONFIRM LOCALLY: relocation mileage and day thresholds current as of send date]
- [CONFIRM LOCALLY: how the {{PM_SYSTEM}} closing note is worded and who enters it]
- [CONFIRM LOCALLY: whether both appearing attorneys must sign, per this firm's practice]
- [CONFIRM LOCALLY: who may sign a communication announcing that representation has ended — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: approved email sign-off block for scope-ending communications]
- [CONFIRM LOCALLY: whether limited-scope re-engagement requires a new written agreement — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: who notifies opposing counsel that the firm is no longer attorney of record, and by what instrument]
- [CONFIRM LOCALLY: whether this firm offers any practice area outside family law; if not, no cross-sell paragraph may appear in any closing letter]
- [CONFIRM LOCALLY: whether the firm's flat fee is in fact earned upon receipt under its own fee agreement, before using the earned-on-receipt recital]
- [CONFIRM LOCALLY: whether the firm wants an hourly-equivalent value comparison in closing correspondence at all — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: the retention period that "our standard file retention policy" refers to — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: who authorizes a fee waiver and how the waiver is recorded in {{PM_SYSTEM}} and with the role that handles trust and billing reconciliation at your firm]
- [CONFIRM LOCALLY: the channel named for post-closing client questions — the source names a client portal, which may be {{UPLOAD_PORTAL}} or a separate system]

## Coverage

**Readiness standard for this spec is structural completeness, not example count.** Every
sub-type below has a full set of banks — opening, body modules, consequence/deadline
language, post-representation warnings, file retention, closing, signature — even where
only one example backs it. Remaining holes are named, not filled by invention.

examples harvested: 9 distinct sources (5 distinct matters; 1 firm closing system
containing 10 sub-type templates; 3 approved form letters)
round-2 delta: +2 distinct matters (M04, M10), +1 approved form letter (T-FORM-C)

distinct matters by sub-type:
- CL-1 / CL-2 (full representation): M01, M02, M03 — 3 matters
- CL-3 (limited scope): M04 — 1 matter (**new in round 2; previously template-only**)
- CL-5 (flat-fee task completed): M10 — 1 matter (**new in round 2; previously template-only**)
- CL-4, CL-6, CL-7, CL-8, CL-9, CL-10: 0 matters

structural banks completed in round 2:
- `notify-opposing-counsel` — previously **absent corpus-wide**; no letter or template said
  who informs the other side. Now sourced.
- `future-correspondence-comes-to-you` — consequence-to-client framing of the above.
- `rehire-invitation-on-limited-scope` — limited-scope re-engagement language.
- Email-delivered variant identified as a distinct delivery mode with its own signature
  requirements (bank itself still missing — see below).
- CL-3 escalated from template-only to executed-plus-template.
- **CL-5 escalated from template-only to executed-plus-template (M10)**, and with it an
  entire fee-accounting bank that no other sub-type had: agreements recital, payments
  ledger, per-agreement account summary, earned-on-receipt anchor, balance-waiver with
  no-credit-balance fence, hourly-equivalent value comparison, and
  conclusion-plus-file-availability.
- **Closing letter attaching a final invoice** — previously listed as a gap; M10 attaches
  an itemized invoice and references it in-text. Gap closed.
- **File-retention reference** — partially closed. M10 is the only source that points to a
  retention policy, though it does not state its terms.

gaps — **not found in any source:**
- Executed CL-4 (coaching), CL-6 (substitution), CL-7 (withdrawal
  granted), CL-8 (administrative/dormant), CL-9 (mediation), CL-10 (GAL) closing letters.
  These sub-types exist **only as untested templates**, never as a sent communication from
  a real matter. CL-3 and CL-5 are no longer in this list.
- Any executed substitution-of-counsel letter. Searched both by name and by content,
  including within material assembled for handoff to successor counsel; only intake,
  client-education, and portal-onboarding material was located.
- Any approved email signature block for a scope-ending communication.
- Any statement of who is authorized to sign a representation-ending communication.
- Any file-retention period, destruction schedule, or client file-request deadline. M10
  names a "standard file retention policy" but the policy itself was not located.
- Any closing letter addressed to a GAL matter's parties.
- Any mediation closing letter actually transmitted.
- Any executed trust-refund or credit-balance **refund** letter. M10 is the inverse case —
  a waiver with an express denial of credit balance — so the refund posture remains
  template-only.

partial coverage:
- CL-1, CL-2 and CL-5 are the only sub-types with both an executed matter example and a
  template.
- M10 supplies a complete money bank but no warning bank; the CL-1 warning modules must be
  merged in for any matter with live post-judgment obligations. Neither source is
  sufficient alone.
- All three executed matter letters predate the current closing system by several
  years, so the executed voice and the system voice diverge. Both are captured; a buyer
  must choose.
- Deduplication note: duplicate copies of the same forms were encountered repeatedly.
  Each distinct document is counted once, and re-encounters added no new sentences.
- CL-3's executed example is an **email**, and the corpus's letter-shaped banks do not
  cleanly apply to it. A buyer building CL-3 must decide letter vs. email before drafting;
  the two paths diverge at the signature block and at whether attachments exist at all.

## Tokens introduced by this spec

| Token | Substitutes |
|---|---|
| `{{SCOPE}}` | The limited scope the retainer covered, in the firm's own scope-recital formula. Replaces a prior undeclared single-brace form of the same token. |
| `{{DEADLINE_LIST}}` | The list of known pending deadlines and hearings in the CL-7 known-deadlines block. Never emitted empty — if there are none known, the express no-knowledge disclaimer is used instead. |
| `{{ATTACHMENT_LIST}}` | The enumerated attachments on the signature block. |
| `{{SUBSTITUTING_PARTY}}` | The actor who has substituted as counsel — new counsel, opposing counsel, or the client pro se (CL-6). |
| `{{MEDIATION_OUTCOME}}` | Full agreement, partial agreement, or impasse (CL-9). |
| `{{GAL_CONCLUSION_BASIS}}` | The instrument that ended the GAL appointment — court order, final report, final hearing, or discharge (CL-10). |
