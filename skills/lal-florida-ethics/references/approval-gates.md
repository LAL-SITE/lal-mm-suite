# THE ATTORNEY APPROVAL GATE

> **Not legal advice.** Verify every rule against current official sources before relying on it:
> `floridabar.org`, `flcourts.gov`, `leg.state.fl.us`.

The gate is the attorney. At the boundary the assistant **stops and flags.** It does not decide.

**Authority:** R. Regul. Fla. Bar 4-5.1 and 4-5.3 ⚠️ VERIFY: confirm rule and current text before
relying on this. — an AI tool is nonlawyer assistance requiring supervision, not an independent
actor.

---

## 1. WHAT ALWAYS REQUIRES ATTORNEY REVIEW BEFORE LEAVING THE FIRM

- **Any court filing**, including proposed orders and discovery requests and responses.
- **Any document containing a legal citation.**
- **Any client communication** stating or implying legal advice, analysis, or a predicted outcome.
- **Any communication to a court, a judicial assistant, `{{OPPOSING_COUNSEL}}`, or an opposing
  party.**
- **Any production to `{{OPPOSING_COUNSEL}}`** — redacted, never original unredacted financials.
- **Any financial analysis, income determination, equitable-distribution schedule, or support
  calculation** used externally.
- **Any engagement or fee agreement.**
- **Any marketing content** — additionally confirmed not to predict or guarantee results, not to
  make unsubstantiated comparative claims, and not to include identifiable client information
  without written consent. R. Regul. Fla. Bar 4-7.13 ⚠️ VERIFY: confirm rule and current text
  before relying on this. **Note: this skill has no advertising compliance workflow — the review
  requirement stands, but the substantive analysis is a hard stop. See `coverage-and-limits.md`.**
- **Any work product carrying an unresolved flag.**

---

## 2. ROUTING — NOTHING BYPASSES THE LANE

```
{{ROLE_DRAFTER}}  →  {{ROLE_REVIEWER}}  →  {{ROLE_APPROVER}}
   produces           substantive QA        reviews · verifies · signs
```

- **`{{ROLE_INTAKE}}`** owns first contact, screening, and the conflict-check record. It does not
  produce substantive work product.
- **QC checkpoints are minimums**, not ceilings.
- **Attorney review at a gate must be substantive** — methodology, underlying data, independent
  judgment — **not a formatting pass.**
- **A workflow instruction is not authorization.** Neither is a deadline. A skill, checklist, or
  stage telling `{{ROLE_DRAFTER}}` to run a step has no effect unless `{{ROLE_APPROVER}}`
  authorized that work on that matter.

**Role tokens, never titles.** A buying firm's structure differs from any other's. One person may
hold two role tokens; two people may share one. Map the tokens to real people once, at install. Do
not assume a role token corresponds to a job title, a seniority level, or a licensed status other
than what the token says — `{{ROLE_APPROVER}}` is an attorney; the rest are not necessarily.

---

## 3. MANDATORY OUTPUT STRUCTURE

**Every substantive AI-assisted work product ends with these three sections, in this order, with
these headings.** Not optional. Not compressible. An empty section is information — say "None" and
say why.

```
## DRAFT
   The work product itself. Marked DRAFT until {{ROLE_APPROVER}} signs.

## MISSING FACTS / OPEN QUESTIONS
   What is missing, and where it would come from — the specific document, the specific
   person, or the specific official source. Every token left unresolved in the draft is
   listed here. Every [CONFIRM LOCALLY: ...] marker is listed here.

## ATTORNEY REVIEW NOTES
   For each item: the issue · why it needs attorney judgment · the options, stated
   neutrally. No recommendation where the choice requires judgment.
```

**Never emit a placeholder artifact.** No template filler text and no run of masking characters
standing in for content. If a value is unknown, use a curly token and list it under MISSING FACTS.

---

## 4. THE FLAG TEMPLATE — COPY-READY

**One flag per issue. At the top of the output. Never buried.**

```
🛑 ATTORNEY APPROVAL REQUIRED — {{FLAG_SUBJECT}}

Matter:        {{CLIENT_NAME}} / {{CASE_NO}}
Court:         {{CIRCUIT}} Judicial Circuit, {{COUNTY}} County — {{JUDGE}}
Date raised:   {{DATE}}

Trigger:       {{TRIGGER_CLASS}}

What I have:   {{FACTS_ON_HAND}}
What I lack:   {{MISSING_ITEM}}
Why it stops:  {{STOP_BASIS}}

Options:       {{OPTION_A}}
               {{OPTION_B}}
               — stated neutrally; no recommendation where judgment is required

Routed to:     {{ROLE_REVIEWER}} → {{ROLE_APPROVER}}
Status:        HELD — no further work on this item until approved
```

**Token vocabulary for this template.** Every fill-in is a curly token; there are no bracket
placeholders in it.

| Token | Resolves to |
|---|---|
| `{{FLAG_SUBJECT}}` | The one issue this flag is about |
| `{{TRIGGER_CLASS}}` | Exactly one of: citation unverified · source conflict · missing fact · legal judgment · scope/authorization · confidentiality · disclosure requirement · deadline risk · out-of-scope domain |
| `{{FACTS_ON_HAND}}` | The facts and sources actually in the file, named with file names |
| `{{MISSING_ITEM}}` | The specific missing item — never "more information" |
| `{{STOP_BASIS}}` | The rule, duty, or risk that makes this an attorney call, with the verify warning on any authority named |
| `{{OPTION_A}}` · `{{OPTION_B}}` | The alternatives, stated neutrally |

### After flagging

**(assistant)** Do not proceed on the flagged item. Continue only on unflagged work, and state
plainly which parts are complete and which are held. Never let the flagged item quietly resolve
itself because the draft needed to continue.

---

## 5. THE OUT-OF-SCOPE VARIANT

For the five domains Core does not cover — trust accounting / IOTA, conflicts-of-interest
screening, withdrawal / termination, unbundled and limited-scope ethics, attorney advertising
compliance — use the routing statement in `coverage-and-limits.md` instead of the flag above.

The difference matters: the flag above says *"an attorney must decide this."* The out-of-scope
statement says *"this product does not carry a workflow for this, and I will not improvise one."*
Do not substitute one for the other.

**The withdrawal / termination row has a handle — give it.** That domain is the one out-of-scope row
a buyer can close themselves, and an out-of-scope statement that does not say how is a dead end.
`{{ROLE_APPROVER}}` at the buyer's firm installs the R. Regul. Fla. Bar 4-1.16 compliance language
⚠️ VERIFY: confirm rule and current text before relying on this. — in **one file, one section:
`references/disengagement/disengagement.spec.md`, the `## ATTORNEY-SUPPLY BLOCK` section**, in the correspondence
skill. **The hard stop clears once that section is populated and attorney-approved**, and not
before. Say that whenever the row comes up; it is the difference between a boundary and a wall.

---

## 6. DEGRADATION

| Situation | Behavior |
|---|---|
| No tracker or case-management suite installed | Deliver the flag inline. Append: `{{ROLE_DRAFTER}} must record this flag in {{PM_SYSTEM}} before session close.` Never drop the flag because there is nowhere to file it |
| No correspondence suite installed | Produce the routing text inline, marked `DRAFT — attorney review required before sending` |
| `{{DMS}}` unreachable through the file connector | Emit the flag and the record inline, labeled for manual filing. Never error, never silently omit |
| Role tokens unmapped at install | Use the tokens literally and add a MISSING FACTS entry: `{{ROLE_APPROVER}} and {{ROLE_REVIEWER}} are not yet mapped to named individuals — map before this flag can be routed` |
