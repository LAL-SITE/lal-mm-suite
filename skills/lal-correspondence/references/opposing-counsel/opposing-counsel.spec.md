# Opposing Counsel — Content Spec
lane: opposing-counsel
sources: 4 distinct matters + 10 templates
harvested: 2026-07-29

## When this fires

Any written communication from the firm to the other side. Five distinct
triggers, and the source material treats them as non-interchangeable:

1. **Appearance / initial contact** — the firm has been retained and the Notice
   of Appearance is filed. The letter and the filed Notice go out together.
2. **Discovery deficiency / meet-and-confer** — responses or mandatory
   disclosure have been served and are materially incomplete. Sent far enough
   ahead of the next procedural milestone to leave time to compel.
3. **Scheduling** — coordinating availability before approaching the court, or
   re-noticing an existing setting.
4. **Professional courtesy** — extension request, vacation notice, or a
   discrete reciprocal courtesy.
5. **Settlement transmittal** — a package, a counter, or a statutory proposal.

**Critical sub-lane distinction carried from the matter files:** where the other
side is *unrepresented*, this is not opposing-counsel correspondence. It is
correspondence to an unrepresented adverse party and carries a mandatory
disclaimer, a plainer register, and no assumption of legal knowledge. Two
matters in the harvest wrote directly to a pro se opposing party. Do not send
the counsel-facing version to a pro se party.

## Sub-types

| Sub-type | Signer | Matter-sourced? |
|---|---|---|
| Initial contact / notice of appearance | attorney | template only |
| Substitution of counsel | attorney | template only |
| Mandatory disclosure deficiency (12.285) | attorney | template only |
| Discovery deficiency / meet-and-confer (12.340 / 12.350) | attorney | template only |
| Subpoena duces tecum cover (12.351 / 1.351) | attorney | template only |
| Scheduling / joint availability | attorney or staff | matter-sourced |
| Re-notice / updated setting | attorney or staff | matter-sourced |
| Extension / vacation / professional courtesy | attorney | template only |
| Settlement package transmittal | attorney | matter-sourced |
| Response to counter-proposal | attorney | matter-sourced |
| Offer of judgment / proposal for settlement (§ 768.79 / 1.442) | attorney | template only |
| **Pre-service outreach to unrepresented adverse party** | attorney | matter-sourced |
| **Settlement offer to unrepresented adverse party** | attorney | matter-sourced |

⚠️ VERIFY: confirm rule and current text before relying on this. Applies to every
rule and statute number appearing in the table above.

## Required structure per sub-type

### All counsel-facing letters — common shell
1. Firm letterhead block
2. Date
3. Delivery line (`Via Email`)
4. Recipient block — counsel name, firm, address, email
5. `Re:` block — styling, case number, circuit / county / division, and a
   `Subject:` line naming the specific purpose
6. Representation statement — who the firm represents, in one sentence
7. Body (sub-type specific)
8. Deadline or ask
9. `Sincerely,` + attorney signature with bar number
10. Enclosures line
11. `cc:` line

### Deficiency letter (both flavors)
1. Common shell through representation statement
2. Purpose sentence naming the production and its date, the milestone that makes
   it time-sensitive, and the good-faith-conferral framing
3. `Background` — when served, when due, when responded, current posture
4. Numbered deficiency sections, tiered: high-priority first, then additional
5. Per item, four mandatory elements — see the bank below
6. Improper / boilerplate objections section (discovery flavor)
7. `Requested Response Deadline` with the fallback-identification instruction
8. Escalation sentence naming the rule and the relief
9. Signature, enclosures, cc

### Settlement package transmittal
1. Common shell, with `Confidential — For Settlement Purposes Only` in the
   Subject line
2. Numbered enclosure list
3. One-paragraph statement of what the package covers
4. Review-and-revert invitation routed through the firm, not party-to-party
5. **Inadmissibility paragraph — verbatim, non-negotiable**
6. Deadline plus the concrete consequence
7. Amicable-resolution close

### Response to counter-proposal (matter-sourced)
1. Common shell
2. Purpose sentence naming the documents being responded to
3. Issue-by-issue headed sections; within each, an `Agreed Items` list and a
   `Not Agreed` list
4. Per not-agreed item, the position plus the one-line basis
5. Where a factual claim by the other side is unsupported, a written-confirmation
   request rather than an argument
