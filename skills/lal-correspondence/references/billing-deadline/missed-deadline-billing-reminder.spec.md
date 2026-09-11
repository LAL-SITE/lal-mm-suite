# Missed Deadline and Billing Reminder — Content Spec
lane: client
sources: 3 distinct matters (M06, M07, M10) + 1 firm-level billing language bank (T-CLOSE) + 2 firm-level client-education letters (T-MD, T-FA)
harvested: 2026-07-29

> **HARVEST INTEGRITY NOTE — ASYMMETRIC LANE.**
>
> This lane splits cleanly into two halves and the corpus covers them very unevenly:
>
> - **Document and signature chase (missed-deadline accountability):** genuinely well
>   covered in voice, with one strong executed matter example and supporting
>   client-education letters that establish the escalation vocabulary.
> - **Billing:** still **largely absent as collection correspondence.** There is no
>   past-due notice, no trust replenishment request, no payment-plan default letter, and
>   no fee-arrears escalation letter anywhere in the corpus.
>
> Searches for `trust account replenish`, `retainer past due`, `payment reminder`, and
> `outstanding balance` returned zero collection letters.
>
> **ROUND-2 ADDENDUM — THE BILLING HALF IS NO LONGER EMPTY.** A closed/concluded matter
> (M10) yielded a full executed **fee-accounting and balance-disposition letter**. It is
> the only document in the corpus that reconciles fee agreements against payments, states
> a balance, disposes of that balance, and fences the disposition. It is still
> **closure-context, not mid-matter collection** — so BR-2, BR-3 and BR-4 remain unsourced.
> But BR-1 has grown from a six-row status bank into a structured sub-type with real
> language. See `BR-5` in `## Sub-types` and `## Coverage`.

## When this fires

**Missed-deadline half.** Fires when the client owes the firm something the firm cannot
proceed without: mandatory disclosure documents, a signature, a financial affidavit
answer, a form, a class certificate, or an explanation of a transaction the firm found in
production. The firm's practice is to fire this **iteratively during review**, not once at
a hard deadline.

**Billing half.** In the corpus, billing language fires only **at closure**. No source
shows the firm sending a mid-matter billing communication.

Confirmed triggers:
- Document production is partially complete and a specific item is missing (M06)
- The firm found an item in production that was not on the client's financial affidavit
  and needs an explanation (M06)
- The firm found a recurring payment stream it cannot characterize (M06)
- A class certificate is outstanding and cannot be filed until the client forwards it (T-MD)
- Balance, refund, or payment-plan status must be stated at closure (T-CLOSE)

## Sub-types

| Code | Sub-type | Source status |
|---|---|---|
| MD-1 | Document chase / disclosure gap follow-up | **Executed example** (M06) |
| MD-2 | Explanation request on a specific transaction or account | **Executed example** (M06, embedded) |
| MD-3 | Deliverable chase (certificate, form, class completion) | Template (T-MD) |
| MD-4 | Signature chase | **NOT FOUND — must be drafted** |
| MD-5 | Missed court-ordered deadline / client accountability escalation | **NOT FOUND — must be drafted** |
| BR-1 | Balance / trust status statement at closure | Language bank only (T-CLOSE) |
| BR-2 | Mid-matter past-due notice | **NOT FOUND — must be drafted** |
| BR-3 | Trust replenishment request | **NOT FOUND — must be drafted** |
| BR-4 | Payment-plan default notice | **NOT FOUND — must be drafted** |
| BR-5 | Fee accounting and balance disposition | **Executed example** (M10) — new in round 2 |

## Required structure per sub-type

**MD-1 (executed, M06) — the firm's signature structure, and the highest-value artifact
in this lane. Order is load-bearing:**
1. Letterhead block; date
2. `Re: {{CASE_NO}} — Documents We Still Need From You`
   *(the subject line names the ask, not the problem)*
3. **Acknowledgment and credit first** — thank the client for what arrived, name it
   specifically, and say what it enabled
4. Praise line (`Nice work getting these together quickly.`)
5. `WHAT WE RECEIVED` — bulleted, specific, month-by-month
6. `ONE SMALL GAP TO CLOSE` — the single most acute miss, isolated and minimized
7. `WHAT WE STILL NEED FROM YOU` — bulleted, each item with a one-line reason and a
   both-ways instruction (`If it's filed, send a copy. If not, tell us when.`)
