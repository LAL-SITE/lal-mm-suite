# Bench — Judge / Judicial Assistant — Content Spec
lane: bench
sources: 2 distinct matters + 8 templates
harvested: 2026-07-29

## When this fires

Written communication directed to the court — either to the judge personally or,
far more often, to the judicial assistant. Five triggers:

1. **Scheduling** — requesting a special-set hearing, asking what calendar a
   motion belongs on, or confirming a held date.
2. **Proposed orders** — transmitting an agreed, unopposed, or after-hearing
   proposed order for entry.
3. **Courtesy copies** — delivering a tabbed binder or PDF set in advance of a
   hearing or trial.
4. **Status letters** — advising that the case is ready to be set, or that it is
   being held in abeyance.
5. **Procedural** — withdrawing a motion and releasing calendar time.

The governing constraint on the whole lane: a letter to the bench is a logistics
or transmittal instrument. It is never a vehicle for argument. Where a
substantive point needs to reach the court, it goes in a filed motion or notice.

## Sub-types

| Sub-type | Addressed to | Matter-sourced? |
|---|---|---|
| Special-set hearing request | JA | matter-sourced |
| Calendar-placement inquiry (motion calendar vs. special set) | JA | matter-sourced |
| Date-hold confirmation and notice follow-through | JA | matter-sourced |
| Agreed proposed order cover | Judge | template only |
| Unopposed proposed order cover | Judge | template only |
| After-hearing proposed order cover | Judge | template only |
| Courtesy copy / judge's binder cover | Judge | template only |
| Status letter — case ready for hearing or trial | JA | template only |
| Status letter — case held in abeyance | JA | template only |
| Withdrawal of motion / calendar release | JA | template only |

## Required structure per sub-type

### Formal bench letter — common shell (all template sub-types)
1. Firm letterhead block
2. Date
3. Delivery line — `Via E-Portal Submission and Courtesy Email Copy`
4. Addressee block, in this fixed order:
   `The Honorable {{JUDGE}}` / court name / courthouse address / city, state ZIP /
   `c/o {{JUDICIAL_ASSISTANT}}, Judicial Assistant` / JA email
5. `Re:` block on indented continuation lines:
   styling / `Case No. {{CASE_NO}}` / `{{CIRCUIT}} Judicial Circuit in and for
   {{COUNTY}} County, Florida` / `Division {{DIVISION}}` / `Subject:` line
6. Salutation
7. Body — sub-type specific, short
8. Thanks line
9. `Respectfully submitted,` + attorney signature with bar number
10. `Enclosures:` line where anything is transmitted
11. `cc:` line naming opposing counsel by full name and email

### Proposed order cover (all three flavors)
1. Common shell
2. Single enclosing sentence — what is enclosed and what the court is asked to do
3. **Circulation and position statement** — the flavor-defining paragraph
4. Format statement — Word plus PDF
5. Optional availability-for-questions line
6. Thanks, signature, enclosures, cc

### Courtesy copy / binder cover
1. Common shell
2. Enclosing sentence naming the document, its filing date, and the hearing it
   precedes
3. `Tab index` — enumerated, matching the physical binder
4. Identical-copy-to-OC statement
5. Thanks, signature, enclosures, cc

### Status letter (both flavors)
1. Common shell
2. Representation statement
3. Purpose sentence
4. Posture block — bulleted, dated, factual
5. Joint availability and time estimate, or the abeyance basis and update date
6. The specific request to the court
7. Thanks, signature, cc

### Withdrawal of motion
1. Common shell
2. Representation statement
3. Withdrawal sentence naming the motion and its filing date
4. Optional one-sentence basis
5. **Calendar-release sentence** naming the hearing date and time
6. OC-advised statement
7. Offer to file a formal notice or order if the division requires it
8. Thanks, signature, cc

### JA email — matter-sourced shell
Live practice is email, not letterhead. Observed structure:
1. Subject line: `{{CASE_NO}} - {{CLIENT_NAME}} v. {{OPPOSING_PARTY}} - [purpose]`,
   or `{{CLIENT_NAME}} and {{OPPOSING_PARTY}} - [abbreviated purpose]`. Urgency is signalled by an
   ALL-CAPS prefix: `NEED RESPONSE, PLEASE - RE: ...`
