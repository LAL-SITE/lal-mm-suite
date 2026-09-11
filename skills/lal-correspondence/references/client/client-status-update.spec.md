# Client Status Update — Content Spec
lane: client
sources: 7 distinct matters + 3 firm-agnostic master templates
harvested: 2026-07-29

## When this fires

Three distinct triggers, three distinct documents. They are not interchangeable
and the source is emphatic on that point.

1. **Monthly cadence** — sent to every active matter on a fixed day each month,
   scheduled in {{PM_SYSTEM}} so clients learn to expect it. Procedural recap
   only.
2. **Settlement posture change** — sent when an offer or counter-offer lands and
   the client must make a decision. Substantive; attorney-drafted.
3. **Hearing scheduled** — sent immediately on receipt of the notice of hearing,
   to lock the date in the client's calendar.

Hard rule from source: the monthly status email is never the vehicle for bad news
or substantive strategy. Those get a separate dedicated message.

**Second-pass finding — two live sub-types the masters do not describe.** The
matter harvest turned up a substantial body of sent status correspondence across
seven matters, and it does not map cleanly onto the three master triggers. Two
additional sub-types are in active use:

4. **Document-status / outstanding-items update** — sent after the firm reviews a
   client production. Acknowledges what arrived, names what is missing, explains
   why it matters, and repeats the upload route. Deadline-free by design. The
   most frequently sent status document in the harvest, appearing in five
   matters.
5. **Settlement recommendation with decision checklist** — the live form of the
   settlement posture update. Substantially more granular than the master: it
   attaches reconciliation charts, splits every issue into recommend-agreeing
   versus recommend-holding, and closes with a numbered Yes/No checklist rather
   than three fixed reply options.

Neither is a variant of the monthly cadence. Both are attorney-drafted.

## Required structure

### Monthly status
1. Subject line with matter identifier and period
2. Salutation
3. Cadence reminder (why this arrives when it does)
4. WHERE WE ARE RIGHT NOW — 2–4 sentence plain-language posture summary
5. WHAT HAPPENED THIS MONTH — bulleted, each with a date
6. WHAT'S COMING UP — bulleted, each with a date
7. WHAT WE NEED FROM YOU — bulleted, each with a deadline
8. Acknowledgement request
9. Signature block

### Settlement posture update
1. Subject line
2. Salutation
3. Purpose statement (giving a clear picture so the client can decide)
4. WHAT'S ON THE TABLE
5. WHERE WE AGREE
6. WHERE WE DON'T — our position vs. theirs, side by side
7. HOW I READ THE STRENGTHS AND RISKS — ranged, never predictive
8. MY RECOMMENDATION — with reasoning
9. YOUR DECISION — three fixed reply options
10. Anti-pressure close
11. Attorney signature with bar number

### Hearing / court date confirmation
1. Subject line with hearing type, date, time
2. Confirmation sentence
3. HEARING DETAILS block
4. Calendar instruction
5. Forward-reference to the prep email, with a fallback date
6. Conflict-reporting instruction
7. Signature block

## Subject line bank

Observed, tokenized:

- `[CONFIRM LOCALLY: case surname or matter identifier convention] — Case Status Update for {{DATE}}`
- `Where We Stand on Settlement — [CONFIRM LOCALLY: case identifier]`
- `Confirmed — Your [CONFIRM LOCALLY: hearing type] on {{DATE}}`

Pattern holds across all three: em dash separator, no case numbers in subject
lines, plain English hearing/posture labels rather than procedural titles.

## Opening paragraph bank

**Situation: routine monthly cadence**
> {{CLIENT_NAME}},
> Here is your monthly status update on your case. We send these around the
> [CONFIRM LOCALLY: day of month] of each month so you always know where things
> stand.

**Situation: quiet month, nothing moved**
> This month was quiet — we're waiting on [CONFIRM LOCALLY: the pending item].
> Here's what we're doing in the meantime.

The source directs staff to say this honestly rather than manufacture activity.

**Situation: settlement offer or counter on the table, client decision needed**
> {{CLIENT_NAME}},
> I want to give you a clear picture of where we are on settlement so you can make
> decisions with full information.