6. Reconciliation / methodology section where a computation is in dispute
7. `Authorized Settlement Position` — the single number or term the client has
   authorized, with a bulleted list of what it reflects
8. Enclosure reference to the supporting chart
9. Neutral close

### Pre-service outreach to unrepresented adverse party (matter-sourced)
1. Letterhead, date, `VIA EMAIL:` line
2. `Re:` line identifying the subject of the proceeding
3. First-name salutation
4. Identification — attorney name, firm, and who the firm represents
5. Counsel-referral sentence
6. Candour statement — what has been filed and why
7. Statement of the governing law in plain terms
8. Statement of what the client actually wants, narrowly framed
9. Pre-service rationale — why they are hearing from the firm before service
10. Proposed terms, presented as options rather than a single demand
11. Response deadline with the stated consequence
12. Warm close
13. Signature with bar number, `cc: File`
14. **Mandatory disclaimer paragraph**

## Salutation and address-block conventions

- Counsel is addressed `Dear [Mr./Ms. Last Name]:` — never by first name, never
  `Dear Counsel` unless the recipient is unidentified or the letter goes to a
  firm generally. One template uses `Dear Counsel:` for a disclosure deficiency
  letter addressed to a firm rather than a named lawyer.
- Colon after the counsel salutation. Comma after a first-name salutation to an
  unrepresented party.
- Delivery method is stated on the face of the letter, always.
- The `Re:` block carries styling, case number, circuit, county, and division on
  separate lines, then a `Subject:` line. The Subject line is where the specific
  purpose lives — the `Re:` block is identification only.
- Matter-sourced letters compress this: one `Re:` line with styling, case number,
  and county separated by pipes, then a plain-language purpose line. Both
  conventions appear in the harvest. [CONFIRM LOCALLY: whether the buyer's
  divisions expect the expanded or compressed caption block]
- Unrepresented-party letters carry a `Re:` line naming the subject of the
  proceeding and **omit the case number entirely** when the matter is pre-service.
- `cc:` appears on the face of the letter, not only in the mail client. Where the
  client is copied, the source flags it as a judgment call.

## Opening paragraph bank

**Situation: first substantive contact after retention**
> This firm has been retained to represent {{CLIENT_NAME}} in the above-styled
> matter. A Notice of Appearance has been filed with the Court and a copy is
> enclosed for your records.
[template-sourced]

**Situation: substituting in for prior counsel**
> This firm has been retained to represent {{CLIENT_NAME}} in the above-styled
> matter and is substituting in for prior counsel, [CONFIRM LOCALLY: prior
> counsel name and firm]. Enclosed for your records is the [Joint Stipulation
> for Substitution of Counsel / proposed Order for Substitution of Counsel].
[template-sourced]

**Situation: standard representation statement, all other sub-types**
> This firm represents the [Petitioner / Respondent], {{CLIENT_NAME}}, in the
> above-styled matter.
[template-sourced] — appears in nine of the ten templates as the opening move.

**Situation: mandatory disclosure production is deficient**
> This firm represents the [Petitioner / Respondent], {{CLIENT_NAME}}, in the
> above-styled matter. We write to identify a number of material deficiencies in
> {{OPPOSING_PARTY}}'s mandatory disclosure production served on {{DATE}}, and to
> request supplemental production prior to the parties' [next procedural
> milestone] now scheduled for {{DATE}}. We send this letter in the spirit of
> good-faith conferral under Fla. Fam. L. R. P. 12.285 with the goal of
> resolving these deficiencies short of motion practice.
[template-sourced]
⚠️ VERIFY: confirm rule and current text before relying on this.

**Situation: discovery responses are deficient**
> We write to identify a number of material deficiencies in {{OPPOSING_PARTY}}'s
> [responses to interrogatories / responses to request for production / both]
> served on {{DATE}}, and to request supplemental responses prior to [next
> procedural milestone] now scheduled for {{DATE}}. We send this letter in the
> spirit of good-faith conferral with the goal of resolving these deficiencies
> short of motion practice.
[template-sourced]

**Situation: transmitting a settlement package**
> Please find attached the following documents for your review:
[template-sourced] — the transmittal opens on the enclosure list with no
preamble.