2. Time-of-day greeting — `Good morning,` / `Good afternoon,`
3. The single question or confirmation, in one or two sentences
4. Where relevant, the coordination status of the other side
5. What the firm will do once the JA answers
6. `Best regards,` + staff or attorney signature block
7. Confidentiality footer

## Salutation and address-block conventions

- `Dear Judge [Last Name]:` when the letter is directed to the judge personally.
  Used for all three proposed order covers and the courtesy binder cover.
- `Dear [Ms./Mr. Last Name]:` when the letter is directed to the JA. Used for
  scheduling, both status letters, and the withdrawal letter. The source is
  explicit: most scheduling correspondence is JA-only, and the JA is addressed by
  professional title and surname.
- Colon, never comma, in formal bench correspondence.
- Even a judge-addressed letter routes `c/o` the JA. The JA is always in the
  address block.
- The judge is referred to in-body in the third person and by office —
  `the Court`, `Your Honor` — not by name.
- `Via E-Portal Submission and Courtesy Email Copy` is the default delivery line.
  Where a division takes proposed orders only through the portal, the line is
  modified and the JA email line is removed.
- Matter practice diverges: live JA contact is by email to a division mailbox or
  a named JA address on the circuit's domain, with no letterhead and no formal
  caption block. Both registers are legitimate; the formal letter is for anything
  transmitted for entry or for the file.
  [CONFIRM LOCALLY: whether the division wants a formal letter, an email, or a
  filed notice for each of these purposes]

## Opening paragraph bank

**Situation: transmitting an agreed proposed order**
> Enclosed for the Court's consideration and entry is the proposed Agreed [order
> title]. The form of this proposed order has been agreed upon by all counsel of
> record.
[template-sourced]

**Situation: transmitting an unopposed proposed order**
> Enclosed for the Court's consideration and entry is the proposed Order on
> [Petitioner / Respondent]'s [motion title], filed on {{DATE}}.
[template-sourced]

**Situation: transmitting a proposed order after a ruling**
> Enclosed for the Court's consideration and entry is the proposed Order
> following the hearing held on {{DATE}} on [motion or issue]. The proposed order
> reflects the Court's ruling at hearing.
[template-sourced]

**Situation: delivering a courtesy binder before a hearing**
> Enclosed for the Court's reference is a courtesy copy of [document title],
> filed [or to be filed] on {{DATE}}, in advance of the [hearing / trial]
> scheduled for {{DATE}} at {{TIME}}.
[template-sourced]

**Situation: requesting a special-set hearing**
> This firm represents the [Petitioner / Respondent], {{CLIENT_NAME}}, in the
> above-styled matter. We write to request a special-set hearing on [motion or
> issue], filed on {{DATE}}.
[template-sourced]

**Situation: case is ready to be set**
> This firm represents the [Petitioner / Respondent], {{CLIENT_NAME}}, in the
> above-styled matter. We write to advise the Court of the current status of this
> case and to request that the matter be set for [hearing / final hearing /
> trial].
[template-sourced]

**Situation: parties jointly holding the case**
> This firm represents the [Petitioner / Respondent], {{CLIENT_NAME}}, in the
> above-styled matter. We write to advise the Court that the parties have jointly
> elected to hold this matter in abeyance for the time being.
[template-sourced]

**Situation: withdrawing a motion**
> This firm represents the [Petitioner / Respondent], {{CLIENT_NAME}}, in the
> above-styled matter. We write to advise the Court that [Petitioner /
> Respondent] hereby withdraws the [motion or notice title], filed on {{DATE}}.
[template-sourced]

**Situation: asking the JA which calendar a motion belongs on (matter-sourced)**
> Good afternoon. I had scheduled {{CLIENT_NAME}}'s [motion title] on Motion
> Calendar. Should I cancel that hearing and [set it with the other motion
> instead]? Just another clarification, please, and then I will leave you alone.
[matter-sourced]

**Situation: taking a date the JA has offered, other side not yet confirmed (matter-sourced)**
> Thank you for providing dates. We would like to grab the {{DATE}} date at
> {{TIME}} via {{VIDEO_TOOL}}. Please hold, as the opposing party has not confirmed
> and seems to be unresponsive. But we are good to go on our end.
[matter-sourced]

**Situation: asking the JA for earlier availability (matter-sourced)**
> Thank you for providing dates. Do you by any chance have earlier availability,
> maybe for the summer, to hear these motions? There is a final hearing scheduled
> [CONFIRM LOCALLY: the competing setting that creates the urgency].
[matter-sourced]

