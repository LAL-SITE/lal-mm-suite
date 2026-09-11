# Disengagement Letter — Content Spec
lane: client
sources: 3 distinct matters (M02, M04, M10 — M04 and M10 for adjacent material only) + 1 firm-level closing system (T-CLOSE, withdrawal and administrative templates only) + 1 approved form letter (T-FORM-C)
harvested: 2026-07-29

> **CRITICAL HARVEST FAILURE — READ BEFORE BUILDING.**
>
> This is the thinnest of the four lanes and the one a buyer is most likely to discover
> mid-matter. State the following plainly to any purchasing firm:
>
> 1. The corpus contains **no dedicated disengagement letter**. Not one. Every
>    representation-ending document located is a *closing* letter — it fires after work
>    concludes, not to terminate work early.
> 2. The corpus contains **no non-payment disengagement letter**.
> 3. The corpus contains **no intent-to-withdraw letter** (the pre-motion letter warning
>    a client that the firm will move to withdraw).
> 4. **No source anywhere in the corpus cites, quotes, paraphrases, or alludes to
>    R. Regul. Fla. Bar 4-1.16.** The instruction to preserve Rule 4-1.16 language
>    cannot be satisfied — there is no such language to preserve. Searches for
>    `4-1.16`, `declining or terminating representation`, and `no longer able to
>    continue representing you` returned zero responsive letters.
>
> Everything below is genuine, tokenized, source-traceable. Nothing is invented. Rule
> 4-1.16 must be drafted fresh by counsel; it is not harvested content.
>
> ⚠️ VERIFY: confirm rule and current text before relying on this.
>
> **THE FAILURE WAS RE-TESTED INDEPENDENTLY AND IT HOLDS.** A second, independent search
> was run specifically to find executed representation-ending letters, using different
> strategies from the first. Findings:
>
> - **Still zero occurrences of `4-1.16` or any equivalent ethical-rule basis.** Confirmed
>   twice, by two different search strategies. This is a stable finding, not a miss.
> - **Still no non-payment disengagement letter, no intent-to-withdraw letter, no
>   conflict-based disengagement, and no non-cooperation disengagement.**
> - **Still no executed substitution-of-counsel letter,** including within material
>   assembled for handoff to successor counsel — only intake, client-education, and
>   portal-onboarding material was located.
> - **One genuinely new executed source was found (M04)** and it is a *closing* on a
>   still-pending case, not a disengagement. It is included below only for the mechanic it
>   supplies, and it is labelled as such. It does not reduce the DE-4 through DE-7 gap.
> - **One further executed source was located (M10)** — a fee-accounting and
>   balance-disposition letter from a concluded matter. It is also **not** a disengagement:
>   it fires after a final judgment, and it disposes of a balance the *client* owed the
>   firm. It is recorded here only because it is the corpus's sole written treatment of
>   money on exit, and to state plainly that it **does not** close the unearned-fee-refund
>   gap — a waiver of fees owed to the firm is the opposite transaction from a refund of
>   fees not yet earned. See `## File retention and return-of-file language`.
>
> The lane's substantive shortfall is therefore confirmed, not narrowed. What the later
> harvesting did improve is **structural completeness**: the banks below are now complete
> in shape for every sub-type that has any source at all, and the mechanic hole — who tells
> the other side — is now filled from real language.

## When this fires

Disengagement fires when representation ends **before** the work is complete.
Distinguish sharply from closing:

| | Closing | Disengagement |
|---|---|---|
| Trigger | Work finished | Work stopped early |
| Cause | Final order, completed scope, completed task | Non-payment, breakdown, client direction, conflict, unreasonable demand, client non-cooperation |
| Client posture | Served | Often unhappy, sometimes unreachable |
| Court status | Usually final | Usually **still pending** |
| Central risk | Client thinks the firm still owns future work | Client misses a live deadline while unrepresented |

