---
name: lal-correspondence
description: "Four-lane correspondence engine: client, opposing counsel, bench, third party. Use to draft, revise, or QC any outgoing letter or email on a matter, with approval hard stops and pre-send QC."
---

# Correspondence — Router and Drafting Governor

## When to use this skill (full trigger reference)

The four-lane correspondence engine for a Florida family law practice — client, opposing counsel, bench, and third party. Identifies the lane and sub-type, loads the matching content spec, applies the firm format standard, enforces the spec's attorney-approval hard stops, and runs a pre-send QC pass. Use IMMEDIATELY on: "draft a letter", "draft an email", "write to the client", "welcome letter", "retainer transmittal", "status update", "document chase", "write to opposing counsel", "deficiency letter", "meet and confer", "settlement transmittal", "letter to a pro se party", "letter to the judge", "email the judicial assistant", "proposed order cover", "letter to the GAL", "preservation letter", "litigation hold", "closing letter", "withdrawal letter", "disengagement letter", or any request to write, revise, or QC an outgoing letter or email on a matter. Hard-stops on any firm-initiated disengagement until the attorney-supplied compliance block exists. No case law.

> **Not legal advice. Not authority.** Every rule, statute, and Bar rule named in this skill or
> in any output it produces must be verified against current official sources before it is
> relied on. Official sources only: `floridabar.org`, `flcourts.gov`, `leg.state.fl.us`.
> No case law appears anywhere in this skill, its references, or its output.

**Read `references/conventions.md` before running.** The conventions block is bundled into every
skill, so it sits in this skill's own `references/` folder. It governs environment flexibility, role
self-approval, soft prerequisite checks, whole-file search, transcript preference, command-center
writes, and the token and authority rules. Nothing below repeats it.

This skill does not contain letter language. **The language lives in nine content specs**, each
harvested from real correspondence and each labeling the provenance of every entry it carries.
This skill is the layer above them: it decides which spec applies, loads it, applies the format
standard, enforces the spec's own hard stops, and refuses to release anything that fails QC.

Three things it never does:

1. **It never invents a sub-type a spec does not cover.** Where a spec records that a document
   type has no source, this skill names the gap and stops. It does not scaffold from an adjacent
   type and present the result as sourced.
2. **It never generates letterhead.** See § 8.
3. **It never produces a firm-initiated disengagement letter** while the attorney-supply block is
   empty. See § 6. This is the one hard stop in the product that no role can self-approve past.

---

## 1. THE NINE SPECS

Every one of these is read-only. This skill loads them; it never edits them.

**Paths are relative to this skill's own directory.** In the built plugin the lane subdirectories are
preserved underneath the skill's `references/` folder, so every spec path below begins
`references/`.

| Lane | Spec file | Covers |
|---|---|---|
| client | `references/client/client-welcome-engagement.spec.md` | Welcome / engagement, portal and upload setup, intake-call prep |
| client | `references/client/retainer-transmittal.spec.md` | Executed-retainer transmittal under firm cover |
| client | `references/client/client-status-update.spec.md` | Monthly cadence, settlement posture, hearing confirmation, document-status update, settlement recommendation with decision checklist |
| client | `references/billing-deadline/missed-deadline-billing-reminder.spec.md` | Document chase, transaction-explanation request, deliverable chase, balance status, fee accounting and balance disposition |
| client | `references/closing/closing.spec.md` | Ten closing sub-types — work **completed** |
| client | `references/disengagement/disengagement.spec.md` | Seven disengagement sub-types — work **stopped early** |
| opposing counsel | `references/opposing-counsel/opposing-counsel.spec.md` | Thirteen sub-types, including the unrepresented-adverse-party sub-lane |
| bench | `references/bench/bench-judge-ja.spec.md` | Ten sub-types across the formal letter register and the live judicial-assistant email register |
| third party | `references/third-party/third-party.spec.md` | Six sub-types — court-appointed neutral, preservation, pre-service outreach, provider outreach, release instrument |

Four lanes, but **six client-lane specs**, because the client lane splits by trigger rather than
by recipient. Closing and disengagement are separate specs for a reason: closing fires when the
work finished, disengagement when it stopped early. They are not variants of each other and the
wrong one is a substantive error, not a formatting one.

