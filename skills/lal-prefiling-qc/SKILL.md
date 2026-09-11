---
name: lal-prefiling-qc
description: "Mandatory pre-filing QC gate. Fires when any filable document completes drafting - six screens including anti-hallucination and caselaw compliance. Critical findings block; attorney clears."
---

# {{FIRM_NAME}} Pre-Filing QC — Mandatory Gate

## When to use this skill (full trigger reference)

MANDATORY {{FIRM_NAME}} pre-filing quality control gate. Every document that will be filed with a court, served on a party, or sent outside the firm passes through this gate after drafting and before attorney sign-off. No exceptions. Fires automatically the moment any {{FIRM_NAME}} drafting skill completes a filable document, and on request. Triggers on: "QC this," "is this ready to file," "check before filing," "run prefiling QC," "run the QC gate," "ready to serve," "can we file this," "final check," "send it to {{ROLE_APPROVER}}," "ready for signature," or any request to validate litigation work product. Runs six screens — anti-hallucination, caselaw protocol compliance, evidence-law screening, drafting and formatting QC, scope and pleading discipline, and the attorney hard stop — then returns severity-tiered findings and a verdict. Critical findings BLOCK the document. This gate never clears anything for filing; only the attorney does that.

## WHAT THIS IS

The last mechanical check before a document reaches an attorney. It exists so {{ROLE_APPROVER}}
and {{ROLE_APPROVER}} spend their review time on **legal judgment**, not on catching a missing
certificate of service, a bulleted list in a pleading, or a bracketed placeholder
that survived to the final draft.

**Position in the sequence — this never changes:**

```
DRAFT  →  lal-prefiling-qc  →  ATTORNEY SIGN-OFF  →  FILE / SERVE / SEND
          (this skill)          ({{ROLE_APPROVER}})
```

This gate is **mandatory and blocking**. A document that has not passed it does
not go to the attorney. A document with an unresolved CRITICAL finding does not
advance at all.

**This gate does not approve filings.** It produces a verdict of BLOCKED,
CONDITIONAL, or CLEARED FOR ATTORNEY REVIEW. Only the attorney clears anything
for filing. Never write "approved," "ready to file," or "cleared to serve."

---

## STEP 0 — PREREQUISITES

Before running any screen, confirm you have:

1. **The actual final draft** — not a summary, not a description of it. If the
   document is in {{DMS}}, read it via `lal-file-connector` (Operation 3).
2. **Document type and procedural vehicle** — petition, motion, notice, proposed
   order, response, affidavit, discovery document, memo.
3. **Matter context** — case type, client role (Petitioner or Respondent), county
   and circuit, division, judge if assigned.
4. **What is about to happen to it** — filed, served, sent to OC, sent to client.
   The screens weight differently for a filed pleading than for a discovery
   response that is served but not filed.

If any of the four is missing, ask for it. Do not run a partial gate and imply a
full one ran.

---

## SCREEN 1 — ANTI-HALLUCINATION & FACTUAL GROUNDING

Every factual assertion, date, dollar figure, and record reference in the draft
must trace to something in the file. Claude generates plausible detail. Plausible
detail in a verified pleading is a Bar problem.

Check each of the following. Any failure is **CRITICAL**.

- [ ] Every date in the draft appears in a source document in the matter file
- [ ] Every dollar figure traces to a financial affidavit, statement, or order
- [ ] Every reference to a prior order quotes or cites an order that actually exists
      in `Filed Documents - Client/`, `Filed Documents - OP/`, or `Orders, Agreements, Reports/`
- [ ] Every party name, child initial, and DOB matches the caption and intake
- [ ] Every allegation of fact is either in the client's own account, a produced
      document, or a filed pleading — not inferred, not smoothed, not filled in
- [ ] No statistic, study, or general assertion about the world was invented
- [ ] Exhibits referenced by letter or number actually exist and are attached

**Any fact that cannot be traced gets bracketed and flagged — never left in as
prose.** Convert it to `[CONFIRM: source needed]` and list it in the findings.

Also check the mechanical items under the **two-state model**
(`lal-pleading-standard`): a DRAFT must show its flags, highlighted; a document
represented as FINAL must contain none of them.

**On a DRAFT (the normal case at this gate) — any failure is SIGNIFICANT:**

- [ ] Every attorney note, outstanding fact, and open question is **highlighted**
      (🟨) — an un-highlighted note buried in prose is the violation, not the note
