# Folder Taxonomy — Slot Contract and Default Mapping

Two different things live in this file, and the difference is the whole design.

1. **The functional slot list is contract.** Other skills ask for slots. Slot ids do not change,
   are not localized, and are not invented.
2. **The folder mapping is configuration, and the mapping below is a DEFAULT — nothing more.**
   It is a sensible starting point drawn from how family law matter files are commonly
   organized. It is expected that firms replace it. Replacing it changes no skill, breaks no
   integration, and requires no re-installation of anything but this mapping.

If a firm's existing folder structure works, **keep the firm's structure and remap.** Do not
reorganize a working file room to match a default.

---

## 1. FUNCTIONAL SLOTS — THE CONTRACT

| Slot id | What belongs in it |
|---|---|
| `intake` | Intake questionnaires, client information forms, screening notes |
| `engagement` | Signed engagement or scope documents, scope addenda, fee documents |
| `identification` | Identity and address verification documents |
| `correspondence` | Letters and messages to and from the client, opposing counsel, and third parties |
| `filed-client` | Documents filed by or on behalf of the client |
| `filed-opposing` | Documents filed by the opposing party |
| `filed-pending` | Submitted but not yet accepted or conformed |
| `orders-agreements-reports` | Entered orders, executed agreements, neutral and expert reports |
| `disclosure-client` | The client's mandatory-disclosure production and supporting documents |
| `disclosure-opposing` | The opposing party's production, as received |
| `disclosure-served` | Copies of what was served on the other side, as served |
| `discovery-served` | Formal discovery requests and responses, either direction |
| `notices` | Notices of hearing, mediation, deposition, and unavailability |
| `hearings` | Hearing-specific materials, ordinarily in date-named subfolders |
| `drafts` | Work in progress, pre-review |
| `notes` | Internal notes, trackers, logs, internal memoranda |
| `records` | Records obtained from third parties |
| `billing` | Fee and trust documentation |
| `misc` | Anything that does not belong to a slot above |
| `work-product-output` | **Generated deliverables.** Default write target for every save. |
| `library` | Firm templates, clause banks, master documents. **Read-only, always.** |

**`library` is not inside a matter.** It is firm-level, mapped separately in `libraryLocator`,
and never written to.

**A slot may map to nothing.** An unmapped slot is a legitimate configuration — a firm may not
separate served copies from production, for example. When a skill asks for an unmapped slot, the
connector reports the unmapped slot and asks; it does not improvise a folder.

**Several slots may map to one folder.** Also legitimate. When they do, the connector says so in
the inventory so a downstream skill does not read a combined folder as a clean category.

---

## 2. THE DEFAULT MAPPING — `lal-default`

**This is a default.** Ship it, use it if nothing better exists, replace it freely.

| Slot | Default folder name |
|---|---|
| `intake` | `Intake` |
| `engagement` | `Engagement and Fees` |
| `identification` | `Identification` |
| `correspondence` | `Correspondence` |
| `filed-client` | `Filed - Client` |
| `filed-opposing` | `Filed - Opposing Party` |
| `filed-pending` | `Filed - Pending Acceptance` |
| `orders-agreements-reports` | `Orders, Agreements and Reports` |
| `disclosure-client` | `Disclosure - Client` |
| `disclosure-opposing` | `Disclosure - Opposing Party` |
| `disclosure-served` | `Disclosure - Served` |
| `discovery-served` | `Discovery` |
| `notices` | `Notices` |
| `hearings` | `Hearings` |
| `drafts` | `Drafts` |
| `notes` | `Notes` |
| `records` | `Records` |
| `billing` | `Billing` |
| `misc` | `Miscellaneous` |
| `work-product-output` | `Generated Output` |
| `library` | firm-level, mapped in `libraryLocator` |

### Default disclosure subfolders

Applied inside `disclosure-client` and `disclosure-opposing`. Also a default.

```
Tax Returns
Business Tax Returns
Wage and Income Statements
Recent Pay Records
Checking and Savings Statements
Brokerage and Investment Statements
Credit Card Statements
Other Account Statements
Loans and Loan Applications
Other Liabilities
Deeds and Titles
Insurance Documents
```

`[CONFIRM LOCALLY: which disclosure categories the firm's own production checklist uses, with {{ROLE_REVIEWER}}]` — categories track the disclosure rule's document list, and a firm that
has built its checklist around its own headings should keep them.

⚠️ VERIFY: confirm rule and current text before relying on this. The default categories are an
organizational convenience, not a statement of what the disclosure rule currently requires.

### Default matter folder naming patterns

Used by Operation 1 Step 2 to prefer an active matter over a pre-engagement file. Also a
default, and one firms very often already have their own version of.

```
activePattern    <Client identifier> - <matter identifier>
inquiryPattern   <Client identifier>
```

---

## 3. REPLACING THE MAPPING

```
1. List the firm's existing matter folder structure exactly as it is.
2. Map each functional slot to one of those folders. Leave a slot unmapped rather than
   forcing it.
3. Where the firm has folders that match no slot, leave them alone. The connector reports
   them as UNRECOGNIZED and never moves or renames them.
4. Record the result as a new taxonomyProfile name. Do not edit lal-default in place —
   a named profile makes it obvious later which structure a matter was scanned under.
5. Do not restructure existing matters to match. The taxonomy describes the file room;
   it does not reorganize it.
```

**Two things that are never configuration:**

- **Slot ids.** Renaming a slot silently breaks every skill that asks for it.
- **The read-only status of `library`.** Templates are never written over by generated output.

---

## 4. MISSING FOLDERS

When a required folder does not exist and the provider can create folders, the connector creates
it using the **exact configured name** — never a variant, never a guess at what the firm meant —
and reports that it did. Where the provider cannot create folders, the connector reports the
missing folder and writes nothing.

Creating a folder is the only structural change this connector ever makes. It never moves,
renames, merges, or deletes anything.