**Situation: hearing has been noticed**
> {{CLIENT_NAME}},
> This confirms your [CONFIRM LOCALLY: hearing type] is scheduled as follows:

**Situation: settlement posture change with a revised recommendation (matter-sourced)**
> Dear {{CLIENT_NAME}}:
> I want to update you on where settlement stands and explain a revised
> recommendation after completing a detailed review of both the financial issues
> and the [CONFIRM LOCALLY: the other document in play].
[matter-sourced] — note "revised recommendation" stated up front. The firm flags
that its own advice has changed rather than burying it.

**Situation: client production reviewed, items still outstanding (matter-sourced)**
> {{CLIENT_NAME}},
> Thank you for sending over the [document category] — we've received the
> [items] you uploaded, including [the item that resolves a known gap]. That
> [item] wasn't listed on your Financial Affidavit, so having these now lets us
> get it added and keep your disclosure accurate. Nice work getting these together
> quickly.
>
> As we go through everything, here's where things stand:
[matter-sourced] — opens on acknowledgement and praise, names the specific value
of what arrived, then transitions with a plain hinge sentence.

**Situation: financial analysis complete, options to present (matter-sourced)**
> Hi {{CLIENT_NAME}},
> I've reviewed all of your financial information, including your affidavit and
> the supporting tax records. Below is a summary of your options.
[matter-sourced]

## Body modules

### MODULE: where-we-are-right-now
> WHERE WE ARE RIGHT NOW
> [Plain-language summary in 2–4 sentences. Identify procedural posture, what was
> filed / served / received this period, and what the focus is right now.]

### MODULE: what-happened-dated
Every bullet carries a date. Source examples reference opposing counsel service,
own-side production, and scheduling confirmations.

> WHAT HAPPENED THIS MONTH
> • Opposing counsel served their Financial Affidavit on {{DATE}}.
> • We completed your mandatory disclosure production through
>   {{CLIENT_UPLOAD_TOOL}} on {{DATE}}.
> • We confirmed mediation availability with opposing counsel for {{DATE}}.

### MODULE: whats-coming-up
> WHAT'S COMING UP
> • [Upcoming item — with date]

### MODULE: what-we-need-from-you
Always deadline-bearing. Never open-ended.

> WHAT WE NEED FROM YOU
> • [Action item — with deadline]

### MODULE: settlement-positions-split
Agreement and disagreement are separated into two headed lists, and the
disagreement list states both sides.

> WHERE WE AGREE
> • [Issue — resolved or near-resolved]
>
> WHERE WE DON'T
> • [Open issue — our position vs. their position, in plain terms]

### MODULE: strengths-and-risks-ranged
The single most constrained module in the library. Outcomes are ranged; never
predicted.

> HOW I READ THE STRENGTHS AND RISKS
> [2–4 sentences. Honest assessment of strengths and weaknesses on the open
> issues. Where we have leverage, where they do, and where {{JUDGE}} is likely to
> land if the issue goes to court. Range outcomes, not predictions.]

Permitted form: "If this goes to court, you can reasonably expect a result
between X and Y."
Prohibited form: "You will win."

### MODULE: recommendation-with-reasoning
> MY RECOMMENDATION
> I recommend we [accept / counter-offer / hold the position / propose a different
> structure]. [Reasoning the client can understand.]

### MODULE: your-decision-three-options
Fixed three-option reply structure. Source describes this as what empowers the
client: the firm advises, the client decides.

> YOUR DECISION
> This decision is yours. Reply to this message with one of the following:
> • "Proceed with your recommendation."
> • "I want to discuss before deciding — schedule a call."
> • "I want to make a different choice — here is what I want."

### MODULE: hearing-details-block
The source master ships this block with seven EMPTY bullets — the fields were
never populated. Reconstruct locally.

> HEARING DETAILS
> • [CONFIRM LOCALLY: required fields — the source template's seven detail bullets
>   are blank. At minimum: hearing type, date, time, duration, judge or division,
>   location or {{VIDEO_TOOL}} connection details, and appearance requirement.]

### MODULE: prep-email-forward-reference
> We will send you a separate hearing prep email approximately 10 days before the
> hearing with the courtroom procedures, dress code, and what to bring. If you have
> not received that email by {{DATE}}, reach out and we will send it.

