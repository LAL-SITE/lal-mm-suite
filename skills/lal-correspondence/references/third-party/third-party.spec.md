# Third Party Correspondence — Content Spec
lane: third-party
sources: 4 distinct matters (M04, M05, M08, M09) + 1 firm-level template bank (T-PRESERVE)
harvested: 2026-07-29 (round 2 added M08, M09)

> **HARVEST INTEGRITY NOTE.** This spec falls short of the 25-matter target. The
> harvested corpus contains **no** expert engagement letters, **no** evaluator or
> psychologist engagement letters, **no** mediator engagement letters, **no** subpoena
> cover letters, and **no** process server instruction letters. Round 2 closed two
> previously open holes: GAL outreach addressed *to the collateral itself* (TP-5) and
> a court-appointment-based provider information-release instrument (TP-6).
> Everything below is real, tokenized, source-traceable language. Nothing below is
> invented. See `## Coverage` for the exact gap list.

## When this fires

A third-party letter fires when the matter requires written contact with someone who
is neither the client nor opposing counsel, and where the firm's authority to make
contact derives from a court appointment, an anticipated-litigation preservation duty,
or a pre-service settlement overture.

Three confirmed triggers in the corpus:

1. **Court-appointed neutral must notify parents and counsel that it will contact
   third parties.** Fires immediately after appointment, before the first collateral
   interview. (M04)
2. **Litigation is reasonably anticipated and relevant records sit with a third-party
   custodian.** Fires as soon as anticipation is reasonable — explicitly *before*
   filing, not after. (T-PRESERVE)
3. **The firm wants to resolve before formal service and the other side is
   unrepresented.** Fires after the petition is filed but before service is
   effectuated. (M05)

## Sub-types

| Code | Sub-type | Recipient | Source |
|---|---|---|---|
| TP-1 | GAL collateral-contact notice | Both parents / counsel | M04 |
| TP-2 | Preservation notice — third-party custodian | Bank, processor, employer, exchange, cloud provider, social platform | T-PRESERVE (Version B) |
| TP-3 | Preservation notice — opposing party or counsel | Other side | T-PRESERVE (Version A) |
| TP-4 | Pre-service outreach to unrepresented other parent | Unrepresented adverse party | M05 |
| TP-5 | GAL outreach **to the collateral contact itself**, on court-order authority | Treating therapist / provider | M08 |
| TP-6 | Consent to Release Information — tri-party GAL / consenting parent / provider | Provider, executed by parent | M08, M09 |

**Not found — no sub-type may be built for these without new source material:**
GAL transmittal of report; expert/evaluator engagement; mediator engagement;
subpoena cover letter; records-custodian production request (as distinct from
preservation request); process server instructions.

## Required structure per sub-type

**TP-1 — GAL collateral-contact notice**
1. `Re:` line naming the investigation and the specific issue
2. Authority statement — the appointment requires a thorough and neutral investigation
3. Definition of a collateral contact
4. Illustrative, non-exhaustive category list
5. Purpose — verification, objectivity
6. Limits — collaterals do not decide custody, do not control outcome
7. Confidentiality — what the GAL will and will not disclose to parents
8. Parent objection channel and its ceiling
9. Neutrality restatement
10. Signature as `Guardian ad Litem`, not as advocate

**TP-2 / TP-3 — Preservation notice**
1. Date; delivery legend (`VIA EMAIL & CERTIFIED MAIL`)
2. Recipient block — for TP-2, addressed to `Custodian of Records / Legal Dept.`
3. `Re:` line — Preservation Request / Preservation of Documents and ESI
4. Representation statement and anticipation-of-litigation statement
5. Account or entity identification (TP-2 only)
6. Scope of preservation with date range
7. Enumerated document and data categories
8. Metadata and native-format instruction
9. Enumerated immediate actions required
10. Third-party onward-notice obligation (TP-3 only)
11. Do-not-alter warning
12. Certification demand with a hard day count
13. Preservation cost paragraph
14. Reservation of rights (TP-3) / subpoena-is-coming note (TP-2)
15. Contact line, signature