The one executed example in the corpus (M02) sits exactly on this boundary: the case was
**still pending** and the client had directed the firm to stop. The firm treated it as a
closing letter and bolted a withdrawal mechanic onto it.

## Sub-types

| Code | Sub-type | Source status |
|---|---|---|
| DE-1 | Client-directed stop mid-matter, case still pending | **Executed example exists** (M02) |
| DE-2 | Post-withdrawal confirmation (order already entered) | Template only (T-CLOSE) |
| DE-3 | Administrative/dormant closure for non-payment or non-communication | Template only (T-CLOSE) |
| DE-4 | Non-payment disengagement — firm-initiated, pre-withdrawal | **NOT FOUND — must be drafted** |
| DE-5 | Intent-to-withdraw warning letter | **NOT FOUND — must be drafted** |
| DE-6 | Disengagement for conflict / irreconcilable breakdown | **NOT FOUND — must be drafted** |
| DE-7 | Disengagement for client non-cooperation with discovery | **NOT FOUND — must be drafted** |

## Required structure per sub-type

**DE-1 (executed, M02) — the only structure the firm has actually used:**
1. Thanks-and-feedback opener
2. Case-status statement + stated cause + representation-concluded statement
3. Withdrawal mechanic — the firm will file a Motion to Withdraw
4. Court-correspondence-goes-to-you-now statement
5. Keep-your-address-current instruction
6. Free-of-charge address-update offer
7. Future-representation-requires-new-retainer statement
8. Future-questions-may-be-billable paragraph
9. Review request
10. Warm close
11. Both-attorneys signature block

**DE-2 (template):** effective-date statement with basis; deadline ownership transfer;
known-deadlines list or express no-knowledge disclaimer; documents returned; final
invoice.

**DE-3 (template):** reason for closure; **no-tolling paragraph**; scope fence; final
invoice or account statement.

**DE-4 / DE-5 / DE-6 / DE-7:** no source structure. Do not scaffold from DE-1 — DE-1 is
client-initiated and therefore omits every element that makes a firm-initiated
disengagement defensible (statement of cause, cure period, notice of intent, Rule
4-1.16 basis).

⚠️ VERIFY: confirm rule and current text before relying on this.

## Opening paragraph bank

**DE-1 opener (executed) — note the firm keeps the gratitude and the feedback
invitation even when the engagement is ending badly:**
> Thank you for allowing our firm to represent you in your family law matter. I am
> hopeful that you are happy with your representation. If you are not for any reason, we
> would appreciate feedback as we strive to provide outstanding assistance during
> difficult times.

**DE-2 opener:**
> This confirms that {{FIRM_NAME}} no longer represents you in this matter. The Court
> entered an order allowing withdrawal on {{DATE}}.

Alternate second sentence where no order was entered:
> Our representation ended effective {{DATE}} pursuant to [CONFIRM LOCALLY: basis].

**DE-3 opener — the firm's only explicit non-payment language anywhere in the corpus,
and it is a menu item rather than a paragraph:**
> We are administratively closing your file at this time because [CONFIRM LOCALLY: select
> exactly one — the requested service was completed / we have not received the requested
> information / **payment was not made** / you advised you do not wish to proceed / there
> has been no activity or communication].

> **GAP.** That select-one menu is the entirety of the firm's non-payment disengagement
> vocabulary. There is no paragraph explaining the arrears, no cure window, no amount, no
> escalation sequence, no reference to the fee agreement's termination clause.

## Body modules

### MODULE `de1-cause-and-conclusion` (DE-1, executed) — how the firm states the reason
The firm states the cause in a single dependent clause, attributes it to the client, and
moves straight to the consequence. It does not editorialize, does not express regret,
and does not describe the breakdown:
> Your case is currently pending, but you have requested us not to move it forward,
> thus, our representation in your matter has concluded.

### MODULE `de1-withdrawal-mechanic` (DE-1, executed)
> I will be filing a Motion to Withdraw in the Courts and any future correspondence the
> Court may need to have with you goes directly to you. As such, it is important that you
> keep your contact and address information updated with the Courts.