**Situation: second contact on an unanswered scheduling request (matter-sourced)**
> Good morning. I am sorry to email a second time, but since {{DATE}} is coming
> up fast, I needed to know [the specific question].
[matter-sourced] — sent under an ALL-CAPS `NEED RESPONSE, PLEASE` subject prefix.

**Situation: correcting the firm's own scheduling error (matter-sourced)**
> Actually, I guess we need to schedule this for {{DATE}} so [the other party] can
> be given proper notice. I apologize for the oversight.
[matter-sourced]

## Body modules

### MODULE: circulation-and-position — agreed
> The form of this proposed order has been agreed upon by all counsel of record.
[template-sourced]

### MODULE: circulation-and-position — unopposed
> Counsel for {{OPPOSING_PARTY}} has been provided a copy of this proposed order
> and has confirmed that the motion is unopposed and that they have no
> objection to the form of the proposed order. [Confirmation correspondence from
> opposing counsel is available upon the Court's request.]
[template-sourced] — the source draws a hard line: "unopposed" means OC has
affirmatively confirmed. Silence is a different posture and a different letter.

### MODULE: circulation-and-position — after hearing
Three mutually exclusive states. Exactly one ships.
> In accordance with the Court's instruction at hearing, this proposed order has
> been circulated to counsel of record. [Counsel for {{OPPOSING_PARTY}} has
> approved the proposed order as to form. / Counsel for {{OPPOSING_PARTY}} has
> objected to the form of the proposed order, and their competing proposed
> order is also enclosed for the Court's consideration. / Counsel for [opposing
> party] was provided this proposed order on {{DATE}} and has not responded as of
> the date of this submission.]
[template-sourced]

### MODULE: format-statement
> The proposed order is submitted in Microsoft Word format consistent with the
> Court's standing order on proposed orders. A PDF copy is also enclosed for the
> Court's reference.
[template-sourced]

### MODULE: tab-index
> For the Court's convenience, the enclosed binder is tabbed and organized as
> follows:
> Tab index
> • Tab 1 — [document title]
> • Tab 2 — [document title]
> • [Add tabs as needed]
[template-sourced]

### MODULE: identical-copy-to-oc
> Counsel for {{OPPOSING_PARTY}} has been provided an identical courtesy copy.
[template-sourced] — stated on the face of the letter, not merely done.

### MODULE: posture-block
Factual, dated, and non-characterizing.
> The procedural posture is as follows:
> • Petition filed: {{DATE}}
> • Answer / Counter-Petition filed: {{DATE}}
> • Mandatory Disclosure: [served on both sides / outstanding deficiencies]
> • Mediation: [held on {{DATE}} — resolved / partial / impasse / not yet
>   conducted]
> • Outstanding issues: [the issues remaining for the Court]
[template-sourced]

### MODULE: joint-availability-and-estimate
> Counsel for {{OPPOSING_PARTY}} has been consulted on availability. The parties
> are jointly available on the following dates: [dates]. Estimated time
> required: [estimate].
>
> Please advise of the Court's availability on the dates above or such other date
> as the Court may select.
[template-sourced]

### MODULE: special-set-dates-with-fallback
> Estimated time required: [estimate]. Counsel for {{OPPOSING_PARTY}} has been
> consulted on availability and has confirmed availability on the dates listed
> below.
>
> Available dates
> • {{DATE}} at {{TIME}}
>
> If none of the dates listed above is available on the Court's calendar, please
> let us know and we will coordinate additional dates with opposing counsel.
[template-sourced]

### MODULE: abeyance-basis-and-update-date
> The basis for the abeyance is: [briefly state — the source offers reconciliation
> attempt, settlement negotiation requiring further document exchange, or
> awaiting the outcome of a parallel proceeding].
>
> The parties anticipate that they will be in a position to advise the Court of
> further progress on or before {{DATE}}. We will file an updated status letter or
> appropriate motion at that time.
[template-sourced]

### MODULE: abeyance-joinder-and-dismissal-protection
> Counsel for {{OPPOSING_PARTY}} joins in this request. The parties respectfully
> request that the Court not dismiss the case for lack of prosecution during the
> abeyance period in light of the parties' joint election.
[template-sourced] — the source ties the required update date to dismissal
exposure for lack of prosecution.

