# Deadline Authorities — Florida Family Law

Reference for populating `deadlines[]` objects. For each entry: the authority that creates the
deadline, what it runs from, the computation basis, whether it is jurisdictional, and whether it
can be enlarged.

**This is not legal advice and it is not authority.** It is a starting point for a computation a
human performs and verifies. Rules amend on independent cycles and saved copies go stale.

**Every entry below carries the verify warning. It is not decoration — reproduce it wherever the
deadline is displayed.**

**No case law appears in this file, by rule.** Rules and statutes only.

**Subdivision policy.** Where the sources reviewed do not support a subdivision letter, the entry
reads `<rule number> — subdivision unconfirmed` and carries a `[CONFIRM LOCALLY: ...]` marker. A
rule number is **never inferred, reconstructed, or "corrected" by analogy to a neighbouring rule.**
A flagged uncertainty is the correct output here; a confidently wrong citation in a deadline table
is the worst defect this file could carry. The **periods** in this file are better sourced than the
**subdivision letters**, and the two are flagged separately for that reason.

---

## HOW TO USE THIS FILE

1. Find the trigger. If the triggering **date** is unknown, stop: write the deadline with
   `dueDate: null` and `status: "uncomputable"`, plus a flag. Never estimate.
2. Copy the authority string into `deadlines[].authority` verbatim, including any subdivision
   caveat noted here.
3. Apply the counting rules in § 1, then write what you actually did into `computationBasis` —
   not the period, the counting.
4. Carry `jurisdictional` and `extendable` from the entry.
5. An order that sets a date **controls over any rule default below.** Cite the order as the
   authority. `[CONFIRM LOCALLY: the assigned judge's written procedures and any standing or
   administrative order, with {{ROLE_APPROVER}}]`

---

## 1. THE COUNTING RULES

Time computation is not in the family rules. Fla. Fam. L. R. P. 12.090(a) delegates it to
Fla. R. Gen. Prac. & Jud. Admin. 2.514.

⚠️ VERIFY: confirm rule and current text before relying on this.

| Situation | Rule as recorded in source | Authority |
|---|---|---|
| Period of **7 days or longer** | Begin counting the next day that is not a Saturday, Sunday, or legal holiday; count every intervening day including weekends and holidays; include the last day unless it is a Saturday, Sunday, or legal holiday, in which case roll forward | Fla. R. Gen. Prac. & Jud. Admin. 2.514(a)(1) |
| Period of **less than 7 days** | Saturdays, Sundays, and legal holidays are not counted at all | 2.514(a)(2) |
| Period stated in **hours** | Counting begins immediately on the triggering event; all hours count; a period ending on a weekend or legal holiday runs to the same time on the next qualifying day | 2.514(a)(3) |
| **Backward-counted** periods ("at least 10 days before the hearing") | The "next day" is determined by counting backward | 2.514(a)(5) |
| **Last day ends** | 11:59:59 p.m. Eastern for electronic filing or service by any means; for non-electronic filing, when the clerk's office is scheduled to close | 2.514(a)(4) |
| **Service by mail only** | Add 5 days. Nothing is added for portal service. | 2.514(b) |
| **Legal holiday** | The days set by § 110.117, Fla. Stat., **plus** any day observed as a holiday by the clerk's office or designated by the chief justice or chief judge | 2.514(a)(6) |

⚠️ VERIFY: confirm rule and current text before relying on this.

`[CONFIRM LOCALLY: the assigned clerk's published holiday calendar, loaded annually, with
{{ROLE_INTAKE}}]` — clerk-observed closures count as legal holidays and are the most common
source of a quietly wrong last day.

