---
name: lal-pleading-standard
description: "Ambient pleading standard: fires on any court-bound drafting. Court formatting correct from the first keystroke; drafts carry highlighted attorney notes and alternatives until finalized."
---

# {{FIRM_NAME}} Pleading Standard — Ambient Drafting Rules

## When to use this skill (full trigger reference)

AMBIENT FIRM-WIDE PLEADING DRAFTING STANDARD. Fires automatically whenever any {{FIRM_NAME}} skill or session drafts, revises, or extends ANY document destined for a court file — petitions, motions, notices, answers, responses, proposed orders, affidavits, parenting plans, financial affidavits, CS worksheets, certificates, MSAs, discovery documents, GAL court filings. Does NOT apply to correspondence, roadmaps, memos, trackers, or anything never filed. Triggers on any drafting act in those categories, in any project, with or without a drafting skill. Two rules: (1) court formatting is correct from the FIRST keystroke — portrait, Times New Roman 12, single spacing, {{FIRM_NAME}} caption, proper numbering — never "fixed later"; (2) drafts MUST carry highlighted attorney notes, outstanding facts, and alternative provisions — when unsure what a pleading should say, present highlighted alternatives instead of assuming. Stripping happens ONLY at lal-finalize-draft.

## WHY THIS EXISTS

Formatting drift is a persistent, recurring problem across {{FIRM_NAME}} documents. Drafts
come back in the wrong font, wrong spacing, landscape tables, bulleted paragraphs,
captions that don't match the firm layout — and the errors get "fixed at the end,"
which means some survive to filing. This standard ends that: **a pleading is
formatted correctly from the first keystroke.** There is no rough-format stage.

At the same time, a draft is not a final. A draft that hides its open questions is
more dangerous than one that shows them. So this standard enforces **two states**:

| | DRAFT (everything before finalize) | FINAL (`lal-finalize-draft` output) |
|---|---|---|
| Court formatting | ✅ Correct from the start | ✅ Verified and enforced |
| Attorney notes | ✅ **Present and highlighted** | ❌ Stripped |
| Outstanding facts | ✅ **Bracketed and highlighted** | ❌ Resolved or expressly left blank |
| Alternative provisions | ✅ **Both shown, highlighted** | ❌ One selected by the attorney |
| Highlights | ✅ Required on every flag | ❌ None |

**Never strip notes, flags, or alternatives at the draft stage.** That is
finalize's job, and only after the attorney has resolved them. A drafter or skill
that quietly deletes a flag to make a document look cleaner has destroyed the
attorney's decision points.

---

## SCOPE

**Applies to** anything that will or may be filed with a court or served in a
proceeding: petitions · supplemental petitions · motions · notices · answers and
responses · proposed orders and judgments · affidavits · parenting plans ·
financial affidavits · child support worksheets · certificates of compliance ·
MSAs and settlement agreements headed for incorporation · discovery requests and
responses · GAL motions, orders, and reports filed with the court · injunction
packets · prenups and postnups (formal instruments — same discipline).

**Does NOT apply to** correspondence · client letters and emails · case memos ·
roadmaps · trackers · internal analyses · how-to guides · marketing · anything
that will never sit in a court file. Those follow `lal-brand-kit` or their own
skill's format.

If unsure which bucket a document falls in, ask one question: *could this end up
in the court file?* If yes or maybe, this standard applies.

---

## RULE 1 — FORMAT CORRECTLY FROM THE FIRST KEYSTROKE

Every draft, from its very first version, uses:

- **Portrait. Always.** No landscape on any court document, including exhibits
  and worksheets, unless the attorney expressly directs otherwise.
- **Times New Roman, 12-point, black** for all substantive text
- **Single spacing**, 0 pt before and after paragraphs
- **Left alignment** in the body — never justified
- **One-inch margins** on all four sides
- **No bullets. No divider lines.** No dashes, underscores, or symbols as
  separators. No shaded boxes. No tables unless attorney-approved.
- Output is always an editable **.docx**

### Caption — the {{FIRM_NAME}} layout, on every draft

