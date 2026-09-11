# Client Welcome / Engagement — Content Spec
lane: client
sources: 4 distinct matters + 3 firm-agnostic master templates
harvested: 2026-07-29

## When this fires

Retainer is countersigned, initial payment has cleared trust, and the matter is
active in {{PM_SYSTEM}}. Sent within 24 hours of the matter being opened. The
{{CLIENT_UPLOAD_TOOL}} portal must be provisioned with all upload links BEFORE
this goes out — sending with placeholder links is the single most common
onboarding error in the source library.

Sequencing observed: retainer transmittal (attorney) → welcome / engagement
({{ROLE_DRAFTER}}, within 24h) → portal & upload setup (within 48h) → intake
call prep (within 24h of the call being scheduled).

## Required structure

1. Subject line
2. Salutation — first name only, informal
3. Welcome + file-is-open confirmation (1–2 sentences)
4. Case identification — matter type and {{COUNTY}}
5. Team identification — who the attorney is, who the day-to-day contact is
6. NEXT STEPS — numbered, ordered, non-rearrangeable
7. Document upload links block
8. Documents to gather — split into PRIORITY and secondary tiers
9. HOW WE WORK — communication rules and escalation path
10. Scope reminder tied back to the signed agreement
11. Firm promise line
12. Signature block ({{ROLE_DRAFTER}} signs, not the attorney)

## Subject line bank

Observed, tokenized:

- `Welcome to {{FIRM_NAME}} — Here's What Happens Next`
- `Setting Up Your Client Portal and {{CLIENT_UPLOAD_TOOL}} — Step by Step`
- `Your Intake Call with {{FIRM_NAME}} — How to Prepare`

Pattern: `<Plain benefit or action> — <what the reader does next>`. Em dash
separator in all three. No case numbers, no matter names in subject.

Matter-sourced subject lines diverge sharply from the master pattern. Live
practice uses an ALL-CAPS label plus the matter styling:

- `WELCOME EMAIL - [styling] - [matter type abbreviation]` [matter-sourced]
- `WELCOME LETTER [year]` — used as the document title on the attached letter
  rather than as a subject line [matter-sourced]

Observed in two matters. Note the conflict: the master templates prohibit matter
identifiers in the subject line and the live welcome emails use them. The live
convention is legible in a threaded mailbox; the master convention is safer.
[CONFIRM LOCALLY: whether party styling may appear in email subject lines]

## Opening paragraph bank

**Situation: matter just opened, retainer signed (primary welcome)**
> Hi {{CLIENT_NAME}},
> Welcome to {{FIRM_NAME}}. Your file is open and we are ready to go.
> Your case is: [CONFIRM LOCALLY: matter type and division label as the clerk
> styles it, e.g. Dissolution of Marriage — {{COUNTY}} County]. Your attorney is
> {{ATTORNEY_NAME}}, Esq. I am {{ROLE_DRAFTER}}, who will be
> managing your documents and keeping your file moving.

**Situation: portal / upload tooling setup, sent as a companion**
> {{CLIENT_NAME}},
> Welcome to {{FIRM_NAME}}. This email walks you through the two tools we use to
> communicate with you and to receive your documents: your client portal (for
> messages and case calendar) and {{CLIENT_UPLOAD_TOOL}} (for secure document
> upload). Both are free to you. Both are required.

**Situation: intake call scheduled, may pre-date signature**
> {{CLIENT_NAME}},
> We are looking forward to our upcoming intake call scheduled with
> {{ATTORNEY_NAME}}. This call is an important first step in understanding you,
> your case, and planning together our course of action. We want to understand
> your goals and we want to ensure they are reasonable for your case. The more we
> know up front, the better we can help you and the more financially and time
> efficient we can be.

**Situation: matter onboarded, formal welcome letter (matter-sourced, two matters)**
> Hi {{CLIENT_NAME}},
> Welcome to {{FIRM_NAME}}. We're honored to help you through this important
> chapter of your life. Our goal is to bring clarity, direction, and peace of
> mind to what can often feel like chaos. Below is what you can expect from us
> and how to get the most out of working with our team.
[matter-sourced] — this is the live opening the firm actually sends. It leads
with the client's experience rather than with file status, and it names the
emotional register ("what can often feel like chaos") before any logistics.