**Days added for e-mail service is unsettled in the sources.** One source records that 5 days
are added only where service is by mail alone; another records a committee note stating e-mail
service is treated as mail for computation. These cannot both be operative.
`[CONFIRM LOCALLY: whether any days are added for e-service, with {{ROLE_APPROVER}}]` — resolve
before writing any deadline whose `serviceMethod` is `email`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Enlargement is barred outright for some deadlines.** Fla. Fam. L. R. P. 12.090(b) permits
enlargement before expiry for cause, or after expiry on excusable neglect — but **not** for a
motion for new trial, rehearing, to alter or amend a judgment, for relief under 12.540(b), for
taking an appeal or filing a certiorari petition, or for a directed verdict. Deadlines in that
set are written with `extendable: "no"` and `jurisdictional: "yes"`.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 2. THE CLOCK STARTERS

**Deadlines run from service, not filing.** Establish the service date and method from the source
document before computing anything.

| Method | Date established by | Completion | Authority |
|---|---|---|---|
| Personal service of process | Returned and filed return of service | On service | — |
| Portal e-service | Portal service notification | Complete **on filing** | Fla. R. Gen. Prac. & Jud. Admin. 2.516(b)(1) |
| E-mail, not filed | The sent e-mail | Complete **when sent** | 2.516(b)(2)(C) |
| Mail | Mailing | Complete on mailing; add 5 days | 2.516(b)(3)(C); 2.514(b) |
| Hand or commercial delivery | Delivery date | Day of delivery | 2.516(b)(3)(C) |
| Waiver of service | Filed waiver | Service deemed effected 20 days before the response is due | Fla. Fam. L. R. P. 12.070 — subdivision unconfirmed |

⚠️ VERIFY: confirm rule and current text before relying on this.

**Every `12.070` subdivision reference in this file is unconfirmed, and they are treated the same
way.** An earlier version of this table asserted `12.070(k)(4)` for waiver of service while § 3
hedged between `12.070(j)` and `12.070(l)` for the service window. One file cannot be both certain
and uncertain about subdivisions of one rule, so no `12.070` subdivision letter is asserted
anywhere here. The periods are consistent across sources; the subdivision letters are not.
`[CONFIRM LOCALLY: the current 12.070 subdivision letter for waiver of service before citing it in
any filing, with {{ROLE_REVIEWER}}]`
⚠️ VERIFY: confirm rule and current text before relying on this.

Where a vendor serves but does not file the return, the deadline chain breaks silently. Track who
files it.

---

## 3. PLEADING AND SERVICE DEADLINES

