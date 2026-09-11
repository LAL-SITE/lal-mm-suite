---
name: lal-output-standards
description: "Output format standards for every deliverable. Use whenever a skill produces an Excel, PDF, or Word file to confirm correct format and structure. Sets format only - never redirects work."
---

## When to use this skill (full trigger reference)

{{FIRM_NAME}} output format standards for every deliverable, in any environment. Use whenever a skill produces a file — Excel, PDF, or Word — to confirm the output is in the correct format with the correct structure. Triggers on: "what format should this be," "produce the deliverable," "export this," "build the chart," "generate the report," or any task ending in a file. This skill sets FORMAT ONLY. It never routes, gates, or redirects work to a different environment — per the environment-flexible convention, the task is completed wherever it was started.


## {{FIRM_NAME}} Firm-Wide Conventions (apply to every run of this skill)

These six conventions govern all {{FIRM_NAME}} skills and override any narrower instruction
below that conflicts with them.

1. **Environment-flexible.** Complete the task in the environment you are already in
   — chat, Desktop, or Cowork. If a different environment would be materially better,
   say so in one line and keep working. Never block, never redirect, never hand off
   instead of doing the work.
2. **Identity over lanes.** Staff assignments in this skill are defaults, not gates.
   Anyone may run any skill. **Attorneys self-approve** — if the person running this
   skill is {{ROLE_APPROVER}}, they *are* the approving attorney. Never tell an attorney to
   route their own work to an attorney for approval. Approval gates mean an approving-
   attorney action is recorded, not that the user must go find someone.
3. **Just run it.** Prerequisite stages are soft checks, never hard gates. Pause only
   for a physically necessary input, and ask for that specific item by name — never
   "complete Stage X first."
4. **Read files first.** Search the entire matter file — including misnamed and
   misfoldered documents — before declaring anything missing. If the file is
   disorganized, offer a file-organizer cleanup rather than reporting a gap.
5. **Transcripts preferred, never required.** A typed memo or rough notes always
   suffice as input.
6. **Write to the command center.** Every stage completion, deadline, lifecycle move,
   and attorney flag is written to the matter's command center before the run ends.

---

# {{FIRM_NAME}} Output Standards

## Purpose

This skill does three things:

1. **Routes tasks** — determines whether the task belongs in Cowork or must go to Claude.ai
2. **Governs output format** — every deliverable produced in Cowork follows strict file output rules
3. **Generates handoff packages** — when a task must go to Claude.ai, produces a complete paste-ready briefing so nothing is lost

---


## Output Format Rules (Non-Negotiable)

Every deliverable produced in Cowork must be saved as an actual file and the download link must appear inline in chat. No exceptions. The user must never have to hunt through folders to find output.

### Excel Output Rules

Use when the deliverable is a chart, tracker, or data grid (gap chart, crosscheck chart, ED chart, income analysis, discovery tracker, etc.).