Alternate mechanic used when no motion is required:
> We will be filing a Notice of Non-Representation in the Courts so that any future
> correspondence the Court may need to have with you goes directly to you.

Third variant (T-FORM-C, approved form, round-2 find) — first person, and it makes the
address-currency instruction a consequence of the filing rather than a separate ask:
> Our representation of you is now concluded. I will be filing a Notice of
> Non-Representation in the Courts so that any future correspondence the Court may need to
> have with you goes directly to you. As such, it is important that you keep your contact
> and address information updated with the Courts.

> **The corpus contains three phrasings of the same mechanic and no rule for choosing
> among them.** `Motion to Withdraw` (M02), `Notice of Non-Representation` (T-FORM-C,
> M04), and both offered as alternates in the templates. Which instrument is correct
> depends on posture and division and the corpus never says so.
> [CONFIRM LOCALLY: motion vs. notice, by division and case posture]

### MODULE `notify-opposing-counsel` (M04, executed) — **round-2 find; closes a structural hole**
Round 1 recorded that no source said who informs the other side. One now does. This is
mandatory in any disengagement where the firm was counsel of record, because the client
otherwise has no basis to assume the other side knows they are unrepresented:
> We will notify opposing counsel that we are no longer the attorney of record in your
> matter.

### MODULE `future-correspondence-comes-to-you` (M04, executed)
> Please note that [CONFIRM LOCALLY: opposing counsel / the other party / the Court] will
> need to correspond with you directly regarding your case unless and until you decide to
> rehire us for further representation.

> **DEFECT IN SOURCE — DO NOT PROPAGATE.** M04 reads `the attorney will need to correspond
> with you directly`. `The attorney` is ambiguous and can be misread as the firm's own
> lawyer, which would invert the meaning of the entire communication. Name the actor.
>
> **CAUTION ON REUSE IN THIS LANE.** M04 was a *completed limited scope* on a pending case.
> Its `unless and until you decide to rehire us` framing presumes an amicable exit and puts
> the initiative with the client. In a firm-initiated disengagement that framing is wrong:
> it implies the firm is available on request when the firm has in fact declined to
> continue. Rewrite before use.

### MODULE `de1-address-update-offer` (DE-1, executed) — a distinctive goodwill gesture
> We would be happy to file a Notice of Updated Contact information for you in the
> future, free of charge if required. Simply contact our office and we will assist you.

### MODULE `de1-new-retainer-required` (DE-1, executed)
> We are happy to assist you in the future should you require our services. In order to
> obtain further assistance from our firm, you would need to sign a new retainer
> contract.

### MODULE `de1-future-questions-billable` (DE-1, executed)
> While we are happy to answer any small questions that may come up, we have many
> clients and remembering the details of any one case after the passage of time can be
> difficult. Because of this, if we are required to pull your file, review the pleadings,
> agreements or judgments, and advise you as to your rights and or options there could be
> a charge involved. Feel free to contact us and we will let you know whether we would
> require such a fee.

### MODULE `de2-deadline-ownership-transfer` (DE-2, template) — the core protective clause
> You are responsible for all future deadlines, hearings, filings, discovery, court
> communications, and compliance with court orders unless and until another attorney
> appears for you.

### MODULE `de3-no-tolling` (DE-3, template) — the single most important disengagement paragraph in the corpus
> This letter does not extend any court deadline or pause any requirement in your case.
> If you have a pending court case, you remain responsible for monitoring the docket,
> meeting deadlines, filing documents, attending hearings, and complying with all court
> orders unless you hire an attorney to handle those responsibilities.

### MODULE `scope-fence` (DE-2, DE-3)
> {{FIRM_NAME}} is not responsible for future work in this matter unless a new written
> agreement is signed.