**Situation: {{ROLE_DRAFTER}}'s first contact, portal invitation (matter-sourced)**
> Good afternoon,
> I am {{ROLE_DRAFTER}}, handling your case moving forward. Your
> case has been fully onboarded with us. Therefore, I wanted to introduce myself
> and send you this Welcome to your portal! email.
[matter-sourced] — {{ROLE_DRAFTER}} introduces themselves before giving instructions.
Time-of-day greeting rather than a name salutation.

## Body modules

### MODULE: portal-access-what-it-does (matter-sourced)
The live welcome letter explains the portal by what the client will do in it, not
by what it is.
> Your Client Portal Access
> You'll receive an email invitation to access your secure client portal. This is
> where you'll:
> • Upload documents, complete forms, and view updates.
> • Send and receive secure messages with our team.
> • Review case notes, upcoming deadlines, and invoices.
>
> Important: Check your spam or junk folder if you don't see the email within 24
> hours. If you have any issues logging in, contact {{ROLE_INTAKE}} at
> {{FIRM_EMAIL}} or call {{FIRM_PHONE}}.
[matter-sourced] — the spam-folder line pre-empts the most common onboarding
failure. Login trouble routes to the intake role, not the drafting role.

### MODULE: first-few-days-inventory (matter-sourced)
> Getting Started: The First Few Days
> In the first few days, you'll receive:
> • A welcome message confirming your case type and next steps.
> • Your [CONFIRM LOCALLY: fee or engagement agreement label] and intake forms to
>   complete electronically.
> • Instructions for your mandatory disclosure documents and any other required
>   uploads.
> • An introduction to your {{ROLE_DRAFTER}} and your {{ROLE_APPROVER}} (if not
>   already provided).
>
> Once these items are completed, our team can begin actively working on your
> case.
[matter-sourced] — the closing sentence makes the client's completion the
precondition for firm activity, stated without reproach.

### MODULE: firm-process-team-framing (matter-sourced)
> Our Firm's Process
> Our firm operates as a team — everyone who touches your file works together to
> move your case forward efficiently and strategically. We
> balance strong advocacy with practical solutions, and we only involve the court
> when necessary.
[matter-sourced] — "we only involve the court when necessary" sets a settlement
posture on day one and manages fee expectations.

### MODULE: why-the-portal-three-reasons (matter-sourced)
Channel discipline justified rather than merely asserted.
> Communication through the portal ensures:
> • Accountability — everything is timestamped and recorded.
> • Organization — no lost texts or misfiled emails.
> • Protection — all sensitive information stays secure.
[matter-sourced] — compare MODULE: channel-discipline above, which asserts the
rule. This module gives the client a reason to comply.

### MODULE: general-timeline-banded (matter-sourced)
Phases rather than dates, with an explicit non-commitment.
> General Timeline
> While every case is unique, here's a general outline of what happens next:
>
> Week 1–2:
> • Complete intake forms and document uploads.
> • Review your initial legal strategy and next steps.
>
> Weeks 3–6:
> • We prepare and/or respond to filings.
> • Exchange mandatory disclosures and financial documentation.
>
> Weeks 6–12:
> • Begin mediation, negotiations, or early case management.
> • Focus on resolution where possible before involving the court.
>
> If your case requires litigation, we'll update you on hearing schedules,
> discovery deadlines, and trial preparation timelines.
[matter-sourced] — banded week ranges, hedged at the top, with the litigation
branch acknowledged but not scheduled.
[CONFIRM LOCALLY: whether these bands are achievable in the buyer's venue —
shipping an unachievable timeline is worse than shipping none]

### MODULE: what-to-know-four-commitments (matter-sourced)
Four labeled commitments, two of which bind the client rather than the firm.
> What to Know
> • Response Time: Our firm responds within [CONFIRM LOCALLY: interval] business
>   hours. Urgent matters will always take priority.
> • Transparency: All billing, updates, and filings are visible to you in real
>   time.
> • Respect: We expect communication to remain professional — from everyone
>   involved.
> • Empowerment: You'll always understand what's happening, why, and what comes
>   next.
[matter-sourced] — "from everyone involved" is the firm's only stated behavioural
expectation of the client, and it is deliberately non-specific.