- [ ] Every point where the drafter was unsure presents **highlighted alternatives**
      (🟩, drafted in full) — an assumption written as settled language where an
      alternative belongs is the violation
- [ ] No flag was silently deleted to make the draft look cleaner
- [ ] No facts, names, case numbers, or captions from any other {{FIRM_NAME}} matter — this
      one is **CRITICAL** at any stage

**On a document represented as FINAL (post-finalize) — any failure is CRITICAL:**

- [ ] No highlighting of any color
- [ ] No internal notes, drafting comments, or AI instructions
- [ ] No clause-bank labels, module letters, or template numbering
- [ ] No bracketed placeholders except blanks the attorney expressly left for
      execution
- [ ] No tracked changes or unresolved comments
- [ ] No alternative-provision blocks — one was selected

---

## SCREEN 2 — CASELAW PROTOCOL COMPLIANCE

**This screen does not restate the caselaw rules. It enforces
`lal-caselaw-protocol`, which governs firm-wide.** Load it and check compliance.

Any failure is **CRITICAL**:

- [ ] Every case cited in the draft came from project files — not web search,
      not model memory
- [ ] Every citation carries the attorney verification warning where the document
      is internal (memo, strategy note)
- [ ] For a document that will be filed: the attorney has personally verified
      every citation in {{RESEARCH_PROVIDER}}, Lexis, or a state court database, and has
      confirmed the case is still good law
- [ ] No case was cited broadly without connecting it to the specific relief
      requested
- [ ] No statute is cited that does not say what the draft says it says
- [ ] Statutory subsections are correct, not approximated

**If the draft contains a citation the attorney has not yet verified, the verdict
is BLOCKED.** An unverified citation in a filed document is the single highest
professional-liability exposure in this workflow. There is no urgency exception.

---

## SCREEN 3 — EVIDENCE-LAW SCREENING

Applies to any document that asserts facts to a court, attaches exhibits, or
seeks relief that requires an evidentiary predicate.

- [ ] **Authentication (§90.901)** — every attached exhibit has an identified route
      to authentication. Bank statements, texts, screenshots, and photographs do not
      authenticate themselves. Flag as **SIGNIFICANT** if the route is unclear.
- [ ] **Hearsay in affidavits (§90.801–.803)** — statements attributed to third
      parties in a sworn document need an exception or must be removed. **SIGNIFICANT.**
- [ ] **Privilege exposure** — attorney-client, work product, therapist-patient
      (§90.503), spousal. Check whether the draft discloses privileged material or
      attaches an exhibit that does. **CRITICAL** if privileged material is exposed.
- [ ] **Relevance to pled relief (§90.401)** — every factual allegation supports a
      specific element of the relief requested. Allegations that only make the other
      party look bad invite a motion to strike. **SIGNIFICANT.**
- [ ] **Expert predicate (§90.702)** — if the draft relies on a psychological
      evaluation, vocational assessment, or business valuation, the expert's basis
      and qualification are identified. **SIGNIFICANT.**
- [ ] **Verification** — if the document must be verified or notarized, the
      verification language is present and correct. **CRITICAL** if missing on a
      pleading that requires it.
- [ ] **Confidential material (Rule 2.420)** — see Screen 4 redaction checks.

---

## SCREEN 4 — DRAFTING & FORMATTING QC

Sourced from the {{FIRM_NAME}} Master Pleading Standard. These are firm formatting law.

### Formatting — any failure is SIGNIFICANT

- [ ] Times New Roman, 12-point, black
- [ ] Single spaced, paragraph spacing 0 pt before and 0 pt after
- [ ] Left aligned only — never justified
- [ ] One-inch margins on all sides
- [ ] Section headers in ALL CAPS and bold
- [ ] Sections numbered with Roman numerals; paragraphs with Arabic numerals
- [ ] **No bullet points.** None. Not anywhere.
- [ ] No horizontal lines, divider lines, dashes, underscores, or symbols as
      section breaks
- [ ] No shaded text boxes, no decorative formatting
- [ ] No tables unless the attorney specifically approved one
- [ ] Output is an editable `.docx` — not PDF, not markdown, not plain text

### Caption and identification — any failure is CRITICAL

