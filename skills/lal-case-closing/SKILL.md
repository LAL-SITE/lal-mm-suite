---
name: lal-case-closing
description: "Controlled case-closing workflow, all matter types. Use for closing letters, closing packets, checklists, and closure approval - full rep, limited scope, flat-fee, withdrawal, GAL, mediation."
---

## When to use this skill (full trigger reference)

{{FIRM_NAME}} controlled case-closing workflow for all matter types. Use IMMEDIATELY on any closing task: drafting a closing letter, preparing the closing packet, running the closing checklist, requesting attorney closure approval, entering the {{PM_SYSTEM}} closing note, or marking any matter closed. Triggers on: "close the file," "close this matter," "draft the closing letter," "closing packet," "client terminated," "substitution of counsel," "withdrawal order entered," "dormant file," "administrative closure," "flat fee done," "limited scope complete," "DIY coaching done," "GAL appointment ended," "judgment entered — close it out," "mediation done — close the file," or any variation. Covers all matter types: full rep, limited scope, limited-scope coaching, flat-fee, substitution, withdrawal, administrative, mediation, GAL, and name change. Enforces attorney-approval hard stops before any letter is sent or matter is closed. {{ROLE_DRAFTER}} drafts — {{ROLE_REVIEWER}} reviews — {{ROLE_APPROVER}} approves.


## {{FIRM_NAME}} Firm-Wide Conventions (apply to every run of this skill)

These six conventions govern all {{FIRM_NAME}} skills and override any narrower instruction
below that conflicts with them.

1. **Environment-flexible.** Complete the task in the environment you are already in
   — chat, Desktop, or Cowork. If a different environment would be materially better,
   say so in one line and keep working. Never block, never redirect, never hand off
   instead of doing the work.
2. **Identity over lanes.** Staff assignments in this skill are defaults, not gates.
   Anyone may run any skill. **Attorneys self-approve** — if the person running this
   skill is {{ROLE_APPROVER}}, they *are* the approving attorney. Never tell an attorney to
   route their own work to an attorney for approval. Approval gates mean an approving-
   attorney action is recorded, not that the user must go find someone.
3. **Just run it.** Prerequisite stages are soft checks, never hard gates. Pause only
   for a physically necessary input, and ask for that specific item by name — never
   "complete Stage X first."
4. **Read files first.** Search the entire matter file — including misnamed and
   misfoldered documents — before declaring anything missing. If the file is
   disorganized, offer a file-organizer cleanup rather than reporting a gap.
5. **Transcripts preferred, never required.** A typed memo or rough notes always
   suffice as input.
6. **Write to the command center.** Every stage completion, deadline, lifecycle move,
   and attorney flag is written to the matter's command center before the run ends.

---

# {{FIRM_NAME}} CASE CLOSING SKILL

## SKILL IDENTITY
**Name:** lal-case-closing  
**Version:** 1.0  
**Effective:** May 2026  
**Approved by:** {{ATTORNEY_NAME}} & {{ATTORNEY_NAME}}  
**Primary Operator:** {{ROLE_DRAFTER}} (drafting) → {{ROLE_REVIEWER}} (review) → {{ROLE_APPROVER}} (approval + sign-off)  
**Source Document:** {{FIRM_NAME}} Case Closing System v1.0

---

## TRIGGER CONDITIONS

Fire this skill **immediately** on any of the following:

- "close the file," "close this matter," "close [client name]'s case"
- "draft the closing letter," "write the closing letter," "closing letter for [client]"
- "case is done," "judgment is entered — close it out," "mediation is done — close the file"
- "prepare the closing packet," "build the closing checklist"
- "client terminated," "substitution of counsel," "they got new counsel"
- "withdrawal order entered," "firm withdrew," "we're out"
- "dormant file," "administrative closure," "client stopped communicating"
- "DIY coaching is done," "limited scope is complete," "flat fee task is done"
- "GAL appointment ended," "discharge entered"
- "what do we need to close this," "are we ready to close," "can we close this matter"
- "{{PM_SYSTEM}} closing note," "enter the closing note," "close in {{PM_SYSTEM}}"
- "closing checklist," "staff email for closure approval"
- Any request to prepare, draft, or review any component of a case closing workflow

---

## NON-NEGOTIABLE ATTORNEY CONTROL

**Nothing in this skill finalizes itself.**