8. `WHY THIS MATTERS` — the legal consequence, stated once, briefly
9. `HOW TO SEND THESE` — the mechanism, plus an offer of help
10. Thanks and next-step commitment from the firm
11. Signature block
12. **`INTERNAL — DO NOT SEND` block** — approval status, time-logging instruction, open
    items for attorney

**MD-3 (template):** requirement statement; options list; approval caveat; return
instruction with the filing consequence.

**BR-1:** one sentence selected from the status bank, placed in the closing letter.

**BR-5 (executed, M10) — the only structured billing communication in the corpus. Ten
blocks, in order:**
1. Letterhead; date; addressee
2. `RE:` line naming the letter as an **accounting**, plus the matter identifier
   *(the subject line does not say "balance due" or "payment" — it says "clarification")*
3. Purpose sentence — a clear accounting of the agreements signed and the payments made
4. `YOUR {{FEE_TYPE}} AGREEMENTS` — one named, dated heading per agreement, each with its fee
   amount, its scope sentence, and a bulleted list of what the fee covered
5. `PAYMENTS RECEIVED` — dated ledger plus an explicit total
6. `YOUR ACCOUNT SUMMARY` — per-agreement reconciliation, each ending in a status verdict
   (`PAID IN FULL`, or the outstanding figure)
7. `OUR DECISION` — the contractual position stated first, then the disposition, then the
   fence on the disposition
8. `VALUE OF THE {{FEE_TYPE}} ARRANGEMENT` — hourly-equivalent comparison, attached invoice
   reference *(optional and risk-bearing — see Attorney flags)*
9. `CONCLUSION` — representation concluded, file availability, question channel, thanks
10. Signature; `cc: File`

> Block 7 is the operative block and the order inside it is load-bearing: **entitlement
> before concession.** The firm states what the client contractually owes, only then
> waives it. Reversing this makes the waiver read as an admission the fee was unearned.

**MD-4 / MD-5 / BR-2 / BR-3 / BR-4:** no source structure exists.

## Opening paragraph bank

**MD-1 opener (executed) — the firm leads with receipt, not with the deficiency.** The
three moves are: name what arrived, say what it enabled, then praise. Where production
surfaced an account that does not appear on the financial affidavit, the firm frames that
as a benefit of the client's own production rather than as a discrepancy:
> Thank you for sending over the {{DOCUMENT_CATEGORY}} — we've received the statements you
> uploaded, including the account that wasn't listed on your Financial Affidavit. Having
> those statements now lets us get it added and keep your disclosure accurate. Nice work
> getting these together quickly.
>
> As we go through everything, here's where things stand:

**MD-1 transition into the gap:**
> A few items from our last review remain outstanding. We know this is a lot, so take
> them one at a time — there's no single deadline, but the sooner we have these, the
> stronger your position going into {{NEXT_MILESTONE}} on {{DATE}}.

**MD-3 opener (template):**
> In every divorce action where minor children are involved, and every paternity case,
> the court requires that the parents take a parenting class before a final order can be
> entered.

⚠️ VERIFY: confirm rule and current text before relying on this.

**Initial-disclosure framing (T-MD), useful as the first touch before any chase:**
> We move fast after you hire us — that usually means we also prepare and file a
> Financial Affidavit at intake.

**Sequenced framing (T-FA), used when the affidavit is in hand and documents are next:**
> We have your financial affidavit — next we need to gather your Mandatory Disclosure
> (MD).

**BR-5 opener (executed, M10) — round-2 find; the only billing opener in the corpus.**
Note that it frames the letter as a service to the client (`provide you with a clear
accounting`) rather than as a demand, and it names both halves of the ledger — what the
client agreed to and what the client paid:
> RE: CLARIFICATION OF [CONFIRM LOCALLY: fee type] AGREEMENTS AND PAYMENTS
> Case {{CASE_NO}} | {{CLIENT_NAME}}
>
> Dear {{CLIENT_NAME}},
>
> I am writing to provide you with a clear accounting of the [CONFIRM LOCALLY: fee type]
> agreements you signed with our firm and the payments you made during your representation
> in your [CONFIRM LOCALLY: matter type] case.