### MODULE: conflict-reporting
> If for any reason you cannot attend on this date, tell us IMMEDIATELY.
> Continuance requests must be made well in advance — last-minute requests often
> fail.

### MODULE: attached-charts-enumerated (matter-sourced)
The settlement recommendation leads with its exhibits and says what each one
proves.
> I am attaching two charts for your review:
> 1. [Reconciliation chart name] — this reflects all assets and debts for both
>    parties, reconciled to the financial affidavits, and shows what a true
>    [even] division looks like under Florida law, including credits for payments
>    you have made since the case was filed.
> 2. Revisions Chart — this outlines the specific changes [the other party] is
>    requesting to both [document one] and [document two], along with my analysis
>    and recommendations.
[matter-sourced] — each attachment gets a one-sentence statement of what it
demonstrates. The client is never handed an unexplained spreadsheet.

### MODULE: recommend-vs-hold-split (matter-sourced)
The live settlement update splits every open item into two lists by
recommendation, not by whether the parties agree.
> I recommend agreeing to the following revisions:
> • [item];
> • [item]; and
> • [item].
>
> There are two items where I recommend holding our position:
> • [Item] — [one-line basis].
> • [Item] — [one-line basis, stated as a guideline or statutory reference].
[matter-sourced] — compare MODULE: settlement-positions-split above, which sorts
by agreement status. This sorts by advice, which is what the client actually has
to decide.

### MODULE: concession-permission (matter-sourced)
Distinctive move: the attorney explicitly identifies an item as not worth
fighting over and gives the client permission to drop it.
> The issue of [item] is not legally significant. If you do not feel strongly
> about that issue, it can be conceded without materially affecting your rights.
[matter-sourced] — separates legal significance from emotional significance, and
defers to the client on the latter.

### MODULE: full-picture-correction (matter-sourced)
Where the other side's position is arithmetically incomplete, the firm says so
neutrally and shows the correction rather than characterizing the position.
> [The other party] is asserting that [their position], and based on that
> position is asking that [the requested outcome].
>
> That request does not account for the full financial picture. When all assets
> and debts from both financial affidavits are included — including [our side's
> corresponding categories] — the math changes significantly.
[matter-sourced] — "does not account for the full financial picture" is the
firm's standard formula for an incomplete adverse position. No adjectives, no
imputed motive.

### MODULE: decisions-needed-yes-no-checklist (matter-sourced)
The live decision instrument. Replaces the masters' three fixed reply options with
a numbered, per-issue Yes/No checklist so the client authorizes each item
separately and the authorization is documented.
> DECISIONS NEEDED — PLEASE CONFIRM
> Please respond by indicating your position on each item below:
>
> 1. Authorize an offer of {{AMOUNT}} as the final [equalizing payment]
>    Yes   No
> 2. Hold firm on [position]
>    Yes   No
> 3. Hold firm on [position]
>    Yes   No
> 4. Agree to {{CONCEDED_ITEM}}
>    Yes   No
> 5. Do you have any objection to [the item flagged as not legally significant]?
>    Yes   No
>
> Once I have your responses, I will proceed accordingly and respond to opposing
> counsel.
[matter-sourced] — seven numbered items in the observed instance. Each maps to
exactly one decision the attorney cannot make alone. The closing sentence states
what happens on receipt.

This module is the strongest single artifact in the client lane. It converts a
strategy memo into an authorization record.

### MODULE: what-we-received-acknowledgment (matter-sourced)
> WHAT WE RECEIVED
> • [Document category] for [the periods actually received]
> • [Document category] for [periods]
> • [Document category] for [periods]
[matter-sourced] — itemized by category and period so the client can see exactly
what the firm has, and dispute it if the firm is wrong.

### MODULE: one-small-gap (matter-sourced)
A single missing item gets its own headed section, sized deliberately small.
> ONE SMALL GAP TO CLOSE
> We noticed [period] is the one month missing from [the document category] — we
> have [the periods held], but not [the gap]. Could you upload that one statement
> when you get a chance so the [record] is complete for the whole period we're
> covering?
[matter-sourced] — the header does the emotional work. Naming it "one small gap"
prevents a single missing document from reading as a failure.