- Staff prepares the closing packet and drafts the closing letter
- **Attorney must approve closure before the matter is marked closed**
- **No closing letter goes out without attorney sign-off**
- **No matter is closed in {{PM_SYSTEM}} without attorney sign-off**
- All outputs from this skill are internal drafts only — route to {{ROLE_APPROVER}} before sending anything

---

## STEP 1 — CLASSIFY THE CLOSURE CATEGORY

Before drafting anything, identify the correct closure category. The category controls every output: letter language, checklist items, required warnings, billing language, and {{PM_SYSTEM}} note.

| # | Category | When to Use |
|---|----------|-------------|
| 3.1 | Full Representation — Final Judgment or Order | Final judgment, consent final judgment, final parenting plan, final support order, final modification order, final enforcement order, or other final court resolution entered |
| 3.2 | Limited-Scope Representation Closed | Firm completed a defined task (hearing, mediation, drafting, document review, specific stage) — not full case representation |
| 3.3 | limited-scope coaching Coaching Closed | Client retained coaching, document review, or form assistance — {{FIRM_NAME}} did NOT appear as counsel of record |
| 3.4 | Flat-Fee Task Completed | Defined flat-fee deliverable is complete (uncontested packet, name change, single hearing, agreed order, form prep) |
| 3.5 | Substitution of Counsel | New counsel appeared or client retained another attorney |
| 3.6 | Withdrawal | Court granted withdrawal or representation ended per rule and contract |
| 3.7 | Administrative Closure / Dormant | Client did not hire, did not pay, stopped communicating, chose not to proceed, or task never moved forward |
| 3.8 | Mediation Matter Closed | {{FIRM_NAME}} served as mediator or represented client in mediation and the mediation engagement is complete |
| 3.9 | GAL Matter Closed | GAL appointment ended — report obligations complete, Court discharged GAL, or file administratively closed after final order |

**If the category is unclear, ask before drafting.**

---

## STEP 2 — RUN THE QC HARD STOPS BEFORE ANYTHING ELSE

Check every item below. **If any hard stop applies, do NOT draft the closing letter and do NOT close the matter.** Flag the item and route to the responsible attorney or {{ROLE_REVIEWER}} with a written flag.

- [ ] Attorney approval has been received
- [ ] No pending hearings, motions, proposed orders, or unresolved docket activity (for represented litigation matters)
- [ ] Firm is NOT still counsel of record (if sending a letter that says representation ended)
- [ ] DIY closing letter does NOT imply the firm represented the client in court
- [ ] Limited-scope closing letter clearly defines the completed scope and the client's future responsibility
- [ ] No unresolved trust funds, refund issues, final invoice issues, or payment disputes (unless attorney and bookkeeping have approved a plan)
- [ ] Post-judgment advice does not conflict with the final order
- [ ] Relocation, child support, alimony, and parenting warnings are only included if they actually apply
- [ ] No statement that no deadlines remain unless docket AND attorney both confirm it
- [ ] No tax advice — always defer to a qualified tax professional
- [ ] No advice to ignore or informally change a court order
- [ ] Final documents are organized, labeled, and not mixed with drafts
- [ ] No open tasks remain assigned to the firm

**Any hard stop = flag and stop. Do not proceed.**

---

## STEP 3 — CLOSING INTAKE CHECKLIST

{{ROLE_DRAFTER}} completes this before requesting attorney approval. {{ROLE_REVIEWER}} reviews. Attorney signs off.

| Field | Value |
|-------|-------|
| Matter name | [INSERT] |
| Matter type | Dissolution / Paternity / Modification / Enforcement / Relocation / Name Change / Mediation / GAL / DIY / Limited Scope / Other |
| Closing category | [INSERT — see Step 1] |
| Attorney responsible | [INSERT] |
| Closure approved by attorney | YES / NO |
| Reason for closure | [INSERT] |
| Final order or judgment entered | YES / NO / N/A |
| Date of final order or judgment | [INSERT] |
| Final documents attached | [LIST] |
| Court docket reviewed | YES / NO / N/A |
| Pending hearings / motions / deadlines | NONE / LIST |
| Post-judgment deadline warning needed | YES / NO |
| Parenting plan involved | YES / NO |
| Child support involved | YES / NO |
| Alimony involved | YES / NO |
| Equitable distribution involved | YES / NO |
| Relocation warning needed | YES / NO |
| Medical / reimbursement language needed | YES / NO |
| Beneficiary update reminder needed | YES / NO |
| Tax disclaimer needed | YES / NO |
| Final invoice attached | YES / NO |
| Trust / retainer balance resolved | YES / NO / N/A |
| Refund owed | YES / NO / AMOUNT |
| Client owes balance | YES / NO / AMOUNT |
| Review request appropriate | YES / NO |
| Google review link included | YES / NO |
| Attorney review completed | YES / NO |
| Closing letter sent | YES / NO / DATE |
| Matter closed in {{PM_SYSTEM}} | YES / NO / DATE |

