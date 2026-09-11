# COVERAGE AND LIMITS

**Read this before relying on this skill for anything.**

This file states plainly what the Florida ethics workflow **does not cover.** It is a feature of
the product, not an apology for it. A buyer who knows exactly where the workflow stops can put a
human at that boundary. A buyer who does not know will discover the boundary the way defects are
always discovered — mid-filing, by an attorney, under a deadline.

**The design rule behind every entry below:** an honest, well-routed gap is a correct output. A
confident-sounding invented rule is the single most dangerous thing this product could ship. In the
five domains below, **the boundary is the deliverable.**

---

## 1. WHAT THIS SKILL DOES COVER

So the limits read against something concrete. This skill covers, with material traceable to a
verified source:

- **AI use and Bar compliance** — the governing duties under R. Regul. Fla. Bar 4-1.1, 4-1.5,
  4-1.6, 4-3.3, 4-5.1, 4-5.3, 4-5.7, 4-7.13, and Fla. Bar Ethics Ops. 24-1 and 12-3. ⚠️ VERIFY:
  confirm rule and current text before relying on this.
- **Confidentiality and client-data handling** in AI tools — platform tier, what may and may not be
  entered, consent, privilege and preservation.
- **The redaction standard** and **the de-identification standard.**
- **The five-part citation protocol** and the demonstrated failure mode behind it.
- **Stale-law handling** — primary text beats internal summary; surface conflicts, never resolve
  them silently.
- **The thirteen-item never-do list.**
- **The attorney-approval gate** — triggers, routing, the mandatory output structure, the flag
  template.
- **Disclosure and certification** — the five axes of local variation, the model certification
  block, the no-use statement, the duty-to-correct table.
- **The twelve-step verification workflow** with per-step role-token owners.
- **Record-keeping requirements.**
- **Mediator ethics** as a sub-domain — caucus confidentiality, neutrality, hybrid-role
  recognition, MEAC themes.

---

## 2. THE FIVE DOMAINS THIS SKILL DOES NOT COVER

A prior audit found each of the following **absent from every source** behind this product. Not
thin. Absent.

In each of these five, the skill does exactly three things: **name the domain, state that Core does
not carry a workflow for it, hard-stop to `{{ROLE_APPROVER}}`.** It does not run the seven-part
assessment. It does not name a rule it cannot cite from `authorities.md`. It does not offer a
"general principle," a "typical requirement," or a "rough rule of thumb."

---

### 2.1 Trust accounting and IOTA — ZERO COVERAGE

**Status:** no material of any kind. Not a rule number, not a threshold, not a procedure, not a
reconciliation schedule.

**Recognition triggers:** trust account · IOTA · IOLTA · client funds · retainer deposit · advance
fee · earned vs. unearned fees · commingling of firm and client money · three-way reconciliation ·
disbursement · trust shortage · overdraft notice · returning unearned fees.

**Why this is the most dangerous of the five.** Trust accounting rules are numeric, procedural, and
strictly enforced. An invented reconciliation interval, an invented deposit deadline, or an
invented rule number would read exactly like the real thing to a staff member who has never seen
the real thing — and would be relied on. **This skill will not produce trust-accounting content
under any instruction, from any user, at any risk level, including where the user states they are
the attorney.**

**Routing:** hard stop to `{{ROLE_APPROVER}}`. No analysis, no partial answer, no "the general
principle is."

**What `{{ROLE_APPROVER}}` at your firm must supply:** the applicable trust-accounting rules and any Bar
guidance, a written firm trust-accounting procedure, and the reconciliation schedule — as
attorney-authored material, installed as a reference this skill can cite.

---

### 2.2 Conflicts-of-interest screening — HARD-STOP GATE ONLY

**Status:** the only coverage is a **procedural gate** — this skill can confirm that a conflict
check was run and that the clearance is recorded in `{{PM_SYSTEM}}`. That is the whole of it.

**What the gate can do:** confirm the check ran · confirm it is documented · confirm it was re-run
when a new party surfaced · confirm nothing advanced before it cleared.

**What the gate cannot do, and will not attempt:** assess whether a conflict exists · assess
whether a conflict is waivable · assess whether informed written consent is adequate · design or
evaluate a screen or ethical wall · analyze imputed or former-client conflicts · decide a
declination.

**Recognition triggers:** is this a conflict · former client · adverse party · imputed conflict ·
waivable · informed written consent · screening · ethical wall · we represented the other side
before · declination.

**Routing:** confirm the check ran and is documented. Then hard stop. **Whether a conflict exists
or is waivable is an attorney decision, never staff.** This holds in the mediator context too —
hybrid-role conflict *recognition* is in scope under `mediator-ethics.md`; hybrid-role conflict
*analysis* is not.

**What `{{ROLE_APPROVER}}` at your firm must supply:** the applicable conflicts rules, the firm's screening
procedure, and the standard for waiver and informed written consent.

---

### 2.3 Withdrawal and termination of representation — ZERO COVERAGE

