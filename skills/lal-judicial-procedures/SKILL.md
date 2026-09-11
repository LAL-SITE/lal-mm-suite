---
name: lal-judicial-procedures
description: "Ambient: fires when any judge, magistrate, division, circuit, or Florida county is mentioned. Covers motion practice, hearings, proposed orders, GM procedure. Always live-search, never cached."
---

# Judicial Procedures Skill

## When to use this skill (full trigger reference)

AMBIENT skill — fires the moment any judge name, general magistrate, hearing officer, division, circuit, or Florida county appears anywhere in the session: chat, an uploaded file, an order, a notice, or a caption. Do not wait to be asked. Triggers on "Judge," "the magistrate," "GM," "hearing officer," "what circuit," "how do we set this for hearing," "UMC," "special set," "who's the JA," "standing order," "divisional procedures," "conferral," or any Florida county name. Covers motion practice, notice days, conferral and certification, proposed order format and submission, hearing scheduling, remote appearance, standing and administrative orders, case management deadlines, discovery cutoffs, Rule 12.285 mandatory disclosure, and Rule 12.490 general magistrate procedure including the objection period. ALWAYS run a live web search before answering — never rely on stored or cached knowledge about any judge, magistrate, or division, including one searched earlier this session.

**Rule #1: Always search live. Never answer from memory about a specific judge, general magistrate,
hearing officer, or division — including one you searched earlier in this same session. Procedures
pages get updated without notice, and "I already looked this up" is exactly the assumption that
causes a missed filing requirement.**

This skill is a *process*, not a database. It never hard-codes what a judge requires. The
`references/` folder holds only starting points — circuit numbers, county assignments, starting URLs,
and a note-taking template — and those still get verified against a live search every time they are
used. If you find yourself about to state an officer's requirements without having searched **in this
session**, stop and search first.

## This skill depends on live web search. Say so.

This is one of only two live external dependencies in this product. Everything else in the suite
works from firm-configured sources or, for caselaw, from a single fixed repository. This skill is
different on purpose, because the underlying facts change faster than any file can be maintained:
judges rotate between divisions, retire, get elected out, get reassigned mid-case; divisions get
renumbered; standing orders get replaced; judicial assistants change; remote-appearance links get
reissued.

Practical consequences, which should be stated to the user rather than hidden:

- **If live web search is available in the session:** run the full Step 2 sequence. Normal operation.
- **If it is not available:** say so explicitly and immediately, before answering anything about an
  officer. Then give only what does not depend on a live lookup — the circuit/county mapping, the
  general rule framework, and the checklist structure — and mark every officer-specific or
  division-specific item as unverified with a `[CONFIRM LOCALLY: ...]` flag. Do **not** fill the gap
  from memory, and do not present the reference files as the answer.
- **If a caselaw protocol skill is installed:** any case citation that comes up while working on
  procedures is governed by that protocol, not by this skill. Route it there. **If it is not
  installed:** do not cite cases at all here — statutes, rules, and administrative orders only.

Allowed sources for this skill: official Florida court and government sources —
**flcourts.gov**, individual circuit court websites, **floridabar.org**, and **leg.state.fl.us**.
Nothing else. A blog, a listserv summary, a vendor's judge-analytics page, or a firm's own cached
notes are not sources for what a judge currently requires.

---

## Step 1 — Identify the officer and the circuit

Accept any of: judge / general magistrate / hearing officer name, division number or letter, circuit
number, county, or case number.

If given a **name with no circuit or county, ask which one before searching.** Florida has multiple
judges sharing a last name across circuits, and guessing produces a confidently wrong answer about
the wrong courtroom.

Use `references/fl-circuit-map.md` to convert a county to its circuit number and to find that
circuit's official website as a starting point. Treat every URL in that file as a **starting point to
verify**, never as a guaranteed-current address — circuit sites get restructured. If a link is dead,
search for the circuit's current official site by name rather than guessing at a replacement URL.

Record what you resolved, using tokens so it carries through the session:

> Officer: {{JUDGE}} · Division {{DIVISION}} · {{CIRCUIT}} Judicial Circuit · {{COUNTY}} County ·
> Matter {{CLIENT_NAME}}, Case No. {{CASE_NO}}

If the officer is a general magistrate or hearing officer rather than a judge, note that explicitly —
Step 3's general-magistrate section changes what has to be checked.

---

## Step 2 — Run the live search sequence (do not stop after one hit)

Run all four. One hit is not a search.

1. `{{JUDGE}} {{COUNTY}} Florida family law division procedures` — substitute {{CIRCUIT}} for
   {{COUNTY}} if the circuit is what you have
2. `{{CIRCUIT}} judicial circuit Florida divisions family law` — to confirm the officer's
   **current** division assignment, which is a separate fact from their procedures