---

## 2. HOW THE ROUTER SELECTS A SPEC

Four questions, in this fixed order. Do not draft a word before all four are answered.

### Question 1 — Who receives it?

| Recipient | Lane |
|---|---|
| The firm's own client | **client** |
| A lawyer representing the other side | **opposing counsel** |
| The other side, **unrepresented** | **opposing counsel**, unrepresented sub-lane — *not the counsel-facing version* |
| The judge, or the judicial assistant | **bench** |
| Anyone who is none of the above — a records custodian, a provider, a school, an employer, a neutral, a platform | **third party** |

**Confirm the other side's representation status before choosing.** Sending a counsel-facing
letter to an unrepresented party, or omitting the mandatory disclaimer, is the highest-risk error
in the opposing-counsel lane. Do not infer representation from the fact that a lawyer once
appeared; confirm current status.

Where the firm is acting as a **court-appointed neutral** rather than as counsel, the lane is
third party and the role is carried in the signature. Neutral and advocate roles are kept
strictly separate — a letter never blends them.

### Question 2 — What triggered it?

The trigger, not the topic, selects the spec. `references/lane-selection-matrix.md` carries the
full trigger table. The distinctions that get missed:

- **Retainer countersigned and funded** → retainer transmittal. **Matter opened** → welcome. They
  are two documents in sequence, four hours and twenty-four hours after the same event, signed by
  different roles on purpose.
- **Work finished** → closing spec. **Work stopped early** → disengagement spec. Ask which.
- **A production arrived and something is missing** → the document-chase sub-type in the
  billing-deadline spec, not a status update.
- **A balance has to be reconciled and disposed of** → the fee-accounting sub-type. **A balance
  merely has to be stated at closure** → the one-line status bank inside the closing spec.
- **A decision the client must authorize** → the settlement-recommendation sub-type with its
  per-issue Yes/No checklist, never the monthly cadence. The monthly status email is never the
  vehicle for bad news or substantive strategy.
- **Anything transmitted to the bench for entry or for the file** → the formal letter register.
  **A calendar question** → the judicial-assistant email register. Both are legitimate; they are
  different documents.

### Question 3 — Which sub-type, and is it sourced?

Open the spec. Find the sub-type in its own sub-types table or required-structure list. Then read
the provenance label. See § 3 — this determines what you tell the user before you draft.

If the sub-type is not in the spec at all, **stop**. Report:

> *"The correspondence corpus has no source for a <sub-type>. The <spec> records this as a named
> gap. I will not scaffold it from an adjacent sub-type, because a document assembled that way
> reads as tested when it is not. What I can do: <the nearest genuinely sourced sub-type>, or
> assemble a structure-only outline with every substantive block marked as requiring drafting."*

The sub-types the specs record as having **no source at all** — do not produce these:

- Non-payment disengagement, intent-to-withdraw warning, conflict or breakdown disengagement,
  client non-cooperation disengagement.
- Mid-matter past-due notice, trust or retainer replenishment request, payment-plan default
  notice, signature chase, missed-court-deadline client accountability letter.
- Expert, evaluator, and mediator engagement letters; subpoena cover letters; records-custodian
  **production** requests as distinct from preservation; school and non-clinical records requests;
  process-server instructions; GAL report transmittals.
- Any refund letter. The corpus's only money-on-exit language is a fee **waiver** with credit
  expressly denied, which is the inverse transaction and says the opposite thing about who owes
  whom.

### Question 4 — What must be read from the matter file first?

Per § 4 of the conventions, search the whole matter file before asserting anything is absent.
Specifically, before drafting:

| Sub-type | Read first |
|---|---|
| Retainer transmittal | The executed agreement — scope and fee language are copied verbatim, never paraphrased |
| Welcome / engagement | The executed agreement, and confirmation the upload destinations and intake forms are actually provisioned |
| Any deficiency letter | The actual production, the filed certificate of compliance, and the filed financial affidavit |
| Any settlement letter | The written client authorization for any figure stated |
| Any bench transmittal | The proposed order, the ruling notes or transcript, and opposing counsel's written position |
| Any closing letter | The docket, the final documents, and the trust and invoice position |
| Any status letter | The prior correspondence in the matter, so an ask is not repeated as if new |

