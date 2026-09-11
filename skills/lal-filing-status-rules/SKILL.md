---
name: lal-filing-status-rules
description: "Ambient rule: fires whenever filing or service status is stated, logged, or relied on. Folder location is the evidence of status - a draft is never evidence of filing or service."
---

# {{FIRM_NAME}} Filing Status Rules (Ambient)

## When to use this skill (full trigger reference)

AMBIENT FIRM-WIDE RULE for {{FIRM_NAME}}. Fires automatically whenever ANY document's filing or service status is stated, assumed, logged, tracked, or relied on in any {{FIRM_NAME}} session — no request needed. Triggers on: "was this filed," "what's been filed," "is the motion pending," "update the pleading log," "log the filing," "what's on the docket," any command center or tracker update involving a pleading, notice, or order, and any task that reads documents from a matter folder. Core rule: FOLDER LOCATION IS THE EVIDENCE OF STATUS. A document in DRAFTS is a draft — its existence is never evidence of filing or service. Filed status comes only from the filed folders, a file-stamped copy, or the user saying so. Drafts never enter the pleading log and never update the command center as filings.

Applies to every task in every {{FIRM_NAME}} session that touches a pleading, notice,
order, or any court-bound document. No prompt needed.

## Rule 1 — Folder location is the evidence of status

The matter folder structure IS the docket truth map:

| Folder | What a document there means |
|---|---|
| DRAFTS | A draft. Nothing more. NOT filed, NOT served, NOT sent. |
| FILED BUT NOT ACCEPTED | Submitted to the e-portal, pending clerk acceptance — not yet docketed |
| FILED DOCUMENTS - Client | Filed by our side and accepted |
| FILED DOCUMENTS - OP | Filed by the opposing party |
| NOTICES | Notices issued or received — check the caption for direction |
| ORDERS | Entered by the court |
| DISCO - CLIENT / DISCO - OP | Produced in discovery — not filed |
| Correspondence | Sent or received — not filed |

A document's presence in DRAFTS — however final it looks, whatever its filename
says ("Final", "v9", "SIGNED") — is never evidence it was filed or served.
Evidence of filing is exactly one of: (a) a copy in a FILED folder, (b) a
file-stamped or e-portal-confirmed copy, or (c) the user stating it was filed.

## Rule 2 — Drafts never enter the pleading log or command center as filings

- The command center's pleading log records FILED, SERVED, and RECEIVED documents
  only. A draft is logged, if at all, only as a stage note ("draft in attorney
  review") — never as a docket event.
- When logging any document, state the evidence: folder location, stamp, or user
  statement. If the only evidence is a draft in DRAFTS, say so and ask.
- If the same document appears in DRAFTS and in a FILED folder, the FILED copy
  governs; flag any content differences between the two immediately.

## Rule 3 — Status transitions update the command center

Every observed transition writes a command center event, with its evidence:
draft → submitted (FILED BUT NOT ACCEPTED) → accepted (FILED) → served;
notice issued/received; order entered. Response deadlines start from the
transition, not from the draft date. If a document sits in FILED BUT NOT
ACCEPTED longer than the clerk's normal turnaround, flag it.

## Rule 4 — Never infer, always verify

Before any statement like "the motion is pending" or "the answer was filed":
check the folders. If the folders and the tracker disagree, report the conflict
with both pieces of evidence and route to {{ROLE_REVIEWER}} — never pick one
silently.