**Situation: transmitting a final settlement package, matter-sourced**
> On behalf of our client, {{CLIENT_NAME}}, we are submitting the enclosed final
> settlement proposal in the above-captioned matter. After careful negotiation
> and in response to your client's stated preferences regarding [CONFIRM
> LOCALLY: the issue that drove the concession], {{CLIENT_NAME}} has authorized
> us to present this comprehensive resolution to all outstanding marital and
> domestic issues.
[matter-sourced]

**Situation: responding to a counter-proposal**
> I am writing in response to your client's counterproposals to the Parenting
> Plan and Marital Settlement Agreement. After review with my client, we are in
> agreement on several of the revisions you proposed. Where we do not agree, our
> position and the basis for our revised [CONFIRM LOCALLY: issue] offer are set
> forth below.
[matter-sourced]

**Situation: serving a statutory proposal for settlement**
> Pursuant to § 768.79, Fla. Stat. and Fla. R. Civ. P. 1.442, please find
> enclosed a Proposal for Settlement / Offer of Judgment served on your client
> this date.
[template-sourced]
⚠️ VERIFY: confirm rule and current text before relying on this.

**Situation: serving notice of a non-party subpoena**
> Pursuant to Fla. Fam. L. R. P. 12.351 and Fla. R. Civ. P. 1.351 as applicable,
> please find enclosed:
[template-sourced]
⚠️ VERIFY: confirm rule and current text before relying on this.

**Situation: coordinating availability before approaching the court**
> We write to coordinate availability for [hearing on (motion title) / final
> hearing / trial / mediation].
[template-sourced]

**Situation: first contact with an unrepresented adverse party, pre-service**
> My name is {{ATTORNEY_NAME}}. I'm an attorney with {{FIRM_NAME}}, and I
> represent {{CLIENT_NAME}}. If you have an attorney or decide to retain one,
> please have them reach out to me directly. Otherwise, feel free to contact my
> office.
>
> I want to be upfront with you about what's happening.
[matter-sourced]

## Body modules

### MODULE: issues-on-the-table (initial contact, optional)
Included only when a near-term milestone exists.
> As you are aware, [mediation / a hearing on (motion title)] is scheduled for
> {{DATE}}. My understanding of the issues currently on the table for resolution
> includes:
> • [CONFIRM LOCALLY: issue list — the source names child support, retroactive
>   child support, alimony, the parenting plan, and equitable distribution]
>
> If your client has a settlement proposal addressing any or all of these
> matters, we are open to reviewing it in advance of [mediation / the hearing] in
> an effort to streamline the process and potentially resolve the outstanding
> issues efficiently.
[template-sourced]

### MODULE: deficiency-item-four-part
The single most disciplined module in the OC library. Every item carries four
elements and no item ships without all four.
> {{ITEM_NUMBER}}. [Item title]
> Rule cite: Fla. Fam. L. R. P. 12.285(d)([number]); 12.285(b) (continuing duty).
> ⚠️ VERIFY: confirm rule and current text before relying on this.
> (a) what is missing, (b) what the rule requires, (c) the specific document or
> Financial Affidavit section where the inconsistency appears, and (d) the
> specific supplemental item requested.
[template-sourced]

