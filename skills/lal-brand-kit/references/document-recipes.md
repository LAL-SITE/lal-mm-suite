# Document Structure Recipes

Six output types. Each recipe is an ordered part list plus the archetype the
audience forces. All values are tokens; nothing here supplies content.

**Shared parts vocabulary**

| Part | What it is |
|---|---|
| `BAR` | Colour bar in `{{BRAND_COLOR_BAR_ORDER}}`, `{{BRAND_COLOR_BAR_SEGMENTS}}` segments, `{{BRAND_COLOR_BAR_HEIGHT}}` |
| `IDENT` | `{{FIRM_NAME}}` at `{{WP_SIZE_DISPLAY}}` bold, plus `{{BRAND_TAGLINE}}` in `{{BRAND_COLOR_PRIMARY}}` if supplied |
| `ADDRESS_BLOCK` | Date `{{DATE}}` / To / Re. Re line carries the matter and `{{CASE_NO}}` where one exists |
| `RULE` | Horizontal divider in the colour named by the recipe |
| `BODY` | Written to `{{VOICE_ARCHETYPE}}` under the eight rules |
| `CTA_SET` | The three CTAs, §6 of the skill, fixed ladder order |
| `SIG` | Signature block, §7 |
| `NOTICE` | `{{CONFIDENTIALITY_NOTICE}}`, §8 |
| `FOOT` | Footer, §9 |

**Universal rule:** if a part's token is unfilled, emit the part with a
`[CONFIRM LOCALLY: <what> — with {{ROLE_APPROVER}}]` marker, or omit the part
if omission is safe. Never emit `Click here to enter text.` or `XXXXXXXX`.
Never emit a URL the buyer did not supply.

---

## A. Client emails and letters

**Archetype:** house register — A (Warm Directive) by default; B (Plain-Spoken
Level) where the reader is unrepresented or the document is explanatory.

**Order:** `BAR` → `IDENT` → `ADDRESS_BLOCK` → `RULE` in
`{{BRAND_COLOR_PRIMARY}}` → salutation to `{{CLIENT_NAME}}` → `BODY` →
`CTA_SET` → `SIG` → `NOTICE` → `FOOT`

**Body construction.**
1. One-line statement of why you are writing. Reason before ask.
2. Credit before correction — what arrived and what it made possible.
3. The substance, in short sections with reused scannable heads. Every factual
   bullet dated; every ask deadlined, reasoned, and answerable both ways.
4. Where the practice's advice has changed, say so in the first sentence of
   the relevant section, not buried.
5. Consequence, once, in one short paragraph.
6. Reciprocal commitment — what the practice does next, time-boxed to a
   concrete interval.

**Channel variants.**
- **Letter (attorney-signed):** title-case bold section heads, formal
  `{{CLOSING_SALUTATION}}`, no selective ALL-CAPS emphasis in body text.
- **Portal or plain-text message:** ALL-CAPS section heads, no colour, colour
  bar replaced by a character rule, `{{CTA_TEXT_PREFIX}}` before each CTA
  label. Escalation instruction stated concretely — call the office rather
  than wait on a message.
- **Status update:** cap length so it fits one phone screen in a normal month.
  Honesty about an inactive period is mandatory. Range every outcome. Refer to
  `{{OPPOSING_COUNSEL}}` by role, not by name, in status correspondence.

**Length:** paragraphs capped at `{{PARA_MAX_SENTENCES}}`.

---

## B. Engagement, retainer, and transmittal documents

**Archetype:** E (Protective Declarative) for the fee and scope blocks; A for
the opening and close only. Bookend the warmth.

**Order:** `BAR` → `IDENT` → document title in `{{BRAND_COLOR_PRIMARY}}` →
parties block → scope of representation (`RULE` in
`{{BRAND_COLOR_SECONDARY}}`) → fees and billing → client obligations (`RULE`
in `{{BRAND_COLOR_ACCENT_1}}`) → termination and scope fence → two-column
`SIG` (client left, `{{ATTORNEY_NAME}}` right) → `FOOT`

**Hard rules.**
- Scope and fee language is copied **verbatim** from the executed agreement.
  Never summarised, never restated in friendlier words, never recalculated.
- Name the out-of-scope items explicitly. Do not gesture at limits.
- Show the arithmetic: every fee, credit, payment and balance on its own line.
- Confirm receipt of signature and funds in one sentence, then state matter
  status separately. Never leave payment receipt implied.
- Confirm funds have actually cleared before referencing any figure.
- Time-box every forward commitment with a concrete interval.
- Route questions by type to a role token, not to a person or a title.
- Close with the scope fence: no further work unless a new written agreement
  is signed.
- The transmittal asks the reader for nothing. It removes burden.
- Limited-scope engagements need different scope language **and** a different
  first-week sequence. Never send the full-representation sequence on a
  limited-scope matter.
- No outcome language, no strategy, no legal analysis anywhere in a
  transmittal.
- `CTA_SET` is omitted from executed engagement documents. It may appear in a
  transmittal email.
- No rate figure appears unless it is in `{{OPERATIONAL_FACTS}}` or the
  executed agreement. Otherwise:
  `[CONFIRM LOCALLY: rate and billing cadence — with {{ROLE_APPROVER}}]`

`[CONFIRM LOCALLY: trust-accounting and fee-agreement requirements — with {{ROLE_APPROVER}}]`

> ⚠️ VERIFY: confirm rule and current text before relying on this.
> The Rules Regulating The Florida Bar govern fee agreements, trust
> accounting, and the terms on which a representation may end.

---