---

## 3. PROVENANCE — TEMPLATE-SOURCED VERSUS MATTER-SOURCED

Every bank entry in every spec is labeled `[matter-sourced]` or `[template-sourced]`. The
distinction is the difference between language the source firm actually sent and language the
source firm wrote down but may never have used.

**Surface it to the user before drafting, in one line, and again in the output header.** A buyer
who discovers mid-matter that a letter was untested has been misled by omission.

| Provenance of the sub-type | What you say, before drafting |
|---|---|
| Fully matter-sourced | *"Drafting from language recovered from sent correspondence in <n> matters."* |
| Mixed | *"The structure and <named blocks> come from sent correspondence; <named blocks> exist only as untested firm templates. I'll mark them in the draft."* |
| **Template-only** | *"⚠️ This sub-type is template-sourced only — no sent instance of it exists anywhere in the corpus. The reasoning in the template is sound but the sentence-level voice is unverified. First use on any matter should be reviewed by `{{ROLE_APPROVER}}` against current practice."* |

The template-only sub-types, named so this is not guesswork:

- **Retainer transmittal — the entire document.** A sweep of every matter correspondence folder
  found no firm-drafted retainer transmittal. What occupies this slot in live practice is an
  automated `{{ESIGN_TOOL}}` execution notice, which is a system notice and not correspondence: it
  confirms execution to the file but does not confirm receipt to the client, state scope, route
  questions, set the first-week sequence, or attach an executed copy under firm cover. The gap is
  real and the document is worth sending — but a buyer adopting it is adopting a document the
  source firm specified and never operationalized.
  `[CONFIRM LOCALLY: whether the buyer's {{ESIGN_TOOL}} already sends an execution notice, and whether this transmittal supplements or replaces it, with {{ROLE_APPROVER}}]`
- **Monthly status cadence**, and **hearing / court-date confirmation**. The firm's live status
  correspondence is event-driven, not calendar-driven. The hearing-details block ships with seven
  empty fields and no populated instance exists in either source — reconstruct it locally.
- **Eight of thirteen opposing-counsel sub-types**, including both deficiency flavors. The only
  deficiency letters in the matter files were **incoming**, on another firm's letterhead. The
  four-part item discipline is sourced; the sentence-level voice of a deficiency entry is not.
- **Seven of ten bench sub-types** — every proposed-order cover, the courtesy-binder cover, both
  status letters, and the withdrawal letter. Matter correspondence folders held no outgoing bench
  letters at all; the bench lane lives in email and what is in email is scheduling.
- **Preservation letters** in the third-party lane — a firm-level template bank with no executed
  instance located in any matter.
- **Six of ten closing sub-types** — coaching, substitution, withdrawal-granted,
  administrative/dormant, mediation, and GAL closings exist only as untested templates.
- **Both disengagement sub-types that have any source at all** beyond the single executed
  client-directed stop.

Mark it in the draft too. A template-only draft carries, above the body and stripped before send:

```
PROVENANCE: template-sourced only. No sent instance of this document type exists in the
source corpus. First use requires {{ROLE_APPROVER}} review against current practice.
```

**Two live contradictions of the master templates** must be surfaced rather than smoothed, because
both are in active use and the buyer has to pick:

1. **Deadlines on client document asks.** The masters require every ask to carry a deadline. Live
   practice is deliberately deadline-free and frames the consequence as positional advantage lost
   rather than as a sanction. Ask which the buyer wants.
   `[CONFIRM LOCALLY: whether client document asks carry a stated deadline or are momentum-based, with {{ROLE_APPROVER}}]`
2. **Matter identifiers in subject lines.** The masters prohibit them; live welcome emails use an
   all-caps label plus the party styling. The live convention is legible in a threaded mailbox;
   the master convention is safer.
   `[CONFIRM LOCALLY: whether party styling may appear in email subject lines]`

---