3. `{{JUDGE}} {{CIRCUIT}} Florida "divisional procedures" filetype:pdf` — and again substituting
   `Division {{DIVISION}}` for {{JUDGE}}, since many circuits publish by division rather than by name —
   **fetch and read any PDF found in full. Do not rely on the search snippet.** Divisional procedures
   PDFs bury the operative requirement — notice days, proposed-order submission method, exhibit
   deadlines — in the middle of the document, and snippets routinely surface the header instead.
4. `{{CIRCUIT}} judicial circuit Florida administrative order` plus the current year from {{DATE}}

If the first two searches do not surface a divisional procedures page, try the circuit's own site
search, or a general search for `"{{CIRCUIT}} courts" judge directory`, before giving up. Also check
whether the circuit publishes procedures at the **division** level rather than by named officer —
many do, and searching only the name will miss it.

For a general magistrate or hearing officer, add:

5. `{{CIRCUIT}} judicial circuit Florida general magistrate procedures family` and
   `{{CIRCUIT}} Florida order of referral general magistrate` — magistrate practice is frequently
   governed by a circuit-wide administrative order plus a per-case order of referral, not by a
   personal procedures page.

---

## Step 3 — Report findings, organized and dated

Structure the answer as:

> **{{JUDGE}} — judge, general magistrate, or hearing officer as applicable | Division {{DIVISION}} |
> {{CIRCUIT}} Judicial Circuit — {{COUNTY}} County | Verified: {{DATE}}**

Then cover whichever of these the search actually returned information on. **Report gaps as gaps** —
if the search did not answer a heading, say "not addressed in the sources found," never fill it in
from general practice.

- **Motion practice** — notice days required, conferral and certification requirements, page limits,
  whether a memorandum is required or prohibited
  [CONFIRM LOCALLY: notice days and conferral certification actually required — with the judicial
  assistant]
- **Cover sheets** — required or not, and which form
- **Proposed orders** — format (font, margins, spacing), number of copies, how and where to submit
  (portal, email to chambers, e-filing submission), and whether a Word version is required
  [CONFIRM LOCALLY: proposed-order submission method and format — with the judicial assistant]
- **Hearing scheduling** — how time is obtained: uniform motion calendar, an online scheduling
  portal, an email request to chambers, or a call to the judicial assistant; what length of hearing
  requires a special set; whether coordination with {{OPPOSING_COUNSEL}} is required before
  requesting time
  [CONFIRM LOCALLY: current scheduling method and special-set threshold — with the judicial
  assistant]
- **Judicial assistant contact** — contact **method and channel** as published by the court. Do not
  record a personal name in any file or reusable output; JA staffing changes, and a stale name is
  worse than none. Refer to the role, and confirm the current person by phone when it matters.
- **Remote and video appearances** — platform, meeting identifier, and link **if published by the
  court**, always subject to the 48-hour rule below
- **Standing and administrative orders** — anything affecting this matter type; note the order's date
  and whether anything more recent supersedes it