---

## STEP 4 — 10-STEP CLOSING PROCESS

**Step 1 — Confirm Closure Trigger**
Identify why the matter is closing. The closure reason controls the letter language and workflow. See closure categories in Step 1.

**Step 2 — Confirm Attorney Approval to Close**
Do not close just because the matter appears quiet. Attorney must confirm: no active representation obligation remains, no active court deadline remains, no required filing remains, no unresolved trust issue remains, and the correct closing category has been selected.

**Step 3 — Review Court Docket and File Status**
For represented litigation matters, check the docket or court portal. Confirm final judgment or order status, pending hearings, pending motions, pending proposed orders, pending notices, and upcoming deadlines. Do not assume a case is final just because mediation settled or parties signed an agreement.

**Step 4 — Confirm Final Documents**
Collect final documents to send or reference: Final Judgment, MSA, Parenting Plan, Child Support Guidelines Worksheet, Income Deduction Order, QDRO status note, final modification or enforcement order, dismissal, order of withdrawal, substitution of counsel, mediation agreement, name change final judgment, or any other final deliverable.

**Step 5 — Confirm Billing and Trust Status**
Confirm: final invoice status, outstanding balance, operating retainer or trust balance, refund owed, payment plan status, flat-fee completion status, and whether the final invoice should be attached. If funds remain unresolved, the file does not close without attorney or bookkeeping direction.

**Step 6 — Save and Organize Closing Packet**
Save the closing packet in the correct matter folder in {{DMS}} (ORDERS, AGREEMENTS, REPORTS and CLAUDE OUTPUT). Final versions are not left loose. The packet includes: final order or judgment, agreement, closing letter, final invoice or billing note, and any final deliverables. Draft-only documents remain clearly marked as drafts.

**Step 7 — Draft Correct Closing Letter**
Use the correct template (Step 5 below). Remove inapplicable clauses. Do not send relocation warnings in a no-child case. Do not send alimony tax language in a parenting-only case. Do not tell a DIY client the firm "concluded representation" if the firm never represented them.

**Step 8 — Attorney Review**
Route the closing letter to the attorney. The attorney confirms: attachments, scope language, legal warnings, deadlines, and billing or trust language. No closing letter goes out without this step.

**Step 9 — Send Closing Communication**
Send the approved closing letter through the approved communication method. Save the sent email or letter to the matter in {{PM_SYSTEM}} and to the {{DMS}} matter folder. If sent through {{PM_SYSTEM}} portal, save the portal message.

**Step 10 — Update {{PM_SYSTEM}} and Internal Systems**
After the closing communication is sent: update matter status, close tasks, remove or resolve future workflows, confirm no calendar events remain active unless necessary, enter the closing note (template in Step 6 below), save final documents, and mark the matter closed only after all closing requirements are complete.

---

## STEP 5 — CLOSING LETTER TEMPLATES

### CUSTOMIZATION RULES (apply to every template)
- Remove any warning that does not apply to the case
- Always confirm what is actually attached before sending — never leave [LIST DOCUMENTS] in the final letter
- Always confirm billing status before sending — use the correct billing clause (Step 7 below)
- Never tell a DIY or limited-scope client that "representation has concluded" if the firm never appeared — say the engagement or service has concluded
- All letters go on {{FIRM_NAME}} letterhead: {{FIRM_WEBSITE}} | {{FIRM_ADDRESS}} | Tel: {{FIRM_PHONE}}
- Closing letters use "Sincerely," — not "Warmly," — because closing letters are formal legal communications confirming the end of representation

---

**6.1 MASTER CLIENT CLOSING LETTER — FULL REPRESENTATION**