**Disclosure-requirement framing (T-FA):**
> In every case we must prepare a financial affidavit and produce certain other documents
> called "mandatory disclosure." This letter has lots of information [CONFIRM LOCALLY:
> attach or link the firm's disclosure guide].

## Body modules

### MODULE `md1-what-we-received` (MD-1, executed)
Structural, not verbatim. Always specific, always enumerated, always time-bounded. One
bullet per document category received, each carrying the period it covers:
> **WHAT WE RECEIVED**
> - {{DOCUMENT_CATEGORY}} for {{PERIOD}}
> - {{DOCUMENT_CATEGORY}} for {{PERIOD}}
> - {{DOCUMENT_CATEGORY}} for {{PERIOD}}

### MODULE `md1-one-small-gap` (MD-1, executed) — the firm's minimizing frame
Isolate the single most acute miss, state what is held against what is missing, and ask for
the one item. Do not bundle other asks into this block.
> **ONE SMALL GAP TO CLOSE**
>
> We noticed {{MISSING_PERIOD}} is the one period missing from the {{DOCUMENT_CATEGORY}} —
> we have {{PERIOD}}, but not {{MISSING_PERIOD}}. Could you upload that one statement when
> you get a chance so the history is complete for the whole period we're covering?

### MODULE `md1-still-need-list` (MD-1, executed)
Every bullet follows the same three-part shape: **the item — why we need it — what to do
if it doesn't exist.** Preserve that shape; it is the distinctive move. The bullets below
are generic *categories* of ask, shown to demonstrate the shape. Populate them with the
actual categories outstanding in the matter; do not carry these examples over verbatim.
> - **Annual return status for {{PERIOD}}** — Let us know whether you've filed yet. If
>   it's filed, please send us a copy. If not, tell us when you expect to file so we can
>   note that on your disclosure.
> - **Returns for any entity you hold an interest in** — If any have been filed, please
>   send them. If none have been filed, let us know so we can address that directly.
> - **Formation or organizing documents for any entity** — Whatever you have showing how
>   it is set up. This helps us support the value we've listed for it.
> - **Title or registration documents for any titled asset** — So we can confirm and
>   document your ownership on the disclosure.
> - **A third-party-prepared financial statement, where one exists** — This backs up the
>   corresponding income figure on your Financial Affidavit rather than leaving it as your
>   own estimate.

### MODULE `md2-explain-this-transaction` (MD-2, executed) — narrow, dated, non-accusatory
The pattern: one transaction, identified by amount and date only, with the ask limited to
source and purpose. Never characterize it, never imply concealment.
> An explanation of the {{AMOUNT}} {{TRANSACTION_TYPE}} from {{DATE}} — just a quick note
> on who this was from and what it was for, so we can document it if needed.

### MODULE `md2-characterize-this-stream` (MD-2, executed)
The pattern: a recurring stream the firm can see but cannot characterize. Ask the client to
name what it is and flag the disclosure consequence.
> Clarification on the recurring payments of approximately {{AMOUNT}} per month — please
> let us know what these payments are and whether they arise from another matter or
> obligation. Depending on the answer, we may need to add that to your Financial Affidavit.

### MODULE `md1-why-this-matters` (MD-1, executed) — the accountability lever, used once
> **WHY THIS MATTERS**
>
> Florida law requires both sides to fully disclose their finances before mediation and
> any final agreement. The more complete your disclosure is now, the less room there is
> for the other side to raise questions about it later — whether at mediation or in court.

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `md1-how-to-send` (MD-1, executed)
> **HOW TO SEND THESE**
>
> You can upload everything directly to your {{UPLOAD_PORTAL}}, the same way you sent the
> credit card statements. If anything doesn't apply to you or you're not sure how to
> answer one of these, just reply and let us know — we'll help you sort it out.

### MODULE `md3-deliverable-return-consequence` (MD-3, template)
> Once you complete the class, you will be given a certificate of completion. Please
> forward that certificate to us so we can file it with the court.
>
> [CONFIRM LOCALLY: list approved providers. Source note: if the client finds a different
> class, confirm it is approved by the Florida Supreme Court.]

⚠️ VERIFY: confirm rule and current text before relying on this.

### MODULE `br1-status-bank` (BR-1, T-CLOSE) — the entire billing vocabulary in the corpus

| Situation | Language |
|---|---|
| Final invoice attached | `Attached is your final invoice for services rendered.` |
| No balance due | `As of the date of this letter, your account does not reflect a balance due.` |
| Outstanding balance | `As of the date of this letter, your account reflects a balance of {{AMOUNT}}. Please contact our office to make payment arrangements.` |
| Refund pending | `Our records reflect a remaining trust/retainer balance of {{AMOUNT}}. The refund will be processed according to firm procedure after final reconciliation.` |
| Flat fee earned | `The flat-fee service has been completed and the fee has been earned according to the terms of your agreement.` |
| Payment plan survives closure | `Your file is being closed, but your payment obligation remains active. Please continue making payments according to the agreed payment arrangement unless the firm confirms otherwise in writing.` |

> Only the third and sixth rows are collection-adjacent, and both are closure-context.
> Neither states an amount due date, a late fee, a suspension-of-work consequence, or an
> escalation step. **BR-5 (M10) now supersedes this bank for any matter where a balance
> actually has to be reconciled and disposed of** — use the modules above, not these rows.

### MODULE `br5-agreements-recital` (BR-5, M10) — round-2 find
Each agreement gets a named, dated heading, its fee, its scope, and a bulleted record of
the work it covered. The bullets are what makes the fee defensible.
> You entered into [CONFIRM LOCALLY: number] separate [CONFIRM LOCALLY: fee type]
> agreements with our firm:
>
> **AGREEMENT 1: [CONFIRM LOCALLY: scope name] (Signed {{DATE}})**
> Flat Fee Amount: {{AMOUNT}}
>
> This agreement covered our representation for [CONFIRM LOCALLY: scope] and related
> services through [CONFIRM LOCALLY: the terminating event]. This included:
> - [CONFIRM LOCALLY: enumerate the work actually performed]

### MODULE `br5-payments-ledger` (BR-5, M10)
> **PAYMENTS RECEIVED.** Our records show the following payments received from you:
>
> | Date | Amount |
> |---|---|
> | {{DATE}} | {{AMOUNT}} |
>
> TOTAL PAYMENTS: {{AMOUNT}}

### MODULE `br5-account-summary` (BR-5, M10)
Per-agreement, line-item, ending in a verdict. Credits are shown, never netted silently.
> **AGREEMENT 1: [CONFIRM LOCALLY: scope name]**
> - Flat fee owed: {{AMOUNT}}
> - Less: [CONFIRM LOCALLY: credit description] credit: ({{AMOUNT}})
> - Amount due: {{AMOUNT}}
> - Payment received ({{DATE}}): {{AMOUNT}}
> - STATUS: PAID IN FULL
>
> **AGREEMENT 2: [CONFIRM LOCALLY: scope name]**
> - Flat fee owed: {{AMOUNT}}
> - Payment received ({{DATE}}): {{AMOUNT}}
> - Original outstanding balance: {{AMOUNT}}

### MODULE `br5-entitlement-statement` (BR-5, M10) — must precede any concession
> Per your [CONFIRM LOCALLY: agreement name] Agreement signed on {{DATE}}, you
> contractually owe the full [CONFIRM LOCALLY: fee type] fee of {{AMOUNT}}. The flat fee is
> earned upon receipt and is not refundable or reducible based on actual time spent or case
> outcome.
>
> You have paid {{AMOUNT}}, leaving a balance of {{AMOUNT}} due under the terms of your
> signed agreement.

### MODULE `br5-balance-waiver-and-no-credit-fence` (BR-5, M10) — **highest-risk module in this lane**
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

> This is the only place in the corpus where the firm disposes of money owed to it in
> writing. The three-part shape — **waive, price the waiver, fence the waiver** — is the
> reusable structure. Every figure requires attorney sign-off.

### MODULE `br5-value-comparison` (BR-5, M10) — optional, risk-bearing
> To illustrate the financial benefit of our [CONFIRM LOCALLY: fee type] arrangement, we
> have prepared an itemized summary of all work performed on your case (attached as
> [CONFIRM LOCALLY: invoice reference]). If we had billed you on an hourly basis for the
> same services actually provided, your fees would have totaled {{AMOUNT}}. Instead, by
> using our [CONFIRM LOCALLY: fee type] structure, you paid only {{AMOUNT}} in total fees —
> representing a savings of more than {{AMOUNT}} compared to hourly billing.
>
> The attached invoice demonstrates the substantial volume and scope of work performed on
> your behalf and reflects the true value of the legal services you received.

### MODULE `br5-conclusion-and-channel` (BR-5, M10)
> Your representation on this matter is concluded. The final judgment was entered on
> {{DATE}}, and your case is now closed. All file materials will be made available to you
> per our standard file retention policy.
>
> If you have any questions about this accounting, please do not hesitate to reach out
> through the {{UPLOAD_PORTAL}}. We will be happy to clarify anything further.
>
> Thank you for allowing {{FIRM_NAME}} to assist you with your family law matter.

### MODULE `internal-do-not-send` (MD-1, executed) — a genuine differentiator
The executed letter carried a trailing internal block. Reproduce the pattern; it is
strong product content:
> **INTERNAL — DO NOT SEND**
>
> **Approval status:** Attorney review required before sending (financial
> disclosure/discovery content touching income verification and a previously undisclosed
> account).
>
> **{{PM_SYSTEM}}:** Log time entry for drafting this correspondence and for the
> underlying document review.
>
> **Open items for attorney:**
> 1. Confirm whether any newly surfaced account should be added to an amended Financial
>    Affidavit.
> 2. [CONFIRM LOCALLY: name the still-missing item] — flagged in letter.
> 3. Once any third-party-prepared financial statement is received, route to income
>    analysis.
> 4. Outstanding return and entity-documentation items remain unresolved and may affect
>    equitable distribution valuation.

## Consequence / deadline language bank

**This is the lane's weakest area and the honest finding is unusual: the firm
deliberately declines to impose a deadline.** From the executed letter, verbatim:
> there's no single deadline, but the sooner we have these, the stronger your position
> going into {{NEXT_MILESTONE}}

The consequence is framed as **positional advantage lost**, not as sanction, not as
firm-side penalty, and not as a date:
> The more complete your disclosure is now, the less room there is for the other side to
> raise questions about it later — whether at mediation or in court.

Softeners consistently paired with every ask:
- `when you get a chance`
- `take them one at a time — we know this is a lot`
- `If anything doesn't apply to you or you're not sure how to answer one of these, just reply and let us know`

Deliverable-consequence framing (MD-3) — the only place a hard consequence appears, and
it is procedural rather than punitive:
> the court requires that the parents take a parenting class **before a final order can
> be entered**

> **GAP — severe.** No source provides: a stated deadline date; a `by {{DATE}}`
> construction; a second-or-third-notice escalation; a consequence for continued
> non-response; a suspension-of-work warning; a court-sanction warning to the client; a
> motion-to-compel warning directed at the firm's own client; a late fee; or an interest
> statement.
>
> - [CONFIRM LOCALLY: response deadline convention for client document requests — with {{ROLE_APPROVER}}]
> - [CONFIRM LOCALLY: escalation ladder — how many notices before attorney contact, and what the final notice says]
> - [CONFIRM LOCALLY: whether the firm will state a work-suspension consequence for non-payment or non-response]
> - [CONFIRM LOCALLY: trust replenishment threshold and the notice period tied to it — with the role that handles trust and billing reconciliation at your firm]
> - [CONFIRM LOCALLY: late fee, interest, and payment-plan default terms per the fee agreement]

## Closing bank

- `Thank you again for staying on top of this. We'll be in touch as soon as we've finished reviewing what you've sent.` (MD-1, executed — the firm commits to its own next step)
- `Let us know if you have any questions.` (MD-3)
- `If anything doesn't apply to you or you're not sure how to answer one of these, just reply and let us know — we'll help you sort it out.` (MD-1)
- `If you have any questions about this accounting, please do not hesitate to reach out through the {{UPLOAD_PORTAL}}. We will be happy to clarify anything further.` (BR-5, M10 — the only billing close in the corpus; still collaborative, and it routes the client to a channel rather than to a phone number)
- `Thank you for allowing {{FIRM_NAME}} to assist you with your family law matter.` (BR-5, M10)

> **GAP.** No firm close exists for a final-notice or past-due letter. Every close in
> this lane is collaborative, including the billing close.

## Signature block

MD-1 (executed):
```
Sincerely,

{{ATTORNEY_NAME}}
Florida Bar No. {{BAR_NO}}
{{FIRM_EMAIL}}
{{FIRM_NAME}}
```

Letterhead block above the date, as used:
```
{{FIRM_NAME}}
{{FIRM_ADDRESS}}
Tel: {{FIRM_PHONE}} | [CONFIRM LOCALLY: firm website]
{{FIRM_EMAIL}}
```

BR-5 (executed, M10) — **no bar number, and a title line instead**, with a file cc:
```
Sincerely,

_________________________________
{{ATTORNEY_NAME}}
[CONFIRM LOCALLY: attorney title]
{{FIRM_NAME}}

cc: File
```

> **INCONSISTENCY, FLAGGED.** MD-1 signs with a bar number and no title; BR-5 signs with a
> title and no bar number. Both are executed firm letters. Pick one convention for the
> lane.
> [CONFIRM LOCALLY: whether client correspondence carries the bar number, the title, or
> both — with {{ROLE_APPROVER}}]

## Voice notes

This is the most distinctive voice in the whole harvest. Preserve it precisely.

- **Credit before correction, always.** The letter opens by naming what arrived, in
  detail, and saying what it made possible. The deficiency comes second.
- **Minimize the miss.** `ONE SMALL GAP TO CLOSE.` `that one statement.` The firm
  shrinks the ask linguistically even when the list is long.
- **Acknowledge the burden out loud.** `We know this is a lot, so take them one at a
  time.`
- **Every ask carries its reason.** No bare demands. `This helps us support the value
  we've listed for the business.`
- **Every ask offers a both-ways answer.** `If it's filed, send a copy. If not, tell us
  when you expect to file.` The client can always comply, even with a negative.
- **Sectioned with short all-caps heads.** `WHAT WE RECEIVED` / `ONE SMALL GAP TO CLOSE`
  / `WHAT WE STILL NEED FROM YOU` / `WHY THIS MATTERS` / `HOW TO SEND THESE`. Scannable.
  Reuse these exact heads.
- **Consequence stated once, in one short paragraph, then dropped.** No repetition, no
  escalation of tone within the letter.
- **Contractions throughout.** `we've`, `that wasn't`, `you're`, `doesn't`. Warm register.
- **Em-dashes carry the explanatory clauses.** Heavy, deliberate use.
- **The firm commits to reciprocal action at the close.** It does not simply hand the
  client a to-do list; it says what the firm will do next.
- **Transaction questions are narrow and dated, never accusatory.** `just a quick note on
  who this was from and what it was for.` The word `just` is doing real de-escalation work.
- The BR-1 status bank, by contrast, is flat and transactional.
- **The billing voice (BR-5, M10) is a third register, distinct from both the warm chase
  voice and the flat status bank.** It is formal, declarative, and typographically
  emphatic — ALL-CAPS section heads, a bold `Important:`, capitalized `STATUS: PAID IN
  FULL`, and `does NOT create a credit balance`. No contractions. No em-dash asides. Where
  MD-1 uses softeners on every ask, BR-5 uses emphasis on every protection.
- **Emphasis lands only on sentences that protect the firm.** The waiver is bolded; the
  courtesy is not.
- **The firm shows arithmetic instead of asserting a net.** Fee, credit, payment, and
  balance are each their own line, per agreement.
- **Money is framed as client benefit even while being fenced.** `provide you with a clear
  accounting`, `professional courtesy`, `savings of more than {{AMOUNT}}` — the letter
  disposes of a debt and simultaneously argues its own value.
- **The firm names the awkward thing here too**, consistent with the closing lane: it says
  outright that the waiver `represents a significant financial loss to our firm` and that
  the client `has no credit balance`. It does not soften either.

## Attorney flags

- **DO NOT SHIP BR-2, BR-3, BR-4, MD-4, or MD-5 FROM THIS CORPUS.** Past-due notices,
  trust replenishment requests, payment-plan default notices, signature chases, and
  missed-court-deadline accountability letters have no source. Presenting templates for
  them would be fabrication. **BR-5 does not fill these holes** — it is a closure-context
  accounting, not a mid-matter collection tool, and it must not be repurposed as one.
- **BR-5 is the highest-liability sub-type in this spec.** It reconciles fee agreements,
  states a contractual entitlement, waives a balance, and denies a credit balance. Every
  figure, and the waiver decision itself, require attorney sign-off. None of it may be
  generated as boilerplate and none of it may be sent by staff.
- **Verify the earned-on-receipt recital against the firm's own fee agreement.** BR-5
  states that the flat fee `is earned upon receipt and is not refundable or reducible based
  on actual time spent or case outcome`. That is a recital of one firm's agreement. If the
  purchasing firm's agreement does not say this, the sentence is false and must not ship.
- **The hourly-equivalent comparison invites a fee dispute.** Attaching a constructed
  hourly invoice and asserting a savings figure hands the client an alternative valuation
  of the same work, in writing. If the fee is later challenged, the firm has supplied a
  competing number. Retained because it is genuine firm language; flagged as opt-in only,
  and the hourly figure must never be estimated.
- **A waiver has trust-accounting and billing-record consequences.** The letter is not the
  record. Confirm the waiver is authorized, recorded in {{PM_SYSTEM}}, and reconciled with
  [CONFIRM LOCALLY: which role handles trust and billing reconciliation at your firm]
  before the letter goes out.
- **BR-5 contains no post-judgment warnings at all** despite closing a matter with a final
  judgment. If the accounting letter is doubling as the closing letter, the closing lane's
  orders-still-bind, modifiability, and records-retention modules must be merged in.
- **The executed letter carries a hard attorney gate.** Its own internal block states:
  *"Attorney review required before sending (financial disclosure/discovery content
  touching income verification and a previously undisclosed account)."* Any productized
  version must retain an equivalent gate.