### MODULE: calendar-release
> Accordingly, the hearing on this motion currently scheduled for {{DATE}} at
> {{TIME}} is no longer required and may be removed from the Court's calendar.
> Counsel for {{OPPOSING_PARTY}} has been advised of this withdrawal.
[template-sourced] — the source notes JAs value the explicit release of the time.

### MODULE: offer-to-file-formal-instrument
> If the Court requires a separate Notice of Withdrawal or proposed Order on
> Withdrawal to be filed, please advise and we will submit one without delay.
[template-sourced] — the general move of asking the division what it wants rather
than assuming.

### MODULE: notice-follow-through (matter-sourced)
The firm closes the loop by telling the JA what it will file, then filing it.
> Please confirm we are booked for {{DATE}} at {{TIME}} for [hearing type] via
> {{VIDEO_TOOL}}. Please advise, so I may proceed with filing the Notice of
> Hearing.
[matter-sourced]

> Great. I'll file a new notice. Thank you so much.
[matter-sourced] — sent in response to a JA reset.

### MODULE: proper-notice-self-check (matter-sourced)
The firm raises the other side's notice entitlement against its own interest,
unprompted, and moves the date out.
> We need to schedule this for {{DATE}} so [the other party] can be given proper
> notice.
[matter-sourced]

## Ex parte discipline and copy conventions

This is the load-bearing section of the lane. Both sources are consistent and
strict.

**What the firm always does:**
- `cc:` opposing counsel by full name and email **on the face of the letter**, not
  only in the mail client. The source states this explicitly for the agreed
  proposed order cover and it holds across every template in this lane.
- Confirms in the matter file that OC was advised *before* the letter went to the
  bench. The withdrawal template names this as a sequencing requirement, not a
  courtesy.
- States OC's position on the record of the letter — agreed, unopposed and
  confirmed, objected with a competing order enclosed, or served on a named date
  and unresponsive. The court is never left to infer the other side's posture.
- Delivers an identical courtesy binder to OC and says so in the letter.
- In live JA email threads, keeps the other side on the thread. In the harvested
  matter threads the adverse party was a participant in the scheduling
  correspondence with the JA throughout.
- Confirms OC availability *before* proposing dates to the JA. Both the OC
  scheduling template and the bench special-set template state that listing dates
  without the other side's confirmation manufactures a continuance dispute.
- Where OC has not confirmed, says so to the JA plainly and asks for the date to
  be held rather than booked. [matter-sourced]

**What the firm never does:**
- Never argues the merits in a letter to the bench. Stated as an absolute: "Never
  argue the merits in a cover letter. If a substantive point needs to be made to
  the Court, file a separate motion or notice — not a letter."
- Never argues a form dispute in a proposed-order cover. Where the form is
  contested, both proposed orders are enclosed and the disagreement is identified
  neutrally for the court to resolve.
- Never characterizes the other side or their conduct. The source gives paired
  examples and the rejected version is always the one that editorializes —
  a neutral issue label is correct, a version imputing unreasonableness to the
  other party is not.
- Never argues discovery deficiencies in a status letter. Deficiencies are named
  factually; the argument belongs in a motion to compel.
- Never editorializes on why a motion is being withdrawn. Mootness by agreement
  is acceptable; commentary on the other party's change of position is not.
- Never submits a proposed order that tracks the client's preferred outcome
  rather than the court's actual ruling. The proposed order is reconciled against
  the transcript or ruling notes before submission.
- Never treats OC silence as consent. "Unopposed" requires affirmative
  confirmation.

**Register toward the court and the JA:**
- Deferential without being obsequious. `Respectfully submitted,` in formal
  letters; `Best regards,` in JA email.
- The firm apologizes for its own burden on the JA's time — for a repeat email,
  for an oversight, for a second clarification — and does so briefly and once.
  [matter-sourced]
- Urgency is signalled in the subject line rather than by pressing in the body.
  [matter-sourced]
- The JA is treated as the operator of the calendar and asked direct, answerable
  questions. Requests are single-issue.

**Notes on the observed matter threads:** in one harvested matter the JA
instructed the parties to coordinate between themselves outside the thread with
the court. The firm complied and reported the result back rather than continuing
to negotiate in front of the JA. That pattern — negotiate off-thread, report
on-thread — is the practical expression of the discipline above.

## Closing bank

