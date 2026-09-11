# Brand Kit Intake Fields

Every field the installer must collect before `lal-brand-kit` can produce
output. Collect in this order. **No field has a shipped default value except
where a default is explicitly named below** — the skill supplies structure, the
buyer supplies content.

Legend for **Required**: `HARD` = the skill refuses to draft without it.
`SOFT` = the skill drafts and emits a marked gap. `DEFAULT` = a shipped
structural default the buyer may override.

---

## Group 1 — Identity (8 fields)

| # | Field | Token | Required | Notes |
|---|---|---|---|---|
| 1 | Practice name, exactly as it should appear | `{{FIRM_NAME}}` | HARD | |
| 2 | Signing attorney name, with post-nominal | `{{ATTORNEY_NAME}}` | HARD | |
| 3 | Florida Bar number | `{{BAR_NO}}` | HARD | Rendered only over an attorney's name |
| 4 | Mailing address | `{{FIRM_ADDRESS}}` | HARD | |
| 5 | Phone | `{{FIRM_PHONE}}` | HARD | |
| 6 | Email | `{{FIRM_EMAIL}}` | HARD | |
| 7 | Website, as displayed | `{{BRAND_WEBSITE}}` | SOFT | Omit the line if blank; never invent |
| 8 | Tagline | `{{BRAND_TAGLINE}}` | SOFT | Omit if blank |

## Group 2 — Roles (4 fields)

Collect role labels, not job titles. The skill never writes a title into
output.

| # | Field | Token | Required |
|---|---|---|---|
| 9 | Who drafts | `{{ROLE_DRAFTER}}` | HARD |
| 10 | Who reviews before advancing | `{{ROLE_REVIEWER}}` | HARD |
| 11 | Who approves anything leaving the practice | `{{ROLE_APPROVER}}` | HARD |
| 12 | Who handles intake | `{{ROLE_INTAKE}}` | HARD |

## Group 3 — Systems (4 fields)

Collect these so the skill can reference a system without naming a vendor in
output. Graceful degradation: if a system is not in use, the buyer answers
"none" and the skill drops every step that depends on it rather than
substituting another.

| # | Field | Token | Required |
|---|---|---|---|
| 13 | Practice management / matter system of record | `{{PM_SYSTEM}}` | HARD |
| 14 | Document management | `{{DMS}}` | SOFT |
| 15 | Client document upload channel | `{{UPLOAD_PORTAL}}` | SOFT |
| 16 | Legal research provider | `{{RESEARCH_PROVIDER}}` | SOFT |

## Group 4 — Colour (11 fields)

Eight role colours plus three bar settings. Collect one hex per role. The
installer must confirm contrast: any colour used behind
`{{BRAND_COLOR_PAPER}}` CTA text must carry enough contrast to remain legible
in monochrome print.

| # | Field | Token | Required |
|---|---|---|---|
| 17 | Primary | `{{BRAND_COLOR_PRIMARY}}` | HARD |
| 18 | Secondary | `{{BRAND_COLOR_SECONDARY}}` | HARD |
| 19 | Accent 1 | `{{BRAND_COLOR_ACCENT_1}}` | HARD |
| 20 | Accent 2 | `{{BRAND_COLOR_ACCENT_2}}` | HARD |
| 21 | Ink | `{{BRAND_COLOR_INK}}` | HARD |
| 22 | Paper | `{{BRAND_COLOR_PAPER}}` | HARD |
| 23 | Muted / secondary text | `{{BRAND_COLOR_MUTED}}` | HARD |
| 24 | Rule / border | `{{BRAND_COLOR_RULE}}` | HARD |
| 25 | Colour bar segment order | `{{BRAND_COLOR_BAR_ORDER}}` | DEFAULT | Default: primary → secondary → accent 1 → accent 2 |
| 26 | Colour bar segment count | `{{BRAND_COLOR_BAR_SEGMENTS}}` | DEFAULT | Default: 4 |
| 27 | Colour bar print height | `{{BRAND_COLOR_BAR_HEIGHT}}` | DEFAULT | Default: a thin rule, not a band |

## Group 5 — Typography (21 fields)

Font families (5):

| # | Field | Token | Required | Notes |
|---|---|---|---|---|
| 28 | Word-processor family | `{{BRAND_FONT_WP}}` | HARD | Choose one present on every device in the practice |
| 29 | HTML display family | `{{BRAND_FONT_DISPLAY}}` | SOFT | Falls back if unavailable |
| 30 | HTML heading family | `{{BRAND_FONT_HEADING}}` | SOFT | |
| 31 | HTML body family | `{{BRAND_FONT_BODY}}` | SOFT | |
| 32 | Fallback stack, ending in a generic family keyword | `{{BRAND_FONT_FALLBACK_STACK}}` | HARD | Required because email clients strip web fonts |

Word-processor scale (8):

| # | Field | Token | Required |
|---|---|---|---|
| 33 | Display title size | `{{WP_SIZE_DISPLAY}}` | DEFAULT |
| 34 | Section heading size | `{{WP_SIZE_HEADING}}` | DEFAULT |
| 35 | Sub-label size | `{{WP_SIZE_SUBLABEL}}` | DEFAULT |
| 36 | Body size | `{{WP_SIZE_BODY}}` | DEFAULT |
| 37 | Table text size | `{{WP_SIZE_TABLE}}` | DEFAULT |
| 38 | Caption / footer size | `{{WP_SIZE_CAPTION}}` | DEFAULT |
| 39 | CTA text size | `{{WP_SIZE_CTA}}` | DEFAULT |
| 40 | Body line spacing | `{{WP_LINE_SPACING}}` | DEFAULT |

HTML scale (8):