- **Surfacing a previously undisclosed account triggers an amended affidavit question.**
  The letter flagged this to the attorney rather than resolving it. Preserve that
  routing; staff must not decide it.
- **Time-logging is treated as non-optional.** The internal block instructs logging both
  the drafting time and the underlying review time. Carry this into the product.
- **The deliberate absence of deadlines is a real design choice, not an oversight — but
  it is a risk.** A buyer whose practice needs enforceable client deadlines will find
  this lane too soft. Say so at install.
- Asking a client to characterize a payment stream (e.g. whether payments are support
  from another case) can surface an undisclosed obligation. Route to the attorney before
  amending anything.
- Any dollar figure quoted back to a client must be reconciled to the current affidavit
  and the underlying statements, not to a prior draft.
- Do not state or imply that the firm will continue work while a balance is outstanding
  unless the fee agreement says so.

## [CONFIRM LOCALLY] items

- [CONFIRM LOCALLY: response deadline convention for client document requests — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: escalation ladder and final-notice wording]
- [CONFIRM LOCALLY: trust replenishment threshold, notice period, and who sends it — with the role that handles trust and billing reconciliation at your firm]
- [CONFIRM LOCALLY: late fee, interest, and payment-plan default terms per the fee agreement]
- [CONFIRM LOCALLY: whether the firm states a work-suspension consequence, and at what point]
- [CONFIRM LOCALLY: name of the client upload tool and portal — {{UPLOAD_PORTAL}} / {{CLIENT_UPLOAD_TOOL}}]
- [CONFIRM LOCALLY: approved parenting-class providers for this circuit, and whether the clerk requires a specific certificate form]
- [CONFIRM LOCALLY: whether this division sets a mandatory disclosure deadline by order, and whether that date should appear in the letter]
- [CONFIRM LOCALLY: {{PM_SYSTEM}} time-entry codes for correspondence drafting vs. document review]
- [CONFIRM LOCALLY: who signs a document chase — attorney or {{ROLE_DRAFTER}} under attorney review]
- [CONFIRM LOCALLY: whether client correspondence carries the bar number, the title, or both — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: whether the firm's flat fee is in fact earned upon receipt under its own fee agreement]
- [CONFIRM LOCALLY: whether the firm wants an hourly-equivalent value comparison in fee correspondence at all — with {{ROLE_APPROVER}}]
- [CONFIRM LOCALLY: who authorizes a fee waiver, and how it is recorded in {{PM_SYSTEM}} and with the role that handles trust and billing reconciliation at your firm]
- [CONFIRM LOCALLY: the retention period that "our standard file retention policy" refers to]
- [CONFIRM LOCALLY: the channel named for post-closing billing questions — the source names a client portal, which may or may not be {{UPLOAD_PORTAL}}]

## Coverage

examples harvested: 6 of 25 target (3 distinct matters, 1 firm billing language bank, 2 firm client-education letters)
round-2 delta: +1 distinct matter (M10), +1 sub-type (BR-5)
shortfall: 22 distinct matters

structural holes CLOSED in round 2:
- **A billing communication with actual structure** — previously the lane had none. BR-5
  supplies opener, agreements recital, payments ledger, account summary, entitlement
  statement, waiver-and-fence, value comparison, conclusion, close, and signature.
- **Balance disposition language** — how the firm writes off money owed to it, and how it
  prevents the write-off from becoming a future credit.
- **A billing register / voice profile** — previously absent; the lane had only a flat
  status bank.
- **A billing signature block and a billing close.**
- **Reference to a file-retention policy** (named, though its terms remain unlocated).

gaps — **still not found in any source; must be drafted, not harvested:**
- Any **mid-matter** billing communication of any kind (BR-5 is closure-context)
- Past-due / arrears notice
- Trust or retainer replenishment request
- Payment-plan default notice
- Late fee, interest, or finance-charge language
- Work-suspension-for-non-payment warning
- Any **refund** letter (BR-5 is the inverse case — a waiver with credit expressly denied)
- Signature chase letter
- Missed-court-deadline client accountability letter
- Second-notice or final-notice letter in any series
- Any letter stating a specific response deadline date to the client
- Any consequence-for-non-response language beyond loss of positional advantage
- Any escalation ladder or notice-count policy

partial coverage:
- MD-1 is the strongest single artifact in the entire harvest — structure, voice, and
  internal-routing block are all reusable. But it is **one letter from one matter**.
- MD-2 exists only as two bullets embedded inside MD-1, not as a standalone letter.
- MD-3 is a client-education template, not an accountability letter; it is included
  because it supplies the only hard procedural consequence in the lane.
- BR-1 is a six-row status bank designed for closure context. It is not a collection
  tool and should not be sold as one. BR-5 supersedes it wherever a balance must actually
  be reconciled.
- BR-5 is **one letter from one matter**, and it is a flat-fee matter. No hourly-matter
  fee accounting was located, so the agreements-recital and value-comparison modules are
  untested outside a flat-fee context.
- BR-5 shares its source document with the closing lane (recorded there as the executed
  CL-5 example). It is one letter serving two lanes, counted once per lane and not
  double-counted as two examples.
- The second matter (M07) contributed settlement correspondence that confirmed voice
  register but yielded no billing or deadline content; it is counted as a distinct source
  matter for voice only.

## Tokens introduced by this spec

| Token | Substitutes |
|---|---|
| `{{DOCUMENT_CATEGORY}}` | A category of disclosure document being acknowledged or requested (e.g. account statements, returns, title documents). Never an account number, issuer, or partial card number. |
| `{{PERIOD}}` | The date range a document set covers. |
| `{{MISSING_PERIOD}}` | The single period isolated in the `ONE SMALL GAP TO CLOSE` block. |
| `{{TRANSACTION_TYPE}}` | The generic type of a single transaction being queried (e.g. deposit, transfer, withdrawal). |
| `{{FEE_TYPE}}` | The fee structure named in BR-5 headings (e.g. flat fee, hourly, hybrid). |
| `{{NEXT_MILESTONE}}` | The next case milestone the ask is anchored to (e.g. mediation, hearing, deposition). |
