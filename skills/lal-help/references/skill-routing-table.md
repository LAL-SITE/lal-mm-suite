# Skill Routing Table

**Loaded by `lal-help.SKILL.md` § 2 and § 5.** The nine Core Foundation skills, what each owns, what
routes to it, and what to do when it is not installed.

Core Foundation ships free with every purchase. **Assume all nine are present**, but probe rather
than assert — a buyer can install selectively, and a skill can be present but unconfigured.

---

## 1. THE NINE

| # | Skill | Owns | Fires |
|---|---|---|---|
| 1 | `lal-file-connector` | The single point of contact between every skill and storage. Binds one provider at install, serves seven fixed operations, never names a provider to any other skill | Automatically, whenever any skill needs a file, and silently on the first turn of a matter session |
| 2 | `lal-command-center` | The per-matter state file — position, scope, the deadline register with authority and computation basis, the append-only lifecycle ledger, open attorney flags | On any state question, at session open on a matter, and at the close of any skill that completes a stage, computes a deadline, changes scope, or raises a flag |
| 3 | `lal-start-case` | First-touch scan of a matter file and birth of the command center. Deliberately slim — the full onboarding workflow is a separate suite | On a new matter, a first session on an existing matter, or a request to scan and set up |
| 4 | `lal-florida-ethics` | Ethics and AI-use compliance. Ambient, always-on, and **wins on conflict with any other skill** | On any ethics-adjacent language, in any suite, mid-task, without being invoked |
| 5 | `lal-caselaw-protocol` | Authority provenance. Hard-codes a single permitted source and attaches a verification warning to everything | Whenever any citation, authority, or "is there something supporting this" question appears |
| 6 | `lal-correspondence` | All four correspondence lanes — client, opposing counsel, bench, third party — across nine content specs | On any request to write, revise, or QC an outgoing letter or email |
| 7 | `lal-help` | The front door. Routes, generates how-tos, or answers. **Never says go look it up** | On any question about how the firm or the product works, rather than a request to produce a matter document |
| 8 | `lal-brand-kit` | Voice archetype and always/never phrases, populated from install intake. Non-legal output style | Ambient on any drafting task that has a voice choice |
| 9 | `lal-file-organizer` | Whole-matter audit, rename, and re-folder. Naming convention is swappable | On any request to organize, rename, sort, or audit matter documents — and on offer whenever another skill's search surfaces misnamed or misfoldered files |

**Ambient skills — 1, 2, 4, 5, 8.** They fire without being asked. Do not route to them as though
the asker must invoke them; note that they are already running.

**One decision-locked ambient skill sits alongside these nine:** a judicial-procedures reference,
locked to Core Foundation, which depends on live web lookup. Where it is present, run it before any
bench transmittal. Where it is not, emit
`[CONFIRM LOCALLY: this division's proposed-order format, submission channel, and binder policy, with {{ROLE_APPROVER}}]`
and proceed. Note the web-lookup dependency to the buyer either way.

---

## 2. ROUTING BY WHAT THE ASKER SAID

| They said something like | Route to | Note |
|---|---|---|
| "Where's the matter folder" · "scan the file" · "what's new since last time" · "read that document" · "save this" · "pull the template" · "connect my storage" · "we use a local folder" | **1 — file connector** | Cloud storage is not required. A firm on plain uploads is fully supported |
| "Where are we" · "what's the status" · "what's next" · "what's due" · "calendar this" · "how was that date computed" · "scope changed" · "flag this" · "what changed since last session" | **2 — command center** | Every deadline carries authority and computation basis. Append, never overwrite |
| "New client" · "set up this matter" · "open a file" · "first look at this case" | **3 — start case** | Scan and birth the command center. The full onboarding workflow is a separate suite |
| "Is this ethical" · "is that a conflict" · "can I put this in the AI" · "do I need client consent" · "who signs this" · "can staff do this" · "trust account" · "withdraw" · "sanctions" · "Bar complaint" · "advertising" · "neutral versus counsel" | **4 — ethics** | Already ambient. Wins on conflict. Never advises a client, never files, never signs |
| "Find me authority" · "is this case real" · "cite something for this" · "did anyone verify this" | **5 — case-law protocol** | Single permitted source, verification warning on everything. **Core skills carry no case law at all** |
| "Draft a letter" · "welcome email" · "status update" · "deficiency letter" · "letter to the judge" · "letter to the assistant" · "preservation letter" · "closing letter" · "disengagement letter" | **6 — correspondence** | Four lanes, nine specs. Hard-stops on firm-initiated disengagement until the attorney block exists |
| "How do I" · "walk me through" · "which skill" · "what's installed" · "I'm stuck" · "make me a checklist" | **7 — help** | You are here |
| "Does this sound like us" · "on brand" · "what's our voice" | **8 — brand kit** | Ambient on drafting. Non-legal output style only |
| "Organize this folder" · "rename these" · "sort the documents" · "are the folders right" · "fix the file names" · "audit the matter file" | **9 — file organizer** | Never moves a document between matters. Never renames without confirming document identity |

---

## 3. THE THREE REAL OVERLAPS

