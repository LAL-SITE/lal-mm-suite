---
name: lal-document-intake-rules
description: "Ambient rule: fires whenever any PDF or scanned document is read, reviewed, renamed, sorted, or used for feedback. Requires OCR verification before feedback; unreadable files must be reported."
---

# {{FIRM_NAME}} Document Intake Rules (Ambient)

## When to use this skill (full trigger reference)

AMBIENT FIRM-WIDE RULE for {{FIRM_NAME}}. Fires automatically whenever ANY PDF is read, reviewed, summarized, audited, renamed, sorted, cross-checked, or used as the basis for feedback in any {{FIRM_NAME}} session — no request needed. Triggers on any task involving PDF documents, scanned documents, discovery documents, bank statements, tax returns, pleadings, or uploaded client files. Governs OCR-before-feedback and unreadable-file reporting. Never give feedback on a PDF that has not been OCR-verified.

These rules apply to EVERY task in ANY {{FIRM_NAME}} session that touches a PDF or scanned document. They are not optional and require no prompt from the user.

## Rule 1 — OCR every PDF before giving feedback

Before providing ANY feedback, summary, analysis, audit result, rename, categorization, or cross-check based on a PDF:

1. Attempt to extract text from the PDF.
2. If the PDF has no text layer or the text layer is garbled/incomplete, run OCR on it (e.g., `ocrmypdf` or equivalent available tooling) before reading.
3. Verify the extracted text is coherent — spot-check that names, dates, and dollar amounts extracted are actual readable values, not OCR garbage.
4. Only THEN proceed with the substantive task.

Never summarize, audit, or rename a PDF based on filename alone, partial extraction, or assumptions about its contents.

## Rule 2 — List every unreadable file

At the end of any task involving multiple documents, include a section titled **"Files That Could Not Be Read"** listing:

- Exact filename and folder location
- Why it failed (password-protected, corrupted, image quality too poor for OCR, unsupported format, cloud-only file that failed to download, etc.)
- Recommended fix (request a new copy from client, ask {{ROLE_DRAFTER}} for the password, rescan at higher resolution, etc.)

If every file was readable, state: "All files were read successfully." Never silently skip an unreadable file. Never guess at the contents of a file that could not be read.

## Rule 3 — Unexpected results require suggestions

If the outcome of any document task differs from what was expected — fewer documents than the tracker says, a statement period missing, a category with zero documents, totals that do not reconcile, duplicates, or documents that do not match the matter — do not just report the discrepancy. Always add a **"Suggestions"** section with concrete next steps (e.g., "the Chase statements for Mar–May 2025 are missing; suggest checking FILED DOCUMENTS - Client for misfiled copies, then adding to the deficiency list for {{ROLE_DRAFTER}}").