**Service of process outside date — 120 days**
Authority: Fla. Fam. L. R. P. 12.070. **Subdivision uncertain**: sources in the corpus cite both
`12.070(j)` and `12.070(l)` for the 120-day window. The period is consistent at 120 days in both.
`[CONFIRM LOCALLY: the current subdivision letter before citing in any filing, with
{{ROLE_REVIEWER}}]`
Runs from: filing of the pleading directed to a respondent.
Basis: 120 days, calendar-day counting, last day rolls forward.
Jurisdictional: `yes` — on expiry the court must direct service by a date certain, dismiss
without prejudice, or drop the party. Extendable: `yes`, for good cause or excusable neglect.
Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Response to petition — 20 days**
Authority: Fla. Fam. L. R. P. 12.140(a)(1).
Runs from: service of original process and the initial pleading. Or the date fixed in a notice by
publication.
Basis: 20 days, calendar-day counting, last day rolls forward; add 5 if served by mail alone.
Jurisdictional: `yes` — grounds not raised are waived and a default becomes available.
Extendable: `only-before-expiry` in the ordinary case; a party may plead at any time **before** a
default is entered. Owner: `{{ROLE_APPROVER}}`; `{{ROLE_DRAFTER}}` prepares.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Response to counterpetition or crosspetition — 20 days**
Authority: Fla. Fam. L. R. P. 12.140(a)(1). Counterpetitions are served through the e-portal; no
new summons issues.
Runs from: service of the counterpetition or crosspetition.
Basis: as above. Jurisdictional: `yes`. Extendable: `only-before-expiry`.
Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Responsive pleading after a 12.140(b) motion is denied or deferred — 10 days**
Authority: Fla. Fam. L. R. P. 12.140(a)(2).
Runs from: notice of the court's action.
Basis: 10 days, calendar-day counting, last day rolls forward.
Jurisdictional: `yes`. Extendable: `only-before-expiry`. Owner: `{{ROLE_DRAFTER}}` →
`{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Responsive pleading after a more definite statement is ordered — 10 days**
Authority: Fla. Fam. L. R. P. 12.140(a)(2). Runs from: service of the more definite statement.
Basis: 10 days, calendar-day counting. Jurisdictional: `yes`. Extendable:
`only-before-expiry`. Owner: `{{ROLE_DRAFTER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Response to an amended pleading — 10 days**
Authority: Fla. Fam. L. R. P. 12.190(a), unless the court orders otherwise.
Runs from: service of the amended pleading. Basis: 10 days, calendar-day counting.
Jurisdictional: `no`. Extendable: `yes`. Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Action at issue — 20 days**
Authority: Fla. Fam. L. R. P. 12.440 — subdivision unconfirmed.
`[CONFIRM LOCALLY: confirm which subdivision of Rule 12.440 governs this deadline, with
{{ROLE_REVIEWER}}]`
Runs from: service of the last pleading, where no
motions are directed to it. Basis: 20 days, calendar-day counting. Jurisdictional: `no` — it is a
readiness marker, not a forfeiture. Extendable: not applicable. Owner: `{{ROLE_REVIEWER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 4. MANDATORY DISCLOSURE

**Subdivision caveat for the whole of Rule 12.285.** The sources reviewed for this file disagree
about the subdivision lettering of 12.285, and the rule has been renumbered on its own amendment
cycle. **The periods below are consistent across sources; the subdivision letters are not, and no
subdivision letter in this section is asserted.** Treat every `12.285(...)` below as unconfirmed.
`[CONFIRM LOCALLY: the current 12.285 subdivision letter for each period before citing it in a
filing, with {{ROLE_REVIEWER}}]`
⚠️ VERIFY: confirm rule and current text before relying on this.

**Mandatory disclosure served — 45 days**
Authority: Fla. Fam. L. R. P. 12.285(b)(2). **Subdivision conflict in the sources**: one source
places the 45-day period at 12.285(d), which in the rule text reviewed addresses disclosure for
temporary financial relief. The 45-day period itself is consistent across sources.
`[CONFIRM LOCALLY: the current subdivision letter before citing in a filing, with
{{ROLE_REVIEWER}}]`
Runs from: service of the initial pleading on the respondent.
Basis: 45 days, calendar-day counting, last day rolls forward.
Jurisdictional: `no`, but consequential — documents not served within the rule's periods before a
nonfinal hearing, or in violation of a pretrial order, are **inadmissible** at that hearing
absent a good-cause finding (12.285(g)). Extendable: `yes` — by agreement, or by a motion to
enlarge filed **before** the due date, which the court must grant for good cause (12.285(h)).
Owner: `{{ROLE_DRAFTER}}` with the client contact.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Objection to mandatory disclosure — at least 5 days before the due date**
Authority: Fla. Fam. L. R. P. 12.285(i).
Runs backward from: the disclosure due date.
Basis: fewer than 7 days — weekends and legal holidays are **not counted**; count backward.
Jurisdictional: `yes` — a late objection is **waived**. Extendable: `only-before-expiry`; the
court may permit an untimely objection for good cause. Owner: `{{ROLE_APPROVER}}` — whether to
object at all is an attorney decision, and meritless objections carry a mandatory-sanctions risk.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Temporary financial relief hearing — party seeking relief — at least 10 days before**
Authority: Fla. Fam. L. R. P. 12.285(b)(1)(A). Runs backward from: the hearing.
Basis: 10 days, calendar-day counting, counted backward. Jurisdictional: `no`, but late
documents are inadmissible absent good cause. Extendable: `unknown` — treat as no.
Owner: `{{ROLE_DRAFTER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Temporary financial relief hearing — responding party not seeking relief — at least 5 days
before**
Authority: Fla. Fam. L. R. P. 12.285(b)(1)(B). Runs backward from: the hearing.
Basis: fewer than 7 days — weekends and legal holidays not counted; counted backward.
Jurisdictional: `no`, same admissibility consequence. Owner: `{{ROLE_DRAFTER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Certificate of compliance — on service of disclosure**
Authority: Fla. Fam. L. R. P. 12.285(j); Florida Supreme Court Approved Form 12.932.
Runs from: service of the mandatory disclosure. No numeric period; the obligation attaches to the
service event. It is sworn, must identify the documents with particularity, and must certify the
service date. Jurisdictional: `no`. Owner: `{{ROLE_DRAFTER}}` drafts; `{{ROLE_APPROVER}}` signs
and files. Confirm the current form version on the official forms index before use.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Child support guidelines worksheet — at or before the hearing**
Authority: Fla. Fam. L. R. P. 12.285(k); Form 12.902(e). Runs backward from: the hearing to
establish or modify support. Jurisdictional: `yes` in effect — the requirement cannot be waived.
Extendable: `no`. Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Continuing duty to supplement — no fixed date**
Authority: Fla. Fam. L. R. P. 12.285(f). Trigger: any material change in financial status.
Write this as a deadline object with `dueDate: null` and `status: "open"`, `notes` recording that
the duty is continuing. It is the one legitimate open-ended entry in the register.
Owner: client contact → `{{ROLE_DRAFTER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Financial affidavit in enforcement or contempt — 10 days**
Authority: Fla. Fam. L. R. P. 12.287. Runs from: written request. Basis: 10 days, calendar-day
counting. Serve the affidavit and file the notice of compliance. Jurisdictional: `no`.
Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 5. DISCOVERY

**Interrogatory answers — 30 days, or 45 for a respondent**
Authority: Fla. Fam. L. R. P. 12.340(c). Runs from: service of the interrogatories; a
**respondent** may take 45 days from service of process and the initial pleading.
Basis: 30 or 45 days, calendar-day counting, last day rolls forward; add 5 if served by mail
alone. Record in `computationBasis` **which posture you used and why** — the two are not
interchangeable. Jurisdictional: `no`. Extendable: `yes`, by agreement or order.
Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Response to request to produce — 30 days, or 45 for a respondent**
Authority: Fla. Fam. L. R. P. 12.350(b). Runs from: service of the request; respondent or
third-party defendant, 45 days from service of process. Basis: as above. Jurisdictional: `no`.
Extendable: `yes`. Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Response to request for admission — 30 days, or not required before 45 for a respondent**
Authority: Fla. Fam. L. R. P. 12.370(a)(3), (b).
Runs from: service of the request; a respondent is not required to respond before 45 days after
service of process. Basis: as above.
Jurisdictional: **`yes`. `selfExecuting: true`.** Miss the window and the matter is **admitted
and conclusively established** — no motion by the other side is required.
Extendable: `yes` before expiry; after expiry, relief requires a motion to withdraw or amend the
admission. Owner: `{{ROLE_APPROVER}}`.
Write this one with a flag at creation, not on approach.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Notice of intent to subpoena documents from a nonparty — at least 10 days before issuance**
Authority: Fla. Fam. L. R. P. 12.351(b). 15 days if served by mail.
Runs backward from: issuance of the subpoena. Basis: 10 or 15 days, calendar-day counting,
counted backward. Any party's objection inside the same window blocks production pending
resolution. Jurisdictional: `no`. Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_REVIEWER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Assertion of privilege after inadvertent disclosure — `[CONFIRM LOCALLY: the applicable period, with {{ROLE_APPROVER}}]`**
Authority: **Fla. R. Civ. P. 1.285.** There is no Rule 12.281 in the Family Law Rules; an earlier
version of this entry cited one and it does not exist. The inadvertent-disclosure provision is a
**civil** rule, so its reach into a family proceeding is not settled on the face of the family
rules.
`[CONFIRM LOCALLY: whether and how this provision applies in a family law proceeding in your
circuit, with the presiding judge's chambers]`
Runs from: actually discovering the disclosure. Basis: calendar-day counting. The sources reviewed
for this file record a **10-day** period; that figure is **not verified here** and is not asserted
— compute nothing until the period is confirmed against current rule text.
Jurisdictional: `unknown` — treat as yes and flag. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Motion to compel — no deadline, but a gate**
Authority: Fla. Fam. L. R. P. 12.380(a)(1)–(2). No fixed period. Must be on reasonable notice
**and must include a good-faith conferral certification.** Record as a deadline object only where
an order or a strategic date makes it time-bound; otherwise it is a task, not a deadline. Whether
the conferral certification can honestly be made is an `{{ROLE_APPROVER}}` decision.
Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 6. CASE MANAGEMENT, MEDIATION, MAGISTRATES

**Request for a case management conference — 30 days after service**
Authority: Fla. Fam. L. R. P. 12.200(a)(1). Runs from: service of the petition. A party **may**
request after 30 days. Jurisdictional: `no`. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Notice of pretrial conference — 20 days**
Authority: Fla. Fam. L. R. P. 12.200(c). Case management conferences require reasonable notice;
pretrial conferences require 20 days. Jurisdictional: `no`. Owner: `{{ROLE_DRAFTER}}` calendars.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Objection to the mediator's compensation rate — 15 days**
Authority: Fla. Fam. L. R. P. 12.740(c)(3). Runs from: the order of referral to mediation.
Basis: 15 days, calendar-day counting. Jurisdictional: `no`. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Mediation completed — 75 days**
Authority: Fla. Fam. L. R. P. 12.740(e), unless the court orders otherwise.
Runs from: the first mediation conference. Basis: 75 days, calendar-day counting.
Jurisdictional: `no`. Extendable: `yes`, by order. Owner: `{{ROLE_REVIEWER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Objection to referral to a general magistrate — 10 days**
Authority: Fla. Fam. L. R. P. 12.490 — subdivision unconfirmed. Rule 12.490 has been amended and
renumbered, and the subdivision letter recorded in the sources cannot be stood behind.
`[CONFIRM LOCALLY: the current 12.490 subdivision letter for the objection period, with
{{ROLE_REVIEWER}}]`
Runs from: service of the order of referral. If the
hearing is set sooner than 10 days, before the hearing begins. If the referral is served within
the first 20 days after process, the window extends to the responsive-pleading due date.
Basis: 10 days, calendar-day counting, with the two alternate outside dates above — record which
one you applied. Jurisdictional: **`yes`. Silence is deemed consent to the referral.**
Extendable: `no`. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Motion to vacate a general magistrate's recommended order — 15 days**
Authority: Fla. Fam. L. R. P. 12.490 — subdivision unconfirmed.
`[CONFIRM LOCALLY: the current 12.490 subdivision letters for the motion-to-vacate, hearing, and
ruling periods, with {{ROLE_REVIEWER}}]`
Runs from: entry of the recommended order.
Cross-motion within 5 days. The motion must be **heard within 30 days of filing**, ruling within
30 days after the hearing, and the movant must seek a hearing date when filing — so write three
linked deadline objects, not one. Jurisdictional: `yes` — review of the recommended order is
otherwise lost. Extendable: `no`. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Exceptions to a special magistrate's report — 10 days**
Authority: Fla. Fam. L. R. P. 12.492 — subdivision unconfirmed.
`[CONFIRM LOCALLY: the current 12.492 subdivision letter for exceptions and cross-exceptions, with
{{ROLE_REVIEWER}}]`
Runs from: service of the report. Cross-exceptions
within 5 days of the filing of exceptions. Basis: 10 days, calendar-day counting; the 5-day
cross-exception period is under 7 days, so weekends and legal holidays are not counted.
Jurisdictional: `yes`. Extendable: `no`. Owner: `{{ROLE_APPROVER}}`.
Do not conflate this with the general-magistrate motion to vacate — different officer, different
instrument, different period.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 7. TRIAL AND ORDER-CREATED DEADLINES

**Trial-order deadlines are the highest-risk category** because they are set by *order*, not by
rule, and vary by judge and division. Cite the order as the authority. Failure to comply
"subjects the party or attorney to appropriate court sanctions" (Fla. Fam. L. R. P. 12.440 —
subdivision unconfirmed).
`[CONFIRM LOCALLY: confirm which subdivision of Rule 12.440 governs this deadline, with
{{ROLE_REVIEWER}}]`
`[CONFIRM LOCALLY: the assigned judge's written procedures and division practice, with
{{ROLE_APPROVER}}]`
⚠️ VERIFY: confirm rule and current text before relying on this.

**No `12.440` subdivision letter is asserted in this section.** An earlier version of this file
gave `12.440(c)` as the authority for **two unrelated deadlines** — the pretrial exchange and the
notice of trial after a default. At most one of those can be right, and the sources reviewed do not
resolve which. The subdivision is therefore flagged on every `12.440` entry rather than guessed at,
and no subdivision letter has been inferred or "corrected."

**Pretrial exchange — 72 hours before the pretrial conference, or 30 days before trial**
Authority: Fla. Fam. L. R. P. 12.440 — subdivision unconfirmed.
`[CONFIRM LOCALLY: confirm which subdivision of Rule 12.440 governs this deadline, with
{{ROLE_REVIEWER}}]`
Reciprocal exchange and filing of documents, witness
list, issues, undisposed motions, and time estimate. Runs backward from the conference or trial —
whichever the order fixes. Basis: 72 hours is an **hours** period (2.514(a)(3)); 30 days is
calendar-day counting; both counted backward. Jurisdictional: `no`, but sanctions and exclusion
of untimely disclosure follow. Owner: `{{ROLE_DRAFTER}}` → `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Notice of trial where a default has been entered — not less than 10 days**
Authority: Fla. Fam. L. R. P. 12.440 — subdivision unconfirmed.
`[CONFIRM LOCALLY: confirm which subdivision of Rule 12.440 governs this deadline, with
{{ROLE_REVIEWER}}]`
Runs backward from trial. Basis: 10 days, calendar-day
counting, counted backward. Owner: `{{ROLE_DRAFTER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Proposed order furnished to all parties — no less than 24 hours before submission**
Authority: Fla. Fam. L. R. P. 12.080 — subdivision unconfirmed — where the court so requires.
`[CONFIRM LOCALLY: the current 12.080 subdivision letter, and whether the assigned division imposes
this requirement at all, with {{ROLE_APPROVER}}]`
Hours period. Owner: `{{ROLE_DRAFTER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Notice for any motion not heard ex parte — a reasonable time before the hearing**
Authority: Fla. Fam. L. R. P. 12.090(c). No numeric period. Owner: `{{ROLE_DRAFTER}}` →
`{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 8. POST-JUDGMENT — THE NON-EXTENDABLE SET

Write every deadline in this section with `jurisdictional: "yes"` and `extendable: "no"`, and
flag each at creation. Rule 12.090(b) expressly forecloses enlargement.

**Motion for new trial or rehearing — not later than 15 days**
Authority: Fla. Fam. L. R. P. 12.530(a), (b). Runs from: return of the verdict, or the filing of
the judgment in a non-jury matter. Required to preserve an appellate challenge to missing findings
of fact. Basis: 15 days, calendar-day counting, last day rolls forward.
Owner: `{{ROLE_APPROVER}}`.
One source in the corpus records a 10-day period for some bases under 12.530; the rule text
reviewed states 15 days in both relevant subdivisions.
`[CONFIRM LOCALLY: the operative period before calendaring, with {{ROLE_APPROVER}}]`
⚠️ VERIFY: confirm rule and current text before relying on this.

**Motion to alter or amend a judgment — not later than 15 days**
Authority: Fla. Fam. L. R. P. 12.530 — subdivision unconfirmed.
`[CONFIRM LOCALLY: the current 12.530 subdivision letter for a motion to alter or amend, with
{{ROLE_REVIEWER}}]`
Runs from: entry of the judgment. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Rehearing or clarification — 15 days**
Authority: Fla. Fam. L. R. P. 12.530. Calendar this at entry of every final judgment, together
with the appeal window, before the closing task is opened. Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Notice of appeal — 30 days from rendition**
Authority: Fla. R. App. P. 9.110; rendition and tolling under Fla. R. App. P. 9.020.
Runs from: rendition of the order. Basis: 30 days, calendar-day counting, last day rolls forward.
Jurisdictional: `yes`. Extendable: `no`. Owner: `{{ROLE_APPROVER}}`.
Whether an authorized motion tolls rendition is an attorney determination — do not compute this
date around a tolling assumption without `{{ROLE_APPROVER}}` confirmation.
⚠️ VERIFY: confirm rule and current text before relying on this.

**Relief from judgment — reasonable time; 1 year for some grounds; no limit for one**
Authority: Fla. Fam. L. R. P. 12.540(b). Within a reasonable time generally; **not more than 1
year** for mistake, excusable neglect, newly discovered evidence, or fraud; and **no time limit**
for motions based on fraudulent financial affidavits in marital or paternity cases.
Runs from: entry of the final judgment, order, or proceeding.
Jurisdictional: `yes`. Extendable: `no` — 12.090(b) bars enlargement.
Owner: `{{ROLE_APPROVER}}`.
⚠️ VERIFY: confirm rule and current text before relying on this.

---

## 9. WHAT IS NOT IN THIS FILE

Marked as gaps rather than filled with values the sources did not support.

- **Injunction and domestic violence timelines.** Not sourced here. Non-DV injunctive relief is
  routed to Fla. R. Civ. P. 1.610 by Fla. Fam. L. R. P. 12.605 — subdivision unconfirmed; DV
  timelines are statutory and locally administered. `[CONFIRM LOCALLY: the applicable injunction
  timelines and the assigned division's procedures, with {{ROLE_APPROVER}}]`
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- **Relocation objection period.** Governed by § 61.13001, Fla. Stat. The specific period is not
  recorded in the sources reviewed for this file and is not stated here rather than guessed.
  `[CONFIRM LOCALLY: the § 61.13001 objection period against current statutory text, with
  {{ROLE_APPROVER}}]`
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- **Name change fingerprinting and background-check timing.** Governed by § 68.07, Fla. Stat.,
  and administered locally. `[CONFIRM LOCALLY: ORI and fingerprint processing timing, with
  {{ROLE_INTAKE}}]`
  ⚠️ VERIFY: confirm rule and current text before relying on this.
- **Emergency motion thresholds and timing.** Set by circuit administrative order and variable.
  One source in the corpus mis-cites a family rule as a civil rule on this point.
  `[CONFIRM LOCALLY: the current administrative order for the assigned circuit, with
  {{ROLE_APPROVER}}]`
- **Civil case-management deadlines.** The Civil Rules impose case-management tracks and initial
  discovery disclosures that the Family Law Rules do not. Do not import them into a family matter.
  `[CONFIRM LOCALLY: whether the assigned circuit has extended civil case-management practice to
  the family division by administrative order, with {{ROLE_APPROVER}}]`
- **Case law.** Excluded by rule. No entry in this file rests on a decision, and none should be
  added.