- **Case management and discovery** — whether the division issues a standing case management order,
  and if so what deadlines it sets: discovery cutoff, mediation deadline, exchange of witness and
  exhibit lists, pretrial filings
  [CONFIRM LOCALLY: whether a case management order has issued in {{CASE_NO}} specifically — with the
  clerk's docket]
- **Mandatory disclosure handling** — see the dedicated section below
- **General magistrate specifics, if applicable** — see the dedicated section below
- **Emergency and expedited motions** — what the division treats as qualifying, the certification
  required, and the physical or electronic protocol for getting it in front of the officer
  [CONFIRM LOCALLY: emergency motion protocol — with the judicial assistant]

### The 48-hour video-hearing rule — mandatory, no exceptions

**Any detail about a remote or video hearing — platform, meeting ID, passcode, link, dial-in, or
whether the hearing is remote at all — carries a mandatory verification flag, regardless of source.**
This applies even when the detail came directly off the court's own website today, even when it is in
a signed order, and even when the same link worked for a hearing last month.

Emit this with every such detail:

> ⚠️ **VERIFY WITH THE JUDICIAL ASSISTANT WITHIN 48 HOURS OF THE HEARING.** Remote-appearance details
> are reissued without notice and are the single most common cause of a missed appearance. Confirm the
> platform, meeting identifier, passcode, and whether the hearing is remote or in person.
> [CONFIRM LOCALLY: remote appearance details for {{CASE_NO}} — with the judicial assistant]

Never present a link as settled. Never omit the flag because the source looked authoritative.

### Flags that must be raised out loud in the response

- **Stale source** — any source that appears older than 12 months, or undated. Say how old it is and
  recommend confirming with the judicial assistant before filing.
- **Reassignment or retirement** — any indication the officer has moved divisions, retired, left the
  bench, or that the division has been renumbered. Flag it and ask whether to re-run the sequence for
  the current assignee. Do not blend an old officer's procedures with a new assignment.
- **Nothing found** — after the full sequence, say so explicitly, list what was searched, and
  recommend a direct call to chambers rather than guessing. Then fall back only to the Florida Family
  Law Rules of Procedure defaults, labeled as rule defaults rather than as this division's practice.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- **Conflicting sources** — where a divisional procedures page and an administrative order disagree,
  report both, note which is more recent, and flag the conflict for {{ROLE_APPROVER}}. Do not
  silently pick one.

---

## General magistrates and hearing officers

Magistrate practice differs from judicial practice in ways that change deadlines, so it gets its own
handling. Florida Family Law Rule of Procedure 12.490 governs general magistrates.
⚠️ VERIFY: confirm rule and current text before relying on this.

What to establish, in order:

1. **Is there consent or referral?** General magistrate referral in family cases turns on the order
   of referral and on the parties' response to it. Locate the order of referral in {{CASE_NO}} before
   assuming the magistrate has authority over the issue.
   [CONFIRM LOCALLY: whether an order of referral has entered and what it covers — with the clerk's
   docket]
2. **Objection to referral** — the rule provides a window to object to referral to a general
   magistrate, running from service of the order of referral. Calendar it the day the order is seen.
   ⚠️ VERIFY: confirm rule and current text before relying on this.
   [CONFIRM LOCALLY: the objection window and how the division computes it — with the judicial
   assistant]
3. **Recommendation, not a final order** — a general magistrate issues a report and recommendation.
   It does not become an enforceable order until the circuit judge ratifies or adopts it. Never treat
   a recommendation as a final order, and never advise a client that a matter is concluded at the
   recommendation stage.
4. **The 10-day exception window** — Rule 12.490 provides a **10-day** period after service of the
   report and recommendation in which to serve exceptions. This is short, it is the single most
   commonly blown deadline in magistrate practice, and it is measured from service, not from the
   hearing.
   ⚠️ VERIFY: confirm rule and current text before relying on this — including whether the period is
   counted in days or business days, and how service method affects the computation.
   [CONFIRM LOCALLY: the exception period, the required form of exceptions, and whether a hearing on
   exceptions must be separately requested — with the judicial assistant and with {{ROLE_APPROVER}}]
   Operationally: the day a report and recommendation is received, calendar the deadline, notify
   {{ROLE_REVIEWER}} and {{ROLE_APPROVER}} the same day, and open the exceptions question — do not
   wait for the client to raise it.
5. **Transcript** — exceptions practice generally depends on a transcript of the proceeding before
   the magistrate. Order it immediately rather than after deciding to file, because transcript
   turnaround does not stretch to fit the deadline.
   [CONFIRM LOCALLY: whether the division requires the transcript filed with the exceptions, and the
   court reporter arrangements for magistrate hearings — with the judicial assistant]
6. **Hearing officers** — child support hearing officers operate under their own rule and their own
   scheduling and review procedures, distinct from general magistrates. Do not carry magistrate
   procedure across to a hearing officer.
   ⚠️ VERIFY: confirm rule and current text before relying on this.

---

## Mandatory disclosure handling

Rule 12.285 mandatory disclosure obligations are set by rule and apply regardless of division.
⚠️ VERIFY: confirm rule and current text before relying on this.

What this skill contributes is the **division layer** on top of the rule — because divisions vary on
what they add, and that variation is what gets missed:

- **The rule sets the baseline.** Which documents are required, and the timing measured from service
  of the initial pleading, come from the rule and not from the judge.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- **Divisions layer on top.** Some divisions add case-management-order deadlines that run earlier than
  the rule's timing, require a certificate confirming service of disclosure, require the financial
  affidavit filed rather than only served, or require disclosure completion before a hearing can be
  set or before mediation.
  [CONFIRM LOCALLY: whether the division adds disclosure deadlines, requires a compliance
  certificate, and requires the financial affidavit filed — with the judicial assistant]
- **Filing versus serving is division-sensitive.** Whether a document is filed with the clerk or only
  served on {{OPPOSING_COUNSEL}} is not uniform across the state, and getting it backwards creates
  either a confidentiality problem or a compliance gap.
  [CONFIRM LOCALLY: filing versus service treatment for each disclosure item — with the clerk of
  court in {{COUNTY}} County]
- **Simplified, waived, or limited procedures.** Some case types and some agreements alter the
  disclosure obligation. Confirm what applies in {{CASE_NO}} before producing or demanding anything.
  [CONFIRM LOCALLY: whether disclosure has been waived or limited in this matter — with
  {{ROLE_APPROVER}}]
- **Hand-off.** **If a discovery or disclosure suite is installed,** hand the actual document
  inventory, naming, and compliance tracking to it — this skill supplies the deadlines and the
  division requirements, not the document handling. **If it is not installed,** produce a plain dated
  list of what the rule requires, what has been served, and what is outstanding, and mark every gap
  as a gap. Route client-facing collection through {{UPLOAD_PORTAL}} and log the work in
  {{PM_SYSTEM}}.

Never state a disclosure deadline as a bare date without identifying what it was computed from.

---

## Step 4 — Apply it to the whole session without being asked again

Once an officer and division are identified and verified in this session, apply what was found to
everything else in the session without re-prompting:

- **Drafting** — correct caption for {{COUNTY}} County and {{CIRCUIT}} Judicial Circuit, correct
  division designation, required certifications, cover sheet, page limits, proposed-order format and
  submission method. Signature block from {{ATTORNEY_NAME}}, {{BAR_NO}}, {{FIRM_NAME}},
  {{FIRM_ADDRESS}}, {{FIRM_PHONE}}, {{FIRM_EMAIL}}.
- **Deadlines** — case management order dates, discovery cutoffs, disclosure deadlines, conferral
  timing, mediation prerequisites, and any magistrate exception window. Calendar each in
  {{PM_SYSTEM}} with the source it came from.
- **Scheduling** — the division's actual method, the coordination expected with
  {{OPPOSING_COUNSEL}}, and the 48-hour remote-appearance verification flag on anything remote.
- **Filing and storage** — file work product to {{DMS}} through the session's file connector
  abstraction. Never assume a local path, drive letter, or synced-folder location.

**Hearing prep checklist** — auto-generate at the end of any hearing-related discussion:

> **Hearing prep — {{CLIENT_NAME}} · {{CASE_NO}} · {{JUDGE}}, Division {{DIVISION}} · {{COUNTY}}
> County, {{CIRCUIT}} Judicial Circuit · prepared {{DATE}}**
> - [ ] Confirm the matter is on the docket
> - [ ] Verify remote or courtroom details with the judicial assistant within 48 hours ⚠️ mandatory
> - [ ] Exchange exhibits per the division's rules — [CONFIRM LOCALLY: exhibit exchange deadline and
>       format, including whether digital exhibits are required — with the judicial assistant]
> - [ ] Submit any required proposed order in advance, in the required format
> - [ ] Witness list, if the hearing is evidentiary — [CONFIRM LOCALLY: witness list deadline]
> - [ ] Court reporter arranged, if required or advisable
> - [ ] Interpreter or accommodation request, if needed — [CONFIRM LOCALLY: request lead time]
> - [ ] Client arrival time, attire, and meet location; or remote-appearance instructions
> - [ ] Confirm who is appearing for {{OPPOSING_COUNSEL}}
> - [ ] *one line per division-specific item surfaced by the live search*
> Prepared by {{ROLE_DRAFTER}} · reviewed by {{ROLE_REVIEWER}} · cleared by {{ROLE_APPROVER}}