### MODULE `rule-4-1-16-basis` — **NOT HARVESTED. NOT DRAFTED HERE.**
Confirmed absent by two independent searches of the corpus. Do not reverse-engineer it from
the closing templates — they do not address it. This module must be supplied by
{{ROLE_APPROVER}} at your firm and is governed by the hard stop in
`## ATTORNEY-SUPPLY BLOCK — R. Regul. Fla. Bar 4-1.16 compliance language` below. Do not
place drafted text here.

⚠️ VERIFY: confirm rule and current text before relying on this.

## ATTORNEY-SUPPLY BLOCK — R. Regul. Fla. Bar 4-1.16 compliance language

**STATUS: NOT DRAFTED. NOT HARVESTABLE. OWNED BY {{ROLE_APPROVER}} AT YOUR FIRM.**

⚠️ VERIFY: confirm rule and current text before relying on this.

This block is intentionally empty. **{{ROLE_APPROVER}} at your firm must supply the
R. Regul. Fla. Bar 4-1.16 compliance language for this lane before any firm-initiated
disengagement letter is produced.** It is **not** supplied by this corpus, by any agent, or
by any downstream skill author. Two independent searches of the entire corpus confirmed that
no source document anywhere in the corpus cites, quotes, paraphrases, or alludes to Rule
4-1.16. There is nothing to preserve, so nothing has been preserved. Any text appearing in
this block that was not supplied by {{ROLE_APPROVER}} is fabricated and must be deleted.

**What {{ROLE_APPROVER}} is expected to supply.** Listed as a scope boundary for the block,
not as a draft of it, and not as legal advice:

- the permissive- or mandatory-withdrawal basis being relied on
- the reasonable-notice statement
- the statement of steps taken to avoid reasonably foreseeable prejudice to the client
- the surrender-of-papers-and-property statement
- the refund-of-unearned-fee statement
- whether and how the letter references the fee agreement's termination clause

**HARD STOP — BINDING ON THE SKILL.** The disengagement skill **must refuse to produce a
sendable firm-initiated disengagement letter while this block is empty.** It must not
degrade gracefully, must not substitute the closing lane's scope-fence language, must not
assemble something adjacent from DE-1 through DE-3, and must not emit a draft carrying a
`[CONFIRM LOCALLY]` marker in place of this block. The required behaviour is to stop, state
that the Rule 4-1.16 block has not been supplied by {{ROLE_APPROVER}}, and route the
matter to {{ROLE_APPROVER}}. A disengagement product that can ship a letter without this
block is not fit for use in Florida.

Scope of the hard stop:

⚠️ VERIFY: confirm rule and current text before relying on this.

| Sub-type | Hard stop applies |
|---|---|
| DE-1 client-directed stop | No — client-initiated; attorney should still review |
| DE-2 post-withdrawal confirmation | Yes — the order rests on a 4-1.16 basis |
| DE-3 administrative / dormant closure | Yes, where the ground is non-payment or non-cooperation |
| DE-4 non-payment disengagement | Yes — absolute |
| DE-5 intent-to-withdraw warning | Yes — absolute |
| DE-6 conflict / breakdown | Yes — absolute |
| DE-7 client non-cooperation | Yes — absolute |

## What the firm declines to state

Derived from the one executed example and the templates. This is a real, harvestable
pattern and it is consistent:

- **It does not describe the breakdown.** No narrative of what went wrong, no
  characterization of the client's conduct, no defense of the firm.
- **It does not express regret or blame.** No "we regret," no "unfortunately," no
  "despite our repeated efforts."
- **It does not quantify the arrears.** Even the non-payment closure option says only
  `payment was not made`. No figure, no aging, no invoice reference.
- **It does not state a cure period.** No "if payment is received by {{DATE}} we will
  reconsider."
- **It does not cite an ethical rule or the fee agreement.** No rule number, no contract
  clause.
- **It does not warn about the specific consequences of proceeding unrepresented** beyond
  the generic deadline-ownership transfer. It does not name the next hearing.
- **It keeps the gratitude and the review request even on a bad exit.** M02 solicited a
  public review in the same letter that announced a Motion to Withdraw.