| # | Field | Token | Required |
|---|---|---|---|
| 41 | Display size | `{{HTML_SIZE_DISPLAY}}` | DEFAULT |
| 42 | Heading size | `{{HTML_SIZE_HEADING}}` | DEFAULT |
| 43 | Body size | `{{HTML_SIZE_BODY}}` | DEFAULT |
| 44 | Small-print size | `{{HTML_SIZE_SMALL}}` | DEFAULT |
| 45 | Button label size | `{{HTML_SIZE_BUTTON}}` | DEFAULT |
| 46 | Display weight | `{{HTML_WEIGHT_DISPLAY}}` | DEFAULT |
| 47 | Heading weight | `{{HTML_WEIGHT_HEADING}}` | DEFAULT |
| 48 | Body line height | `{{HTML_LINE_HEIGHT}}` | DEFAULT |

## Group 6 — Voice (7 fields)

| # | Field | Token | Required | Notes |
|---|---|---|---|---|
| 49 | House voice archetype — one ID from A–F | `{{VOICE_ARCHETYPE}}` | HARD | See `voice-archetypes.md` |
| 50 | Always-phrases, verbatim | `{{VOICE_ALWAYS_PHRASES}}` | SOFT | Conflicts with the eight rules are flagged, not silently dropped |
| 51 | Never-phrases, verbatim | `{{VOICE_NEVER_PHRASES}}` | SOFT | Applied as a hard filter before delivery |
| 52 | Promise set — name plus one-line gloss each | `{{PROMISE_SET}}` / `{{PROMISE_N_NAME}}` / `{{PROMISE_N_GLOSS}}` | SOFT | Reject any promise that predicts a result |
| 53 | Heading case convention | `{{HEADING_CASE}}` | DEFAULT | Buyer picks one and it holds everywhere |
| 54 | Maximum sentences per client-facing paragraph | `{{PARA_MAX_SENTENCES}}` | DEFAULT | Default: 4 |
| 55 | Closing salutation | `{{CLOSING_SALUTATION}}` | HARD | Collect one per register the buyer uses; the formal paper of record and the warm client email should not share one |

## Group 7 — Calls to action (7 fields)

| # | Field | Token | Required | Notes |
|---|---|---|---|---|
| 56 | CTA 1 label — lowest commitment | `{{CTA_1_LABEL}}` | HARD | |
| 57 | CTA 1 destination | `{{CTA_1_DESTINATION}}` | HARD | Never invented at draft time |
| 58 | CTA 2 label — paid or mid commitment | `{{CTA_2_LABEL}}` | HARD | |
| 59 | CTA 2 destination | `{{CTA_2_DESTINATION}}` | HARD | |
| 60 | CTA 3 label — proceed directly | `{{CTA_3_LABEL}}` | HARD | |
| 61 | CTA 3 destination | `{{CTA_3_DESTINATION}}` | HARD | |
| 62 | Plain-text CTA prefix character | `{{CTA_TEXT_PREFIX}}` | DEFAULT | |

If the buyer offers fewer than three commitment levels, collect what exists and
the skill renders that many. It never pads the ladder with an invented step.

## Group 8 — Services (3 fields, two of them repeating per service)

| # | Field | Token | Required | Notes |
|---|---|---|---|---|
| 63 | Full service list, exact names | `{{SERVICE_LIST}}` | HARD | These names are used verbatim everywhere |
| 64 | Per service: name | `{{SERVICE_N_NAME}}` | HARD | |
| 65 | Per service: badge colour role | `{{SERVICE_N_COLOR}}` | HARD | One colour per service, never reassigned |

**Do not accept an estate-planning service into this list unless the buyer
affirmatively offers it as a family law adjacent line and `{{ROLE_APPROVER}}`
confirms it in writing.** The corpus this product derives from does not offer
it and a prior template wrongly implied otherwise.

## Group 9 — Standing text and output settings (4 fields)

| # | Field | Token | Required | Notes |
|---|---|---|---|---|
| 66 | Confidentiality notice, exact text | `{{CONFIDENTIALITY_NOTICE}}` | HARD | Never drafted at run time |
| 67 | Footer left content pattern | `{{DOC_TITLE}}` slot confirmed | DEFAULT | Default: name • Confidential • document title |
| 68 | Operational facts list | `{{OPERATIONAL_FACTS}}` | SOFT | Billing cadence, scope rules, stage map. Rate figures only if the buyer chooses to include them, and copied verbatim from the executed engagement document |
| 69 | Keyword count for long-form posts | `{{POST_KEYWORD_COUNT}}` | DEFAULT | Used by recipe E |

---

## Total: 69 intake fields

Across nine groups: identity 8, roles 4, systems 4, colour 11, typography 21,
voice 7, calls to action 7, services 3, standing text and output settings 4.

## Installer checklist

- [ ] Every HARD field collected. The skill refuses to draft without them.
- [ ] Every SOFT field either collected or explicitly marked "none" — never
      left ambiguous.
- [ ] DEFAULT fields reviewed once; buyer either accepts or overrides.
- [ ] `{{VOICE_ARCHETYPE}}` is a single ID, not a blend.
- [ ] Colour contrast confirmed for CTA text and for monochrome print.
- [ ] Fallback font stack present and ends in a generic family keyword.
- [ ] No estate-planning service in `{{SERVICE_LIST}}` absent written
      approver confirmation.
- [ ] Confidentiality notice text supplied by the practice, not generated.
- [ ] No destination URL in any CTA field that the buyer did not supply.
- [ ] Filing-format standard identified and routed separately — this skill
      does not govern it.
- [ ] File access confirmed through the file connector abstraction only. No
      provider named, no path or site recorded in any intake field.
