---
name: lal-exemplar-library
description: "Ambient rule: fires when a template can't be found or output is rejected despite following the skills. Search the firm exemplar library for real exemplars and retry; strip prior-client facts."
---

# {{FIRM_NAME}} Exemplar Library Fallback (Ambient)

## When to use this skill (full trigger reference)

AMBIENT FIRM-WIDE RULE for {{FIRM_NAME}}. Fires whenever a template, form, or exemplar cannot be found, AND whenever the user says output is not right even though skills and templates were followed. The firm exemplar library ({{TEMPLATE_LIBRARY}}) holds ALL firm trainings, old matters, and templates — search it for real exemplars, use them as the reference for structure, language, and format, then try again. Old-matter documents are exemplars for FORM only: strip all prior-client facts. Triggers on: "that's not right," "this doesn't look like ours," "wrong format," "template is missing," "can't find the template," or any rejected output after skill compliance. Turns rejection into a retry-with-evidence loop instead of a dead end.

Extends Rule 1 of lal-integrity-rules. Applies in every {{FIRM_NAME}} session, no prompt needed.

## The library

The **firm exemplar library ({{TEMPLATE_LIBRARY}})** holds ALL of the firm's trainings, old matters, and templates:

{{TEMPLATE_LIBRARY_LINK}}

Access via the firm document-storage connector ({{DMS}}), or the synced local folder when mounted.

## When this fires

1. A template, form, master, or exemplar cannot be found — search the library BEFORE declaring it missing.
2. The user says the output is not right even though the governing skill, template, and format rules were followed — the firm's real documents are the ground truth the skills approximate. Find one and match it.

## Protocol

1. Search the library for real examples of the document type: prior filed version, training exemplar, or firm template. Search by document type, matter type, and filename patterns; check template folders AND old-matter folders.
2. Use what is found as the reference for structure, language, formatting, and conventions — then produce the corrected output and state which exemplar was used and what changed.
3. **Old-matter documents are exemplars for FORM only.** Strip and replace every party-specific fact with the current matter's facts or [BRACKETED PLACEHOLDERS]. Never let a prior client's data leak into new work product.
4. If the library search also comes up empty, apply lal-integrity-rules Rule 1: stop, report exactly what was searched, and ask. Never fabricate.

## The loop

Comply with the skill → output rejected or template missing → find the firm's real exemplar → conform and retry → report the exemplar used. Never a dead end, never an invitation to invent.