> [DATE]
>
> Re: Closing of Your Family Law Matter
>
> Dear [CLIENT FIRST NAME],
>
> Our representation of you in this matter has now concluded. Attached are copies of the final documents you should keep for your records, including [LIST FINAL DOCUMENTS]. Please save these documents somewhere you can access them later. You may need to refer to them if questions come up about support, parenting, property, reimbursement, enforcement, modification, or future compliance.
>
> Even though our representation has ended, the orders entered in your case still matter. You are responsible for following the Final Judgment, Parenting Plan, Marital Settlement Agreement, support order, or any other court order that applies to you. Do not rely on verbal side agreements. If you and the other party decide to do something different, you should get legal advice before treating that change as enforceable.
>
> [INSERT APPLICABLE WARNING CLAUSES FROM STEP 6]
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> This letter confirms that our representation in this matter has concluded. We are not responsible for future filings, deadlines, hearings, enforcement issues, modifications, appeals, rehearing deadlines, compliance issues, or new disputes unless a new written agreement is signed.
>
> It was a pleasure working with you. If you need help in the future with a modification, enforcement issue, mediation, or another family law matter, please contact our office. We would also appreciate your review of our services here: {{FIRM_REVIEW_LINK}}
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}
>
> Attachments: [LIST]

---

**6.2 SHORT CLOSING LETTER — FULL REPRESENTATION (SIMPLE MATTERS)**

Use when full representation has ended but the matter is simple and the full warning suite is not needed. Attorney still approves.

> [DATE]
>
> Re: Closing of Your Matter
>
> Dear [CLIENT FIRST NAME],
>
> Our representation of you in this matter has concluded. Attached are the final documents for your records: [LIST DOCUMENTS]. Please keep these documents somewhere safe because you may need them later.
>
> You remain responsible for following all court orders and agreements entered in your case. If the other party does not comply, or if your circumstances change, do not ignore the order or make informal changes without legal advice. Future issues such as modification, enforcement, child support, alimony, parenting, relocation, reimbursements, or property compliance may require a new legal review and a new written agreement with our office.
>
> This letter confirms that {{FIRM_NAME}} is no longer responsible for future filings, hearings, deadlines, or legal work in this matter unless we both sign a new agreement.
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> Thank you for trusting us with your case. If you need assistance in the future, please contact us. We would also appreciate your review: {{FIRM_REVIEW_LINK}}
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}

---

**6.3 LIMITED-SCOPE CLOSING LETTER**

> [DATE]
>
> Re: Completion of Limited-Scope Representation
>
> Dear [CLIENT FIRST NAME],
>
> The limited-scope service you retained {{FIRM_NAME}} to perform has been completed. Our work was limited to [DESCRIBE SCOPE]. That limited scope is now finished.
>
> This means we are not responsible for any future filings, deadlines, hearings, discovery, service requirements, mediation preparation, trial preparation, enforcement, modification, appeal, rehearing deadline, or court communication unless a new written agreement is signed.
>
> Please review your documents and court notices carefully. If you have future deadlines, you are responsible for meeting them unless you hire us again under a new agreement. If you are unsure about what comes next, contact our office before the deadline passes.
>
> Attached are the documents completed or provided as part of this limited-scope service: [LIST DOCUMENTS].
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> Thank you for allowing us to assist you. If you need additional help, you may contact us about a new limited-scope service, limited-scope coaching coaching, mediation, full representation, or another appropriate service.
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}

---

**6.4 DIY LEGAL COACHING CLOSING LETTER**

> [DATE]
>
> Re: Completion of limited-scope coaching Coaching / Unbundled Legal Service
>
> Dear [CLIENT FIRST NAME],
>
> This confirms that the limited-scope coaching coaching and unbundled legal service you retained us to provide has been completed. The service provided was [DESCRIBE SERVICE: coaching session, document review, form preparation, strategy session, procedural guidance, etc.].
>
> {{FIRM_NAME}} did not become your attorney of record in court unless there is a separate written agreement and a Notice of Appearance filed by our office. You remain responsible for filing your documents, serving the other party, monitoring deadlines, attending hearings, complying with court orders, and taking the next steps in your case.
>
> Attached are the materials provided as part of your limited-scope coaching service: [LIST DOCUMENTS]. Please review them carefully and save them for your records.
>
> This closes our current limited-scope coaching engagement. Future coaching, document review, drafting, representation, or court assistance requires a new agreement and payment arrangement.
>
> Thank you for using limited-scope coaching by {{FIRM_NAME}} If you need additional help, contact us before any deadline passes.
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}} / limited-scope coaching

---