> Whether the last item is a strength or a defect is an attorney judgment. Flag it; do
> not silently normalize it.

## Consequence / deadline language bank

**Deadline ownership (DE-2):**
> You are responsible for all future deadlines, hearings, filings, discovery, court
> communications, and compliance with court orders unless and until another attorney
> appears for you.

**Known-deadlines disclosure (DE-2) — one or the other, never blank:**
> If there are pending deadlines or hearings, they are listed below based on the
> information currently available to us:
>
> {{DEADLINE_LIST}}
>
> Or, where there are none known, state instead: We are not aware of any currently
> scheduled hearings as of the date of this letter, but you are responsible for checking
> the court docket.

**No tolling (DE-3):** see `de3-no-tolling` above.

**Address-currency warning (DE-1):**
> As such, it is important that you keep your contact and address information updated
> with the Courts.

**Billing on exit:**

| Situation | Language |
|---|---|
| Final invoice | `Attached is your final invoice.` |
| Outstanding balance | `As of the date of this letter, your account reflects a balance of {{AMOUNT}}. Please contact our office to make payment arrangements.` |
| Refund pending | `Our records reflect a remaining trust/retainer balance of {{AMOUNT}}. The refund will be processed according to firm procedure after final reconciliation.` |
| Payment plan survives closure | `Your file is being closed, but your payment obligation remains active. Please continue making payments according to the agreed payment arrangement unless the firm confirms otherwise in writing.` |

> **GAP.** No source provides a deadline by which the client must pay, respond, cure,
> collect the file, or retain new counsel. Every deadline in this lane must be set locally.

## Post-representation warning clause bank

Disengagement inherits the closing lane's clause bank, but only a subset is appropriate
when work stopped early. Use:

**Unrepresented-status warning — assembled from DE-2 and DE-3 source language:**
> You are responsible for all future deadlines, hearings, filings, discovery, court
> communications, and compliance with court orders unless and until another attorney
> appears for you. This letter does not extend any court deadline or pause any
> requirement in your case. You remain responsible for monitoring the docket.

**Scope fence:**
> {{FIRM_NAME}} is not responsible for future work in this matter unless a new written
> agreement is signed.

**Enforcement / anti-retaliation (from closing bank, applies equally):**
> If the other party does not comply with the order, keep records and seek legal advice.
> Do not retaliate by violating the order yourself. Your own noncompliance can hurt your
> ability to enforce the order later.

**Tax disclaimer:**
> {{FIRM_NAME}} does not provide tax advice. Speak with a qualified tax professional
> about the tax impact of support, property transfers, retirement division, sale of
> property, dependency exemptions, filing status, or settlement terms.

**Do NOT carry over from the closing bank:** the modification, relocation, child support,
alimony, and parenting-plan clauses. Those presuppose a final order. In an early exit
there usually is none, and including them implies work was completed that was not.

> **GAP.** No source contains a warning that a specific upcoming hearing will proceed
> without counsel, that a default may be entered, or that a pending motion will go
> unopposed. These are the warnings a disengagement letter most needs and the corpus does
> not have them.
> [CONFIRM LOCALLY: name the next scheduled hearing and its date, and state the
> consequence of appearing without counsel — with {{ROLE_APPROVER}}]

## File retention and return-of-file language

**Documents returned (DE-2):**
> Attached are documents from your file that you should keep for your records:
> [CONFIRM LOCALLY: list documents].

**Transfer to successor counsel (from the substitution template, reusable):**
> We have provided or will provide your file materials as follows: [CONFIRM LOCALLY:
> describe transfer method]. If your new counsel needs additional documents, they may
> contact our office.