**TP-4 — Pre-service outreach**
1. Delivery legend and `Re:` line identifying the child by name and DOB
2. Attorney self-identification, who the firm represents, counsel-routing instruction
3. Candor paragraph — what has been filed and why
4. Legal-reality explanation (why the filing was necessary)
5. De-escalation paragraph — what the client does *and does not* want
6. Explicit statement that the letter precedes service and why
7. Substantive proposal, broken into named options
8. Support figure and how it interacts with any payments already being made outside an
   order
9. `What Happens Next` — response deadline in days, and the stated consequence
10. Warm close
11. Signature block
12. **Mandatory closing disclaimer** — see Body modules

**TP-5 — GAL outreach to the collateral contact itself** (M08)
1. Date; salutation to the provider by name
2. Courtesy line
3. Self-identification as **court-appointed** Guardian ad Litem, with the matter
   identified and the court/division named
4. Enclosure reference — the appointment/directive order is attached
5. Authority consequence — because the order directs disclosure, no advance question
   list is required of the GAL
6. The specific ask: a time to speak, and about whom
7. Objection channel — invitation to review the order or consult the provider's own
   counsel
8. Firmness clause — the order is clear, so cooperation is expected without delay
9. Response-expectation close
10. Signature with credentials; no "Guardian ad Litem" role line in this letter — the
    role is carried in the body instead

**TP-6 — Consent to Release Information** (M08, M09)
Court-caption format, not letter format. Ten numbered clauses in fixed source order:
1.1 Parties involved · 1.2 Purpose · 1.3 Scope of Information · 1.4 Authorization ·
1.5 Duration · 1.6 Revocation · 1.7 Confidentiality · 1.8 Legal Compliance ·
1.9 Acknowledgment · 1.10 Signatures. Signature block is dual — consenting party
above, Guardian ad Litem below.

## Opening paragraph bank

**TP-1 opener (verbatim structure, tokenized):**
> As part of my appointment as Guardian ad Litem, I am required to conduct a thorough
> and neutral investigation focused on the best interests of the children. This
> process includes speaking not only with each parent and the children, but also,
> when appropriate, with collateral contacts.

**TP-3 opener:**
> We represent the Petitioner, {{CLIENT_NAME}}. This letter gives formal notice that
> litigation involving the parties regarding [CONFIRM LOCALLY: brief description of
> the dispute — e.g. dissolution of marriage, parenting, and financial matters] is
> reasonably anticipated. Accordingly, you and any persons or entities acting on your
> behalf are required to preserve all relevant documents and electronically stored
> information (ESI) described below. This legal preservation obligation applies
> regardless of format or location and includes backup and archived data.

**TP-2 opener:**
> Dear Custodian of Records / Legal Department:
>
> We represent {{CLIENT_NAME}}. Litigation is anticipated against {{THIRD_PARTY_NAME}}.
> We request that you immediately preserve and retain all documents and ESI (including
> metadata) related to the accounts and persons listed below, pending formal legal
> process (subpoena, court order).

**TP-4 opener:**
> My name is {{ATTORNEY_NAME}}. I'm an attorney with {{FIRM_NAME}}, and I represent
> {{CLIENT_NAME}}. If you have an attorney or decide to retain one, please have them
> reach out to me directly. Otherwise, feel free to contact my office.
>
> I want to be upfront with you about what's happening.

**TP-5 opener (M08):**
> Dear {{THIRD_PARTY_NAME}}:
>
> I hope this email finds you well. I am the court-appointed Guardian ad Litem in the
> matter of {{CLIENT_NAME}} and {{OPPOSING_COUNSEL}} [CONFIRM LOCALLY: the correct
> party-naming convention — the source names both parents, not counsel], Case No.
> {{CASE_NO}}, pending in {{COUNTY}} Family Court.

## Body modules