### MODULE: intake-forms-gate (matter-sourced)
The live sequence gates the attorney call on form completion, and says so
plainly.
> The first thing we need you to do is complete your intake forms. You will have
> [CONFIRM LOCALLY: number], depending upon the issues involved. These are VERY
> IMPORTANT as they provide us with the information we need to begin preparing
> the drafts for your pleadings and for your intake call with the attorney. We
> cannot book your intake call until you have completed these forms — I have sent
> them to you via the client portal. Attached you will find the instructions on
> how to access this portal. Once you have accessed the portal and completed the
> forms, I will be in touch with you to get some drafts ready for you and
> schedule your intake call with the attorney.
[matter-sourced] — a hard gate, stated as a fact about sequence rather than as a
condition or a threat.

### MODULE: portal-migration-instruction (matter-sourced)
Sent while the thread is still running in ordinary email.
> Please also note, if you have not done so yet, please log into the client
> portal as we will be communicating from now on in there.
>
> Please reply all to this email.
[matter-sourced] — the two instructions sit together in live practice: migrate to
the portal, but reply-all on this thread until you have. The transition itself is
the gap where communication leaks off-platform.

### MODULE: next-steps-ordered
Four numbered steps. The source is explicit that these are not optional and must
not be rearranged — the firm's onboarding sequence depends on the client
completing them in order.

> YOUR NEXT STEPS — IN ORDER
> 1. Review and sign your [CONFIRM LOCALLY: primary initiating document for this
>    matter type]. {{ATTORNEY_NAME}} has sent you a separate letter with
>    instructions. You will need to sign in front of a notary and return the
>    signed copy to us.
> 2. Answer one question: [CONFIRM LOCALLY: the single matter-specific question,
>    e.g. prior-name restoration — reply yes or no, and if yes provide the exact
>    prior legal name].
> 3. Upload your documents through your secure {{CLIENT_UPLOAD_TOOL}} portal
>    (links below). Start with the priority items — those are needed first before
>    {{ATTORNEY_NAME}} can begin drafting.
> 4. Complete your intake form (link below). This gives us the detailed
>    background information we need to build your Financial Affidavit and
>    settlement agreement.

### MODULE: upload-links-block
Three separate upload destinations plus the intake form. Source uses one link per
category, never a single combined link.

> DOCUMENT UPLOAD LINKS
> • General Documents: {{UPLOAD_PORTAL}}
> • Evidence / Supporting Docs: {{UPLOAD_PORTAL}}
> • Mandatory Financial Disclosure: {{UPLOAD_PORTAL}}
> • Intake Form: {{UPLOAD_PORTAL}}

### MODULE: documents-to-gather-tiered
> Please start collecting these. Upload them as you get them — you do not need
> everything at once. The items marked PRIORITY are needed before
> {{ATTORNEY_NAME}} can begin drafting.
>
> PRIORITY — Get these first:
> • [CONFIRM LOCALLY: three matter-specific priority items]
> • Marital home deed (if applicable)
> • Mortgage statement (if applicable)
> • All joint bank/financial account statements — past 3 months
> • Joint tax returns — past 3 years
>
> When you have them:
> • [CONFIRM LOCALLY: secondary items]
> • Any life insurance policies

### MODULE: how-we-work
> • All documents and communication go through your client portal. Check it
>   regularly.
> • If something urgent comes up — a legal deadline, the other party taking
>   action, anything unexpected — call the office directly. Do not wait for a
>   portal message.
> • Your attorney is {{ATTORNEY_NAME}}. I ({{ROLE_DRAFTER}}) am your day-to-day
>   contact for documents, status updates, and intake.
> • Your case moves at the speed of your documents. The faster we have what we
>   need, the faster {{ATTORNEY_NAME}} can move your case forward.

### MODULE: channel-discipline
Flagged in source as non-negotiable — it prevents communication drifting
off-platform.

> All of our communication with you runs through the portal — not through text,
> not through WhatsApp, not through personal email.

### MODULE: upload-hygiene-instructions
> • Upload one category at a time. Do not combine bank statements, tax returns,
>   and pay stubs into one PDF.
> • If a category does not apply to you, send us a short note instead of leaving
>   it blank — that way we know it was reviewed.
> • Phone camera scans must be PDF, not photo. Use a scanning app so each
>   document is one clean PDF.
> • Name files using your first name, the document type, and the date range.

### MODULE: scope-reminder
> As a reminder — your agreement covers: [CONFIRM LOCALLY: scope and fee
> structure exactly as written in the executed agreement]. Mediation attendance
> and additional services, if needed, are a separate addendum.