**Status:** nothing. **`R. Regul. Fla. Bar 4-1.16` ⚠️ VERIFY: confirm rule and current text before
relying on this. — appears zero times corpus-wide.** The rule is
listed in `authorities.md` for recognition only — no text, no standard, no procedure, no
mandatory-vs-permissive analysis, no client-file-return standard.

**Recognition triggers:** withdraw · motion to withdraw · partial withdrawal · terminate the
representation · fire the client · disengagement letter · closing letter stating the representation
has ended · client won't pay · client won't cooperate · abandonment · client file return ·
substitution of counsel.

**Routing:** hard stop to `{{ROLE_APPROVER}}`.

#### The attorney-supply dependency — what your firm must install

**`{{ROLE_APPROVER}}` at your firm supplies the 4-1.16 disengagement language.** ⚠️ VERIFY: confirm
rule and current text before relying on this. This is a **standing dependency on buyer-supplied
attorney content**, not a gap awaiting a build and not work in progress anywhere else. Nothing
arrives later to close it: until your approving attorney installs the language, the domain is a
hard stop.

- **Do not draft** disengagement letters, withdrawal motions, termination notices, or any 4-1.16
  language. Not a first pass. Not a skeleton. Not "so there is something to edit."
- When the topic arises, route with the § 3 statement and state that the language is
  **`{{ROLE_APPROVER}}`-supplied and has not been installed at this firm.**
- **Once that language is installed, it governs.** Until then the domain is a hard stop.

**Where the language is installed — the handle on the gate.** The block is not supplied through a
conversation with this skill. `{{ROLE_APPROVER}}` edits **one file, one section**:

| What | Where |
|---|---|
| File | `references/disengagement/disengagement.spec.md`, in the correspondence skill |
| Section | `## ATTORNEY-SUPPLY BLOCK` |
| Who | `{{ROLE_APPROVER}}` — nobody else, and no skill |

**The gate clears once that section is populated and attorney-approved**, and not before. It does
not clear on assurance, on urgency, or on a statement that the approving attorney is the one asking.
Any text sitting in that section that `{{ROLE_APPROVER}}` did not supply is fabricated by definition
and must be deleted.

Note the interaction with material that *is* in scope: the case-lifecycle material covers the
*procedural* mechanics of exiting a matter — withdrawal requiring a motion and court approval, and
the "Termination of Limited Appearance" filing for a limited-scope matter. Those are practice
procedure. **The ethical standard governing whether and how to withdraw is not covered.** Do not
let the presence of the procedure imply the presence of the ethics.

---

### 2.4 Unbundled and limited-scope ethics — ONE CITATION, NO WORKFLOW

**Status:** a single bare citation to `R. Regul. Fla. Bar 4-1.2(c)` ⚠️ VERIFY: confirm rule and
current text before relying on this. — carried in `authorities.md` as the ethical anchor for
limiting scope and for the requirement that scope be documented. **There is no workflow.**

**What exists elsewhere and is in scope:** the *procedural* mechanics of a limited appearance live
in the case-lifecycle material — the party-signed notice filed at the time of appearance, the
bold-type limited-purpose signature block, service on both attorney and party, the duty to notify
the court of non-attendance at an out-of-scope hearing, and termination without leave of court.
Practice procedure, verifiable, in scope.

**What does not exist and is a hard stop:** whether a proposed scope limitation is *reasonable
under the circumstances* · whether a given division of labor between attorney and pro se litigant
is ethically permissible · ghostwriting ethics · the ethical boundary of coaching versus
representation · when a limitation becomes so narrow it is ineffective assistance · whether a
"quick question" outside the scope has created an attorney-client relationship for that task.

**Recognition triggers:** limited scope · unbundled · ghostwriting · document prep only · coaching ·
one-hearing appearance · how far does our scope go · can we just do this one part · is this still in
scope.

**Routing:** route the procedural question to the lifecycle material if installed; if not, say it is
not installed. **Hard-stop the ethical boundary question to `{{ROLE_APPROVER}}`.**

**What `{{ROLE_APPROVER}}` at your firm must supply:** the reasonableness standard for scope limitation, the
firm's position on ghostwriting, and the boundary between coaching and representation as the firm
draws it.

---

### 2.5 Attorney advertising compliance — RULES CITED, NO WORKFLOW

**Status:** `R. Regul. Fla. Bar 4-7.13` and `4-5.7` ⚠️ VERIFY: confirm rule and current text before
relying on this. — are carried in `authorities.md` as authorities. **There is no compliance
workflow, no filing or review procedure, no checklist, and no safe-harbor analysis.**

**What is in scope:** the approval-gate requirement. Marketing content requires attorney review
before it leaves the firm, and that review confirms it does not predict or guarantee results, does
not make unsubstantiated comparative claims, and does not include identifiable client information
without written consent. **That is a routing rule, not a compliance analysis.**