> **GAP — material for a disengagement product.** No source states: a retention period; a
> destruction schedule; a deadline for the client to collect the file; what happens if
> the client never collects; whether original documents are returned or copies; who bears
> copying cost; or any surrender-of-papers language tied to Rule 4-1.16(d). All of it
> must be drafted locally.
>
> ⚠️ VERIFY: confirm rule and current text before relying on this.
>
> - [CONFIRM LOCALLY: file retention period and destruction policy — with {{ROLE_APPROVER}}]
> - [CONFIRM LOCALLY: deadline for client to request the file, and disposition after that date]
> - [CONFIRM LOCALLY: originals vs. copies, and who bears reproduction cost]
> - [CONFIRM LOCALLY: unearned-fee refund mechanics and timing — with the role that handles trust and billing reconciliation at your firm]

**Round-3 partial find (M10) — a retention policy is *referenced* but never stated:**
> All file materials will be made available to you per our standard file retention policy.

> This is the only sentence in the corpus that acknowledges a retention policy exists. It
> supplies no period, no destruction schedule, no collection deadline, and no
> originals-versus-copies rule, so every gap above stands. It is recorded because it tells a
> buyer the phrase the firm actually uses, and because a productized letter that says
> "per our standard file retention policy" while no such policy is written down is a defect.
> [CONFIRM LOCALLY: locate or write the policy this sentence refers to before using the
> sentence — with {{ROLE_APPROVER}}]

**Money on exit — what M10 does and does not supply.** M10 waives a balance the client owed
the firm, prices the waiver as a firm loss, limits it to one time, and expressly denies that
it creates any credit balance. That is a **fee-disposition** posture, not a refund posture.
> **DOES NOT CLOSE THE UNEARNED-FEE GAP.** A refund of unearned fees on early termination is
> the inverse transaction and remains entirely unsourced. Do not adapt M10's waiver language
> into a refund letter — the two say opposite things about who owes whom, and M10's
> `no credit balance` fence would be affirmatively wrong in a refund context.

## Closing bank

- `Please give us a call if you have any questions or need legal services in the future. Thank you!` (DE-1, executed)
- `We wish you the best moving forward.` (substitution template)
- Review request as used in DE-1, tokenized: `We would greatly appreciate your review of our services on [CONFIRM LOCALLY: review platforms]. This helps other prospective clients know the types of attorneys they would be hiring.`
  — **flagged**: soliciting a public review in a disengagement letter is an attorney call.

> **GAP.** No source provides a neutral, non-solicitous close appropriate to an adverse
> exit. Every close in the corpus is warm or promotional.
> [CONFIRM LOCALLY: adopt a neutral close for firm-initiated disengagement]

## Signature block

DE-1 (executed) used the full block, and because two attorneys had appeared, **both
signed**:

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

Templates used the shorter form:

```
Sincerely,

{{ATTORNEY_NAME}}
{{FIRM_NAME}}
```

**Recommendation, flagged as such:** a firm-initiated disengagement should be signed by
{{ROLE_APPROVER}}, not by {{ROLE_DRAFTER}}, and should carry the delivery legend and a
retained proof of transmission. The corpus does not state this; it is inferred from the
closing workflow's requirement to save the sent communication and any proof of mailing.

## Voice notes

- **Cause is stated in one clause and attributed, not argued.** `you have requested us
  not to move it forward, thus, our representation in your matter has concluded.` One
  sentence. Cause, connective, consequence.
- **The register does not shift when the news is bad.** The disengagement letter opens
  with the same thanks-and-feedback paragraph as a successful closing. The firm does not
  have a separate "bad exit" voice.
- **Deadline warnings are stated as the client's responsibility, never as the firm's
  regret.** `You are responsible for...` never `we are sorry we cannot...`
- **The firm offers one free future service on exit** (filing an updated-contact notice)
  while simultaneously warning that substantive questions may be billable. That
  combination — a small free gesture next to a clear fee fence — is the firm's
  characteristic exit posture.
- Short sentences in the operative paragraphs. Longer, more conversational sentences in
  the courtesy paragraphs.
- No passive voice in the deadline transfer. No hedging verbs anywhere in the operative
  blocks.

## Attorney flags