- [ ] Correct court, judicial circuit, county, division, case number
- [ ] Caption centered, matching Florida circuit court format
- [ ] Party designations correct and **consistent throughout** — Petitioner and
      Respondent only. Never Husband, Wife, Mother, Father, Former Wife, or a
      client's first name unless the case style and posture actually support it
- [ ] Document title matches the procedural act being taken
- [ ] Party names identical to the caption in every occurrence

### Signature block and service — any failure is CRITICAL

- [ ] Signature block identifies the correct attorney, firm name, address, phone,
      primary and secondary email, Florida Bar number, and party represented
- [ ] Certificate of service present where required
- [ ] Certificate identifies service method, date, and each recipient with enough
      specificity to show proper service
- [ ] Represented parties served on counsel through the e-Portal
- [ ] Pro se parties: designated email confirmed, or formal service route identified
- [ ] Nonparty service (subpoena, records custodian, employer, bank, school,
      medical provider) — method and timing confirmed
- [ ] No generic certificate where a pro se party, nonparty, or separate email
      service is involved

### Confidentiality and redaction — any failure is CRITICAL

Confirm the document does not contain or attach, unredacted:
Social Security numbers · bank or credit card account numbers · tax records ·
child dates of birth or full names where initials are required · school records ·
medical, therapy, psychological, or substance-use records · domestic violence
facts · adoption records · sealed material · financial records subject to
privacy restrictions.

- [ ] Redactions intact and legible
- [ ] Notice of Confidential Information Within Court Filing prepared if required

### Internal consistency — any failure is SIGNIFICANT

- [ ] Pronouns match the parties
- [ ] Relief requested in the prayer matches the allegations in the body
- [ ] No conflicting or contradictory provisions
- [ ] Numbering is sequential with no gaps or repeats
- [ ] Cross-references point to the paragraph they claim to

---

## SCREEN 5 — SCOPE & PLEADING DISCIPLINE

The right relief in the wrong vehicle gets denied. Sourced from {{FIRM_NAME}}'s motion
practice standards.

- [ ] **Correct procedural vehicle.** Clarification is not rehearing. Clarification
      is not enforcement. Enforcement is not modification. A clerical correction is
      not substantive relief. **CRITICAL** if the vehicle is wrong.
- [ ] **No disguised relief.** A motion seeking to change timesharing, support,
      parental responsibility, alimony, or equitable distribution is a modification,
      whatever it is titled. **CRITICAL.**
- [ ] **No incompatible theories.** A draft cannot claim an order is clear enough
      for contempt and too unclear to follow, unless it pleads in the alternative
      and says so explicitly. **CRITICAL.**
- [ ] **Relief is convertible to an order.** Every request must be capable of
      becoming a specific paragraph in a proposed order. If it cannot, it is not
      relief — it is argument. **SIGNIFICANT.**
- [ ] **Within scope of representation.** Check the retainer. Limited scope and
      DIY matters cannot quietly expand. **CRITICAL** if out of scope.
- [ ] **Notice discipline.** A notice that argues facts or requests relief is not a
      notice. If it runs past six numbered paragraphs, it is drifting into motion
      territory. **SIGNIFICANT.**
- [ ] **Answers follow {{FIRM_NAME}} format.** Three permitted responses only: ADMITS,
      DENIES, or without knowledge and therefore denies. No argument, no elaboration
      inside a numbered response. No affirmative defenses unless the attorney
      specifically instructed them. **CRITICAL** if violated.
- [ ] **Tone.** Direct, professional, fact-based. No exaggerated accusations, no
      dramatic framing, no bloated language. **MINOR** unless it rises to a
      credibility problem, then **SIGNIFICANT**.

---

## SCREEN 6 — ATTORNEY HARD STOP

These conditions stop the document regardless of how clean everything else is.
Any one of them is **CRITICAL** and the verdict is BLOCKED.

- [ ] Attorney has not reviewed and approved the final version
- [ ] Any caselaw citation remains unverified
- [ ] The filing involves children's records, medical records, mental health or
      therapy records, substance-use records, domestic violence, sealed filings,
      emergency relief, defaults, adoption, TPR, or name-change safety concerns
      — all require express attorney approval
