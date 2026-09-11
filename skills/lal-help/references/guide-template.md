# How-To Guide Template

**Loaded by `lal-help.SKILL.md` § 3.** The output shape for every Type B question, plus the
non-negotiables block that goes into every guide and the follow-ups that close it.

---

## 1. THE TEMPLATE

Reproduce this structure exactly. Every section appears, in this order. A section with nothing in it
says so — it is never deleted, because a missing section reads as "not applicable" when it usually
means "nobody checked."

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
HOW-TO: <TASK NAME IN ALL CAPS>
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

WHAT THIS COVERS:
<One sentence. What task this covers and when to use it. Name the boundary — what
this guide does NOT cover, if a reader could reasonably expect it to.>

WHO DOES THIS:
<Role tokens only. {{ROLE_DRAFTER}} drafts; {{ROLE_REVIEWER}} reviews;
{{ROLE_APPROVER}} approves. Never a job title, never a name. Add: "Roles are
defaults, not gates — anyone may run this. If you hold {{ROLE_APPROVER}}, you
approve your own output at the approval step.">

BEFORE YOU START — REQUIREMENTS:
□ <A requirement that is physically necessary — an input, a document, a fact>
□ <Another>
□ <Note: a prior stage is NOT a requirement. If a stage has not been logged,
   proceed and note it. Only list what the task genuinely cannot run without.>

━━━━━━━━━━━━━━━━━━━━━━━━━━━━
STEP-BY-STEP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━

STEP 1: <Short action title, imperative>
  → What to do, exactly.
  → Where: <the system, by token or by skill name — {{PM_SYSTEM}}, {{DMS}},
    {{UPLOAD_PORTAL}}, {{ESIGN_TOOL}}, {{PAYMENT_PROCESSOR}}, the file connector,
    lal-correspondence. Never a vendor name.>
  → Done looks like: <the observable result. What the reader sees when this step
    worked.>

STEP 2: <Short action title>
  → What to do.
  → Where: <system>
  → Done looks like: <observable result>

<Continue. Numbered only. No "as needed." No step without a system and a result.>

━━━━━━━━━━━━━━━━━━━━━━
⚠️ FIRM RULES & FLAGS
━━━━━━━━━━━━━━━━━━━━━━
• <Any rule that binds this task specifically>
• <Approval gate, if one applies — and who satisfies it, including self-approval>
• <Deadline or sequencing rule, if one applies>
• <Confidentiality or client-data rule, if one applies>
• <Any [CONFIRM LOCALLY: <what>, with <whom>] items that belong to the task as a
   whole rather than to one step>

━━━━━━━━━━━━━━━━━━━━
✅ DONE WHEN:
━━━━━━━━━━━━━━━━━━━━
<Completion criteria. Exactly what confirms the task finished correctly. Testable,
not aspirational — "the ledger entry exists and names the trigger," not "the file
is in good order.">

━━━━━━━━━━━━━━━━━━━━
📂 WHERE TO SAVE:
━━━━━━━━━━━━━━━━━━━━
<Destination by role in the matter, reached through the file connector. Never a
path, never a drive letter, never a provider name, never a URL. What gets written
to the command center, if anything.>

━━━━━━━━━━━━━━━━━━━━
📌 SOURCES USED:
━━━━━━━━━━━━━━━━━━━━
<Never blank. Name each source: a Core skill and its reference file, a content
spec, a training module by number and title, the matter file itself, or "general
Florida family law practice knowledge — unverified." If a step rests on the last
one, say which step.>
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 2. THE NON-NEGOTIABLES BLOCK

**Injected into every guide, on every topic, without exception.** It sits immediately below
`FIRM RULES & FLAGS`, or is folded into that section where the list is short.

Written as tokens and roles, so it is true at every buyer.

```
━━━━━━━━━━━━━━━━━━━━━━
STANDING RULES — THESE APPLY TO EVERY TASK
━━━━━━━━━━━━━━━━━━━━━━
• AUTHORITY. Rules, statutes, and Bar rules only — never case law, never from
  memory, never from a general web search. Every authority carries:
  ⚠️ VERIFY: confirm rule and current text before relying on this.
  Official sources only: floridabar.org, flcourts.gov, leg.state.fl.us.

• CLIENT DATA. Confidential and privileged. It stays inside the matter it belongs
  to. Never move a document between matters. Never share, export, or reference
  matter content outside the matter without instruction from a named person.

• THE COMMAND CENTER IS THE RECORD. Stage completions, deadlines, lifecycle moves,
  and attorney flags are written there. Work that is not recorded there is
  invisible to every other suite. Append; never overwrite. Never drop a flag.

• EVERY DEADLINE CARRIES ITS BASIS. The authority that creates it, the event it
  runs from, and the counting rule actually applied. A date without a recorded
  basis cannot be audited, and an unauditable jurisdictional date is worse than
  no date.

• APPROVAL GATES. Anything going to a court, a client, opposing counsel, or a
  third party is approved before it leaves. If you hold {{ROLE_APPROVER}}, you
  satisfy that gate yourself — record it and continue. Three gates survive
  self-approval, because none is about seniority: text an attorney has not yet
  supplied, a figure the client has not authorized in writing, and an authority
  whose current text has not been checked.

• NEVER FABRICATE. An unknown value is null plus a flag. An unsourced step is
  marked unsourced. A named gap is a required output; invented content is a defect
  the buyer finds mid-matter.

• NEVER GUESS BETWEEN MATTERS. Two plausible matter folders is a question for a
  person, not a coin flip. Mismatched matter folders are how privileged content
  leaks between cases.

• TIME. Log it in {{PM_SYSTEM}} before the session closes — including the
  underlying review time, not only the drafting time.
```