## 4. APPLY THE FORMAT STANDARD

Load `references/format-standard.md`. It carries the layout, register, header, salutation,
caption, signature, enclosure, and copy conventions for all four lanes, plus the four voice lanes
and the two client-lane delivery registers.

The four rules that are violated most often:

1. **No bullets in letters to the bench or to opposing counsel.** Bullets are permitted in
   client-facing instructional letters and emails where readability requires them, and in the
   enumerated factual blocks the specs define — a posture block, a deficiency list, an enclosure
   list, a tab index. Not in running prose to a court or to counsel.
2. **The register tracks the signer, not the topic.** All-caps section headers in the plainer
   letters; title case in the attorney-signed substantive letters. First person singular in an
   attorney's strategy or recommendation letter; first person plural in a staff-drafted operational
   letter. Do not mix within one document.
3. **Exactly one option block ships.** Several specs carry mutually exclusive alternatives — the
   three professional-courtesy options, the three after-hearing circulation states, the three
   phrasings of the withdrawal mechanic. Pick one and delete the rest. A letter shipped with
   competing option blocks is named in the source as the most common formatting error.
4. **The signer is specified by the spec, and it is deliberate.** The retainer transmittal is
   attorney-signed; the welcome message is signed by `{{ROLE_DRAFTER}}`. That split is intentional.
   Formal bench correspondence is attorney-signed with no exception. Every opposing-counsel
   sub-type is attorney-signed. A representation-ending communication defaults to attorney
   signature and requires an explicit override to go out over any other signature.

---

## 5. ENFORCE THE SPEC'S OWN HARD STOPS

Each spec carries an `## Attorney flags` section. **Those flags are this skill's stop conditions,
not advisory notes.** Read them for the sub-type before drafting and check them again before
release.

Per § 2 of the conventions, an approving attorney running this skill **self-approves** every gate
that exists for reasons of seniority — "route to the attorney," "requires attorney review,"
"needs sign-off." Record the approval and continue. Do not tell an approving attorney to seek
attorney approval.

Three classes of stop survive self-approval, because none of them is about seniority:

### 5.1 Absent text — no role can approve text into existence

The disengagement attorney-supply block. See § 6.

### 5.2 Absent client authorization — the authorization is the client's, not the firm's

- **Never state a settlement figure the client has not authorized in writing.** Only one number in
  a letter is ever labeled authorized.
- **Never pre-fill the per-issue Yes/No decision checklist.** The checklist exists to create the
  authorization; pre-filling it destroys the thing it produces.
- **Never state a dollar figure not reconciled to the current affidavit and the underlying
  statements.** Not to a prior draft, and never estimated.

### 5.3 Unverified authority or unverified fact — verification is an act, not a permission

- Every rule, statute, and Bar rule carries
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- Where a client letter asserts a legal entitlement in plain language — a credit, a guideline
  treatment, a statutory allocation — the assertion is verified. Plain language does not lower the
  accuracy bar.
- A confirmation the letter says is "available upon request" must actually be in the file.
- A proposed order is reconciled against the ruling notes or transcript before transmittal. It
  tracks the ruling, not the client's preference.
- "Unopposed" requires affirmative written confirmation from opposing counsel. Silence is a
  different posture and a different letter.
- Confirm any statutory settlement-proposal mechanism actually reaches the claim before serving
  one. ⚠️ VERIFY: confirm rule and current text before relying on this.
- Never tell a client no deadlines remain unless the docket and `{{ROLE_APPROVER}}` confirm it.

### 5.4 The release steps that are not formatting

- **Strip any internal block before sending.** One observed letter shipped as a single file
  containing both the client letter and an `INTERNAL — DO NOT SEND` block carrying approval status,
  time-logging instructions, and open attorney questions. Removal is a release step with its own
  check.
- **Attach what the letter says is attached.** A transmittal without its attachment defeats its
  purpose. Enclosures are enumerated, never gestured at.
- **`cc:` opposing counsel on the face of any bench letter**, not only in the mail client, and
  confirm opposing counsel was advised *before* the letter went to the bench where the spec
  requires sequencing.