- `Thank you for the Court's time and consideration.` [template-sourced] — the default for anything transmitted for entry.
- `Thank you for the Court's time.` [template-sourced] — courtesy copies.
- `Thank you for the Court's consideration.` [template-sourced] — abeyance and withdrawal.
- `Thank you for your assistance.` [template-sourced] — JA-directed scheduling and status letters.
- `Please contact our office if Your Honor or the Judicial Assistant has any questions or requires any additional information.` [template-sourced]
- `If the Court requires [a formal instrument], please advise and we will submit one without delay.` [template-sourced]
- `If none of the dates listed above is available on the Court's calendar, please let us know and we will coordinate additional dates with opposing counsel.` [template-sourced]
- `Please advise, so I may proceed with filing the Notice of Hearing.` [matter-sourced]
- `Thank you for confirming.` [matter-sourced]
- `Thanks so much.` [matter-sourced] — JA email register.
- `and then I will leave you alone.` [matter-sourced] — used once, self-deprecating, to close a third clarification request. Distinctive; ship only if the buyer's register supports it.

## Signature block

Formal bench correspondence — attorney only, no exceptions:
> Respectfully submitted,
>
> {{ATTORNEY_NAME}}, Esq.
> Florida Bar No. {{BAR_NO}}
> {{FIRM_EMAIL}}
>
> Enclosures: [as described]
> cc: {{OPPOSING_COUNSEL}}, Esq. (opposing counsel email)
>     [co-counsel, mediator, or GAL if applicable]

The source states the rule directly: bench correspondence is attorney-signed
only, and the approval trigger is `REQUIRED` on all eight templates.

JA email, matter-sourced, staff-signed:
> Best regards,
>
> {{ROLE_DRAFTER}}
> {{FIRM_NAME}}
> {{FIRM_EMAIL}}
> {{FIRM_NAME}} website
> {{FIRM_PHONE}}
> {{FIRM_ADDRESS}}
>
> [confidentiality footer]

**Tension the buyer must resolve:** the template library requires attorney
signature on everything to the bench; live matter practice has staff emailing the
JA directly on pure calendar logistics. Both are defensible, but the line has to
be drawn deliberately.
[CONFIRM LOCALLY: whether staff may correspond with a JA on scheduling without
attorney signature, and where the boundary sits]

## Voice notes

- Short. The longest body in the library is four paragraphs; most are two.
- The enclosing sentence does the work of the letter. Everything else is
  identification, position, format, and thanks.
- Passive-to-the-court constructions: "Enclosed for the Court's consideration and
  entry is…" The firm does not put itself at the head of the sentence.
- `the Court` in the third person throughout; `Your Honor` only in the direct
  address of the optional questions line.
- Factual bullets carry dates. Issue lists carry no adjectives.
- Every request the letter makes is answerable with a yes, a no, or a date.
- The firm consistently asks the division what it requires rather than assuming a
  practice — for order format, for whether a formal notice is needed, for whether
  binders are accepted. This is the single most repeated move in the lane.
- Neutrality is a drafting rule, not a tone preference. The source treats a
  characterizing adjective in bench correspondence as a defect.
- In JA email the register loosens markedly — contractions, one-line messages,
  time-of-day greetings, plain thanks — but the substance stays purely logistical.
- Nothing in the lane predicts, argues, or persuades.

## Attorney flags

- Attorney approval is `REQUIRED` on all eight formal sub-types. No formal bench
  letter is staff-sendable.
- Run the buyer's judicial-procedures reference before every bench transmittal.
  Format is judge-specific and the source flags all of the following as varying:
  Word with or without electronic signature, PDF only, portal-only submission,
  whether a separate courtesy email to the JA is expected, whether paper or PDF
  binders are accepted, whether a separate filed Notice for Trial is required,
  whether a filed Notice of Withdrawal is required in addition to or instead of a
  letter, and how special-set hearings are reserved.
- Confirm the proposed order has been signed or e-signed by all counsel of record
  before transmittal.
- Reconcile any after-hearing proposed order against the transcript or the ruling
  notes before it goes out. It must track the ruling, not the client's preference.
- If the form of an order is contested, enclose both and describe the dispute
  neutrally. Do not argue it.
- Save OC's confirmation to the matter file before representing to the court that
  a motion is unopposed, and before saying the confirmation is available on
  request.
- Tab numbers must match the binder. Page-number binders for hearings over 30
  minutes.
- Never state an abeyance with no update date. Open-ended abeyance invites
  dismissal for lack of prosecution.
