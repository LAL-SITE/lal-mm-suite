# Correspondence Pre-Send QC Checklist

**Loaded by `lal-correspondence.SKILL.md` § 9.** A gate, not a review. Run it on every output.
Report the result in the output: **PASS**, **PASS WITH FLAGS** naming each flag, or **FAIL** naming
the condition. A silent pass is not a pass.

Run the passes in order. Pass 0 stops everything.

---

## PASS 0 — HARD FAILS

Any one of these and the output does not release. No override, no role, no deadline.

| # | Condition | Why |
|---|---|---|
| 0.1 | `Click here to enter text.` appears anywhere | An unfilled word-processor content control. Confirmed present in a real approved source form, in the letterhead, addressee, delivery-method, and salutation fields |
| 0.2 | `XXXXXXXX` or any run of placeholder X's appears | Same class of defect |
| 0.3 | An unresolved `{{TOKEN}}` remains in a document represented as ready to send | A token is a fill instruction, not content |
| 0.4 | A bracket-style placeholder appears that is not `[CONFIRM LOCALLY: …]` | The only permitted bracket construction |
| 0.5 | A case name, a reporter citation, a parenthetical case reference, or a "courts have held" construction appears | **No case law anywhere.** Rules, statutes, and Bar rules only |
| 0.6 | A rule, statute, or Bar rule is cited without ⚠️ VERIFY: confirm rule and current text before relying on this. | Verification is an act, not a permission |
| 0.7 | A firm-initiated disengagement letter exists and the attorney-supply compliance block is empty | Skill § 6. The one stop no role can self-approve past |
| 0.8 | Any text sits inside the attorney-supply block that `{{ROLE_APPROVER}}` did not supply | Fabricated by definition. Delete it |
| 0.9 | An estate-planning reference appears anywhere | The source library wrongly asserted the firm offered it |
| 0.10 | A practice-area cross-sell appears in a closing letter | It contradicts the paragraph disclaiming responsibility for future work |
| 0.11 | A review solicitation appears in **any** representation-ending document — closing, disengagement, withdrawal, substitution, non-representation | One executed source letter solicited a public review in the same letter announcing a motion to withdraw |
| 0.12 | A settlement figure appears that the client has not authorized in writing | The authorization is the client's |
| 0.13 | The per-issue decision checklist is pre-filled | The checklist exists to create the authorization |
| 0.14 | A dollar figure appears that is not reconciled to the current affidavit and the underlying statements | Never to a prior draft, never estimated |
| 0.15 | An `INTERNAL — DO NOT SEND` block, drafting note, voice note, template header, or QC comment remains | Stripping is a release step, not formatting |
| 0.16 | A sub-type the matrix marks **NONE** has been produced | No source exists. Name the gap instead |

---

## PASS 1 — IDENTITY SWEEP

The output is white-labeled. Search for and remove:

| # | Check |
|---|---|
| 1.1 | No source-firm name or brand, in any form, anywhere |
| 1.2 | No staff first name |
| 1.3 | **No staff job title.** Buyer org charts differ. Role tokens only |
| 1.4 | No named practice-management, e-signature, upload, payment, or transcription vendor. Use the token |
| 1.5 | No literal bar number. `{{BAR_NO}}` only |
| 1.6 | No billing rate |
| 1.7 | No tenant, site, drive letter, local path, or storage-provider name |
| 1.8 | No URL other than `floridabar.org`, `flcourts.gov`, `leg.state.fl.us`. No review link, no social handle, no firm website hardcoded — the executed source letters carried live review links to three named platforms and a social page |
| 1.9 | No prior-matter fact, party name, or figure. Cross-matter content in a single source file is documented and real |

---

## PASS 2 — ROUTING AND PROVENANCE