Two topic-specific additions, added only where the guide's subject reaches them:

```
• PROPERTY MATTERS. Pull the instrument and confirm ownership from the record.
  Never rely on a party's description alone.

• REPRESENTATION-ENDING DOCUMENTS. No review solicitation, no cross-sell, and no
  reference to a service the firm does not offer. A firm-initiated disengagement
  letter cannot be produced at all until {{ROLE_APPROVER}} supplies the
  compliance block.
```

---

## 3. RULES FOR WRITING THE STEPS

| Rule | Why |
|---|---|
| **Numbered only** | A reader following a guide under time pressure needs a sequence, not a set |
| **One action per step** | Two actions in one step means one of them gets skipped |
| **Imperative titles** | "Confirm the trust deposit cleared," not "Trust deposit" |
| **Every step names its system** | The reader should never have to guess where to go. By token or by skill name; never by vendor |
| **Every step names its observable result** | "Done looks like" is what makes the guide self-checking |
| **No "as needed," no "if appropriate," no "as applicable"** | If the condition matters, state the condition. If it does not, drop the hedge |
| **No step that is only "get approval"** | Name who, on what, and what they are deciding — and note that an approving attorney satisfies it themselves |
| **No step that says look something up** | Either the guide knows, or the step is marked unsourced with a `[CONFIRM LOCALLY]` |
| **Mark an unsourced step on the step** | Not in a footnote. The reader must see it where they will act on it |
| **Plain language** | Write for someone new. Define any legal term the first time it appears in a step |
| **Role tokens, never job titles** | Buyer org charts differ; an asserted title is wrong somewhere |

**Marking an unsourced step:**

```
STEP 4: File the completed petition
  → Submit through the county's e-filing portal.
  → Where: [CONFIRM LOCALLY: this county's e-filing portal and whether the clerk
    requires a cover sheet, with {{ROLE_INTAKE}}]
  → Done looks like: a filing confirmation with a stamp date.
  → ⚠️ This step is not sourced from installed reference material. Confirm before
    relying on it.
```

The guide still ships. Every other step still works. The reader knows exactly which one to check.

---

## 4. THE CHECKBOX VARIANT

Offered after every guide, generated on request. Same content, stripped to what a person ticks off
in a note field.

```
<TASK NAME> — CHECKLIST
□ 1. <action> — <system>
□ 2. <action> — <system>
□ 3. <action> — <system>
□ ⚠️ <any gate or flag, inline where it falls in the sequence>
□ Save: <destination by role>
□ Command center: <what gets written>
□ Time logged in {{PM_SYSTEM}}
```

Rules: preserve the order; keep every gate inline where it falls rather than collecting them at the
end; keep the save, write-back, and time lines — they are the three most-skipped steps in every
workflow.

---

## 5. POST-GUIDE FOLLOW-UPS

Deliver the guide, then offer these. In this order, and only the ones that apply.

1. **Depth check** — *"Does this cover it, or should I go deeper on any step?"*
2. **Checklist** — *"Want the checkbox version to paste into `{{PM_SYSTEM}}` notes?"*
3. **Run it** — *"Want me to do step <n> now?"* Offer this wherever an installed skill would perform
   a step. **Do not make them ask twice.**
4. **Gap escalation** — where a step was unsourced: *"Step <n> isn't sourced from anything installed.
   Want me to draft the question for `{{ROLE_APPROVER}}` so you can settle it once?"* Then draft it,
   ready to send.
5. **Cleanup** — where searching the matter file surfaced misnamed or misfoldered documents: name
   them and offer the file-organizer pass.
6. **Install note** — where the gap is structural rather than matter-specific: *"This is a gap the
   firm should close at install, not per matter. I've flagged it."* Then raise the `informational`
   flag.

**Never close with "let me know if you need anything else."** Close with a specific next action.

---

## 6. WHAT NEVER APPEARS IN A GUIDE

- A source-firm name or brand, a staff first name, or **any staff job title**.
- A named practice-management, e-signature, upload, payment, or transcription vendor. Use the token.
- A literal bar number, a billing rate, a tenant, a site, a path, a drive letter, or a
  storage-provider name.
- Any URL except `floridabar.org`, `flcourts.gov`, `leg.state.fl.us`.
- Case law of any kind — no case name, no reporter citation, no "courts have held."
- An estate-planning reference.
- `Click here to enter text.` or any run of placeholder X's.
- An unresolved `{{TOKEN}}` in a guide presented as ready to follow.
- A bracket-style placeholder other than `[CONFIRM LOCALLY: <what>, with <whom>]`.
- Any instruction to go look something up, check the handbook, see the SOP, or search for the answer.
- Any instruction telling an approving attorney to seek attorney approval.
- Any instruction to complete a prior stage before starting. Ask for the missing input instead.
- An empty `SOURCES USED` section.