### MODULE: what-we-still-need-with-rationale (matter-sourced)
Each outstanding item carries a one-line reason, and several offer an
if-it-doesn't-exist branch so the client can close the item either way.
> WHAT WE STILL NEED FROM YOU
> A few items from our last review remain outstanding. We know this is a lot, so
> take them one at a time — there's no single deadline, but the sooner we have
> these, the stronger your position going into [the milestone].
>
> • [Item] — Let us know whether [condition]. If [yes], please send a copy. If
>   not, tell us when you expect to [act] so we can note that on your disclosure.
> • [Item] — If [it exists], please send it. If none have been [created], let us
>   know so we can address that directly.
> • [Item] — Whatever you have showing [what it establishes]. This helps us
>   support [the position it supports].
> • [Item] — [What it documents] on the disclosure.
> • [Item] — This should [what it must separate or show]. It backs up [the figure]
>   on your Financial Affidavit.
> • An explanation of [the transaction] — Just a quick note on who this was from
>   and what it was for, so we can document it if needed.
> • Clarification on [the recurring item] — Please let us know whether these are
>   [the likely characterization]. If so, we need to add that to your Financial
>   Affidavit.
[matter-sourced] — every item states why it is needed. Every ambiguous item has a
"tell us if it doesn't exist" escape so the client can never be stuck.
Deliberately deadline-free, which contradicts the masters' rule that every ask
carries a deadline. Both approaches are in live use.
[CONFIRM LOCALLY: whether the buyer wants deadline-bearing or
momentum-based document asks]

### MODULE: why-this-matters (matter-sourced)
> WHY THIS MATTERS
> Florida law requires both sides to fully disclose their finances before
> mediation and any final agreement. The more complete your disclosure is now, the
> less room there is for the other side to raise questions about it later —
> whether at mediation or in court.
[matter-sourced] — the consequence is framed as the other side's leverage, not as
the firm's inconvenience or the court's displeasure.

### MODULE: how-to-send (matter-sourced)
> HOW TO SEND THESE
> You can upload everything directly to your {{CLIENT_UPLOAD_TOOL}} portal, the
> same way you sent [the prior production]. If anything doesn't apply to you or
> you're not sure how to answer one of these, just reply and let us know — we'll
> help you sort it out.
[matter-sourced] — references the client's own prior success rather than
re-teaching the tool.

### MODULE: internal-approval-footer (matter-sourced)
Structurally important. The observed letter shipped as a single file containing
both the client-facing letter and an internal block below it, under a hard
`INTERNAL — DO NOT SEND` rule.
> INTERNAL — DO NOT SEND
> Approval status: [Attorney review required before sending / cleared] — [reason
> the letter needs review].
> {{PM_SYSTEM}}: Log time entry for drafting this correspondence and for the
> underlying document review ([the document set reviewed]).
> Open items for attorney: (1) [decision needed]. (2) [flagged in the letter].
> (3) [routing on receipt]. (4) [unresolved items and what they may affect].
[matter-sourced] — three functions in one block: it names why attorney review is
triggered, it forces the time entry, and it carries the open questions forward so
they are not lost between the letter and the next step.

The risk is obvious and must be controlled: this block sits in the same file as
the client letter. Stripping it is a release step, not a formatting preference.

## Closing / next-steps bank

- `Reply to this message in your portal with any questions. If you don't have
  questions, a quick "got it, thanks" tells us this reached you and you have the
  picture.`
- `Take a day if you need it. Don't decide under pressure.`
- `This date is now on your calendar in your portal. Please block the time.`
- `Once I have your responses, I will proceed accordingly and respond to opposing
  counsel.` [matter-sourced] — states the consequence of the client's reply.
- `Thank you again for staying on top of this. We'll be in touch as soon as we've
  finished reviewing what you've sent.` [matter-sourced] — closes a document-status
  letter with reciprocal commitment rather than a further ask.
- `This approach applies the statute correctly, accounts for all assets, debts,
  and post-filing payments, and puts us in a strong position to conclude the
  case.` [matter-sourced] — the recommendation close: three grounds, then the
  strategic payoff. Note it claims a strong position, not a specific outcome.