### MODULE: intake-call-expectations
Used in the intake-call variant. Four labeled sub-blocks in source: what to
expect, how to prepare, maximizing the call, what you will leave with.

> WHAT TO EXPECT
> • Case Overview. We will review the information you have provided in your
>   intake forms and discuss any additional details that may be pertinent.
> • Financial Affidavit. We will go over your Financial Affidavit and discuss any
>   clarifications needed.
> • Roadmap Creation. Together, we will outline a preliminary roadmap for your
>   case, identifying key steps and timelines.
> • Discovery Needs. We will discuss the discovery process and any documents or
>   information we may need from you or expect from the opposing party.
>
> MAXIMIZING THE CALL
> • Be open and honest. The more information you give us up front, the better we
>   can assist you.
> • Take notes. It is helpful to jot down any important points or next steps
>   discussed during the call.
> • Ask for clarification. Do not hesitate to ask for clarification on any points
>   that are unclear.
>
> WHAT YOU WILL LEAVE THE CALL WITH
> • A clear understanding of the next steps in your legal process.
> • An outline of your case strategy and objectives.
> • A list of additional information or documents you need to provide.
> • Answers to any questions you had prior to the call.

## Closing / next-steps bank

- `{{PROMISE_SET}}` — the source flags an onboarding promise line in this slot.
  The buyer must supply their own promise set here, or delete the line. Do not
  ship a borrowed promise as generic filler.
- `Welcome aboard. Let's get this done.`
- `Reply to this message in the portal so we know your portal is working.`
- `We are committed to providing you with the best possible legal support and
  guidance.`
- Confirmation-of-receipt ask: a short acknowledgement reply is requested so the
  firm knows the message landed.
- `We're Glad You're Here` — used as a closing section header, not a sentence.
  [matter-sourced]
- `We take pride in combining strong legal representation with clear
  communication and compassion. You're in capable hands — and we'll walk with you
  through every step.` [matter-sourced]
- `Welcome to {{FIRM_NAME}}.` repeated as the final line, closing the letter with
  the same words that opened it. [matter-sourced]
- `{{BRAND_TAGLINE}}` — the firm tagline sits below the final welcome line.
  Buyers must supply their own or delete; do not ship a borrowed tagline.
  [matter-sourced]
- `Please advise if you have any questions, looking forward to working with you.`
  [matter-sourced] — {{ROLE_DRAFTER}}'s standard close on the live welcome email.

## Signature block

The welcome message is signed by {{ROLE_DRAFTER}}, NOT {{ROLE_APPROVER}}. The attorney
sends a separate signed transmittal. This split is deliberate.

> {{ROLE_DRAFTER}}
> {{FIRM_EMAIL}}
> {{FIRM_PHONE}}
> {{FIRM_NAME}}

Companion onboarding emails (portal setup, intake prep) are signed:

> Sincerely,
>
> {{ATTORNEY_NAME}}
> {{FIRM_NAME}}

## Voice notes

- Second person throughout. Short declarative sentences. Frequent sentence
  fragments for emphasis ("Both are free to you. Both are required.").
- ALL-CAPS section headers, never bold-styled headings, in the portal-message
  format.
- Imperative mood for instructions. "Check it regularly." "Block the time."
- The firm states consequences plainly rather than softening: "Your case moves at
  the speed of your documents."
- Numbered lists for sequence; bulleted lists for inventories. Never mixed.
- Avoids legalese in client-facing onboarding entirely — no "herein," no
  "aforementioned," no rule citations in the welcome message.
- Avoids promising outcomes. Onboarding language is procedural only.
- Consistently tells the client what is needed FIRST rather than dumping the full
  document list as equally urgent.
- Escalation instruction is always concrete: call the office, do not wait for a
  portal message.

Additional notes from the matter-sourced letters and emails:

- Live practice uses contractions throughout ("you'll," "we'll," "here's"). The
  master templates do not. The sent letters are warmer than the masters.
- The live welcome letter names the client's emotional state once, early, and
  then never again — "what can often feel like chaos." No further sympathy
  language appears anywhere in the document.
- Title Case section headers with bold in the letter format; ALL-CAPS headers in
  the portal-message format. Two distinct house styles for two delivery channels.
