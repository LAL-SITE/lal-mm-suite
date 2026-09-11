---
name: lal-finalize-draft
description: "Final production step for court documents. Use after QC to produce the filing-ready Word and matching PDF - firm formatting enforced, internal notes stripped. Never runs on a blocked draft."
---

# {{FIRM_NAME}} Finalize Draft — Production Step

## When to use this skill (full trigger reference)

{{FIRM_NAME}} final production step for any court document. Takes an approved draft and produces the filing-ready Word document AND a matching PDF, with formatting forced to firm standard and every internal artifact stripped. Runs after lal-prefiling-qc and before attorney signature. Triggers on: "finalize the draft," "finalize this," "make it filing ready," "clean it up for filing," "produce the final," "give me the Word and PDF," "strip the notes and highlights," "format this for filing," "ready to sign," "final version," "make the PDF," or any request to convert a working draft into the document that will actually be filed or served. Enforces portrait orientation, Times New Roman 12, all black, single spacing, one-inch margins, and the {{FIRM_NAME}} caption layout. Always checks lal-judicial-procedures for the assigned judge or division before producing output. Never runs on a draft the QC gate blocked.

## POSITION IN THE SEQUENCE

```
DRAFT  →  lal-prefiling-qc  →  lal-finalize-draft  →  ATTORNEY SIGNATURE  →  FILE / SERVE
          (mandatory gate)      (this skill)
```

This skill is **production, not review**. It does not judge the document. It makes
the approved draft physically correct and produces the two files that actually
leave the firm: an editable `.docx` and a `.pdf`.

**Hard prerequisite:** `lal-prefiling-qc` must have run and returned CONDITIONAL
or CLEARED. If the verdict was **BLOCKED**, stop and say so — do not finalize a
blocked draft, and do not run the gate's fixes silently to get past it. If no QC
report exists for this document, run the gate first.

---

## STEP 0 — CHECK JUDICIAL PROCEDURES. ALWAYS.

Before producing anything, run `lal-judicial-procedures` live for the assigned
judge, general magistrate, hearing officer, division, circuit, and county.

Judge-specific requirements override the firm default. Look for:
- Proposed order format and whether Word is required alongside PDF
- Cover sheet or coversheet requirements
- Page limits, font or spacing directives in a standing order
- Whether the division requires a specific caption or case-style variation
- Signature-block or certificate-of-service preferences
- e-Portal document-type selection for this filing

If judicial procedures cannot be retrieved, say so plainly and produce output on
the firm default — but flag that the judge's requirements were not confirmed. Do
not guess at a standing order.

---

## STEP 1 — FORMATTING STANDARD (NON-NEGOTIABLE)

| Element | Standard |
|---|---|
| Orientation | **Portrait. Always.** No landscape, ever, on a court document. |
| Font | Times New Roman, 12-point |
| Color | All black. No colored text anywhere. |
| Line spacing | **Single**, 0 pt before, 0 pt after |
| Alignment | Left only in the body — never justified |
| Margins | One inch on all four sides |
| Format | Editable `.docx` — plus a `.pdf` of the same document |
| Prohibited | Bullet points · horizontal or divider lines · dashes or underscores as separators · shaded boxes · decorative formatting · tables unless the attorney approved one |

---

## STEP 2 — CAPTION LAYOUT

```
        IN THE CIRCUIT COURT OF THE ELEVENTH          ← centered
        JUDICIAL CIRCUIT IN AND FOR
        MIAMI-DADE COUNTY, FLORIDA

                                    CASE NO.: [####]  ← right justified
                                    DIVISION: [##]

JANE DOE,                                             ← left justified
        Petitioner,
and
JOHN DOE,
        Respondent.
______________________________________/               ← rule line, ends in slash

        PETITION FOR DISSOLUTION OF MARRIAGE           ← centered, BOLD, ALL CAPS
```

Rules:
- Court and county block **centered**
- Case number and division **right justified**, sitting beside/below the court block
- Party names and role designations **left justified**
- A rule line immediately under the second party, terminating in `/`
- Document title **centered, bold, all caps**, directly beneath the rule line
- **Petitioner and Respondent only.** Never Husband, Wife, Mother, Father, or a
  client's first name unless the case style genuinely supports it
- Party names identical to the caption in every occurrence throughout the document

---

## STEP 3 — NUMBERING HIERARCHY

```
I.      SECTION HEADING              ALL CAPS, bold, Roman numerals
1.      Numbered paragraph           Arabic, continuous through the document
        a.   Sub-paragraph           lowercase letters
             i.   Sub-sub-paragraph  lowercase roman
```

Paragraph numbering runs continuously across sections — it does not restart at
each Roman numeral. Never use bullets at any level.


---

## STEP 4 — STRIP EVERY INTERNAL ARTIFACT

Under `lal-pleading-standard`, drafts arrive here **correctly formatted and
deliberately highlighted** — notes 🟨, outstanding facts 🟨, alternatives 🟩.
That is the correct draft state, not an error. This step runs only AFTER the
attorney has resolved every flag: picked the alternative, confirmed the facts,
answered the notes. If unresolved 🟩 alternative blocks remain, STOP — that is
an attorney decision not yet made, not something to strip.

Removed automatically — none of this may survive into a filed document:

- Highlighting of any color
- Non-black text — forced to black
- Tracked changes — insertions accepted, deletions dropped
- Comments and comment anchors
- `[DRAFTER NOTE: ...]`, `[INTERNAL NOTE: ...]`, `NOTE TO ATTORNEY`
- `AI INSTRUCTION` blocks
- Clause-bank labels, module letters, template numbering
- `[OPTION A] / [OPTION B]` markers
- `TODO`, HTML comments, code comments

**Reported but never auto-removed: bracketed placeholders.** A blank may be
intentional — a date left open for execution immediately before filing, a
signature line. The script lists every one and a human decides. Finalization
exits with a review-required status when any remain.

---

## STEP 5 — RUN THE BUILDER

```bash
python3 scripts/finalize_pleading.py DRAFT.docx FINAL.docx
```

Exit codes: `0` clean · `2` finalized but placeholders remain, review required.

The script is validated — it enforces every rule above and converts to PDF via
`soffice`. It uses python-docx rather than the Node `docx` library used by the
generation skills, because Node `docx` cannot open an existing file and this step
must read the draft. Generation-from-scratch skills keep using the Node builders.

**Verify visually before releasing.** Render page one and look at it:

```bash
pdftoppm -png -r 100 -f 1 -l 1 FINAL.pdf page
```

Confirm: portrait, caption alignment correct, title centered and bold, no stray
highlighting, nothing colored, rule line ends in a slash.

---

## STEP 6 — PRODUCE BOTH FILES

Every finalization returns **two** files. Never one.

- `MM.DD.YY - LastName - DocTitle - FINAL - v1.docx` — editable, for filing and
  for any judge who requires Word alongside PDF
- `MM.DD.YY - LastName - DocTitle - FINAL - v1.pdf` — the filing copy

Report with both:
- Which judicial procedures were checked, or that they could not be retrieved
- Artifact lines removed
- Placeholders still outstanding
- Caption elements reformatted
- Confirmation the PDF was visually verified

---

## HARD STOPS

Do not produce final output when:

- `lal-prefiling-qc` returned **BLOCKED**
- The gate has not run on this document at all
- Any caselaw citation remains unverified by the attorney
- Bracketed placeholders remain and no one has confirmed they are intentional
- The document title cannot be identified — a pleading without a title is not a
  pleading
- Judicial procedures were required and could not be checked, on a filing where
  the judge has a known standing order

Finalizing is not approving. The attorney still signs.

**Approval behavior:** if the person in the session is an {{FIRM_NAME}} attorney ({{ROLE_APPROVER}} or
{{ROLE_APPROVER}}), her instruction to finalize IS the attorney resolution of flags — proceed
without asking her to approve her own direction. If staff, every unresolved flag
routes to the attorney and finalization waits.

---

## AMBIENT STANDARD — {{FIRM_NAME}} PLEADING FORMAT & DRAFT-STATE RULES

`lal-pleading-standard` governs every court-bound document this skill produces.
Two rules, from the first keystroke:

1. **Format correctly immediately** — portrait, Times New Roman 12 black, single
   spacing 0pt before/after, left aligned, 1" margins, {{FIRM_NAME}} caption (court centered ·
   case/division right · parties left · rule line ending in `/` · title centered
   bold ALL CAPS), numbering I. → 1. → a. → i. continuous. No bullets, no dividers.
   There is no rough-format stage that gets fixed later.
2. **Drafts show their work, highlighted** — attorney notes 🟨, outstanding facts 🟨,
   alternative provisions 🟩 drafted in full. When unclear what the pleading should
   contain, present highlighted ALTERNATIVES — never assume and draft one version
   as if decided. Never strip flags at draft stage; only `lal-finalize-draft`
   strips, after the attorney resolves them.

---

## MANDATORY HANDOFF — PRE-FILING QC GATE

This skill runs **after** `lal-prefiling-qc`, not instead of it. If a draft
arrives here without a QC report, run the gate first and finalize only on a
CONDITIONAL or CLEARED verdict.

```
DRAFT  →  lal-prefiling-qc  →  THIS SKILL  →  ATTORNEY SIGN-OFF  →  FILE / SERVE
```

---

## OUTPUT DELIVERY — FIRM STANDARD (v2, {{DMS}}-native)

All output from this skill is delivered through `lal-file-connector` (Operation 4).
This is the firm-wide standard — it overrides any older save instruction.

**Destination:** `Notes/` in the {{DMS}} matter folder
`Last, First - [Matter Type] (####-####)`. There is no `CLAUDE OUTPUT` folder and
no {{DMS}} path. Once the attorney signs and the document is filed, the stamped
accepted copy goes to `Filed Documents - Client/` and replaces the unstamped version.

**Filename:** `MM.DD.YY - LastName - DocTitle - FINAL - v1.docx` and `.pdf` —
versioned, never overwritten.

**Delivery depends on where this skill is running:**

- **Claude.ai (chat / Projects)** — Claude cannot write to {{DMS}}. Present both
  files as downloads and print the destination block: matter folder → `Notes/`,
  filenames, version. Never write "saved to {{DMS}}." The correct line is
  *"Ready to download — save to `Notes/`."*
- **Cowork (desktop)** — write both files to the folder designated for the session.
  Ask once at first delivery, then reuse it. Confirm the **actual paths written**
  and state where they belong in {{DMS}}.

Nothing is filed or sent without attorney sign-off. Time is tracked in {{PM_SYSTEM}},
including Claude-assisted work.

---

*{{FIRM_NAME}} Internal Skill — Production Layer — runs after the QC gate, before signature*