| Overlap | Owner | Rule |
|---|---|---|
| Correspondence versus court-document drafting | **Correspondence** owns letters and emails. **Drafting** owns pleadings, motions, notices, orders | A cover letter transmitting a pleading is correspondence. The pleading is drafting. Keep the boundary explicit |
| Command center versus roadmap | **Command center** owns current state. **Roadmap** owns the forward plan | State is Core. The plan is a separate suite |
| Help versus ethics | **Ethics** owns whether something is permitted. **Help** routes and does not opine | Where help touches an ethics question, it names what the question turns on and hands off |

Two smaller boundaries worth stating:

- **File connector versus file organizer.** The connector reads and writes. The organizer decides
  what a file should be called and where it belongs. The organizer calls the connector; never the
  reverse.
- **Start case versus command center.** Start case births the file. The command center owns it from
  then on.

---

## 4. WHEN A CORE SKILL IS NOT INSTALLED

| Missing | Fallback |
|---|---|
| **1 — file connector** | Work from pasted or uploaded material. Say the matter file was not read. **Never assert a document is absent on the basis of a failed read** |
| **2 — command center** | Ask the one or two facts the task needs — posture and scope. Emit any intended entry in the output as a fenced `PENDING COMMAND CENTER WRITE` block, name where it should be saved, and continue. Never block on its absence |
| **3 — start case** | Ask for matter name, county, matter type, and posture directly, and proceed |
| **4 — ethics** | Name what the question turns on, cite the rule family with ⚠️ VERIFY: confirm rule and current text before relying on this., and draft the question for `{{ROLE_APPROVER}}`. Do not opine |
| **5 — case-law protocol** | Rules, statutes, and Bar rules only, each with the verification warning. **No case law under any circumstance.** Official sources only |
| **6 — correspondence** | Give the required structure and the element order from the content specs and say a draft needs the skill. Do not freehand a letter |
| **7 — help** | Not applicable — this is the help skill |
| **8 — brand kit** | Use the content spec's own voice notes, which are lane-specific and sufficient |
| **9 — file organizer** | List the misnamed and misfoldered documents so the asker can move them. Do not rename or move as a side effect of another task |

**"Installed but not configured" is a distinct state and the more common one.** A connector present
but unauthorized is not absent. A brand kit present but unpopulated is not absent. Say which one
thing is needed and continue in the degraded mode.

---

## 5. THE OTHER SUITES — ROUTE OR DEGRADE

Not Core. Route where installed; degrade honestly where not. Names may vary by install; match on
subject matter rather than on a literal skill name.

| Subject | Suite | If not installed |
|---|---|---|
| Discovery routing, financial intake, disclosure organization and tracking, financial affidavit building and cross-check, opposing production review, undisclosed-account detection, non-standard income, gap analysis, equitable distribution chart and equalizer, certificate of compliance | Financial Discovery | Give the structure and the inputs from the command center schema and the correspondence specs; do the analysis by hand and say so |
| Complex and variable income analysis, deep asset tracing | Financial Discovery — Advanced | Same |
| Pleadings, motions, notices, orders, matter-type drafting, clause libraries | Drafting — Core and Advanced | Give the required elements and the instrument choice; correspondence still handles any cover letter |
| Contempt, enforcement, modification | Contempt & Enforcement | Give the structure and the elements; flag every authority for verification |
| Mediation readiness, session support, settlement agreements | Mediation & Settlement | Give the readiness checklist inputs; correspondence handles the transmittals |
| Guardian ad Litem intake, tracking, interviews, chronology, reports, documents, QC | GAL System | Correspondence covers the court-appointed-neutral third-party sub-types; nothing else |
| Legal research, provider handoff, contribution capture | Research | Case-law protocol still governs. Do not substitute general knowledge for authority |
| Case roadmap, case closing, case memo | Roadmap & Case Management | Ask the closure reason directly — it controls the letter, and the same letter is never used for every file |
| The 22 firm-neutral training modules | Knowledge base add-on | `references/topic-map.md` § 5 |

---

## 6. THE ONE STOP HELP CANNOT CLEAR

A **firm-initiated disengagement letter** while the `{{ROLE_APPROVER}}`-supplied compliance block is
empty. No role self-approves past it, no deadline authorizes it, and no skill drafts around it.

Where an asker is stuck on it, the help answer is four things and no redirect:

1. **What the block requires** — stated as scope, not as a draft: the withdrawal basis relied on; the
   reasonable-notice statement; the steps taken to avoid reasonably foreseeable prejudice; the
   surrender of papers and property; the refund of unearned fees; and whether the letter references
   the fee agreement's termination clause. ⚠️ VERIFY: confirm rule and current text before relying on
   this.
2. **Who owns it** — `{{ROLE_APPROVER}}`. Nobody else, and no skill.
3. **Where it is installed** — `references/disengagement/disengagement.spec.md`, the
   `## ATTORNEY-SUPPLY BLOCK` section, in the correspondence skill. **The stop clears once that
   section is populated and attorney-approved**, and nothing else clears it. Never state the stop
   without stating the handle; a stop with no handle reads to a buyer as a broken product.
4. **The offer** — assemble the sourced operative paragraphs around the gap as a partial draft marked
   **NOT SENDABLE**, so `{{ROLE_APPROVER}}` writes one block rather than a whole letter.

See the **correspondence skill**, § 6 — the skill body itself, not a path from here.