- Abeyance letters require joint election. A unilateral request is a motion, not
  a letter.
- Handle reconciliation-based abeyance language with care — the parties may resume
  or dismiss, and the letter must commit to neither.
- Confirm the time estimate is the parties' stipulated estimate, not a unilateral
  one. JAs hold calendar time against it.
- Check the other party's notice entitlement before accepting a date from a JA.
  A date the firm cannot properly notice is worse than no date.
- Where a scheduling letter follows an abatement or a filed motion, cross-
  reference the filed instrument rather than restating it.

## [CONFIRM LOCALLY] items

- Whether the division accepts courtesy binders at all, and in what medium.
- Proposed order format: Word, PDF, both; electronic signature permitted or not.
- Whether proposed orders may be emailed to the JA or must go through the portal
  only.
- Whether a filed Notice of Withdrawal, a letter to the JA, or both are required
  to withdraw a motion.
- Whether a separate filed Notice for Trial is required, or a status letter
  suffices.
- How special-set hearings are reserved in the division — online reservation
  system, email to the JA, or a required cover sheet.
- Motion calendar versus special set: which motions belong on which, and the time
  limits for each.
- Local minimum notice period for a hearing, and the practical lead time the
  division expects.
- Whether staff may correspond with the JA directly, and on what subjects.
- Remote-appearance platform and whether the division permits remote hearings.
- Whether the division wants the JA copied on filings, and whether it wants the
  Notice of Hearing emailed in addition to filed.
- The dismissal-for-lack-of-prosecution exposure window in the buyer's
  jurisdiction and how abeyance interacts with it.
- Whether bar number is required in the signature block.
- Form of address for the JA, and whether any division prefers first-name
  contact.

## Coverage

matters harvested: 2 distinct
templates harvested: 8
matter-sourced bank entries: 11
template-sourced bank entries: 27

Provenance split by sub-type is recorded in the Sub-types table above. Three of
the ten sub-types have matter-sourced language; seven are template-only.

structural holes closed:
- Every bank in the required structure is populated.
- The ex parte discipline section — the readiness-critical section for this lane
  — is built from both sources and specifies affirmative practice, prohibitions,
  register, and the negotiate-off-thread / report-on-thread pattern.
- The formal-letter register and the live JA email register are both captured, and
  the conflict between them is surfaced rather than smoothed over.
- Live scheduling language, absent from the template library, was recovered from
  matter email: calendar-placement inquiry, date-hold-pending-OC, earlier-
  availability request, second-contact escalation, self-corrected notice defect,
  and notice follow-through.

remaining holes:
- **No matter-sourced proposed order cover, courtesy binder cover, status letter,
  or withdrawal letter.** These four sub-types are template-only. The source
  matters contained no outgoing bench letters at all — the bench
  lane lives in email, and what is in email is scheduling.
- No matter-sourced letter addressed to a judge personally. Every observed live
  bench contact was JA-directed.
- No emergency or ex parte motion cover letter, and no language for the one
  posture where genuinely one-sided contact is permitted. This is a real gap in a
  lane whose defining discipline is ex parte conduct.
- No trial-setting-conference, case-management-conference, or pretrial-compliance
  correspondence.
- No language for responding to a JA's rejection of a proposed order, or for
  resubmitting a corrected order.
- No continuance request to the bench; the continuance language in the library is
  OC-directed only.
- No language for correcting a misstatement previously made to the court.
- No multi-judge, multi-division, or consolidated-case variant.
- The four proposed-order and status templates ship as scaffolding with bracketed
  drafting instructions in the substantive slots, so sentence-level voice for the
  body of a status letter could not be extracted — only the scaffolding and the
  neutrality rules.
- Template library duplication note: several bench sub-types ship a duplicate
  "example" alongside the template. On inspection the duplicates are identical
  scaffolding, not worked examples. They add no coverage and should not be
  counted as such.

## Tokens introduced by this spec

- `{{JUDICIAL_ASSISTANT}}` — the judicial assistant's name, used in the addressee
  block.
- `{{TIME}}` — the clock time of a hearing or held calendar slot.
- `{{CASE_NO}}`, `{{CLIENT_NAME}}`, `{{OPPOSING_PARTY}}` — already standard
  corpus tokens; introduced into this spec in place of bracket placeholders in
  the JA email subject line and the proposed-order and scheduling modules.