- `Nice work getting these together quickly.` [matter-sourced] — praise for client
  compliance, placed in the opening rather than the close.

## Signature block

Monthly status and hearing confirmation:
> Sincerely,
>
> {{ATTORNEY_NAME}}
> {{FIRM_NAME}}

Settlement posture update — fuller block, attorney only:
> Sincerely,
>
> {{ATTORNEY_NAME}}, Esq.
> Florida Bar No. {{BAR_NO}}
> {{FIRM_EMAIL}}

## Voice notes

- Length is deliberately capped. The monthly email should fit on one phone screen
  in a typical month, because "clients skim, they don't read."
- Every factual bullet carries a date. Every ask carries a deadline.
- Honesty about inactivity is mandated rather than avoided.
- Outcomes are always ranged. The library treats prediction as a drafting defect.
- The firm separates advice from decision explicitly and repeatedly — "This
  decision is yours."
- Anti-pressure language is built into the settlement close rather than left to
  the attorney's discretion.
- First person singular in the settlement update ("I want to give you," "How I
  read," "My recommendation") versus first person plural in the monthly recap
  ("We send these," "We completed"). The strategy document is personally owned.
- ALL-CAPS section headers throughout. Em dash as the standard connector.
- Selective ALL-CAPS for urgency inside body text ("tell us IMMEDIATELY") — used
  sparingly, only for client-conduct instructions.
- Opposing counsel is referred to by role, never by name, in status correspondence.
- No rule citations, no case citations, no statutory references in any of the
  three.

Additional notes from the matter-sourced letters:

- Live practice contradicts the masters on citation. Sent status letters do
  reference Florida law, statutory sections, and guideline standards — in plain
  language, without formal citation format. "Under Florida law, you are entitled
  to a credit for one-half of those post-filing payments."
- Every adverse position is described without adjectives. The standard formula is
  "that request does not account for the full financial picture," never a
  characterization of the other party's motive.
- Where the firm's own advice has changed, it says so in the first sentence.
- The attorney distinguishes legal significance from personal significance and
  hands the latter back to the client explicitly.
- Authorization is captured per-issue, not in aggregate. The Yes/No checklist is
  the live mechanism; the three fixed reply options in the master are the
  simplified form.
- Document asks carry reasons. Nothing is requested without a stated use.
- Ambiguous asks carry an if-it-doesn't-exist branch, so the client can always
  close the item.
- Client compliance is acknowledged specifically and early. The praise names what
  arrived and why it helped.
- Missing items are sized down by the header that introduces them.
- Consequences are framed as the other side's leverage rather than the firm's
  burden.
- Section headers are ALL-CAPS in the plainer letters and Title Case in the
  attorney settlement letters — the register tracks the signer.
- First person singular throughout the attorney-drafted letters, first person
  plural in the document-status letters drafted at staff level and
  attorney-reviewed. This matches the masters' pattern.
- No outcome is ever predicted. The strongest claim observed is that a position is
  strong, or that a step "puts us in a strong position to conclude the case."

## Attorney flags

- The monthly status email must never carry bad news or substantive strategy. Use a
  separate dedicated message.
- Settlement posture updates require attorney drafting and attorney signature.
  This is not a staff-sendable document under any circumstance.
- Never predict an outcome. Range it.
- Monthly status: {{ROLE_DRAFTER}} may draft from the running case file, but
  {{ROLE_APPROVER}} reviews and approves before send.
- Hearing confirmations: verify courthouse address, parking, and division-specific
  procedure before sending — these vary by judge and county.
- For remote hearings, include connection details in the email body.
- Where a matter has additional parties or intervenors, attendance requirements
  differ. Verify before sending.
- Any status language touching the merits, a discrepancy, or a strategic choice
  leaves the staff lane entirely and goes to the approving attorney.
- **Strip the internal approval block before sending.** The observed
  document-status letter shipped as one file containing both the client letter and
  an `INTERNAL — DO NOT SEND` block with approval status, time-logging
  instructions, and open attorney questions. Treat removal as a release step with
  its own check, not as formatting.
- Document-status letters that touch income verification or a previously
  undisclosed account require attorney review before sending. The source letter
  flags exactly this trigger.
- Never state an authorized settlement figure the client has not confirmed. The
  Yes/No checklist exists to create that confirmation — do not pre-fill it.
- Where the letter asserts a legal entitlement in plain language (a credit, a
  guideline treatment, a statutory allocation), the attorney must verify the
  assertion. Plain language does not lower the accuracy bar.
- Log time for both the correspondence and the underlying document review in
  {{PM_SYSTEM}} before closing the session.
- Do not name a child, a date of birth, an account number, or an employer in a
  status letter unless the client needs it to act.

## [CONFIRM LOCALLY] items

- Matter identifier convention for subject lines (surname, file number, or both).
- Day of month for the status cadence.
- The seven hearing-detail fields — blank in the source master.
- Local continuance practice and how far in advance requests must be filed.
- Courthouse logistics, parking, security, and dress expectations per division.
- Remote-appearance platform and whether the division permits it.
- Whether the buyer's jurisdiction requires anything specific in a written
  settlement recommendation.
- Whether bar number is required in the signature block for client correspondence.
- Lead time for the hearing prep email — the source assumes ~10 days.

## Coverage

matters harvested: 7 distinct
templates harvested: 3 firm-agnostic masters
matter-sourced bank entries: 24
template-sourced bank entries: 17

The strongest matter harvest in the corpus. Every bank in the required structure
is populated, and the substantive body language that the first pass could not
extract is now present from live sent correspondence.

structural holes closed since the first pass:
- The first pass harvested no matter-level instances and reported that
  sentence-level voice for the body of a status update could not be extracted
  because the masters ship as bracketed drafting instructions. That hole is closed
  — realized prose was recovered from seven matters.
- Two live sub-types absent from the masters are now specified: the
  document-status / outstanding-items update (five matters) and the settlement
  recommendation with decision checklist (two matters).
- Recovered and specified twelve matter-sourced modules:
  attached-charts-enumerated, recommend-vs-hold-split, concession-permission,
  full-picture-correction, decisions-needed-yes-no-checklist,
  what-we-received-acknowledgment, one-small-gap,
  what-we-still-need-with-rationale, why-this-matters, how-to-send,
  internal-approval-footer, and the matter-sourced closing bank.
- The `decisions-needed-yes-no-checklist` module supersedes the masters'
  three-fixed-options module as the firm's live authorization instrument, and is
  the highest-value artifact recovered in the client lane.
- The internal-approval-footer pattern is documented, along with the release risk
  it creates.
- Two live contradictions of master rules are surfaced rather than smoothed:
  document asks are deadline-free in live practice, and status letters do
  reference Florida law in plain language.

remaining gaps:
- **The monthly cadence sub-type remains template-only.** No sent monthly status
  email was found in any matter. The firm's live status correspondence is
  event-driven, not calendar-driven, which raises a real question about whether
  the monthly cadence in the master is practiced at all.
- **The hearing / court date confirmation sub-type remains template-only,** and
  its hearing-details block is still structurally incomplete — seven empty bullets
  in the master, no populated instance anywhere in either source.
- No bad-news or adverse-ruling update language in either source, despite the
  master requiring it be a separate document. The document it points to does not
  exist.
- No trial-setting, discovery-deadline-slipping, or case-management-conference
  status variant.
- No dormant-matter or client-non-responsiveness escalation language.
- No post-judgment or enforcement status variant.
- No quarterly or milestone-based cadence alternative.
- No bad-news / adverse-ruling update language anywhere, despite the source
  requiring that it be a separate document. The document it points to does not
  exist in the library.
- No trial-setting, no discovery-deadline-slipping, and no
  case-management-conference status variants.
- No language for a stalled or dormant matter beyond the one "quiet month"
  sentence.
- No status variant for post-judgment or enforcement postures.
- No client-non-responsiveness escalation language.
- No quarterly or milestone-based cadence alternative for low-activity matters.

## Tokens introduced by this spec

- `{{CONCEDED_ITEM}}` — the specific item the client is being asked to concede,
  used in the Yes/No decision checklist.
