---
name: lal-draft-versioning
description: "Ambient rule: fires whenever any draft is produced, revised, or finalized. Enforces the three draft tiers - Attorney Review, Client Review, Final - each independently versioned."
---

# {{FIRM_NAME}} Draft Versioning System (Ambient)

## When to use this skill (full trigger reference)

AMBIENT FIRM-WIDE RULE for {{FIRM_NAME}}. Fires automatically whenever ANY draft document is produced, revised, or finalized in an {{FIRM_NAME}} session — pleadings, agreements, letters, parenting plans, financial affidavits, memos, or any client-facing or court-facing document. Triggers on "draft," "revise," "update the draft," "client version," "final version," "send to the client," "ready for review," or any document production task. Enforces the firm's three working draft tiers: Attorney Review Draft, Client Review Draft, and Final Draft — each independently versioned.

Every substantive draft produced at {{FIRM_NAME}} exists in up to three working versions. Apply this system automatically to every drafting task — do not wait to be asked.

## The three tiers

### 1. Attorney Review Draft
- Full internal working copy.
- Contains highlighted attorney notes, open questions, flagged assumptions, alternative provisions (Option A/B), missing-fact placeholders, and citation verification warnings.
- Never leaves the firm. Saves to DRAFTS.
- Filename: `[Matter]_[DocName]_AttorneyReview_v1.docx` (v2, v3... on each revision).

### 2. Client Review Draft
- Produced only AFTER attorney review, or when explicitly requested.
- Contains NO attorney notes, no internal commentary, no strategy remarks, no alternative-provision discussion.
- The ONLY highlights permitted are for the client's attention, limited to three kinds:
  - **Items the client must note or confirm** (dates, names, amounts)
  - **Options the client must choose between** (stated neutrally, without attorney recommendation)
  - **Missing information the client must supply**
- Before creating this tier, strip every internal artifact from the attorney draft and verify none remain (search for comments, tracked changes, highlighted internal notes).
- Filename: `[Matter]_[DocName]_ClientReview_v1.docx` (versioned independently).

### 3. Final Draft
- Clean, execution- or filing-ready. No highlights, no notes, no placeholders of any kind.
- Produced only after attorney sign-off. If sign-off has not been confirmed in the session, say so and stop before producing a Final.
- Filename: `[Matter]_[DocName]_Final_v1.docx` (+ PDF where required).
- Court documents also pass through lal-prefiling-qc and lal-finalize-draft where those skills exist.

## Rules

1. Each tier is versioned independently — a v3 Attorney draft may feed a v1 Client draft.
2. Never overwrite a prior version; save a new version number.
3. Never skip the Attorney Review tier. A document goes to a client or a court only after an attorney has had a reviewable draft.
4. When asked for "the draft," confirm which tier is wanted if not obvious from context.
5. When converting between tiers, state what was stripped or added so the change is auditable.
6. If a client-facing version is requested but attorney notes cannot be cleanly removed (e.g., substantive gaps remain), flag it back for attorney review instead of sending it forward.