- **DO NOT SHIP DE-4 THROUGH DE-7 FROM THIS CORPUS.** Non-payment disengagement,
  intent-to-withdraw, conflict-based disengagement, and non-cooperation disengagement
  have no source. Any template presented for those sub-types would be fabricated.
- **Rule 4-1.16 must be drafted by counsel.** It is absent from every source, confirmed
  twice. {{ROLE_APPROVER}} at your firm must supply it. See the
  `## ATTORNEY-SUPPLY BLOCK` and its hard stop. A disengagement product without it is not
  fit for sale in Florida, and the skill must refuse to send rather than approximate it.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- **{{ROLE_DRAFTER}} signed the one new executed representation-ending communication
  (M04).** It went out over {{ROLE_DRAFTER}}'s name with {{ROLE_APPROVER}} copied. Whether a
  non-attorney may sign a communication that ends the firm's status as attorney of record is
  an attorney decision. Default the skill to attorney signature and require an explicit
  override.
  [CONFIRM LOCALLY: who may sign a representation-ending communication — with
  {{ROLE_APPROVER}}]
- **M04's `unless and until you decide to rehire us` framing must not be carried into a
  firm-initiated exit.** It presumes the firm is available on request. In a DE-4 through
  DE-7 posture that is affirmatively misleading.
- **An approved-forms library is not automatically QC clean.** T-FORM-C is a form the firm
  treats as approved, and it ships with unfilled `Click here to enter text.` placeholders, a
  duplicated sign-off, live third-party review URLs, and cross-practice marketing language
  the firm's actual scope does not support. Nothing may be lifted from such a library
  without being opened and read first.
- **DE-1 solicits a public review while announcing a Motion to Withdraw.** Attorney must
  decide whether to retain that in a productized disengagement letter. Default
  recommendation: remove.
- **DE-1 does not name the pending hearing.** The case was still pending and the letter
  did not identify a single upcoming date. This is the highest-severity substantive gap
  in the lane.
- The non-payment ground appears only as a bracketed menu option. It has never been
  written out as a paragraph by this firm.
- No source addresses unearned-fee refund on early termination, surrender of papers and
  property, or steps taken to avoid foreseeable prejudice.
- Whether a Motion to Withdraw or a Notice of Non-Representation is required varies by
  posture and division. The corpus shows the firm using both without stating the rule
  that distinguishes them.
- Do not close a matter with unresolved trust funds, refund issues, or payment disputes
  without {{ROLE_APPROVER}} and [CONFIRM LOCALLY: which role handles trust and billing reconciliation at your firm] approving it.
- Do not state that no deadlines remain unless the docket and the attorney confirm it.

## [CONFIRM LOCALLY] items