- [ ] The filing is a withdrawal, substitution, or limited appearance
- [ ] The filing is a Notice for Trial or a Notice of Production from Nonparty
- [ ] Initial service, supplemental petition service, or contempt service is involved
- [ ] A hearing is noticed that has not actually been reserved with the JA
- [ ] Mediation is noticed that is not confirmed
- [ ] Formal service may be required and the attorney has not confirmed the route
- [ ] The e-Portal document type or filing packet is unclear
- [ ] **TPR matter:** the petition does not address consent or no-consent upfront
- [ ] **TPR matter:** {{FIRM_NAME}} is being asked to represent a putative father — this is
      an intake disqualifier and the matter should not exist

Where a judge, division, or hearing is involved, run `lal-judicial-procedures`
live before clearing. Standing orders and JA requirements change.

---

## FINDINGS FORMAT

Report every finding in this structure. Do not summarize into prose.

```
PRE-FILING QC — [DOCUMENT TITLE]
Matter: Last, First - [Matter Type] (####-####)
Document type: [petition / motion / notice / order / response / affidavit]
Destined for: [filed / served / sent to OC / sent to client]
Run by: [staff member]        Date: MM.DD.YY

VERDICT: [BLOCKED | CONDITIONAL | CLEARED FOR ATTORNEY REVIEW]

CRITICAL — [N] finding(s). Document does not advance until resolved.
  C1. [Screen #] [What is wrong] → [Exact fix required]
  C2. ...

SIGNIFICANT — [N] finding(s). Fix, or attorney must expressly accept.
  S1. [Screen #] [What is wrong] → [Exact fix required]

MINOR — [N] finding(s). Fix before it goes out.
  M1. [Screen #] [What is wrong] → [Exact fix required]

SCREENS RUN:
  1 Anti-hallucination & factual grounding    [PASS / N findings]
  2 Caselaw protocol compliance               [PASS / N findings / N/A - no citations]
  3 Evidence-law screening                    [PASS / N findings]
  4 Drafting & formatting QC                  [PASS / N findings]
  5 Scope & pleading discipline               [PASS / N findings]
  6 Attorney hard stop                        [PASS / N findings]

UNTRACEABLE FACTS REQUIRING CONFIRMATION:
  [Every item converted to [CONFIRM: ...] — or "None"]

FOR ATTORNEY JUDGMENT:
  [Items this gate cannot resolve — strategy, tone, risk calls]

ROUTED TO: [{{ROLE_APPROVER}}]
```

### Verdict rules

- **Any CRITICAL finding → BLOCKED.** The document does not go to the attorney.
  Return it to the drafter with the fix list.
- **No CRITICAL, one or more SIGNIFICANT → CONDITIONAL.** Goes to the attorney
  with the findings attached. The attorney either directs the fix or expressly
  accepts the risk in writing.
- **No CRITICAL, no SIGNIFICANT → CLEARED FOR ATTORNEY REVIEW.** Minor findings
  still get fixed first.

Never issue a verdict without listing which screens ran. A partial gate reported
as a full gate is worse than no gate.

---

## WHO IS IN THE SESSION — APPROVAL BEHAVIOR

**{{FIRM_NAME}} attorneys: {{ATTORNEY_NAME}} and {{ATTORNEY_NAME}}.** Everyone else is staff.

- **Attorney in the session** — attorney-approval items are satisfied by the
  attorney's own instruction in the chat. Do not ask her to approve what she just
  directed, do not route her work to herself, do not repeat "attorney review
  required" back to the attorney conducting the review. State findings once,
  plainly, and proceed on her direction. Her "GO" is the sign-off.
- **Staff in the session** — every attorney-gated item routes to {{ROLE_APPROVER}} and
  waits. Staff direction never substitutes for attorney sign-off, no matter how
  confident or urgent.
- If the session doesn't identify who is working, ask once at the first
  attorney-gated item, then remember for the session.

The firm non-negotiable is unchanged — nothing is filed or sent without attorney
sign-off. This rule only fixes WHERE the sign-off comes from: when the attorney is
the one at the keyboard, her instruction IS the sign-off, and asking again is noise.

---

## STAFF LANES

| Role | Responsibility |
|---|---|
| **Drafter** ({{ROLE_DRAFTER}} or {{ROLE_REVIEWER}}) | Runs the gate on their own draft. Fixes everything they can resolve without legal judgment. |
| **{{ROLE_REVIEWER}}** | Confirms docket, deadlines, hearing reservations, service routes, and e-Portal packet before the gate clears. |
| **{{ROLE_DRAFTER}}** | Confirms exhibits exist and are attached, redactions are intact, and discovery references are accurate. |
| **{{ROLE_APPROVER}}** | Resolves every item under FOR ATTORNEY JUDGMENT. Verifies all citations. Signs off. |
| **{{ROLE_APPROVER}}** | Final approval on high-exposure filings, GAL work, and anything flagged in Screen 6. |