**6.5 FLAT-FEE TASK COMPLETION LETTER**

> [DATE]
>
> Re: Completion of Flat-Fee Service
>
> Dear [CLIENT FIRST NAME],
>
> The flat-fee service you retained us to complete has been finished. The completed service was [DESCRIBE SERVICE]. Attached are the final documents or deliverables: [LIST DOCUMENTS].
>
> Unless your written agreement says otherwise, this flat-fee service does not include future filings, hearings, amendments, negotiations, enforcement, modification, court appearances, or additional legal advice after completion of the task. If additional work is needed, we will need a new written agreement or approved scope expansion.
>
> Please keep these documents for your records. If there is anything you are required to file, sign, serve, notarize, record, or provide to the Court or another party, that responsibility is listed here: [INSERT CLIENT RESPONSIBILITIES OR "No additional client action is currently required based on this completed task."]
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}

---

**6.6 SUBSTITUTION OF COUNSEL CLOSING LETTER**

> [DATE]
>
> Re: Closing of File Following Substitution of Counsel
>
> Dear [CLIENT FIRST NAME],
>
> This confirms that {{FIRM_NAME}} no longer represents you in this matter because [NEW COUNSEL / YOU] has substituted as counsel effective [DATE / ORDER DATE / NOTICE DATE].
>
> Your new counsel is responsible for future filings, deadlines, hearings, communications, and case strategy. We are not responsible for future work in this matter unless a new written agreement is signed.
>
> We have provided or will provide your file materials as follows: [DESCRIBE TRANSFER METHOD]. If your new counsel needs additional documents, they may contact our office.
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> We wish you the best moving forward.
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}

---

**6.7 WITHDRAWAL CLOSING LETTER**

> [DATE]
>
> Re: Closing of File Following Withdrawal
>
> Dear [CLIENT FIRST NAME],
>
> This confirms that {{FIRM_NAME}} no longer represents you in this matter. [The Court entered an order allowing withdrawal on [DATE] / Our representation ended effective [DATE] pursuant to [BASIS].]
>
> You are responsible for all future deadlines, hearings, filings, discovery, court communications, and compliance with court orders unless and until another attorney appears for you. If there are pending deadlines or hearings, they are listed below based on the information currently available to us:
>
> [LIST KNOWN DEADLINES/HEARINGS OR STATE "We are not aware of any currently scheduled hearings as of the date of this letter, but you are responsible for checking the court docket."]
>
> Attached are documents from your file that you should keep for your records: [LIST DOCUMENTS].
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}

---

**6.8 ADMINISTRATIVE CLOSURE / DORMANT FILE LETTER**

> [DATE]
>
> Re: Administrative Closure of File
>
> Dear [CLIENT FIRST NAME],
>
> We are administratively closing your file at this time because [REASON: the requested service was completed / we have not received the requested information / payment was not made / you advised you do not wish to proceed / there has been no activity or communication].
>
> This letter does not extend any court deadline or pause any requirement in your case. If you have a pending court case, you remain responsible for monitoring the docket, meeting deadlines, filing documents, attending hearings, and complying with all court orders unless you hire an attorney to handle those responsibilities.
>
> {{FIRM_NAME}} is not responsible for future work in this matter unless a new written agreement is signed.
>
> [INSERT BILLING LANGUAGE FROM STEP 7]
>
> Sincerely,
>
> [ATTORNEY NAME]
> {{FIRM_NAME}}

---

**6.9 MEDIATION CLOSING LETTER**