## C. Guides, explainers, roadmaps, and workbooks

**Archetype:** B (Plain-Spoken Level), or A where the document is procedural
rather than explanatory.

**Order:** `BAR` → title in `{{HEADING_CASE}}` at `{{WP_SIZE_DISPLAY}}` +
subtitle + `{{BRAND_WEBSITE}}` → full-width `BAR` as a visual break → "what
this covers" list with `{{BRAND_COLOR_ACCENT_2}}` checkmarks → body sections
divided by `RULE` in `{{BRAND_COLOR_SECONDARY}}` → numbered steps where a
process is involved → callout box (left border `{{BRAND_COLOR_PRIMARY}}`,
tinted fill) for anything the reader must not miss → three-column `CTA_SET`
table → `{{BRAND_WEBSITE}}` centred → `FOOT`

**Content rules.**
- Numbered lists for sequence, bulleted lists for inventories. Never mixed in
  one list.
- Tell the reader what is needed *first*, not the whole list as equally
  urgent.
- Range every outcome. Separate advice from decision: the decision is the
  reader's, and say so.
- Explain why a requirement exists, not only that it exists.
- Rules and statutes only, each with `⚠️ VERIFY: confirm rule and current text
  before relying on this.` **No case law.**
- Anywhere a step varies by court, insert
  `[CONFIRM LOCALLY: <the step> — with {{ROLE_APPROVER}}, per {{CIRCUIT}} / {{COUNTY}} / division / {{JUDGE}} / clerk]`
- No estate-planning content, at all.

---

## D. Social captions

**Archetype:** B (Plain-Spoken Level).

**Order:** hook line, no preamble → body in short paragraphs with line breaks
→ takeaway or call-out → single CTA (the ladder does not fit a caption; use
`{{CTA_1_LABEL}}` unless the post is about a paid offering) → hashtags last.

**Rules.**
- Drop the reader into the reality in the first line.
- One idea per paragraph, generous line breaks.
- No prediction, no guarantee, no result claim, no adjective about any party.
- No client facts, ever — not paraphrased, not composited, not "a client I
  once had."
- Distinguish coaching or unbundled offerings from educational products
  explicitly, using the exact `{{SERVICE_N_NAME}}` values.
- Length and emoji policy are buyer settings; the default is no emoji in any
  post that touches a legal proposition.

`[CONFIRM LOCALLY: advertising and solicitation compliance for public content — with {{ROLE_APPROVER}}]`

> ⚠️ VERIFY: confirm rule and current text before relying on this.
> Rules Regulating The Florida Bar, chapter 4, subchapter 4-7, governs
> lawyer advertising and information about legal services.

---

## E. Long-form posts and articles

**Archetype:** B, with A for any procedural section.

**Required sections, in order.** Every one is mandatory; a post missing any is
incomplete.
1. Title
2. Meta title — under 60 characters
3. Meta description — under 155 characters
4. Summary — two to three sentences
5. Keywords — `{{POST_KEYWORD_COUNT}}` terms
6. Image direction — describe the visual; do not source or embed an image
7. Body — H2/H3 structure, intro, sections, practical application
8. `CTA_SET`
9. Bottom line — one paragraph
10. Tags

**Rules.** Same authority rules as C. No case law. Every rule or statute
reference carries the verify warning. No client facts. No estate planning.
Compliance marker as in D.

Introduces one token: `{{POST_KEYWORD_COUNT}}`.

---

## F. Internal-origin documents seen externally

Documents drafted for internal use that a client, counsel, court, or vendor
may end up reading: cover memos, transmittal notes, summaries, intake
confirmations, process one-pagers.

**Archetype:** C (Neutral Procedural), or F (Institutional Limiting) where the
document grants or limits.

**Order:** `BAR` → `IDENT` → subject line → `BODY` → `SIG` → `NOTICE` →
`FOOT`. `CTA_SET` omitted.

**Rules.**
- Write it as if it will be read outside the practice, because it may be.
- No internal shorthand, no casual chat register, no channel-specific slang.
- No staff job titles. Role tokens only.
- Where a document reports on a matter, `{{PM_SYSTEM}}` is the system of
  record and the document defers to it on any conflict.
- No legal analysis. Route analysis to the practice's legal skills.
- A cover memo transmitting a filing is governed by this recipe; the filing
  itself is not governed by this skill at all. Route it.

---

## Pre-delivery checklist — run on every draft

- [ ] Correct recipe and correct archetype for the audience.
- [ ] One register held throughout. No drift.
- [ ] Warmth bookended, not interleaved.
- [ ] Every factual statement dated. Every ask deadlined, reasoned, and
      answerable both ways.
- [ ] No adjective characterising any party's motive.
- [ ] No outcome prediction. Outcomes ranged. Decision assigned to the client.
- [ ] No case law. Every rule or statute carries the verify warning.
- [ ] No estate-planning reference.
- [ ] `{{VOICE_NEVER_PHRASES}}` filter run and clean.
- [ ] Colour bar order matches `{{BRAND_COLOR_BAR_ORDER}}`.
- [ ] `{{BAR_NO}}` present only over an attorney's name.
- [ ] No job titles. Role tokens only.
- [ ] No storage provider, path, site, tenant, or unsupplied URL anywhere.
- [ ] No `Click here to enter text.` and no `XXXXXXXX`.
- [ ] Every unresolved curly token listed in the handoff note, not guessed.
- [ ] `{{ROLE_REVIEWER}}` review before advancing; `{{ROLE_APPROVER}}`
      approval before anything leaves.
- [ ] Work logged in `{{PM_SYSTEM}}`.