### MODULE `gal-collateral-definition` (TP-1)
> Collateral contacts are neutral third parties who have direct, real-world interaction
> with the children and may provide relevant information regarding the children's
> functioning and well-being. These individuals are not advocates for either parent and
> are not asked to take sides. Their role is limited to providing factual observations
> within the scope of their professional or personal interaction with the children.

### MODULE `gal-collateral-categories` (TP-1)
> Examples of collateral contacts may include, but are not limited to:
> - School personnel (teachers, administrators, counselors)
> - Medical or mental health providers
> - Childcare providers
> - Coaches or extracurricular supervisors

### MODULE `gal-collateral-purpose` (TP-1)
> Information obtained from collateral contacts assists in verifying concerns raised by
> either parent and helps ensure that recommendations are grounded in objective
> information rather than parental disagreement. This is a standard and expected
> component of any Guardian ad Litem investigation.

### MODULE `gal-collateral-limits` (TP-1)
> Collateral contacts do not make custody decisions and do not control the outcome of
> the case. Their input is considered alongside all other information obtained during
> the investigation.

### MODULE `gal-collateral-confidentiality` (TP-1)
> Please be advised that my communications with collateral contacts are part of my
> court-appointed duties. I will not disclose detailed statements made by collateral
> contacts to either parent, except as summarized in reports or recommendations
> submitted to the Court, as appropriate.

### MODULE `gal-collateral-objection-ceiling` (TP-1)
> If either parent has concerns regarding specific collateral contacts, those concerns
> should be raised in writing. However, the decision regarding which collateral
> contacts are consulted rests with the Guardian ad Litem, consistent with the scope of
> the appointment.

### MODULE `tp5-order-authority` (TP-5) — M08
> Attached, you will find the court order directing you to provide information to me in
> my role as Guardian ad Litem. As such, I am not required to submit a list of questions
> in advance. I am requesting a time to speak with you at your earliest convenience
> regarding {{THIRD_PARTY_NAME}} in accordance with the court's directive.

### MODULE `tp5-availability-ask` (TP-5) — M08
> Please provide your availability for a call at your earliest convenience.

### MODULE `tp5-objection-and-firmness` (TP-5) — M08
This module is load-bearing: it grants the provider a legitimate objection channel and
then closes it in the same breath.
> If you have any concerns regarding the order or your obligations, I encourage you to
> review it or consult with legal counsel as needed. However, as the order is clear in
> its requirements, I appreciate your cooperation in facilitating this conversation
> without further delay.

### MODULE `tp6-parties-and-purpose` (TP-6) — M08, M09
> **1.1 Parties involved.** This Consent to Release Information ("Consent") is made and
> entered into by and between {{CLIENT_NAME}} ("Consenting Party"),
> {{THIRD_PARTY_NAME}} (Therapist), and {{ATTORNEY_NAME}} serving as Guardian ad Litem.
> This release is on behalf of any consenting party individually, the parties jointly,
> and/or the parties on behalf of the following children in any combination applicable
> to the provider's relationship with the family, [CONFIRM LOCALLY: child names, with
> {{ROLE_APPROVER}}].
>
> **1.2 Purpose.** The purpose of this Consent is to authorize the release and exchange
> of information between the Guardian and {{THIRD_PARTY_NAME}}.

### MODULE `tp6-scope-of-information` (TP-6) — M08
> **1.3 Scope of Information.** The information to be released and exchanged may
> include, but is not limited to, first-hand impressions, recollections and
> observations, notes, medical records, educational records, psychological evaluations,
> social service records, and any other information pertinent to the welfare and best
> interests of the individual(s).

### MODULE `tp6-authorization` (TP-6) — M08
> **1.4 Authorization.** The Consenting Party hereby authorizes the Guardian to request,
> receive, and disclose information to and from any third parties, including but not
> limited to healthcare providers, educational institutions, social service agencies,
> and legal entities, as deemed necessary by the Guardian in the performance of their
> duties.