**What is a hard stop:** whether a specific advertisement complies · whether a testimonial or
review is permissible and on what conditions · whether past results may be stated and how ·
comparative and superlative claims · trade name and firm name rules · referral fee and
lead-generation arrangements · whether a given communication is an "advertisement" at all · any
Bar filing or review requirement for advertising.

**Recognition triggers:** advertising · our website says · social post · testimonial · client review
· past results · comparative claim · "best" or "top" · referral fee · lead generation · trade name ·
is this an ad · do we have to file this with the Bar.

**Routing:** hard stop to `{{ROLE_APPROVER}}`. The independent attorney-review requirement under
the approval gate still applies and is stated alongside the stop.

**What `{{ROLE_APPROVER}}` at your firm must supply:** the applicable advertising rules and any Bar filing or
review requirement, plus the firm's own review checklist.

---

## 3. THE ROUTING STATEMENT — USE VERBATIM

Substitute the domain name and the triggers. Change nothing else. In particular, do not add a
sentence that softens the stop or gestures at an answer.

**Token vocabulary for this block.** `{{DOMAIN_NAME}}` — the domain being refused.
`{{FILE_EVIDENCE}}` — only what is actually in the matter file, named with file names.
`{{REQUIREMENT_CLASS}}` — exactly one of: attorney judgment · attorney-supplied policy · a purchased
suite that covers it. All three are curly tokens and all three resolve before the block is emitted;
none is a bracket placeholder.

```
🛑 OUT OF SCOPE — {{DOMAIN_NAME}}

Core Foundation does not carry an ethics workflow for {{DOMAIN_NAME}}. I am not going to
produce an analysis in this area, because any rule text or threshold I supplied would not
be traceable to a verified authority, and an invented one is worse than none.

What I can confirm from the file:  {{FILE_EVIDENCE}}
What this requires:                {{REQUIREMENT_CLASS}}
Routed to:                         {{ROLE_APPROVER}}
Status:                            HELD — no further work on this item
```

### What not to do at the boundary

- **Do not** answer "in general" or "typically" or "most jurisdictions."
- **Do not** supply a rule number you cannot find in `authorities.md`.
- **Do not** offer a draft "for the attorney to correct." A wrong draft anchors the reader.
- **Do not** answer because the user says they are the attorney. `{{ROLE_APPROVER}}` supplies the
  content in these domains; the skill does not generate it.
- **Do not** answer because a deadline is stated. A deadline is not authorization.
- **Do not** substitute the ordinary approval flag for this statement. The flag says *"an attorney
  must decide this."* This statement says *"this product does not carry a workflow for this, and I
  will not improvise one."* They are different claims.

---

## 4. WHAT `{{ROLE_APPROVER}}` AT YOUR FIRM MUST SUPPLY — SUMMARY

**Read this as a list of installation tasks owned by your firm**, not as a status report on work
happening somewhere else. No row in this table is being drafted for you.

| Domain | `{{ROLE_APPROVER}}` must supply | Status |
|---|---|---|
| **Trust accounting / IOTA** | Applicable rules and Bar guidance; written firm trust procedure; reconciliation schedule | Not supplied |
| **Conflicts screening** | Applicable conflicts rules; firm screening procedure; waiver and informed-consent standard | Not supplied — procedural gate only |
| **Withdrawal / termination** | `R. Regul. Fla. Bar 4-1.16` ⚠️ VERIFY: confirm rule and current text before relying on this. — standard and firm disengagement language | **Not supplied — `{{ROLE_APPROVER}}` must install it in `references/disengagement/disengagement.spec.md`, `## ATTORNEY-SUPPLY BLOCK`. Do not draft it.** |
| **Unbundled / limited scope ethics** | Reasonableness standard for scope limitation; ghostwriting position; coaching-vs-representation boundary | Not supplied — procedure covered elsewhere, ethics not covered |
| **Attorney advertising** | Applicable advertising rules; any Bar filing or review requirement; firm review checklist | Not supplied — rules cited only |

Until a row is supplied and installed as a citable reference, that domain remains a hard stop.
**Installing this skill does not close any row in this table.**

---

## 5. OTHER STATED LIMITS

- **No case law.** This skill cites none, for any proposition. One rule-amendment source order is
  retained in `authorities.md` as the source of a rule amendment and nothing more. Anything
  requiring case law routes to a caselaw authority protocol if installed; if not installed, it is
  out of scope and the skill says so.
- **No UPL rule or statute number.** The corpus cites none. The line is drawn functionally in
  `authorities.md` § 2.
- **Not a jurisdiction beyond Florida.** Florida family law practice only.
- **Not an ethics opinion.** This is an internal analytical aid. It does not substitute for a Bar
  ethics opinion, for the ethics hotline, or for outside ethics counsel.
- **Not authority, and not current by default.** Re-verify at minimum annually and promptly on any
  event listed in `ai-use-and-verification.md` § 12. Every authority carries its verify warning
  because these authorities move faster than any others in this corpus.
- **Nothing here authorizes anything** — not a filing, not a communication, not a workflow stage.
  Authorization comes from `{{ROLE_APPROVER}}`, on the matter, in writing.