| # | Check |
|---|---|
| 2.1 | Lane, spec, and sub-type are stated in the output header |
| 2.2 | The recipient's representation status was confirmed, not inferred — a counsel-facing letter has not gone to an unrepresented party |
| 2.3 | Where the recipient is unrepresented, the **mandatory disclaimer** closes the letter |
| 2.4 | Closing versus disengagement was decided by asking whether the work finished or stopped early |
| 2.5 | Provenance class is stated. A template-only sub-type carries the warning block, and it is stripped before send |
| 2.6 | Where the sub-type is template-only, first-use review by `{{ROLE_APPROVER}}` is named |
| 2.7 | Advocate and court-appointed-neutral roles are not blended in one document |

---

## PASS 3 — FORMAT

| # | Check |
|---|---|
| 3.1 | Letterhead or email signature block is a **position marker**, not a rendered block |
| 3.2 | Element order matches the shell for this lane |
| 3.3 | Recipient identified by full legal name and current address or email |
| 3.4 | Matter identified by styling, case number, and division where applicable. Date current |
| 3.5 | Subject or `Re:` line specific and accurate. `Re:` is identification; `Subject:` is purpose |
| 3.6 | Delivery method stated on the face of the letter |
| 3.7 | Salutation and punctuation match the recipient — colon to a court or to counsel |
| 3.8 | Signature block matches the signer the spec specifies. A representation-ending communication defaults to attorney signature; any other signer required an explicit override |
| 3.9 | Where two attorneys appeared, both sign |
| 3.10 | **Exactly one option block survives.** Courtesy options; after-hearing circulation states; the withdrawal-versus-notice mechanic |
| 3.11 | No bullets in running prose to the bench or to counsel |
| 3.12 | Register is consistent — header style, person, and contraction use do not switch mid-document |
| 3.13 | Numbered for sequence, bulleted for inventories, never mixed in one block |
| 3.14 | A duplicated sign-off has not survived — a real approved source form ships with `Sincerely,` twice |

---

## PASS 4 — ENCLOSURES AND COPIES

| # | Check |
|---|---|
| 4.1 | Enclosures enumerated by title, never gestured at |
| 4.2 | Everything the letter says is attached **is** attached. A transmittal without its attachment defeats its purpose |
| 4.3 | `cc:` sits on the face of the letter and is accurate and complete |
| 4.4 | A bench letter copies opposing counsel by full name and email |
| 4.5 | A courtesy set went identically to the other side, and the letter says so. Tab numbers match the binder |
| 4.6 | Any confirmation described as "available upon request" is actually in the file |
| 4.7 | Where dual delivery is specified, the legend is present and proof of transmission will be saved |

---

## PASS 5 — CONTENT, BY LANE

### 5.1 Client