**Formatting standards:**
- File name format: `[CaseName]_[StageName]_[YYYY-MM-DD].xlsx`
- Tab name: short descriptor (e.g., "Gap Chart", "ED Chart", "Tracker")
- Row 1: Title block — Case name, stage, date, "INTERNAL WORK PRODUCT — ATTORNEY REVIEW REQUIRED"
- Row 2: Blank spacer
- Row 3+: Column headers in bold, frozen
- Alternating row shading: white / light gray (#DDDDDD)
- Header row fill: {{FIRM_NAME}} Signature Pink (#FF1F8E), white text, bold
- Column widths: auto-fit to content, minimum 15 characters wide
- All currency fields: formatted as `$#,##0.00`
- All date fields: formatted as `MM/DD/YYYY`
- No merged cells in data rows (merged cells break sorting)
- Freeze top row always

**After saving:** Present the file path inline:
`📊 Excel ready: [filename] — [click to download]`

### PDF Output Rules

Use for every memo, summary, report, stage output, and internal work product. PDF is produced for EVERY deliverable — even when Excel is also produced.

**{{FIRM_NAME}} Branded PDF Header (apply to every PDF):**

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[COLOR BAR: Pink #FF1F8E | Orange #FF6B00 | Lime #C8D400 | Teal #00B5B8]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

{{FIRM_NAME}}
Internal Work Product — Confidential — Attorney Review Required

Document: [Document Title]
Matter:   [Case Name]
Date:     [Current Date]
Prepared: [Stage Name / Task]
```

**PDF Body:**
- Font: Arial 11pt body, Arial 13pt bold section headings
- Section headings: ALL CAPS, bold, color Signature Pink (#FF1F8E) or black
- Page numbers: bottom center, format `- X -`
- Footer every page: `{{FIRM_NAME}}  •  Confidential  •  [Document Name]  •  Page X of Y`
- Footer separator: four-color bar (Pink → Orange → Lime → Teal), 4pt height

**Required closing block on every PDF:**
```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
⚠️  AI-GENERATED WORK PRODUCT
This document was produced with AI assistance. It has not been reviewed or
approved by a licensed attorney. Do not file, serve, share with clients, or
use in any legal proceeding without full attorney review and sign-off.
All facts, figures, dates, and legal characterizations must be independently
verified before reliance.
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**File name format:** `[CaseName]_[StageName]_[YYYY-MM-DD].pdf`

**After saving:** Present the file path inline:
`📄 PDF ready: [filename] — [click to download]`

### When Both Excel and PDF Are Produced

Present both links together immediately after saving:
```
📊 Excel ready: [filename.xlsx] — [click to download]
📄 PDF ready:   [filename.pdf]  — [click to download]
```

Do not bury the links in a paragraph. They go at the top of the response summary, before any explanatory text.

---


## Session Wrap

At the end of every Cowork session, automatically produce a session summary:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
SESSION SUMMARY — [Case Name] — [Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

FILES PRODUCED THIS SESSION:
[List every file with name and format]

STAGES COMPLETED:
[List every stage run with one-line finding]

COMMAND CENTER UPDATES WRITTEN:
[Stages, deadlines, lifecycle moves, and attorney flags logged this session]

OPEN ITEMS / NEXT STEPS:
[What still needs to be done]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

Save this summary as: `[CaseName]_SessionSummary_[YYYY-MM-DD].pdf`
Present as: `📋 Session summary: [filename] — [click to download]`

---

## Standing Rules — Output Quality

1. **Never produce a Word document in Cowork.** All .docx output goes to Claude.ai. No exceptions.

2. **Never leave output buried in a folder.** Every file gets a presented download link in chat, immediately after it is saved. Always.

3. **Never skip the PDF.** Even when Excel is produced, PDF is also produced. Every time.

4. **Never skip the AI disclosure block.** The closing AI-generated work product warning appears on every PDF, every time.

5. **Never advance a stage without confirming the prior stage is complete.** If the user jumps ahead, flag it and ask to confirm before proceeding.

6. **Never draft legal strategy.** This skill, and all skills run through it, produce internal work product only. Flag issues for attorney review — do not resolve them.

7. **Always check for a judge name.** The moment any judge, GM, hearing officer, division number, or county appears in the session — even in an uploaded document — the lal-judicial-procedures skill fires automatically. Cowork is not exempt from this rule.

---

## OUTPUT DELIVERY — FIRM STANDARD (v2, {{DMS}}-native)

All output from this skill is delivered through `lal-file-connector` (Operation 4).

**Destination:** `Notes/` in the {{DMS}} matter folder
`Last, First - [Matter Type] (####-####)`. There is no `CLAUDE OUTPUT` folder and
no {{DMS}} path. (`GAL Notes/` on GAL matters.)

**Filename:** `MM.DD.YY - LastName - DocTitle - v1.ext` — versioned, never overwritten.

**Delivery depends on where this skill is running:**

- **Claude.ai (chat / Projects)** — Claude cannot write to {{DMS}}. Present the file
  as a **download** and print the destination block: matter folder → `Notes/`, filename,
  version. Never write "saved to {{DMS}}."
- **Cowork (desktop)** — write to the folder designated for the session (ask once at
  first delivery, reuse thereafter), confirm the **actual path written**, and state
  where the file belongs in {{DMS}}.

Nothing is filed or sent without attorney sign-off. Time is tracked in {{PM_SYSTEM}},
including Claude-assisted work.