- **Prune inapplicable warning clauses.** A relocation warning in a matter with no children is a
  defect. So is a modifiability clause where no ongoing obligation exists.
- **Never argue the merits to the bench.** Where a substantive point must reach the court it goes
  in a filed motion or notice, not a letter. Where the form of an order is contested, enclose both
  and describe the disagreement neutrally.
- **Never characterize the other side.** The standard formula for an incomplete adverse position
  is that the request *does not account for the full financial picture* — no adjectives, no imputed
  motive.
- **No review solicitation in any representation-ending document.** Closing, disengagement,
  withdrawal, substitution, non-representation. One executed source letter solicited a public
  review in the same letter that announced a motion to withdraw; that does not propagate.
- **No practice-area cross-sell in a closing letter**, and **no estate-planning reference
  anywhere.** A closing letter is the worst possible place for a cross-sell because it sits beside
  the sentence disclaiming responsibility for future work; the two paragraphs contradict each
  other. A beneficiary-review reminder is permitted and must refer out.

---

## 6. THE DISENGAGEMENT HARD STOP

**Binding. Absolute. Not subject to self-approval, urgency, or operator override.**

`references/disengagement/disengagement.spec.md` carries a section headed
`## ATTORNEY-SUPPLY BLOCK — R. Regul. Fla. Bar 4-1.16 compliance language`. It is **deliberately
empty.** ⚠️ VERIFY: confirm rule and current text before relying on this.

Two independent tenant-wide sweeps confirmed that no source document anywhere in the corpus cites,
quotes, paraphrases, or alludes to that rule. There is nothing to preserve, so nothing was
preserved. **`{{ROLE_APPROVER}}` at your firm supplies it.** Nobody else is drafting it and nothing
arrives later to close it. This skill does not draft it, and neither does any other skill.

**Where it gets installed — the handle on this gate.** `{{ROLE_APPROVER}}` edits one file, one
section: **`references/disengagement/disengagement.spec.md`, the `## ATTORNEY-SUPPLY BLOCK`
section.** **The hard stop clears once that section is populated and attorney-approved**, and not
before. State that whenever the stop fires — a hard stop with no stated handle is a wall, and the
buyer cannot tell the difference between a boundary and a bug.

### 6.1 What the skill does

On any request for a **firm-initiated** representation-ending letter, before anything else:

1. Read the attorney-supply block in the spec.
2. **If it is empty — stop.** Do not draft. Output:

> **HARD STOP — disengagement compliance block not supplied.**
>
> A firm-initiated disengagement letter requires the R. Regul. Fla. Bar 4-1.16 compliance
> language, and that block has not been supplied by `{{ROLE_APPROVER}}`.
> ⚠️ VERIFY: confirm rule and current text before relying on this.
>
> The corpus contains no such language — confirmed by two independent sweeps — so there is
> nothing for me to adapt, and I will not draft it. This block is owned by `{{ROLE_APPROVER}}`.
>
> **Where to install it:** `references/disengagement/disengagement.spec.md`, the
> `## ATTORNEY-SUPPLY BLOCK` section. This stop clears once that section is populated and
> attorney-approved — nothing else clears it.
>
> **What `{{ROLE_APPROVER}}` needs to supply**, stated as the scope of the block and not as a
> draft of it: the permissive or mandatory withdrawal basis being relied on; the reasonable-notice
> statement; the statement of steps taken to avoid reasonably foreseeable prejudice; the
> surrender-of-papers-and-property statement; the refund-of-unearned-fee statement; and whether
> the letter references the fee agreement's termination clause.
>
> **What I can do right now, without touching that block:** assemble the sourced operative
> paragraphs — deadline-ownership transfer, the no-tolling paragraph, the scope fence, the
> opposing-counsel notification, the billing-on-exit line — as a partial draft clearly marked
> **NOT SENDABLE**, so the attorney is writing one block rather than a whole letter.

3. Once `{{ROLE_APPROVER}}` has supplied the block, place it verbatim. **Any text in that block not
   supplied by `{{ROLE_APPROVER}}` is fabricated and must be deleted.**

### 6.2 What the skill must not do