Findings requiring legal judgment go straight to {{ROLE_APPROVER}} — the drafter does not guess
at them and does not quietly delete the flagged language to make the gate pass.

---

## ROUTING — WHO CALLS THIS SKILL

Every {{FIRM_NAME}} skill that produces a filable or servable document hands off here
before the attorney sees it:

`lal-drafting-advanced` · `lal-msa-drafter` · `lal-parenting-plan-drafter` ·
`lal-contempt-movant` · `lal-contempt-defense` ·
`lal-fa-builder` · `lal-cs-worksheet` · `lal-cert-of-compliance` ·
`lal-advanced-discovery` · `lal-divorce-petitioner` · `lal-divorce-respondent` ·
`lal-prenup-drafter`

Skills with their own domain QC chain into this gate rather than replacing it:
`lal-name-change-qc` and `lal-disco-qc` run first on their own subject matter,
then hand the document here for the firm-wide screens. `lal-gal-qc` governs GAL work
product and runs in place of this gate for GAL reports — but any GAL **court
filing** still passes through here.

---

## WHAT THIS GATE DOES NOT DO

- It does not approve anything for filing. Only the attorney does.
- It does not substitute for reading the document. It structures the read.
- It does not make strategy calls, tone calls, or risk calls.
- It does not verify caselaw. It confirms the attorney did.
- It does not check whether the legal position is *correct* — only whether the
  document is filing-ready and internally sound.
- It does not silently fix substantive problems. It flags them.

---

## OUTPUT DELIVERY — FIRM STANDARD (v2, {{DMS}}-native)

All output from this skill is delivered through `lal-file-connector` (Operation 4).
This is the firm-wide standard — it overrides any older save instruction.

**Destination:** `Notes/` in the {{DMS}} matter folder
`Last, First - [Matter Type] (####-####)`. There is no `CLAUDE OUTPUT` folder and
no {{DMS}} path. Never `Drafts/` unless the attorney specifically directs it.

**Filename:** `MM.DD.YY - LastName - Prefiling QC - [DocTitle] - v1.docx` —
versioned, never overwritten. Scan `Notes/` for the same date + title and increment.

**Delivery depends on where this skill is running:**

- **Claude.ai (chat / Projects)** — Claude cannot write to {{DMS}}. Build the file
  with the correct filename, present it as a **download**, and print the destination
  block: matter folder → `Notes/`, filename, version. Never write "saved to
  {{DMS}}." The correct line is *"Ready to download — save to `Notes/`."*
- **Cowork (desktop)** — write to the folder designated for the session. Ask once at
  first delivery, then reuse it for the rest of the session. Confirm the **actual
  path written**, and state where the file belongs in {{DMS}} so it gets filed.

The QC report is a matter record. It is delivered and saved even when the verdict
is CLEARED — the file needs to show the gate ran.

Nothing is filed or sent without attorney sign-off. Time is tracked in {{PM_SYSTEM}},
including Claude-assisted work.

---

*{{FIRM_NAME}} Internal Skill — QC Layer — MANDATORY GATE — no filable document bypasses this*

---

## AMBIENT STANDARD — {{FIRM_NAME}} PLEADING FORMAT & DRAFT-STATE RULES

`lal-pleading-standard` governs every court-bound document this skill produces.
Two rules, from the first keystroke:

1. **Format correctly immediately** — portrait, Times New Roman 12 black, single
   spacing 0pt before/after, left aligned, 1" margins, {{FIRM_NAME}} caption (court centered ·
   case/division right · parties left · rule line ending in `/` · title centered
   bold ALL CAPS), numbering I. → 1. → a. → i. continuous. No bullets, no dividers.
   There is no rough-format stage that gets fixed later.
2. **Drafts show their work, highlighted** — attorney notes 🟨, outstanding facts 🟨,
   alternative provisions 🟩 drafted in full. When unclear what the pleading should
   contain, present highlighted ALTERNATIVES — never assume and draft one version
   as if decided. Never strip flags at draft stage; only `lal-finalize-draft`
   strips, after the attorney resolves them.