**Two officers in one session:** if more than one officer is relevant — a judge and a general
magistrate on the same case, two judges across two matters, or a reassignment mid-session — track
each separately, search each separately, and **label every output by officer name and division** so
nothing is attributed to the wrong courtroom. Never merge findings into one summary. Before switching
which officer is being discussed, state the switch explicitly and confirm it. If a division has been
reassigned, the outgoing officer's procedures do not carry over — re-run Step 2 for the incoming
officer.

---

## Hard rules

- **Never record a real officer or judicial-assistant name into a reference file, template, or reusable
  output.** Names go stale, and a judge's name paired with a client matter re-identifies the matter.
  Use {{JUDGE}} in reusable content; a live search result may name the officer in the session's
  response, but it does not get written into the reference files.
- **Never fabricate.** No invented notice periods, no assumed proposed-order format, no guessed
  judicial-assistant contact, no reconstructed URL. A gap is stated as a gap.
- **Never cite case law in this skill's output.** Statutes, rules, and administrative orders only,
  each with `⚠️ VERIFY: confirm rule and current text before relying on this.` If caselaw is needed,
  route to the caselaw protocol skill.
- **Never emit** `Click here to enter text.` or `XXXXXXXX`. Unknown values are tokens or
  `[CONFIRM LOCALLY: ...]` flags.
- **Nothing is filed or served from this skill.** {{ROLE_DRAFTER}} prepares, {{ROLE_REVIEWER}}
  reviews, {{ROLE_APPROVER}} approves and files. Log the work in {{PM_SYSTEM}}.

---

## Keeping this skill honest

This skill is only as good as its habit of searching. See `references/how-this-works.md` for what is
expected of the person using it, and `references/circuit-starter-example.md` for a worked
starting-point example — one circuit, used purely as an illustration of the note-taking pattern — that
should be maintained exactly the way any other circuit's notes would be.

`references/fl-circuit-map.md` maps all 20 Florida judicial circuits to their counties and gives a
starting URL for each. It contains no officer-specific information by design.