- [CONFIRM LOCALLY: R. Regul. Fla. Bar 4-1.16 basis, notice, and prejudice-avoidance language — with {{ROLE_APPROVER}}. Not present in corpus.] ⚠️ VERIFY: confirm rule and current text before relying on this.
- [CONFIRM LOCALLY: whether withdrawal in this division requires a motion, a notice, or client consent, and whether a hearing is set]
- [CONFIRM LOCALLY: this judge's practice on granting withdrawal close to a scheduled hearing or trial]
- [CONFIRM LOCALLY: name the next scheduled hearing and state the consequence of appearing unrepresented]
- [CONFIRM LOCALLY: cure period and dollar threshold before non-payment disengagement is triggered — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: fee agreement's termination clause and whether the letter must cite it]
- [CONFIRM LOCALLY: file retention period, client collection deadline, and post-deadline disposition]
- [CONFIRM LOCALLY: unearned-fee refund mechanics and timing — with the role that handles trust and billing reconciliation at your firm]
- [CONFIRM LOCALLY: whether a review request is appropriate on an adverse exit]
- [CONFIRM LOCALLY: delivery method and proof-of-transmission requirement for disengagement]
- [CONFIRM LOCALLY: whether all appearing attorneys must sign]

## Coverage

**Readiness standard for this lane is structural completeness, not example count.** Where a
sub-type has any source at all, its banks are now complete in shape — opening, body
modules, consequence/deadline language, post-representation warnings, file retention,
closing, signature. Where a sub-type has no source, that is stated rather than papered over.

examples harvested: 6 distinct sources (3 distinct matters; 2 templates from a single
firm-level system; 1 approved form letter)
round-2 delta: +1 distinct matter (M04, mechanic only — it is a closing, not a
disengagement), +1 approved form letter (T-FORM-C)
round-3 delta: +1 distinct matter (M10, money-on-exit and file-retention-reference only —
it is a post-judgment closing, not a disengagement). **No new disengagement sub-type was
sourced in round 3.** The round-3 contribution to this lane is one corrected map finding
and two honest negatives.

distinct matters by sub-type:
- DE-1 client-directed stop: M02 — 1 matter
- DE-2, DE-3: 0 matters (templates only, apparently never sent)
- DE-4, DE-5, DE-6, DE-7: 0 matters, 0 templates, 0 sentences — **unchanged after repeated
  independent searching**

structural banks completed in round 2:
- `notify-opposing-counsel` — previously **absent corpus-wide**. Now sourced from real
  language. This was the single largest structural hole in the lane: every prior template
  transferred deadline ownership to the client without ever saying the other side would be
  told.
- `future-correspondence-comes-to-you` — the client-facing consequence of the above.
- Third phrasing of the withdrawal/non-representation mechanic (T-FORM-C), which exposed
  that the corpus holds three phrasings and no selection rule. Now flagged.
- `## ATTORNEY-SUPPLY BLOCK` established with a per-sub-type hard-stop table, so the lane
  now has a defined refusal behaviour instead of an open gap.
- Signature bank extended to cover email delivery and the staff-vs-attorney question.

gaps — **not found in any source; must be drafted, not harvested:**
- **R. Regul. Fla. Bar 4-1.16 language of any kind.** Zero occurrences corpus-wide,
  confirmed by two independent searches using different strategies. Owned by
  {{ROLE_APPROVER}} at your firm; see the ATTORNEY-SUPPLY BLOCK.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- Dedicated disengagement letter (as opposed to a closing letter)
- Non-payment disengagement letter
- Intent-to-withdraw / pre-motion warning letter
- Disengagement for conflict of interest or irreconcilable breakdown
- Disengagement for client non-cooperation with discovery or disclosure
- Any cure period, arrears figure, aging, or escalation sequence
- Any warning naming a specific upcoming hearing or the risk of default
- Surrender of papers and property language
- Unearned-fee refund language on early termination. **Re-confirmed in round 3.** M10
  supplies a fee *waiver* with credit expressly denied, which is the inverse transaction and
  must not be adapted into a refund letter.
- Steps-taken-to-avoid-prejudice language
- File retention period, collection deadline, or destruction schedule. **Partially advanced
  in round 3:** M10 references a "standard file retention policy" by name, but the policy
  itself was not located and no term of it is stated anywhere in the corpus.
- Neutral (non-promotional) closing appropriate to an adverse exit

partial coverage:
- DE-1 is the only executed example and it is client-initiated. The firm has no executed
  firm-initiated disengagement letter in this corpus.
- DE-2 and DE-3 are templates that have, so far as the harvest can establish, never been
  sent.
- Non-payment appears once, as one option inside a bracketed menu.
- Deduplication note: duplicate copies of the same forms were encountered repeatedly. Each
  distinct document is counted once, and re-encounters added no new sentences to this lane.
- **Net assessment unchanged across every harvesting round.** This lane is still the
  thinnest of the four and still the one a buyer is most likely to hit mid-matter. Later
  harvesting improved its shape, not its substance.

## Tokens introduced by this spec

| Token | Substitutes |
|---|---|
| `{{DEADLINE_LIST}}` | The list of known pending deadlines and hearings in the DE-2 known-deadlines block. Never emitted empty — if there are none known, the express no-knowledge disclaimer is used instead. |