| # | Check |
|---|---|
| 5.1.1 | The four questions are answered: what is happening, what it means, what to do, by when |
| 5.1.2 | No outcome is predicted. Ranged, never predicted |
| 5.1.3 | No promise, no guarantee, no legal jargon left untranslated |
| 5.1.4 | Every factual bullet carries a date. Every ask carries a reason |
| 5.1.5 | Every ambiguous ask carries an if-it-does-not-exist branch |
| 5.1.6 | Inapplicable warning clauses are pruned — a relocation warning in a matter with no children is a defect, as is a modifiability clause where no ongoing obligation exists |
| 5.1.7 | Bad news or substantive strategy is **not** riding in a monthly status email |
| 5.1.8 | Scope and fee language is copied verbatim from the executed agreement, never paraphrased |
| 5.1.9 | Upload destinations and intake forms are provisioned — no placeholder links |
| 5.1.10 | Where the retainer is unsigned, the letter says *matter*, not *case*, and states the signature precondition |
| 5.1.11 | No child's name, date of birth, account number, or employer appears unless the reader needs it to act |
| 5.1.12 | Where a legal entitlement is asserted in plain language, it has been verified |
| 5.1.13 | Trust deposit cleared before any dollar amount is referenced |
| 5.1.14 | Every closing or disengagement letter carries the scope fence |
| 5.1.15 | A known-deadlines block is either a real list or the express no-knowledge disclaimer — **never blank, never placeholder** |
| 5.1.16 | No statement that no deadlines remain unless the docket and `{{ROLE_APPROVER}}` confirm it |
| 5.1.17 | No tax advice. No advice to ignore or informally change a court order. No post-judgment advice conflicting with the final order |
| 5.1.18 | A fee accounting states entitlement **before** concession, and fences the disposition |
| 5.1.19 | The earned-on-receipt recital was verified against the buyer's own fee agreement, or removed |
| 5.1.20 | An hourly-equivalent comparison appears only on attorney direction, and the figure is not estimated |
| 5.1.21 | Where a fee accounting doubles as the closing letter, the closing warning blocks are merged in |
| 5.1.22 | A representation-ending letter names the next scheduled hearing and the consequence of appearing unrepresented, or states the express no-knowledge disclaimer |
| 5.1.23 | The letter says who notifies the other side that the firm is no longer counsel of record, and names the actor explicitly — never an ambiguous "the attorney" |
| 5.1.24 | Amicable-exit framing does not appear in a firm-initiated exit |
| 5.1.25 | No sentence refers to a written policy the firm does not actually have — a letter promising materials "per our standard file retention policy" where no policy exists is a defect |

### 5.2 Opposing counsel

| # | Check |
|---|---|
| 5.2.1 | One-sentence representation statement opens the letter |
| 5.2.2 | Every substantive assertion is anchored to a rule, statute, or specific document |
| 5.2.3 | Concessions stated first, fully, unhedged; disagreements follow as position plus one-line basis |
| 5.2.4 | No adjective characterizing the other side, and no imputed motive |
| 5.2.5 | Only one number is labeled authorized |
| 5.2.6 | Computations are shown, numbered, and attached |
| 5.2.7 | Every deadline is concrete, carries a named consequence, and is tied to a step the firm will actually take. Clock time on a hard deadline |
| 5.2.8 | A demand carries the fallback-identification clause — the item, the reason for delay, the date it will be produced |
| 5.2.9 | A cure deadline leaves the two-week minimum buffer before the milestone |
| 5.2.10 | Every deficiency item carries all four required elements. No item ships with three |
| 5.2.11 | The letter was built against the actual production, the filed certificate, and the filed affidavit |
| 5.2.12 | The settlement inadmissibility paragraph is present, verbatim, on any settlement transmittal, and the confidential designation is in the `Subject:` line or as a banner |
| 5.2.13 | Counsel is served before any records custodian |
| 5.2.14 | A statutory settlement-proposal mechanism was confirmed to reach the claim before service |
| 5.2.15 | A substitution letter goes out only after the order is entered, with the filed order attached |
| 5.2.16 | No merits argument in a scheduling or procedural letter |
| 5.2.17 | No child's name, date of birth, or school unless identification is legally necessary |
| 5.2.18 | Proposals are framed as proposals; *demand* is reserved for an authorized final demand |

### 5.3 Bench

