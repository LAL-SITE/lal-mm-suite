# Topic Map

**Loaded by `lal-help.SKILL.md` § 3.** Maps a how-to topic to the firm-neutral training module that
covers it, and to the installed skill that does the work.

---

## 1. WHERE THE MODULES LIVE, AND WHAT SHIPS INSIDE CORE

The reference corpus behind this map is a **firm-neutral Florida family law training guide in 22
numbered modules**, plus two always-on components. Its own index states its scale: 22 modules,
roughly 175,000 words, built from 488 extracted documents of a working practice's internal training
library.

**None of the 22 modules ships inside Core Foundation.** State that plainly rather than implying
otherwise.

The modules ship as the **knowledge-base add-on** — a load-on-demand knowledge pack, not a workflow
skill. Core Foundation ships nine workflow skills and their reference files. Where a Core skill
needs module content, it either carries the necessary substance in its own references or degrades
per § 4.

Three modules cover ground Core Foundation covers **with its own skills**, which is the closest
thing to "shipping inside Core":

| Module | Core skill that covers the same ground |
|---|---|
| 03 — Case Lifecycle & Scope of Representation | `lal-command-center`, `lal-start-case` |
| 21 — Glossary, Abbreviations & Forms Map | `lal-help` answers Type C definition questions directly |
| 22 — AI Use, Verification & Bar Compliance | `lal-florida-ethics`, `lal-caselaw-protocol` |

Module 22 and the guide's `DISCREPANCIES.md` are **always-on** in the guide's own architecture:
Module 22 is its operating constitution, and `DISCREPANCIES.md` must be checked for any module
before that module is relied on. The guide's own header states that its source materials contain
internal conflicts, stale law, and at least three citations that appear to be fabricated, and that
those are documented rather than hidden. **Anything drawn from a module carries a verification
warning, and no case law is carried across at all.**

---

## 2. THE 19 TOPIC ROWS

Sixteen of nineteen map to a real module. Three have **no module in the 22** — those three are named
as gaps, not papered over.

| # | Topic | Module(s) | Suite that owns the module's subject | Installed skill that does the work |
|---|---|---|---|---|
| 1 | New client intake and onboarding | **03**; **05** for the service sequence | Knowledge base; lifecycle ground is Core | `lal-start-case`, `lal-command-center`, `lal-correspondence` (welcome) |
| 2 | Retainer and engagement agreement | **03** — scope of representation, limited scope versus full | Knowledge base; Core covers lifecycle | `lal-correspondence` (retainer transmittal), `lal-florida-ethics` (scope and fee rules) |
| 3 | Practice-management tasks and workflows | **03**; **02** for deadline control | Knowledge base | `lal-command-center` |
| 4 | Discovery and mandatory disclosure | **07**; **08** for enforcement | Financial Discovery | Financial Discovery suite; `lal-correspondence` for deficiency letters |
| 5 | Financial affidavit | **07**; **09** and **11** for the inputs | Financial Discovery | Financial Discovery suite |
| 6 | Drafting pleadings and motions | **04**; **02** for the deadline the filing answers | Drafting | Drafting suite |
| 7 | Filing and service | **05**; **02** for e-filing and e-service | Drafting | Drafting suite; `lal-command-center` for the resulting deadline |
| 8 | Billing and time entry | **NO MODULE.** Nearest is **22** for fee and billing ethics | — | `lal-florida-ethics`; `lal-correspondence` for fee accounting. **Named gap — see § 3** |
| 9 | Client communications | **NO MODULE.** | — | `lal-correspondence` — nine content specs. **Named gap — see § 3** |
| 10 | Name change | **17** | Drafting Advanced | Drafting Advanced |
| 11 | Injunctions and domestic violence | **16**; **20** for the full hearing | Drafting Advanced | Drafting Advanced |
| 12 | Contempt and enforcement | **15**; **08** for enforcement discovery; **20** for the hearing | Contempt & Enforcement | Contempt & Enforcement suite |
| 13 | Modifications | **15**; **13** if relocation is the ground | Contempt & Enforcement | Contempt & Enforcement suite |
| 14 | Paternity | **14**; **11** and **12** for the relief that follows | Drafting Advanced | Drafting Advanced |
| 15 | Mediation preparation and agreements | **18**; **07**, **09**, **11**, **12** as the readiness inputs | Mediation & Settlement | Mediation & Settlement suite |
| 16 | AI use, verification, and Bar compliance | **22** — always-on | Knowledge base; **Core covers this ground** | `lal-florida-ethics`, `lal-caselaw-protocol` |
| 17 | Adoptions | **NO MODULE.** | — | **Named gap — see § 3** |
| 18 | Temporary custody by extended family and grandparent visitation | **14** — covers Ch. 751 alongside paternity | Drafting Advanced | Drafting Advanced |
| 19 | Relocation | **13**; **12** for the long-distance schedule; **04** for the instrument | Drafting Advanced | Drafting Advanced |

**Cross-reference chains.** The guide's own index carries task-to-module chains, and a how-to should
follow them rather than loading one module. Examples it names: opening a divorce with children runs
03 → 06 → 12 → 11 → 05 → 04; responding to a served petition runs 02 → 06 → 04 → 07; a hidden-income
question runs 07 → 08 → 11; mediation preparation runs 18 → 07 → 09 → 11 → 12; trial preparation runs
20 → 02 → 08 → 04; closing a file runs 03 → 15.

---

## 3. THE THREE TOPICS WITH NO MODULE

Named honestly. A guide on any of these is generated from installed skills plus general practice
knowledge, and **every step that rests on general knowledge is marked unverified.**

### 3.1 Billing and time entry — row 8

The 22 modules contain no billing, trust-accounting, or time-entry module. Module 22 reaches fee and
billing **ethics** only. Two consequences:

- Fee, trust, and billing-conduct questions route to `lal-florida-ethics`, which carries the rule
  family. ⚠️ VERIFY: confirm rule and current text before relying on this.
- Mechanical time-entry and invoicing procedure is **buyer-specific and unsourced**. Emit
  `[CONFIRM LOCALLY: {{PM_SYSTEM}} time-entry codes and the firm's invoicing cadence, with {{ROLE_APPROVER}}]`
  rather than a step.

The correspondence corpus is asymmetric in the same direction and this must be said at install: the
document-chase half is well covered, the billing half is almost entirely absent as collection
correspondence. There is **no** past-due notice, no trust replenishment request, no payment-plan
default letter, and no fee-arrears escalation letter anywhere in the corpus. The one structured
billing document is a closure-context fee accounting and it must not be repurposed as a mid-matter
collection tool.

### 3.2 Client communications — row 9

No module covers correspondence. This is not a defect in the guide — correspondence is a Core
Foundation skill with its own nine content specs, and those specs are the authoritative source. Route
row 9 to `lal-correspondence` and its `references/lane-selection-matrix.md`.

Two things a how-to on this topic must carry, because a buyer will otherwise be surprised
mid-matter:

- Many sub-types are **template-sourced only** — no sent instance exists anywhere in the corpus. The
  matrix labels every one.
- A **firm-initiated disengagement letter cannot be produced** until `{{ROLE_APPROVER}}` at the
  buyer's firm supplies the compliance block. That is a hard stop no role can self-approve past.
  Say where it is installed as well as that it is missing:
  `references/disengagement/disengagement.spec.md`, the `## ATTORNEY-SUPPLY BLOCK` section, in the
  correspondence skill.
  **The stop clears once that section is populated and attorney-approved.**

### 3.3 Adoptions — row 17

No adoption module exists in the 22, and no adoption content ships in Core. A guide here is general
practice knowledge only, marked unverified throughout, with
`[CONFIRM LOCALLY: this circuit's adoption procedure and the required forms, with {{ROLE_APPROVER}}]`
on every procedural step.

Do not scaffold adoption procedure from the name-change or paternity modules. They are different
statutory schemes and a borrowed step reads as sourced when it is not.

---

## 4. MODULES NOT REACHED BY THE 19 ROWS

The 19 rows were inherited from a firm's own how-to inventory, and the 22 modules are wider than
that inventory. These are reachable and useful:

| Module | Load it when |
|---|---|
| 01 — Court System, Jurisdiction, Venue & Sources of Law | Which court, which division, whether Florida can hear it, home-state analysis, long-arm, venue, magistrates and hearing officers, what authority controls |
| 02 — Rules of Procedure, Deadlines & Time Computation | Any deadline calculation, day counting, e-filing and e-service, trial-order deadline control, a missed deadline |
| 06 — Dissolution of Marriage | Any divorce matter — grounds, residency, simplified versus regular, required filings, petitioner versus respondent sequencing, temporary relief, final judgment |
| 09 — Equitable Distribution | Classifying and valuing assets and liabilities, the schedule, tracing, dissipation, retirement division, business interests, the equalizer |
| 10 — Alimony | Need and ability, the statutory forms, marriage-length brackets, durational caps, security, termination, modification |
| 11 — Child Support | Guidelines calculation, income determination, imputation, deviation, retroactive support, health insurance, childcare, income deduction, termination |
| 12 — Timesharing & Parenting Plans | Building or reviewing a parenting plan — schedules, holidays, exchanges, the clause library, high-conflict and safety provisions, enforceability |
| 19 — Guardian ad Litem Practice | Serving as or dealing with a family-case guardian — appointment, investigation method, reports, recommendations, testimony |
| 20 — Hearings, Trial & Evidence | Getting a hearing, the trial order, the pretrial stipulation, laying a predicate, witnesses, the trial notebook, proposed final judgments |

Module 02 deserves a standing note: **every deadline this product records carries its authority and
its computation basis.** Module 02 is where the counting rules live, and a deadline question routes
there and to `lal-command-center` together. ⚠️ VERIFY: confirm rule and current text before relying
on this.

---

## 5. DEGRADING WHEN A MODULE IS NOT INSTALLED

The knowledge-base add-on is a **premium add-on**. Assume it is absent unless a probe finds it.

| State | Behaviour |
|---|---|
| Module readable | Load it, follow the cross-reference chain, name the module in Sources Used, carry the verification warning, check its discrepancy record before relying on it, and carry no case law across |
| Add-on installed, module unreadable | Say which module the answer lives in, answer from installed skills, mark the guide unverified |
| Add-on not installed | Answer from installed skills and their references. Where the module was the only source, say so on the step and emit `[CONFIRM LOCALLY]`. **Still produce the guide** |
| Neither module nor skill | § 6 of the help skill. Guide from general knowledge, marked unverified throughout, with the drafted question for whoever owns the answer |

**In no state does the answer become "check the training guide."** That is the one failure this skill
exists to prevent.

---

## 6. TOKEN AND ROLE NOTE

The modules are firm-neutral and use the same curly-token schema this product uses, and they tag
every checklist item with the **role** that owns it rather than a name or a title. A guide built from
a module inherits that discipline: role tokens, never job titles, and
`[CONFIRM LOCALLY: <what>, with <whom>]` wherever practice varies by circuit, county, division,
judge, or clerk.

The modules use a small number of tokens beyond this product's required set — among them
`{{CLIENT_UPLOAD_TOOL}}`, `{{VIDEO_TOOL}}`, `{{PASSWORD_MANAGER}}`, and `{{TRANSCRIPTION_TOOL}}`.
They are curly and follow the same rules. A guide may use them; it may not invent a new bracket
syntax.