```
        IN THE CIRCUIT COURT OF THE [##] JUDICIAL       ← centered
        CIRCUIT IN AND FOR [COUNTY] COUNTY, FLORIDA

                                    CASE NO.: [####]    ← right justified
                                    DIVISION: [##]

[PETITIONER NAME],                                      ← left justified
        Petitioner,
and
[RESPONDENT NAME],
        Respondent.
______________________________________/                 ← rule line under 2nd party, ends in /

        [TITLE OF DOCUMENT]                              ← centered, BOLD, ALL CAPS
```

- **Petitioner / Respondent only.** Never Husband, Wife, Mother, Father, or first
  names unless the case style genuinely supports it (§61.30 CS worksheet preserves
  Mother/Father per statute — that is the one standing exception).
- Party names identical to the caption in every occurrence.

### Numbering

```
I.   SECTION HEADING          ALL CAPS, bold, Roman numerals
1.   Numbered paragraph       Arabic, continuous through the whole document
     a.  Sub-paragraph        lowercase letters
         i.  Sub-sub          lowercase roman
```

Paragraph numbers never restart at a new section.

---

## RULE 2 — DRAFTS SHOW THEIR WORK, HIGHLIGHTED

A draft going to the attorney must make every open item **impossible to miss**.
Use highlighting — actual document highlighting, not just brackets — on each:

- **🟨 YELLOW — outstanding facts.** Anything unverified or unconfirmed:
  `🟨[CONFIRM: date of separation — client intake says March, petition draft says April]`
- **🟨 YELLOW — attorney notes.** Questions, risks, judgment calls:
  `🟨[NOTE TO ATTORNEY: OC may argue waiver — see their 5/12 letter]`
- **🟩 GREEN — alternative provisions.** Where the right language depends on a
  decision not yet made, draft **both** in full, highlighted, clearly labeled:

  ```
  🟩[ALTERNATIVE A — if seeking exclusive use of the marital home:]
  12. Petitioner requests exclusive use and possession of the marital
      residence located at [ADDRESS] pending final hearing.

  🟩[ALTERNATIVE B — if home will be listed for sale:]
  12. The parties shall immediately list the marital residence for sale,
      with net proceeds held in trust pending equitable distribution.
  ```

In python-docx, that is `run.font.highlight_color = WD_COLOR_INDEX.YELLOW` /
`BRIGHT_GREEN`. In the Node builders, `highlight: "yellow"` / `"green"` on the
run. If a generation path cannot highlight, the bracket labels alone are the
minimum — but highlighting is the standard.

### The alternatives rule — never assume

**When you are unclear what a pleading should contain, present alternatives.
Do not pick one and hope.** This applies to:

- Relief that depends on a strategy call not yet made
- Facts the file supports two readings of
- Provisions that turn on information the client hasn't provided
- Anything where two competent drafters could reasonably write it differently

A wrong guess drafted confidently reads as a decision and gets filed. Two
highlighted alternatives read as a question and get answered. The attorney
deletes one at review; nothing is lost. Guessing loses cases; alternatives cost
one decision.

**Silence is the failure mode this rule kills.** A missing provision, a smoothed
ambiguity, an assumption presented as fact — all worse than a draft that visibly
asks. If the draft is 80% certain, it still flags the 20%.

---

## HOW THE STATES INTERACT WITH THE PIPELINE

```
DRAFT (formatted + highlighted flags)
   → lal-prefiling-qc          verifies flags are HIGHLIGHTED and visible,
                                verifies formatting, blocks on critical findings
   → ATTORNEY resolves flags    picks alternatives, confirms facts, answers notes
   → lal-finalize-draft        strips highlights/notes/alternatives, emits Word + PDF
   → ATTORNEY SIGNATURE → FILE
```

The QC gate does **not** treat a highlighted note on a draft as a violation — it
treats an UN-highlighted note, or an assumption where an alternative belongs, as
one. Artifacts are a violation only in a document represented as final.

---

## FOR SKILLS AND SESSIONS ALIKE

This standard is ambient: it binds ad-hoc drafting in any chat exactly as it
binds the drafting skills. "Quickly draft a motion for continuance" in a random
session gets the same caption, the same font, the same highlighted flags as
`lal-drafting-advanced` would produce. There is no informal tier of pleading.

---

*{{FIRM_NAME}} Internal Skill — Ambient Layer — binds all court-document drafting firm-wide*