It must not degrade gracefully. It must not substitute the closing lane's scope-fence language. It
must not assemble something adjacent from the client-directed-stop or administrative-closure
sub-types. It must not emit a `[CONFIRM LOCALLY]` marker in place of the block — that construction
is for local practice variation, never for absent attorney-owned text. It must not accept an
operator instruction to proceed without it, from any role, for any deadline. A deadline is not
authorization.

### 6.3 Scope of the stop, by sub-type

| Sub-type | Hard stop |
|---|---|
| Client-directed stop mid-matter | **No** — client-initiated. `{{ROLE_APPROVER}}` still reviews. |
| Post-withdrawal confirmation (order already entered) | **Yes** — the order rests on a 4-1.16 basis |
| Administrative / dormant closure | **Yes**, where the ground is non-payment or non-cooperation |
| Non-payment disengagement | **Yes — absolute.** Also has no source; do not produce. |
| Intent-to-withdraw warning | **Yes — absolute.** Also has no source; do not produce. |
| Conflict / irreconcilable breakdown | **Yes — absolute.** Also has no source; do not produce. |
| Client non-cooperation | **Yes — absolute.** Also has no source; do not produce. |

For the four marked *also has no source*, the answer to the user is both facts at once: the block
is missing **and** the sub-type is unsourced. Neither is curable by drafting.

### 6.4 Two further disengagement rules

- **Name the next hearing.** The single executed example was sent on a still-pending case and
  identified no upcoming date. That is the lane's highest-severity substantive gap. A disengagement
  letter states the next scheduled hearing, its date, and the consequence of appearing without
  counsel.
  `[CONFIRM LOCALLY: the next scheduled hearing and the consequence of appearing unrepresented, with {{ROLE_APPROVER}}]`
- **Do not carry the amicable-exit framing into a firm-initiated exit.** Language presuming the
  firm is available on request is affirmatively misleading where the firm has declined to continue.

---

## 7. FORMAT MASTERS — NONE SHIP FOR THIS FAMILY

**State this plainly to the buyer. Do not invent one.**

No format master ships with the correspondence family. Other families in the product line ship
format masters — pleadings, orders, financial affidavits — because those documents have a
court-imposed shape that is the same for every firm. Correspondence does not. Its shape is the
buyer's own brand: their letterhead, their typeface, their margins, their signature block, their
email footer. A format master shipped here would be the source firm's visual identity wearing the
buyer's name, which is the opposite of a white-labeled product.

What ships instead: **`references/format-standard.md`**, which carries the layout in prose —
every element, its order, and its content rule — so the buyer applies it inside their own
template. That is a deliberate substitution, and it is stated rather than hidden.

---

## 8. NO LETTERHEAD IS GENERATED

This skill **does not generate letterhead.** Not as an image, not as a text block, not as a table,
not as a header row.

What it does: places a **letterhead position marker** at the top of any letter-format output, and
instructs the buyer to apply their own.

```
{{FIRM_NAME}} LETTERHEAD — apply the firm's own letterhead template to this document.
Position: top of page one. Content: firm name, {{FIRM_ADDRESS}}, {{FIRM_PHONE}},
{{FIRM_EMAIL}}. Continuation pages per the firm's own template.
```

The layout spec — what the block contains, where it sits, what appears on continuation pages, and
what changes for an email — is in `references/format-standard.md` § 2, in prose. Reasons this is a
rule and not a convenience:

- A generated letterhead carries the source firm's visual identity into the buyer's product.
- Firms have letterhead already, produced by a designer, and a generated substitute will differ
  from every other document the firm sends.
- Real approved source forms contain unfilled word-processor content controls in exactly the
  letterhead, addressee, delivery-method, and salutation fields. Generating that region is how
  `Click here to enter text.` reaches an outgoing letter.

Where output is an **email** rather than a letter, there is no letterhead at all — the firm's
standard email signature block applies, and this skill marks its position the same way.

---

## 9. PRE-SEND QC

Load `references/qc-checklist.md` and run it on every output. It is a gate, not a review.

Four hard-fail conditions, checked first, that stop release regardless of anything else:

1. `Click here to enter text.` or any run of placeholder X's appears anywhere.
2. An unresolved `{{TOKEN}}` remains in a document represented as ready to send.
3. A case name, reporter citation, or "courts have held" construction appears. **No case law.**
4. A firm-initiated disengagement letter exists with the attorney-supply block empty.

Then the lane-specific passes, the enclosure and copy check, the option-block check, the
internal-block strip, the prune-inapplicable-clauses check, and the identity sweep — source-firm
name, staff first name, **staff job title**, named vendor, literal bar number, billing rate,
tenant, path, drive letter, URL other than the three official Florida sources, estate-planning
reference, and review solicitation in a representation-ending document.

**Report the QC result in the output.** Pass, pass-with-flags naming each flag, or fail naming the
condition. A silent pass is not a pass.

---

## 10. WHAT THE SKILL WRITES BACK

Per § 6 of the conventions and **the write contract — the `references/write-contract.md` document
that belongs to the command-center skill**, not to this one:

| Event | Write |
|---|---|
| Correspondence drafted and released | Ledger entry naming lane, sub-type, provenance class, and recipient class |
| A letter sets a response deadline | A deadline object with all nine mandatory fields, its authority, and its computation basis |
| A letter completes a lifecycle stage — engagement confirmed, matter closed, representation ended | Stage completion per the write-contract sequence, plus the two ledger entries |
| An attorney flag was raised or a hard stop was hit | A flag at the severity the spec implies; a disengagement hard stop is at minimum `attorney-review` |
| A sub-type was template-only | An `informational` flag recording that untested template language went out |

If the command center does not exist, follow the write contract's table for that case. Never block
on its absence, and never drop the entry.

**Log the time.** The source treats time-logging as non-optional: both the drafting time and the
underlying document-review time are logged in `{{PM_SYSTEM}}` before the session closes.
`[CONFIRM LOCALLY: {{PM_SYSTEM}} time-entry codes for correspondence drafting versus document review]`

---

## 11. GRACEFUL DEGRADATION

| Dependency | If installed | If not |
|---|---|---|
| File connector | Read the matter file, the executed agreement, prior correspondence, and the production through it | Work from what the user pastes or uploads; say plainly the matter file was not read; never assert a document is absent |
| Command center | Read scope and position before drafting; write per § 10 | Ask the two questions you need — posture and scope — and emit the intended entry in your output as a `PENDING COMMAND CENTER WRITE` block |
| Ethics skill | Route ethics-adjacent questions to it; it wins on conflict | Apply § 5 and § 6 of this skill as written and flag the question to `{{ROLE_APPROVER}}` |
| File organizer | Offer a cleanup pass when the search surfaces misnamed or misfoldered documents | List the misnamed and misfoldered documents so the user can move them |
| Brand kit | Take voice archetype and always/never phrases from it | Use the spec's own voice notes, which are lane-specific and sufficient |
| Discovery suite | Build a deficiency letter against its audit output | Build it against the production, the certificate, and the affidavit read directly; say which |
| Judicial-procedures reference | Run it before every bench transmittal | Emit `[CONFIRM LOCALLY: this division's proposed-order format, submission channel, and binder policy, with {{ROLE_APPROVER}}]` and proceed |
| Roadmap / case-closing suite | Take the closure reason and checklist state from it | Ask the closure reason directly — it controls the letter, and the same letter is never used for every file |

---

## 12. OUTPUT SHAPE

Every output, in this order:

1. **Routing line** — lane, spec, sub-type, signer, delivery mode.
2. **Provenance line** — per § 3, and the template-only warning block where it applies.
3. **The draft** — letterhead or signature-block position marker, then the document.
4. **`[CONFIRM LOCALLY]` list** — everything the buyer must confirm before this goes out, each
   naming the item and the person.
5. **Attorney flags** — the spec's flags that apply to this draft, and any raised while drafting.
6. **QC result** — pass, pass-with-flags, or fail, per § 9.
7. **Command-center entry** — written, or emitted as `PENDING COMMAND CENTER WRITE`.

Nothing in this skill is filed, served, or sent. It produces drafts and it says so.