### MODULE `tp6-duration-and-revocation` (TP-6) — M08
> **1.5 Duration.** This Consent shall remain in effect until the termination of the
> Guardians' appointment as Guardian ad Litem unless revoked in writing by the
> Consenting Party prior to such termination.
>
> **1.6 Revocation.** The Consenting Party may revoke this Consent at any time by
> providing written notice to the Guardian. Such revocation shall not affect any actions
> taken by the Guardians prior to the receipt of the revocation notice.

### MODULE `tp6-confidentiality-compliance-acknowledgment` (TP-6) — M08
> **1.7 Confidentiality.** The Guardian agree to maintain the confidentiality of the
> information received and disclosed under this Consent, except as required by law or as
> necessary to perform their duties as Guardian ad Litem.
>
> **1.8 Legal Compliance.** The release and exchange of information under this Consent
> shall comply with all applicable federal, state, and local laws and regulations,
> including but not limited to the Health Insurance Portability and Accountability Act
> (HIPAA) and the Family Educational Rights and Privacy Act (FERPA).
>
> ⚠️ VERIFY: confirm rule and current text before relying on this.
>
> **1.9 Acknowledgment.** The Consenting Party acknowledges that they have read and
> understood the terms of this Consent and that they have the legal authority to grant
> such consent.
>
> **1.10 Signatures.** This Consent is executed by the Consenting Party and the
> Guardians as of the date set forth below.

