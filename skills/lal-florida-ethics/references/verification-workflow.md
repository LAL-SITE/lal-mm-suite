# THE TWELVE-STEP VERIFICATION WORKFLOW

> **Not legal advice.** Verify every rule against current official sources before relying on it:
> `floridabar.org`, `flcourts.gov`, `leg.state.fl.us`.

Run this **before any AI-assisted work product is filed or sent.** Every step has a named owner
expressed as a role token.

**`{{ROLE_APPROVER}}` owns the outcome regardless of who owns the step.** Delegating a step never
delegates the responsibility. R. Regul. Fla. Bar 4-5.1 and 4-5.3 ⚠️ VERIFY: confirm rule and
current text before relying on this.

---

| # | Check | Owner |
|---|---|---|
| 1 | **Facts traced to the file** — every assertion tied to a specific document, page, or communication | `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}` |
| 2 | **Tokens and assumptions resolved** — no unresolved token and no unlabeled assumption survives into a filed document | `{{ROLE_DRAFTER}}` |
| 3 | **Every citation verified** — it exists; the holding matches the proposition; it is still current; checked **against the source, not against the AI** | `{{ROLE_APPROVER}}` |
| 4 | **Every quotation checked against the original**, word for word | `{{ROLE_REVIEWER}}` |
| 5 | **Statute and rule text re-pulled from the current official source** — sections, subdivisions, thresholds, deadlines. **Never from a template** | `{{ROLE_REVIEWER}}` → `{{ROLE_APPROVER}}` |
| 6 | **Math re-run independently** — support, equalization, arrears, income averaging, date computations. **Re-run, not re-read** | `{{ROLE_REVIEWER}}` |
| 7 | **Names, dates, case number, court, division, and party designations confirmed** against the caption and the docket; opposing-party documents correctly attributed | `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}` |
| 8 | **Form version current** — the Florida Supreme Court Approved Family Law Form in use is the current one; local form requirements checked | `{{ROLE_REVIEWER}}` |
| 9 | **Masking confirmed** — no full account numbers, SSNs, routing numbers, or card numbers anywhere, including exhibits and attachments; masking is permanent, not an annotation layer | `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}` |
| 10 | **Disclosure / certification block correct for this court and this judge** — fields completed, tool named to the required specificity, no-use statement included if applicable | `{{ROLE_APPROVER}}` |
| 11 | **All 🛑 flags cleared** — resolved on the record, or consciously accepted on the record | `{{ROLE_APPROVER}}` |
| 12 | **The attorney has read the document end to end** and it reflects their judgment and the client's position | `{{ROLE_APPROVER}}` |

---

## THE SEND-BACK RULE

**(`{{ROLE_REVIEWER}}`)** If any line fails, **the document goes back.** It does not go forward with
a note.

A note is not a fix. "Flagging for the attorney to check step 5" is how an unverified statutory
threshold reaches a filing — because the attorney received it as a completed document with a
comment attached, and comments get cleared faster than they get checked.

---

## SEQUENCING NOTES

- **Step 10 begins before step 1.** `{{ROLE_APPROVER}}` confirms the circuit AI order and the
  assigned judge's standing order **before drafting begins**, not at signature.
  `[CONFIRM LOCALLY: the current AI disclosure and certification requirement for this judge and division, with the assigned judge's chambers and the circuit administrative orders page on flcourts.gov]`
- **Steps 3 and 5 cannot be delegated downward.** Step 3 is the attorney's because it is the
  attorney's signature that certifies it. R. Regul. Fla. Bar 4-3.3 ⚠️ VERIFY: confirm rule and
  current text before relying on this.
- **Step 2 and step 9 are the two steps most often skipped under time pressure**, and both are
  visible in the filed document. Run them last as well as in sequence.
- **Step 11 is not a formality.** "Consciously accepted" means the attorney read the flag, decided,
  and the decision is recorded. An unread flag is not a cleared flag.

---

## RECORD

The completed checklist goes in the matter file in `{{DMS}}`, and the activity is logged in
`{{PM_SYSTEM}}`, reached through the file connector abstraction. It carries the tool name and
version, the manner of use, the disclosure block used, and who verified the citations.

This is the documented proof of compliance in a challenge, a sanctions inquiry, or a Bar
proceeding. It is the reason the checklist is written down rather than remembered.

---

## DEGRADATION

| Dependency | If installed | If not installed |
|---|---|---|
| **File connector** | Pull the source documents for steps 1, 4, 5, 7, and 9 | Ask `{{ROLE_DRAFTER}}` for the specific documents by name. Mark any step you could not perform as `NOT RUN — source unavailable` and list it under MISSING FACTS. **Never mark a step passed that you did not run** |
| **Case management / tracker** | Log the completed checklist against the matter | Emit the checklist inline labeled `RECORD — must be filed to {{DMS}} and logged in {{PM_SYSTEM}} by {{ROLE_DRAFTER}} before session close` |
| **Judicial procedures** | Route step 10 there for the assigned judge and division | Emit the `[CONFIRM LOCALLY: ...]` marker above and **hold the filing.** Step 10 unconfirmed is a High risk level, not a Low one |
| **Research provider `{{RESEARCH_PROVIDER}}`** | Use it as a verification source for step 3 — never as a substitute for reading the authority | Step 3 is performed against official sources only. If neither is available, step 3 fails and the document goes back |
| **Forms library** | Check step 8 against it | Emit `[CONFIRM LOCALLY: current approved form version and any local form requirement, with the clerk of court in {{COUNTY}} County]` |

Never error. Never silently omit a step. **A step you could not run is reported as not run.**