- Selective ALL-CAPS for emphasis inside body text ("VERY IMPORTANT"), used by
  staff in email and not in the attorney-signed letter.
- The firm explains *why* a rule exists rather than only stating it. The portal
  requirement gets three named reasons.
- Client obligations are framed as sequence, not as conditions: "Once these items
  are completed, our team can begin actively working on your case." Cause and
  effect, no reproach.
- Timelines are banded and hedged ("While every case is unique"), never dated.
- Staff sign with `Best regards,`; the letter closes with a section header and a
  tagline rather than a valediction.
- Live email opens with a time-of-day greeting rather than a name. The letter
  opens with `Hi [first name],`.
- The firm states a settlement-first posture in the welcome document — "we only
  involve the court when necessary" — which doubles as fee-expectation
  management.

## Attorney flags

- Never send with unprovisioned or placeholder upload links.
- Confirm intake forms have been provisioned before the welcome goes out; confirm
  intake forms are RECEIVED before the intake-call prep goes out.
- Scope and fee language must be copied from the executed agreement, never
  paraphrased from memory.
- If the retainer is not yet signed when the intake-call prep is sent, do not
  write "your case" — write "your matter," and state that the retainer must be
  signed before substantive case work begins.
- Confirm which attorney is taking the call before sending; correct the body if
  only one attorney is assigned.
- First use of this template on any matter requires approving-attorney sign-off;
  routine thereafter.

## [CONFIRM LOCALLY] items

- Matter type and division label as the local clerk styles it.
- Primary initiating document for the matter type.
- The single matter-specific question for step 2.
- Priority document tiers — vary by matter type and by what the division requires
  early.
- Whether {{ROLE_DRAFTER}} or {{ROLE_APPROVER}} signs the welcome message in the buyer's
  practice.
- Local intake form set and whether it is provisioned pre- or post-signature.
- Whether the buyer runs one upload destination or three.

## Coverage

matters harvested: 4 distinct
templates harvested: 3 firm-agnostic masters
matter-sourced bank entries: 16
template-sourced bank entries: 14

Readiness is structural, and every bank in the required structure is now
populated from both provenances.

structural holes closed since the first pass:
- The first pass harvested no matter-level instances. This pass recovered live
  sent correspondence from four distinct matters: two formal welcome letters
  (byte-equivalent to each other — deduplicated to one variant), and two
  {{ROLE_DRAFTER}}-authored welcome email threads.
- Recovered and specified nine matter-sourced modules absent from the masters:
  portal-access-what-it-does, first-few-days-inventory, firm-process-team-framing,
  why-the-portal-three-reasons, general-timeline-banded,
  what-to-know-four-commitments, intake-forms-gate,
  portal-migration-instruction, and the closing/tagline bank.
- The intake-forms gate — the firm's actual onboarding control point, and the
  reason welcome sequencing works — appears nowhere in the master templates. It is
  now specified.
- The two competing subject-line conventions (masters prohibit matter
  identifiers; live practice uses them) are surfaced rather than reconciled
  silently.
- The channel-discipline rule in the masters is now paired with the live
  justification language, and the portal-migration gap is named.

remaining gaps:
- The masters remain the only source for the ordered-next-steps, upload-links,
  tiered-document-gather, upload-hygiene, scope-reminder, and intake-call-
  expectations modules. No matter-sourced instance of any of these was found.
- No welcome variant found for limited-scope, {{SERVICE_NAME}} coaching /
  limited-scope service lines, flat-fee-only, or
  Guardian ad Litem engagements. The source notes these "different sequences
  apply" but the alternate sequences are not written anywhere in the library.
- No welcome variant for post-judgment / modification matters opened on an
  existing relationship.
- No Spanish-language or plain-language-tier variant.
- No variant for a client who is a co-petitioner in an uncontested matter.
- The source library carries a new-client letters template slot with no content
  in it — a named place where new-client letter language should live, empty.
- No observed language for declining or deferring engagement.

## Tokens introduced by this spec

- `{{PROMISE_SET}}` — the buyer's own onboarding promise line or set of promise
  lines, used in the closing bank. No default; delete the line if the buyer has
  none.
- `{{BRAND_TAGLINE}}` — the buyer's own tagline, placed below the final welcome
  line. No default; delete the line if the buyer has none.
- `{{SERVICE_NAME}}` — the buyer's name for a coaching or limited-scope service
  line, where one exists.