For the interrogatory / RFP flavor the four parts are labeled explicitly:
> Interrogatory No. [#]: [restatement of the interrogatory]
> Response served: [quote or summarize the deficient response]
> Deficiency: [why the response is non-compliant — incomplete, evasive,
> improperly objecting]
> Requested supplemental response: [what a complete response would include]
[template-sourced]

### MODULE: deficiency-tiering
Two tiers, headed and numbered separately. High-priority items are not mixed
into the general list.
> I. High-Priority Deficiencies
> II. Additional Deficiencies
[template-sourced]

### MODULE: boilerplate-objection-waiver
> Identify objections that are boilerplate, overbroad, or unsupported. Cite the
> rule basis for waiver where applicable.
The source names the stacked formula — "vague, ambiguous, overly broad, unduly
burdensome, irrelevant, not reasonably calculated" asserted without elaboration
— and treats this section as the place the waiver argument is preserved for
later motion practice.
[template-sourced]

### MODULE: agreed-and-not-agreed-split
Matter-sourced structure for responding to a counter. Concessions are listed
first and in full; disagreements follow with a one-line basis each.
> [Issue heading]
> Agreed Items
> My client agrees to the following revisions proposed by your office:
> • {{CONCEDED_ITEM}}
>
> Not Agreed
> My client does not agree to:
> • [item], as [one-line basis]; and
> • [item]. [One-line basis stated as a rule or guideline reference.]
[matter-sourced]

### MODULE: unsupported-assertion-confirmation-request
Where the other side has asserted something orally or outside the documents, the
firm asks for it in writing instead of arguing it.
> My client has advised that your client has recently stated an intention to
> [CONFIRM LOCALLY: the asserted position]. No such proposal appears in the
> revised [document] we received. If your client is seeking any [relief], please
> confirm that request in writing so it can be addressed appropriately and in
> compliance with Florida law.
[matter-sourced]

### MODULE: consistency-reconciliation
Used when the other side has proposed treating one category of item favourably
to itself. The firm's move is to apply the other side's own rule symmetrically
rather than to reject it.
> The primary financial dispute arises from your client's request that
> {{CATEGORY}} be treated as [characterization]. In response to that position, my
> client completed a full reconciliation treating all assets and liabilities on
> both sides consistently, rather than selectively reclassifying only one party's
> {{CATEGORY}}.
>
> For clarity, the calculation is as follows (also reflected in the attached
> chart):
> 1. [Other side's asserted figure and their requested treatment]
> 2. [Our side's corresponding items that must be included if the same rule
>    applies]
> 3. [Baseline computation]
> 4. [Post-filing credits, with the statutory basis]
> 5. [Adjusted result]
[matter-sourced] — every figure omitted; the numbered skeleton is the reusable
asset.

### MODULE: authorized-position
The single authorized number is stated once, labeled as authorized, and followed
by a bulleted list of what it reflects.
> Based on the above, my client is authorized to offer {{AMOUNT}} as a final
> [equalizing payment / resolution] to resolve [issue] in full. This figure
> reflects:
> • consistent treatment of both parties' {{CATEGORY}},
> • proper credit for {{CATEGORY}} paid solely by {{CLIENT_NAME}}, and
> • a straight application of [CONFIRM LOCALLY: the governing statute].
[matter-sourced]

### MODULE: enclosure-list-numbered
> 1. Proposed Parenting Plan
> 2. Proposed Marital Settlement Agreement
> 3. Full Settlement Letter / Term Summary
> 4. [CONFIRM LOCALLY: financial summary, equitable distribution chart, child
>    support worksheet]
[template-sourced]

### MODULE: key-terms-summary-by-category
Matter-sourced. The final-offer letter summarizes terms under category headings
so counsel can brief a client without opening the agreement.
> KEY SETTLEMENT TERMS (SUMMARY):
> [Category heading — e.g. Equitable Distribution]
> [Two to three sentences stating what each party receives and what is not owed.]
> [Category heading — e.g. Support]
> [Amount, duration, commencement, modifiability, and the statutory basis.]
> [Category heading — e.g. Timesharing]
> [The schedule in summary, and the responsibility allocation.]
[matter-sourced] — all figures, dates, places, and durations omitted.

### MODULE: route-through-counsel
> Please review the attached documents carefully. If your client has any
> questions or would like to suggest changes, please contact our office and I
> will relay them to my client for consideration.
[template-sourced] — the firm routes everything through counsel and says so.

### MODULE: subpoena-objection-window
> Service on the records custodian is anticipated to occur on or about {{DATE}}.
> Any objection to the subpoena must be served within ten (10) days of the date
> this notice is served on your office, in accordance with Fla. Fam. L. R. P.
> 12.351(b). ⚠️ VERIFY: confirm rule and current text before relying on this.
>
> If you have any objection to the form or scope of the subpoena, please contact
> our office and we will confer in good faith. We anticipate compliance by the
> records custodian on or before {{DATE}}.
[template-sourced]

### MODULE: courtesy-three-options
Three mutually exclusive blocks. Exactly one ships.
> Option A — Request for Extension: We respectfully request a [#]-day extension
> of time to respond to [item], originally due on {{DATE}}. Our requested new
> deadline is {{DATE}}. [Brief reason if appropriate.] This is [our first / a
> second] request for extension. We anticipate that the additional time will
> allow us to provide a complete and considered response without need for
> further extension.
>
> Option B — Notice of Counsel's Vacation: Please be advised that the
> undersigned will be on a planned absence from {{DATE}} through {{DATE}}.
> During this period, please do not set hearings, depositions, or mediation. If a
> deadline falls during this period, we will be unable to respond and request
> that any deadline falling within the absence be extended by stipulation. The
> firm will be staffed during this period — emergency matters may be directed to
> {{FIRM_EMAIL}} and {{FIRM_PHONE}}.
>
> Option C — Professional Courtesy Request: We respectfully request the courtesy
> of [specific request]. [Brief reason.] We will of course extend the same
> courtesy to your office on the next appropriate occasion.
[template-sourced]

### MODULE: scheduling-availability-block
> Estimated time required: [time estimate]. Our office's availability for the
> next [60/90] days is as follows:
> • {{AVAILABLE_DATE}} at [available times]
>
> Please advise of your client's availability. Once we have mutual availability,
> we will coordinate with the Court / JA to set the matter on the Court's
> calendar. If you would like to propose alternative dates, please feel free.
[template-sourced]

### MODULE: re-notice-restate-operative-detail
> Updated date: {{DATE}}
> Reason for re-notice: [stipulated continuance / Court reset / mediator's
> unavailability / other]
> All other terms of the original notice — location, {{VIDEO_TOOL}} connection
> details, mediator, time required — [remain unchanged / are updated as noted in
> the enclosed Re-Notice].
>
> Please confirm receipt and update your calendar. The filed Re-Notice is
> enclosed.
[template-sourced]

### MODULE: plain-statement-of-law (unrepresented party)
Matter-sourced. The firm states the governing law neutrally, including the part
that is unfavourable to its own client's sympathy case, then explains why the
filing follows from it.
> In Florida, [statement of the legal rule in one sentence, no citation]. That's
> the law regardless of [the equitable consideration the reader is likely to
> raise]. [One sentence acknowledging the reader's likely position.] This filing
> is about fixing that. It is not about attacking you or making your life harder.
[matter-sourced] — the case-specific narrative that followed this pattern in the
source has been omitted entirely as re-identifying.

### MODULE: mutual-benefit-framing (unrepresented party)
> What {{CLIENT_NAME}} wants is straightforward: [the narrow relief, in plain
> words]. That's it. [Statement of what the client is not seeking.] A court order
> protects both of you — it means neither of you is at the other's mercy.
[matter-sourced]

### MODULE: pre-service-rationale (unrepresented party)
> We are reaching out before {{CLIENT_NAME}} is served because we'd genuinely
> rather work this out with you than go to a hearing. If you're open to it,
> here's what we're proposing as a starting point for a temporary arrangement.
[matter-sourced]

### MODULE: options-not-ultimatum (unrepresented party)
The firm presents two labeled alternatives rather than one demand, and says it
will take either.
> Option A — [label]:
> • [term]
> Option B — [label]:
> • [term]
>
> We're open to either option, or a combination that makes more sense for your
> schedules.
[matter-sourced]

## Demand / deadline / cure-period language bank

- **Discovery / disclosure cure deadline, with fallback identification:**
  > Please produce the supplemental items identified above no later than
  > {{DATE}}, so that the parties may proceed to [mediation / hearing / trial]
  > without delay. If any item cannot be produced by that date, please identify
  > (a) the item, (b) the reason for the delay, and (c) the date by which it will
  > be produced.
  [template-sourced] — the fallback clause is what converts a demand into a
  conferral. It appears in both deficiency templates verbatim.

- **Escalation sentence — disclosure flavor:**
  > We remain available to confer in good faith on any item in this letter. If we
  > do not receive the requested supplemental production or a written response
  > identifying the items in dispute by {{DATE}}, we will have no alternative but
  > to file an appropriate motion under Fla. Fam. L. R. P. 12.285 and seek the
  > relief available under the rule, including attorney's fees.
  [template-sourced]
  ⚠️ VERIFY: confirm rule and current text before relying on this.

- **Escalation sentence — discovery flavor:** identical construction, citing
  Fla. Fam. L. R. P. 12.380. [template-sourced]
  ⚠️ VERIFY: confirm rule and current text before relying on this.

- **Hard-deadline demand with clock time (matter-sourced):**
  > We require a written response to this offer on or before {{TIME}} on {{DATE}}
  > ([#] calendar days from the date of this letter). Your response should
  > either: (a) accept the offer and authorize execution of the enclosed
  > documents; (b) present a counter-proposal with specific modifications; or
  > (c) indicate your client's intent to proceed to mediation or litigation.
  [matter-sourced] — note the three enumerated permissible responses. The
  deadline carries a clock time, not just a date.

- **Consequence-bearing deadline, soft form:**
  > If we do not hear from you within [#] days, we will [proceed with the next
  > procedural step]. We hope to resolve this matter amicably and without further
  > litigation.
  [template-sourced]

- **Consequence-bearing deadline to an unrepresented party:**
  > Please respond to this office within ten (10) days. If you have questions or
  > want to talk through the [proposed terms], you're welcome to call my office.
  > If you're getting an attorney, just have them reach out.
  >
  > If we don't hear back, {{CLIENT_NAME}} will proceed with formal service and
  > we'll be requesting a temporary hearing. That's not what either of us wants.
  > A negotiated agreement is faster and a lot less disruptive.
  [matter-sourced]

- **Mediation fallback rather than litigation threat (matter-sourced):**
  > Should your client decline to accept this offer and is unable or unwilling to
  > present a reasonable counter-proposal by the deadline above, {{CLIENT_NAME}}
  > is prepared to immediately schedule a full-day mediation session to attempt
  > resolution of any outstanding issues. Our client is committed to reaching a
  > fair settlement and believes mediation is the appropriate next step if this
  > proposal does not result in an agreement. Please confirm your availability
  > and your mediator preference at your earliest convenience.
  [matter-sourced]

- **Statutory acceptance window:**
  > The Proposal is open for acceptance for thirty (30) days from the date of
  > service. If not accepted in writing within thirty (30) days, the Proposal
  > shall be deemed rejected.
  [template-sourced]

- **Statutory objection window:** ten (10) days from service on counsel, per
  Fla. Fam. L. R. P. 12.351(b). Jurisdictional — calendar it before the
  custodian is served. [template-sourced]
  ⚠️ VERIFY: confirm rule and current text before relying on this.

Deadline discipline observed across both sources: every deadline is tied to a
step the firm will actually take. The source is explicit that empty deadlines
train the other side to ignore them.

## Reservation-of-rights and preservation language

- **Settlement inadmissibility — keep verbatim:**
  > This proposal is offered for settlement purposes only and shall not be
  > admissible at trial except as provided in § 90.408, Fla. Stat.
  > [CONFIRM LOCALLY: whether any procedural rule on settlement communications
  > applies in your division, with the presiding judge's chambers]. This proposal
  > does not constitute an admission of liability or a waiver of any claim or
  > defense.
  [template-sourced] — flagged non-negotiable.
  ⚠️ VERIFY: confirm rule and current text before relying on this.

- **Caption-level settlement designation:**
  > Subject: Settlement Package — Confidential — For Settlement Purposes Only
  [template-sourced]

- **Matter-sourced variant, placed as a banner above the salutation:**
  > FOR SETTLEMENT PURPOSES ONLY (Not admissible in court except for purposes
  > allowed under [CONFIRM LOCALLY: the controlling fee-shifting authority in the
  > buyer's jurisdiction])
  [matter-sourced]

- **Statutory rights reservation:**
  > The Proposal is made in good faith and our client reserves all rights under
  > the statute and rule, including the right to seek attorney's fees and costs
  > in the event the Proposal is rejected and judgment is entered in accordance
  > with the statute.
  [template-sourced]

- **Objection waiver preservation:** see MODULE: boilerplate-objection-waiver.
  The deficiency letter is the instrument that preserves the waiver argument;
  the source treats failure to itemize as forfeiting it.

- **Continuing-duty citation:** disclosure deficiency items cite both the
  specific category and Fla. Fam. L. R. P. 12.285(b) for the continuing duty, so
  the demand covers documents that come into existence later.
  [template-sourced]
  ⚠️ VERIFY: confirm rule and current text before relying on this.

- **Confirmation-available-on-request reservation:**
  > [Confirmation email or correspondence from opposing counsel is available upon
  > the Court's request.]
  [template-sourced] — only include if the confirmation is actually in the file.

- **Evidence preservation:** a separate preservation-of-evidence letter exists in
  the source library in two versions, one to the party or their counsel and one
  to a third-party custodian. Not harvested into this spec — it belongs to the
  third-party lane. Noted so the gap is not mistaken for absence.

- **Unrepresented-party disclaimer — mandatory, closes the letter:**
  > This letter is from an attorney representing {{CLIENT_NAME}}. It is not legal
  > advice to you. You have the right to consult with your own attorney at any
  > time.
  [matter-sourced]

## Closing bank

- `We remain available to confer in good faith on any item in this letter.` [template-sourced]
- `Please advise of your client's position at your earliest convenience.` [template-sourced]
- `Please feel free to send any proposal at your convenience. I look forward to working toward a resolution.` [template-sourced]
- `We are available to discuss the Proposal at your convenience.` [template-sourced]
- `Thank you for your courtesy.` [template-sourced] — the default scheduling and procedural close.
- `Thank you for your attention to this matter.` [template-sourced]
- `I look forward to your response.` [matter-sourced] — the close on a substantive counter-response; no softening, no gratitude.
- `We hope to resolve this matter amicably and without further litigation.` [template-sourced]
- `I hope we can work together on this.` [matter-sourced] — unrepresented-party close.
- `Please direct all future correspondence, pleadings, notices, and discovery to the undersigned at the address and email above.` [template-sourced] — substitution close.

## Signature block

Counsel-facing, standard:
> Sincerely,
>
> {{ATTORNEY_NAME}}, Esq.
> Florida Bar No. {{BAR_NO}}
> {{FIRM_EMAIL}}

Matter-sourced letters show two live variants:
> Warmly,
>
> {{ATTORNEY_NAME}}, Esq.

> Sincerely,
>
> {{ATTORNEY_NAME}}, Esq.
> {{FIRM_NAME}}

`Warmly,` appears on a final settlement offer and on a pre-service outreach
letter to an unrepresented party — the firm uses it where it wants to signal that
an adversarial document is not personally adversarial. [CONFIRM LOCALLY: whether
the buyer's practice permits a warm valediction on a demand letter]

Unrepresented-party letters use a full signature block with a signature rule,
credential line, bar number, firm name, address, phone, and email, followed by
`cc: File`. [matter-sourced]

Bar number appears on counsel-facing correspondence in every template. Matter
practice is inconsistent — some sent letters omit it.

## Voice notes

- One-sentence representation statement opens almost every counsel-facing
  letter. It is never assumed, even where counsel plainly knows.
- Every substantive assertion is anchored to a rule, a statute, or a specific
  document. The templates cite; the matter letters cite and additionally attach a
  chart.
- Neutral characterization is enforced. The source explicitly contrasts
  acceptable and unacceptable phrasings, and the unacceptable version is always
  the one that editorializes about the other side's motives.
- Concessions are stated first, fully, and without hedging. The
  agreed-then-not-agreed order appears in every matter-sourced negotiation
  letter.
- Disagreement is expressed as a position plus a basis, never as an accusation.
  "My client does not agree to X, as Y" — two clauses, no adjectives.
- The firm answers an aggressive position by applying the other side's own logic
  symmetrically rather than by rejecting it. This is the most distinctive move in
  the OC harvest.
- Where the other side has asserted something outside the record, the firm
  requests written confirmation instead of arguing about it.
- Computations are shown, numbered, and attached. The letter states the method so
  the number is checkable.
- Only one number is ever labeled `authorized`.
- Deadlines are concrete and carry a named consequence. Clock times appear on
  hard deadlines.
- Reciprocity is stated explicitly in courtesy letters and tracked internally.
- Register shifts hard for unrepresented parties: contractions, second person,
  short sentences, no citations, no Latin, no defined terms. "That's it." "This
  filing is about fixing that."
- Even in the plain register the firm does not oversell. It names the adverse
  consequence of non-response in the same paragraph as the invitation to talk.
- No merits argument ever appears in a scheduling or procedural letter.
- Enclosures are enumerated, never gestured at.

## Attorney flags

- Every sub-type in this lane carries `Attorney approval trigger: REQUIRED` in
  the source. There is no staff-sendable OC letter in the library. Simple
  courtesy *confirmations* may go out over staff signature after the attorney has
  approved the underlying request.
- Deficiency letters must be built against the actual production, the filed
  certificate of compliance, and the filed financial affidavit. The source
  routes this work to a browser-based project, not to Cowork. Generic
  deficiency complaints draw generic responses.
- Cure deadlines must leave time to draft, file, and have heard a motion to
  compel before the milestone. Source specifies a two-week minimum buffer.
- Serve counsel before serving a records custodian. The rule sequence is not
  discretionary.
- Confirm § 768.79 actually applies before serving a proposal for settlement.
  The source is emphatic that it does not reach most equitable family-law claims
  — timesharing and parental responsibility — and applies to monetary claims.
  Rule 1.442's specificity requirements must be reviewed first.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- Pick exactly one option block in the courtesy template. Shipping a letter with
  competing option blocks is named as the most common formatting error.
- Never state a settlement figure that the client has not authorized in writing.
- Confirm the other side's representation status before choosing a template.
  Sending a counsel-facing letter to a pro se party, or omitting the disclaimer,
  is the highest-risk error in this lane.
- Pre-service outreach to an unrepresented party requires attorney sign-off on
  both the terms and the tone, and should be reviewed against the buyer's
  jurisdiction's rules on communicating with unrepresented persons.
- Do not include a child's name, date of birth, or school in correspondence to an
  adverse party unless identification is legally necessary.
- Substitution letters go out only after the order is entered, with the filed
  order attached — and only after prior counsel's file has been received or a
  transfer deadline set.
- Verify that any confirmation the letter says is "available upon request" is
  actually in the file.

## [CONFIRM LOCALLY] items

- Expanded versus compressed caption block, by division.
- Whether the client is copied on OC correspondence as a matter of practice.
- Local good-faith conferral requirements before a motion to compel — some
  circuits require a certificate, some a conference, some both.
- Local practice on vacation letters; some divisions have a local rule and a
  required lead time.
- The controlling fee-shifting and settlement-inadmissibility authority cited in
  the settlement banner.
- Whether the buyer's jurisdiction permits a proposal for settlement on the claim
  at issue.
- Whether bar number is required on outbound counsel correspondence.
- Whether a warm valediction is acceptable firm style on adversarial letters.
- Local rules governing communication with unrepresented adverse parties, and
  whether a prescribed disclaimer form exists.
- Objection window and service sequence for non-party subpoenas, and whether the
  parties have stipulated to different terms.
- Time-estimate convention — whether the buyer's JAs require a stipulated joint
  estimate.

## Coverage

matters harvested: 4 distinct
templates harvested: 10
matter-sourced bank entries: 17
template-sourced bank entries: 31

Provenance split by sub-type is recorded in the Sub-types table above. Five of
the thirteen sub-types have matter-sourced language; eight are template-only.

structural holes closed:
- Every bank in the required structure is populated.
- Two sub-types absent from the template library entirely — pre-service outreach
  to an unrepresented adverse party, and settlement offer to an unrepresented
  adverse party — were recovered from matter files and are now specified,
  including the mandatory disclaimer.
- The response-to-counter-proposal sub-type, also absent from the template
  library, was recovered from matter files with its full
  agreed/not-agreed/reconciliation/authorized-position structure.
- Demand, deadline, cure-period, reservation-of-rights, and preservation banks
  are complete and carry both provenances.

remaining holes:
- No matter-sourced example of a mandatory-disclosure or discovery deficiency
  letter in our own voice. The two deficiency letters found in the source matters
  were **incoming** — on another firm's letterhead — and
  were not harvested. Both banks for this sub-type are template-only.
- No matter-sourced initial-contact, substitution, subpoena-cover, offer-of-
  judgment, or extension/vacation letter.
- No cease-and-desist or conduct-complaint language. The settlement template
  cross-references a combined settlement-plus-cease-and-desist letter that does
  not exist in the reviewed library.
- No language for responding to an unreasonable or bad-faith OC letter.
- No sanctions-threat or fee-entitlement demand letter outside the deficiency
  escalation sentence.
- No language for withdrawing or correcting a settlement offer already served.
- No multi-party or intervenor variant; all sources assume two parties.
- No Spanish-language variant, despite unrepresented-party correspondence being
  the sub-type most likely to need one.
- Deficiency templates ship as pure scaffolding — no worked deficiency item
  exists anywhere in the library, so sentence-level voice for the substance of a
  deficiency entry could not be extracted, only its four-part discipline.

## Tokens introduced by this spec

- `{{ITEM_NUMBER}}` — the sequential number of a deficiency item in the tiered
  deficiency list.
- `{{CONCEDED_ITEM}}` — a specific revision the client agrees to, used in the
  Agreed Items list.
- `{{CATEGORY}}` — the asset, liability, or expense category in dispute in a
  reconciliation.
- `{{AVAILABLE_DATE}}` — a date the firm is offering in a scheduling block.
- `{{TIME}}` — the clock time on a hard response deadline.
- `{{OPPOSING_PARTY}}` — already a standard corpus token; introduced into this
  spec in place of bracket placeholders in the deficiency openings.