### MODULE `preserve-scope-header` (TP-2 / TP-3)
> Scope of Preservation — Preserve all documents and ESI dated from [CONFIRM LOCALLY:
> date range start] through [CONFIRM LOCALLY: date range end] (or "all documents
> regardless of date" if appropriate) relating to:

### MODULE `preserve-categories` (TP-3)
Ten enumerated heads, kept in source order:
> 1. **Financial Records** — bank accounts, account numbers, deposit/withdrawal records,
>    check images, wire transfers, ACH traces, merchant settlement reports, credit card
>    statements.
> 2. **Income & Employment** — paystubs, W-2s, 1099s, payroll records, employment
>    agreements, commission statements.
> 3. **Business Records** — invoices, receipts, client lists, contracts, accounting
>    files, merchant processor statements.
> 4. **Payment Applications & Crypto** — peer-to-peer payment apps, exchange accounts,
>    wallet addresses, transaction logs, KYC information.
> 5. **Tax Records** — federal and state tax returns, schedules, attachments, K-1s.
> 6. **Retirement & Investment Accounts** — statements, distributions, QDRO drafts.
> 7. **Real Property & Title Documents** — deeds, mortgage statements, escrow
>    instructions.
> 8. **Communications & ESI** — emails, text messages, instant messages, direct
>    messages, workplace chat, video-conference recordings, voicemails, attachments.
>    Produce native files with metadata where possible.
> 9. **Devices & Backups** — laptops, desktops, tablets, phones (including deleted
>    data), backup systems, cloud accounts, servers.
> 10. **Litigation-Related Documents** — any documents reflecting efforts to delete,
>     transfer, obscure, or conceal assets or records relevant to the dispute.

### MODULE `preserve-custodian-categories` (TP-2)
> - All account statements, deposit/withdrawal items, images of deposited checks, ACH
>   trace records, wire transfer details, and memos.
> - All merchant settlement reports, payout summaries, chargebacks, refunds, dispute
>   details, and merchant IDs.
> - All KYC/identity-verification and account-application materials, IP logs, device
>   identifiers, and contact information.
> - All emails, messages, and internal notes associated with the account.
> - All transactional metadata and native electronic files.
> - Any records of account closures, transfers, freezes, or investigations.

### MODULE `preserve-metadata` (TP-2 / TP-3)
> Preserve Metadata & Native Files. Where documents exist electronically, preserve them
> in native format with associated metadata (creation date, last modified date,
> custodian, path, email headers, etc.). Do not convert to PDF-only versions that remove
> metadata as the sole preserved form.

### MODULE `preserve-immediate-actions` (TP-3)
> - Suspend any routine deletion, overwrite, or modification policies for all
>   custodians/records described above.
> - Suspend scheduled deletion, auto-purging, or recycling of email, chat logs, backup
>   tapes, and cloud content.
> - Preserve backup tapes, snapshots, archives, shadow copies, and disaster recovery
>   images.
> - Preserve mobile device data and any logs, even if the device is replaced.
> - Preserve login credentials and recovery keys for encrypted containers or cloud
>   accounts (do not provide them without subpoena or court order).

### MODULE `preserve-onward-notice` (TP-3)
> Third-Party Records & Custodians. If any potentially relevant documents or ESI may be
> held by third parties (banks, payment processors, exchanges, employers, social media
> companies), you must preserve all communications with those third parties and notify
> us promptly of their identity and contact details. We will pursue third-party
> preservation subpoenas where appropriate.

### MODULE `preserve-do-not-alter` (TP-3)
> Do Not Alter Evidence. You and persons acting on your behalf must not alter, delete,
> destroy, or conceal any potentially relevant documents, ESI, or devices. Alteration or
> destruction of evidence may lead to sanctions, adverse inferences, or other remedies
> under Florida law and the Florida Family Law Rules of Procedure.

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `preserve-subpoena-note` (TP-2)
> We recognize that third-party production may ultimately require a subpoena or court
> order. Nevertheless, courts routinely expect third parties to take voluntary
> preservation steps pending legal process. Your early preservation will avoid loss of
> critical records.

### MODULE `tp4-legal-reality` (TP-4)
The move is: state the legal posture flatly, then immediately disclaim hostility. Supply
the posture paragraph for the actual matter type; do not carry a posture sentence over
from a different matter type.
> In Florida, [CONFIRM LOCALLY: state the correct legal-posture proposition for this
> matter type — e.g. what rights a party does or does not hold absent a court order].
> That's the law regardless of the history between the parties. This filing is about
> fixing that. It is not about attacking you or making your life harder.

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `tp4-de-escalation` (TP-4)
> What {{CLIENT_NAME}} wants is straightforward: consistent, predictable time with
> {{CHILD_OR_CHILDREN}} and a seat at the table when decisions get made. That's it.
> {{CLIENT_NAME}} is not trying to take {{CHILD_OR_CHILDREN}} away from you or turn this
> into a battle. A court order protects both of you — it means neither of you is at the
> other's mercy.

### MODULE `tp4-pre-service-rationale` (TP-4)
> We are reaching out before {{CLIENT_NAME}} is served because we'd genuinely rather
> work this out with you than go to a hearing. If you're open to it, here's what we're
> proposing as a starting point for a temporary arrangement.

### MODULE `tp4-shared-parental-responsibility` (TP-4)
> Both parents make major decisions together — school, medical, the big stuff. Neither
> of you acts alone on anything significant. Both of you have full access to the
> {{CHILD_OR_CHILDREN}}'s records and can attend school and activity events. This is
> Florida's presumed standard and it's what's best for {{CHILD_OR_CHILDREN}}.

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `tp4-support-interaction` (TP-4)
The instructive pattern is: state the guidelines figure, then state how it interacts with
any payments already being made outside an order, then state readiness to begin. Do not
name a particular expense or arrangement.
> Based on both parties' incomes and the proposed schedule, Florida's child support
> guidelines put temporary support at approximately {{AMOUNT}} per month from
> {{CLIENT_NAME}} to you.
>
> If there are payments {{CLIENT_NAME}} has been making informally and outside of any
> order, and {{CLIENT_NAME}} agrees to the {{AMOUNT}} temporary support figure, those
> separate informal payments stop — the support payment replaces them.
>
> {{CLIENT_NAME}} is ready to start paying as soon as we have a written agreement or
> court order in place.

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `tp4-unrepresented-disclaimer` (TP-4) — **MANDATORY, never omit**
> This letter is from an attorney representing {{CLIENT_NAME}}. It is not legal advice
> to you. You have the right to consult with your own attorney at any time.

## Consequence / deadline language bank

| Sub-type | Deadline | Stated consequence |
|---|---|---|
| TP-3 | seven (7) days from date of letter | Certification demanded; spoliation relief reserved |
| TP-2 | five (5) business days | Subpoena or court order to follow |
| TP-4 | ten (10) days | Formal service proceeds and a temporary hearing is requested |

**TP-3 certification demand:**
> Certification & Acknowledgment. Please confirm, within seven (7) days of the date of
> this letter, that you have: (1) implemented a litigation hold for all relevant
> custodians; (2) suspended deletion/alteration routines; and (3) identified the
> custodians and locations of potentially relevant documents and ESI. Provide the name
> and contact information of the person responsible for preservation and the list of
> custodians you have instructed.

**TP-3 cost paragraph:**
> Preservation Costs. Please be aware that preservation may require technical steps that
> incur cost. We expect cooperation in tailoring preservation scope where reasonable to
> avoid undue burden, but preservation obligations are immediate and comprehensive until
> modified by agreement or court order.

**TP-3 reservation of rights:**
> Reservation of Rights. This letter is a preservation notice and not a waiver of any
> rights or claims. We reserve the right to seek appropriate relief for any spoliation
> or failure to preserve.

**TP-2 failure clause:**
> Failure to preserve may lead to court actions to prevent spoliation, including
> sanctions. We expect your cooperation in preserving these records.

**TP-4 consequence:**
> If we don't hear back, {{CLIENT_NAME}} will proceed with formal service and we'll be
> requesting a temporary hearing. That's not what either of us wants. A negotiated
> agreement is faster and a lot less disruptive for everyone, including
> {{CHILD_OR_CHILDREN}}.

## Closing bank

- TP-1: `I appreciate your cooperation as this investigation proceeds. My role is to remain neutral, thorough, and focused on the children's best interests.`
- TP-2/TP-3: `Thank you for your prompt attention. Please direct all correspondence to: {{ATTORNEY_NAME}}, {{FIRM_NAME}}, {{FIRM_PHONE}}, {{FIRM_EMAIL}}.`
- TP-3 alternate: `If you have any questions concerning the scope of this preservation request or the steps required, please contact me at {{FIRM_PHONE}} or {{FIRM_EMAIL}}. Thank you for your prompt attention to this matter.`
- TP-4: `I hope we can work together on this. [CONFIRM LOCALLY: warm child-specific line.]`
- TP-5 (M08): `I look forward to your response.` — one line, no thanks, no hedge.

## Signature block

**TP-1 (court-appointed neutral) — role line is load-bearing:**
```
Sincerely,

{{ATTORNEY_NAME}}
Guardian ad Litem
```

**TP-2 / TP-3:**
```
Sincerely,

{{ATTORNEY_NAME}}
{{FIRM_NAME}}
{{FIRM_PHONE}} | {{FIRM_EMAIL}}
```

**TP-4 — signed over a rule line, with cc and disclaimer beneath:**
```
Warmly,

__________________________________
{{ATTORNEY_NAME}}
Florida Bar No. {{BAR_NO}}
{{FIRM_NAME}}
{{FIRM_ADDRESS}}
{{FIRM_PHONE}} | {{FIRM_EMAIL}}

cc: File
```

**TP-5 (M08) — credentials-forward, no role line, contact channels beneath:**
```
{{ATTORNEY_NAME}}
{{FIRM_NAME}}
{{FIRM_PHONE}}
```
Source sent this as an email, not a letter, and appended the firm's social handle and
website link. **Strip both in any generated version** — do not reproduce handles or
links. [CONFIRM LOCALLY: whether your firm signs GAL collateral outreach with the role
line or with credentials only — with {{ROLE_APPROVER}}]

**TP-6 (M08, M09) — dual signature, court-caption instrument:**
```
Consenting Party:

_________________________
{{CLIENT_NAME}}

{{FIRM_NAME}}
{{FIRM_ADDRESS}}
{{FIRM_PHONE}}
Service E-Mail: {{FIRM_EMAIL}}

Guardian ad Litem

By: _________________________
{{ATTORNEY_NAME}}
Florida Bar No. {{BAR_NO}}
{{FIRM_EMAIL}}
```

## Voice notes

- **TP-1 is flat and institutional.** First person singular (`my appointment`,
  `I will not disclose`). No warmth, no hedging. Every paragraph either grants or
  limits. The GAL never says "I think" — it says "I am required to."
- **TP-2/TP-3 is dense, enumerated, and cold.** Bold run-in heads. Imperatives
  (`Preserve`, `Suspend`, `Do not convert`). Zero relationship language. The only
  concession is the cost-tailoring paragraph.
- **TP-4 is radically different — plain-spoken, contraction-heavy, almost
  conversational.** `I want to be upfront with you.` `That's it.` `the big stuff.`
  It names the emotional stake and disclaims hostility explicitly. This is the
  firm's distinctive register for writing to an unrepresented adverse party, and it
  is the highest-value voice in this lane.
- **TP-5 is polite-but-immovable.** It opens with a social courtesy (`I hope this email
  finds you well`), then pivots entirely to authority. The distinctive move is
  grant-then-close: it invites the provider to consult counsel and immediately says the
  order is clear anyway. `without further delay` is the operative phrase. Unlike TP-1,
  the GAL does not explain its methodology to a collateral — it just invokes the order.
- **TP-6 is instrument-voice, not letter-voice.** Court caption, decimal-numbered
  clauses, `shall`, defined terms in quotes on first use. It is drafted to be signed and
  filed or served, not read for persuasion.
- Across all sub-types the firm states the *reason* for the contact before making the
  *ask*. It never leads with the demand.
- Options are given descriptive names rather than being lettered abstractly — the name
  says what the option actually does — and each option is followed by a one-line
  plain-English summary of its practical effect.

## Attorney flags

- **TP-4 is unreviewed-risk-heavy.** Writing directly to an unrepresented adverse
  party with substantive settlement terms and a support figure requires attorney
  sign-off on every number and on the tone. The mandatory disclaimer is not optional
  and is not sufficient on its own.
- TP-1's confidentiality paragraph commits the GAL to withholding collateral
  statements from parents. Confirm this is consistent with the appointment order in
  the specific case before sending.
- TP-3's preservation scope as drafted is broad enough to draw an overbreadth
  objection. Source guidance says to narrow deliberately: *"Tailor the scope narrowly
  where possible to avoid objections for overbreadth. You can broaden later with
  subpoenas."*
- TP-2 must not request privileged material in a way that risks waiver. Source note:
  *"if privileged items are preserved, they should be logged in a privilege log when
  produced."*
- Any TP-4 support figure must be tied to a current guidelines worksheet, not to a
  prior estimate.
- **TP-5 must not be sent without the order actually attached.** The entire authority
  claim in the letter rests on the enclosure. The source letter's assertion that the GAL
  is "not required to submit a list of questions in advance" is an interpretation of the
  specific appointment order — it is not a general rule. Confirm the order says so.
- **TP-5 tells a provider to consult its own counsel while simultaneously discouraging
  delay.** Attorney should confirm this framing is acceptable in the division before use;
  a provider who is a party's treating therapist may hold privileges the parent has not
  waived.
- **TP-6 clause 1.4 is extremely broad** — it authorizes onward disclosure to and from
  "any third parties." Narrow it to the actual providers in the matter unless the
  appointment order supports the broader grant.
- **TP-6 clause 1.5** ties duration to termination of the appointment. If the GAL is
  discharged and later re-appointed, a fresh consent is required.
- TP-6 as harvested contains a typographical inconsistency in the source (`The Guardian
  agree`, plural/singular mismatch in 1.7 and 1.6). Fix on use; do not propagate.
- Providers may insist on their **own** HIPAA authorization form in addition to TP-6.
  One source packet contained a provider-supplied authorization alongside the firm's
  instrument. Expect to execute both.

## Sender checklist (from source, T-PRESERVE)

- Confirm accurate names, account numbers, and date ranges.
- Send via email to counsel/custodian AND certified mail (or overnight courier with
  signature).
- Include a read receipt request for email.
- Follow up by phone within 48–72 hours if no acknowledgement.
- Keep email/mail proof and save acknowledgements in the file.
- If custodian refuses to preserve, document refusal and prepare to move for a court
  order immediately.
- Timing: send the preservation letter as soon as litigation is reasonably anticipated
  — do not wait until filing.
- Identify key human custodians early, instruct them to preserve, and get signed
  acknowledgments.
- If data destruction is suspected, consider immediate forensic imaging of devices and
  servers.

## [CONFIRM LOCALLY] items

- [CONFIRM LOCALLY: whether the appointment order in this circuit permits the GAL to
  withhold collateral statements from parents — confirm with appointing judge's
  division procedures]
- [CONFIRM LOCALLY: preservation-letter date range — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: whether this circuit/division expects a preservation letter before
  filing or treats it as premature — with local counsel]
- [CONFIRM LOCALLY: certified-mail vs. e-service norms for third-party custodians in
  this county — with {{ROLE_INTAKE}}]
- [CONFIRM LOCALLY: whether pre-service outreach to an unrepresented party is
  customary before your division's judge — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: response-deadline day count acceptable in this circuit for
  pre-service outreach]
- [CONFIRM LOCALLY: substitute the correct legal-posture paragraph for non-paternity
  matter types in TP-4]

## Coverage

examples harvested: 6 of 25 target (4 distinct matters — M04, M05, M08, M09 — plus 1
firm-level template bank)
shortfall: 19

structural holes CLOSED in round 2:
- GAL outreach addressed *to the collateral contact itself* → TP-5 (M08)
- Provider information-release instrument on court-appointment authority → TP-6 (M08, M09)
- Provider records requests (therapy) → covered in substance by TP-5 + TP-6 together

gaps — **still not found in any source, do not build without new material:**
- Expert engagement letters (any discipline)
- Evaluator / social investigator / psychologist engagement letters
- Mediator engagement letters (mediator-side or party-side)
- Subpoena cover letters (to custodian, to witness, or to counsel)
- Records-custodian **production** requests as distinct from preservation requests
- School and non-clinical records requests (only therapy/clinical found)
- Process server instruction letters
- GAL transmittal letters (report, recommendations, discharge)
- Third-party transmittals of any kind
- Fee/retainer terms for any third-party neutral or expert

partial coverage:
- Preservation letters exist only as a firm-level template bank, not as sent/executed
  matter correspondence. No executed preservation letter was located in any matter
  file.
- TP-1 is still represented by exactly one letter from one GAL matter.
- TP-5 is represented by exactly one letter, to one clinical provider, in one matter.
  No non-clinical (school, coach, childcare) collateral outreach letter was found.
- TP-6 appears in executed form for three provider/parent pairings in M08 and in blank
  template form carrying an M09 party name — i.e. the same instrument reused across
  matters. Treated as 2 distinct matters, not 4 examples.

filename / contents mismatch noted at harvest:
- One source PDF is named as a consents packet but actually contains a mixed bundle: one
  GAL outreach letter, three executed release instruments, a provider's own HIPAA
  authorization form, and one blank release template bearing a *different* matter's party
  name. Filename would not have revealed any of this. Cross-matter content in a single
  file — flagged.

## Tokens introduced by this spec

| Token | Substitutes |
|---|---|
| `{{CHILD_OR_CHILDREN}}` | The child or children of the matter, referred to without name, gender, or number. Renders singular or plural as the matter requires; never carries a possessive pronoun. |