> [DATE]
>
> Re: Closing of Mediation Matter
>
> Dear [CLIENT / COUNSEL / PARTIES],
>
> This confirms that the mediation engagement in this matter has concluded. Mediation occurred on [DATE] and resulted in [full agreement / partial agreement / impasse]. [If applicable: The mediator's report has been filed with the Court.]
>
> If an agreement was reached, the parties remain responsible for ensuring the agreement is reduced to the appropriate written documents, signed, filed, and implemented. If the matter impassed, the case will proceed according to the Court's deadlines and any further orders.
>
> Attached are [MEDIATION REPORT / AGREEMENT / INVOICE / OTHER].
>
> Thank you for allowing {{FIRM_NAME}} to assist with mediation.
>
> Sincerely,
>
> [MEDIATOR NAME]
> {{FIRM_NAME}}

---

**6.10 GUARDIAN AD LITEM CLOSING LETTER**

> [DATE]
>
> Re: Closing of Guardian ad Litem File
>
> Dear [RECIPIENT],
>
> This confirms that the Guardian ad Litem appointment and file in this matter has concluded based on [COURT ORDER / FINAL REPORT / FINAL HEARING / DISCHARGE / OTHER].
>
> The GAL's role was limited to the appointment and authority granted by the Court. Any future investigation, testimony, report, review, or involvement would require further Court authorization or a new appointment.
>
> Attached are [FINAL REPORT / DISCHARGE ORDER / INVOICE / OTHER], if applicable.
>
> Sincerely,
>
> [GAL NAME]
> {{FIRM_NAME}}

---

## STEP 6 — POST-CLOSING WARNING CLAUSE BANK

Drop the applicable clauses into the closing letter. **Do NOT include a clause when it does not apply to the case.** The wrong warning in the wrong letter creates confusion and undermines the firm's credibility.

**MODIFICATION**
Some family law orders can be modified later, but only if the legal standard is met and the proper legal process is followed. A substantial change in circumstances may include major changes in income, employment, expenses, child-related needs, health, parenting circumstances, or other legally relevant facts. Do not assume a change is automatic. Get legal advice before relying on an informal agreement.

**ENFORCEMENT AND CONTEMPT**
If the other party does not comply with the order, keep records and seek legal advice. Do not retaliate by violating the order yourself. Your own noncompliance can hurt your ability to enforce the order later.

**CHILD SUPPORT**
Child support must be paid as ordered unless and until the Court changes the order. If you lose your job, your income changes, the parenting schedule changes, or the child's needs change, get legal advice quickly. Waiting can create arrears or enforcement problems.

**ALIMONY**
Alimony obligations and rights depend on the specific language of the order or agreement. Remarriage, death, supportive relationships, retirement, income changes, or other events may affect alimony depending on the facts and the order. Speak with an attorney before stopping, reducing, or relying on a change.

**PARENTING PLAN**
Follow the Parenting Plan unless a true emergency exists or the Court changes it. Keep communication focused on the child. Document issues. Do not use the child as messenger. Do not make unilateral changes simply because the other parent is difficult.

**RELOCATION**
Florida has specific relocation requirements when a parent wants to move more than fifty miles for sixty consecutive days or more. Do not move with a child, or agree to a move, without understanding the legal requirements.

**REIMBURSEMENT**
For reimbursements, keep proof of the expense, proof of payment, proof that the expense was shared or required, and proof that you requested reimbursement. If you only have verbal conversations, enforcement becomes harder.

**BENEFICIARY AND ESTATE UPDATE**
After divorce, separation, or major family changes, review your will, trust, power of attorney, health care documents, life insurance, retirement beneficiaries, payable-on-death accounts, and emergency contacts. Court orders do not automatically clean up every beneficiary issue. Speak with the appropriate professional to update these designations.

**TAX DISCLAIMER**
{{FIRM_NAME}} does not provide tax advice. Speak with a qualified tax professional about the tax impact of support, property transfers, retirement division, sale of property, dependency exemptions, filing status, or settlement terms.

**RECORDS AND DOCUMENTATION**
Keep copies of orders, agreements, proof of payment, reimbursement requests, messages, receipts, account transfers, and compliance documents. If a dispute arises later, documentation matters.

**Warning clause selection guide by matter type:**

| Matter Type | Include |
|-------------|---------|
| Dissolution with children, parenting plan, child support | Modification, Enforcement, Child Support, Parenting Plan, Relocation (if applicable), Reimbursement (if applicable), Beneficiary, Tax, Records |
| Dissolution without children | Modification (alimony only if applicable), Enforcement, Alimony (if applicable), Beneficiary, Tax, Records |
| Paternity | Modification, Enforcement, Child Support, Parenting Plan, Relocation (if applicable), Reimbursement (if applicable), Records |
| Post-Judgment Modification | Modification, Enforcement, Child Support or Alimony (as applicable), Records |
| Contempt / Enforcement | Enforcement, Records |
| Name Change | Records only |
| DIY / Coaching / Limited Scope | Records only — no substantive order advice |
| Administrative / Dormant | None or Records only |
| Mediation | None — mediator's letter does not advise parties |
| GAL | None — GAL's letter does not advise parties |

---

## STEP 7 — BILLING AND TRUST LANGUAGE BANK

Use the exact line that matches the case's billing posture. Confirm with bookkeeping before sending if any balance, refund, or trust amount is involved.

**FINAL INVOICE ATTACHED**
Attached is your final invoice for services rendered.

**NO BALANCE DUE**
As of the date of this letter, your account does not reflect a balance due.

**OUTSTANDING BALANCE**
As of the date of this letter, your account reflects a balance of [AMOUNT]. Please contact our office to make payment arrangements.

**REFUND PENDING**
Our records reflect a remaining trust or retainer balance of [AMOUNT]. The refund will be processed according to firm procedure after final reconciliation.

**FLAT FEE COMPLETE**
The flat-fee service has been completed and the fee has been earned according to the terms of your agreement.

**PAYMENT PLAN CONTINUES**
Your file is being closed, but your payment obligation remains active. Please continue making payments according to the agreed payment arrangement unless the firm confirms otherwise in writing.

---

## STEP 8 — STAFF EMAIL TO ATTORNEY REQUESTING CLOSURE APPROVAL

{{ROLE_DRAFTER}} sends this through {{PM_SYSTEM}} to {{ROLE_APPROVER}} before drafting the closing letter. **Internal communication only — never WhatsApp.**

> Subject: Closure Approval Needed — [Client / Matter]
>
> [Attorney],
>
> Please confirm whether this matter can be closed.
>
> Closure reason: [INSERT]
> Final order / judgment / deliverable: [INSERT]
> Pending hearings / deadlines found: [INSERT]
> Billing / trust status: [INSERT]
> Recommended closing letter type: [INSERT — see Step 1]
> Attachments to send: [INSERT]
>
> Please confirm approval to prepare and send the closing letter and mark the matter closed after completion.
>
> Thank you,
> {{ROLE_DRAFTER}}

---

## STEP 9 — {{PM_SYSTEM}} CLOSING NOTE

Paste into the matter's {{PM_SYSTEM}} notes when closing the file:

> Matter closed on [DATE] after attorney approval by [ATTORNEY]. Closure category: [CATEGORY]. Final documents saved: [LIST]. Closing letter sent to client on [DATE] via [METHOD]. Final invoice / trust status: [STATUS]. Pending deadlines reviewed: [NONE / LIST]. Future work requires new written agreement unless otherwise noted.

---

## STEP 10 — STAFF {{PM_SYSTEM}} CLOSING GUIDE

{{ROLE_DRAFTER}} completes the following before a matter is marked closed in {{PM_SYSTEM}}. {{ROLE_REVIEWER}} reviews. Attorney signs off.

- [ ] Confirm attorney approval to close
- [ ] Confirm closure category
- [ ] Review docket if the firm appeared as counsel
- [ ] Confirm no pending hearing, mediation, trial, motion, deadline, or proposed order remains unresolved
- [ ] Confirm final order, judgment, agreement, or deliverable is saved
- [ ] Confirm final invoice, trust balance, refund, or outstanding balance status
- [ ] Draft correct closing letter using the right template (Step 5)
- [ ] Attach final documents
- [ ] Route closing letter to attorney for approval
- [ ] Send approved closing letter through approved method
- [ ] Save sent communication to {{PM_SYSTEM}} and the matter folder
- [ ] Enter closing note in {{PM_SYSTEM}} (Step 9 template)
- [ ] Close or resolve open tasks
- [ ] Remove or complete workflows that no longer apply
- [ ] Check calendar for future events and remove unnecessary ones
- [ ] Confirm documents are organized in final folders
- [ ] Mark matter closed only after all above items are complete

**Log all time spent on closing workflow in {{PM_SYSTEM}}. Closing work is billable unless the matter is flat-fee complete or administratively closed without further charge.**

---

## AI PROMPT (SECTION 13)

When a staff member uploads case facts and asks Claude to prepare a closing packet, use this framework:

**Classify first.** Choose the closure category (Step 1). Confirm {{FIRM_NAME}}'s role (counsel of record, limited-scope, mediator, GAL, DIY/unbundled).

**Run QC hard stops** (Step 2). If any hard stop applies, flag it and stop. Do not proceed to drafting.

**Gather the following facts before drafting:**
- Matter name
- Matter type
- Closure reason
- Attorney responsible
- Was {{FIRM_NAME}} counsel of record: YES / NO
- Final order / judgment / deliverable entered or completed
- Date of final order or completion
- Final documents to attach
- Known pending deadlines / hearings / motions
- Billing status
- Trust / retainer status
- Refund or balance issue
- Client-specific warnings needed: Modification / Enforcement / Child Support / Alimony / Parenting / Relocation / Reimbursements / Property Transfer / Tax / Beneficiary / None
- Review request appropriate: YES / NO
- Desired output: closing checklist / staff email to attorney / client closing letter / {{PM_SYSTEM}} closing note / all of the above

**Draft in {{FIRM_NAME}}'s direct, practical, legally careful style.** Do not invent facts. Do not include inapplicable warnings. Make clear whether representation has ended, whether future work requires a new written agreement, and what the client remains responsible for.

**End every draft with an attorney-review items block** listing what the attorney must confirm before the letter is sent.

**All output is an internal draft only.** State this at the top of every output produced by this skill.

---

## IMPLEMENTATION NOTES

**Sign-off language:** Closing letters use "Sincerely," — matching {{FIRM_NAME}}'s historical legal-letter style. The Brand Kit's "Warmly," guidance applies to client emails and non-legal branded output. Closing letters are formal legal communications confirming the end of representation.

**Review link:** Include Google review link for full representation closings and short closings. Omit from withdrawal, dormant, substitution, and GAL letters.

**Letterhead:** All letters are content-only in draft. Final version goes on {{FIRM_NAME}} letterhead: {{FIRM_WEBSITE}} | {{FIRM_ADDRESS}} | Tel: {{FIRM_PHONE}}

**Estate planning:** {{FIRM_NAME}} does not offer estate planning. Use the generic "beneficiary update reminder" clause and defer the client to the appropriate professional. Do not add an estate planning closing category unless the Brand Kit is updated first.

**{{PM_SYSTEM}} linkage:** Every minute {{ROLE_DRAFTER}} spends preparing a closing packet, drafting the letter, or updating the file must be logged in {{PM_SYSTEM}}.

---

---

## MANDATORY HANDOFF — PRE-FILING QC GATE

Any document this skill produces that will be **filed with a court, served on a
party, or sent outside the firm** goes to `lal-prefiling-qc` before it reaches
an attorney. This handoff is not optional and is not skippable for urgency.

```
THIS SKILL  →  lal-prefiling-qc  →  ATTORNEY SIGN-OFF  →  FILE / SERVE / SEND
```

- Do not present a draft as "ready for {{ROLE_APPROVER}}" or "ready to file" until the gate has run.
- A **BLOCKED** verdict returns the draft here for correction. Fix and re-run the gate.
- A **CONDITIONAL** verdict goes to the attorney with the findings attached.
- Never resolve a flagged item by deleting the language to make the gate pass.

- After the gate clears, hand the document to `lal-finalize-draft` to produce the
  filing-ready Word file and PDF. That skill enforces portrait, Times New Roman 12,
  all black, single spacing, the {{FIRM_NAME}} caption layout, strips every internal artifact,
  and checks `lal-judicial-procedures` for the assigned judge before output.

**Approval behavior:** if the person in the session is an {{FIRM_NAME}} attorney ({{ROLE_APPROVER}} or
{{ROLE_APPROVER}}), her instruction IS the sign-off — do not ask her to approve what she just
directed. If staff, every attorney-gated item routes to {{ROLE_APPROVER}} and waits.

---

## OUTPUT DELIVERY — FIRM STANDARD (v2, {{DMS}}-native)

All output from this skill is delivered through `lal-file-connector` (Operation 4).

**Destination:** `Notes/` in the {{DMS}} matter folder
`Last, First - [Matter Type] (####-####)`. There is no `CLAUDE OUTPUT` folder and
no {{DMS}} path. (`GAL Notes/` on GAL matters.)

**Filename:** `MM.DD.YY - LastName - DocTitle - v1.ext` — versioned, never overwritten.

**Delivery depends on where this skill is running:**

- **Claude.ai (chat / Projects)** — Claude cannot write to {{DMS}}. Present the file
  as a **download** and print the destination block: matter folder → `Notes/`, filename,
  version. Never write "saved to {{DMS}}."
- **Cowork (desktop)** — write to the folder designated for the session (ask once at
  first delivery, reuse thereafter), confirm the **actual path written**, and state
  where the file belongs in {{DMS}}.

Nothing is filed or sent without attorney sign-off. Time is tracked in {{PM_SYSTEM}},
including Claude-assisted work.