| # | Check |
|---|---|
| 5.3.1 | Not one sentence argues the merits |
| 5.3.2 | Not one characterizing adjective about the other side or their conduct |
| 5.3.3 | Opposing counsel is copied, on the face of the letter, and was advised **before** the letter went to the bench where the spec sequences it |
| 5.3.4 | The other side's position is stated on the record of the letter — agreed, unopposed and affirmatively confirmed, objected with a competing order enclosed, or served on a named date and unresponsive |
| 5.3.5 | "Unopposed" rests on affirmative written confirmation saved to the file. Silence is a different letter |
| 5.3.6 | An after-hearing proposed order was reconciled against the ruling notes or transcript. It tracks the ruling, not the client's preference |
| 5.3.7 | Where the form is contested, both orders are enclosed and the disagreement is described neutrally, not argued |
| 5.3.8 | Dates proposed to the court were confirmed with the other side first; where unconfirmed, the letter says so and asks for a hold |
| 5.3.9 | The other party's notice entitlement was checked before a date was accepted |
| 5.3.10 | An abeyance carries an update date and rests on joint election |
| 5.3.11 | A withdrawal letter releases the calendar time explicitly and does not editorialize on why |
| 5.3.12 | The time estimate is the parties' stipulated estimate, not a unilateral one |
| 5.3.13 | Every request is answerable with a yes, a no, or a date, and is single-issue |
| 5.3.14 | Division-specific format was confirmed, or `[CONFIRM LOCALLY]` was emitted for it |
| 5.3.15 | A formal bench letter is attorney-signed |
| 5.3.16 | Discovery deficiencies are stated factually in a status letter, never argued |

### 5.4 Third party

| # | Check |
|---|---|
| 5.4.1 | Authority is stated before the ask — order, subpoena, appointment, release, or written client authorization |
| 5.4.2 | Where the letter rests on an order, the order **is attached** |
| 5.4.3 | Only what the purpose requires is disclosed. No protected record is requested or transmitted without confirmed authority |
| 5.4.4 | The applicable confidentiality regime is identified |
| 5.4.5 | Preservation scope is narrowed deliberately, not shipped at full width |
| 5.4.6 | No request framed so as to risk a privilege waiver |
| 5.4.7 | A release does not authorize onward disclosure more broadly than the appointment order supports |
| 5.4.8 | A release tied to an appointment's duration is fresh for the current appointment |
| 5.4.9 | No legal advice to the third party. Where they may have their own obligations, they are pointed to their own counsel |
| 5.4.10 | Social handles and website links are stripped |
| 5.4.11 | A neutral signs as the neutral where the role line is load-bearing |
| 5.4.12 | An instrument uses instrument format — caption, numbered clauses, dual signature — not letter format |
| 5.4.13 | Where the recipient is an unrepresented adverse party, the disclaimer closes the letter and every number was attorney-approved against a current worksheet |
| 5.4.14 | No grammatical defect carried over from source — including the known plural/singular verb mismatch in the release instrument |

---

## PASS 6 — WRITE-BACK AND CLOSE

| # | Check |
|---|---|
| 6.1 | A ledger entry records lane, sub-type, provenance class, and recipient class |
| 6.2 | Any response deadline the letter sets is written as a deadline object with all nine mandatory fields, its authority, and a real computation basis |
| 6.3 | Any lifecycle stage the letter completes is recorded per the write-contract sequence, with both ledger entries |
| 6.4 | Every flag raised is open unless a permitted role closed it, and the open count reconciles |
| 6.5 | A template-only send raised an `informational` flag |
| 6.6 | Where the command center could not be written, the intended entry was emitted as `PENDING COMMAND CENTER WRITE` with the save location named |
| 6.7 | Time is logged in `{{PM_SYSTEM}}` for both the drafting and the underlying document review |
| 6.8 | Nothing was filed, served, or sent. The output says it is a draft |

---

## REPORTING

```
QC: PASS — 0 hard fails, 0 flags.

QC: PASS WITH FLAGS — 0 hard fails, 3 flags:
  · 2.5  Sub-type is template-sourced only; first use requires {{ROLE_APPROVER}} review.
  · 5.3.14  Division proposed-order format unconfirmed; [CONFIRM LOCALLY] emitted.
  · 6.6  Command center unreachable; entry emitted as PENDING COMMAND CENTER WRITE.

QC: FAIL — hard fail 0.7. Firm-initiated disengagement with the attorney-supply
compliance block empty. Not released. Skill § 6.
```

A **PASS WITH FLAGS** output is releasable to the reviewer. A **FAIL** output is not releasable to
anyone, and the partial draft it carries is marked **NOT SENDABLE** on its face.
