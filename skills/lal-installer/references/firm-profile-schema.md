# Firm Profile / firm-config Schema

One object. Born in Phase 0, written by every phase after, read by
`lal-installer` at install. "What is still missing" is always answerable by
looking for empty fields.

Every field carries a source and a status:
- `confirmed` — the firm said it in writing, or it was observed in their files
- `inferred` — LAL's read, needs confirmation at install
- `empty` — not yet gathered; feeds the gap sheet

---

## Structure

```yaml
meta:
  firm_short:              # sync path segment — keep short
  profile_version:
  last_updated:
  engagement_type:         # suite_only | suite_plus_coaching

contract:                  # Phase 0, from the contract read
  signed_date:
  systems: []
  coaching_retainer:
  discount_tier:
  add_on_window_ends:
  knowledge_base:
  free_bonus:
  ethics_workflow:

identity:                  # Jotform + Phase 0
  firm_name:
  attorney_names: []
  bar_numbers: {}
  offices: []
  website:

paths:                     # Phase 4, captured live — never hard-coded
  lal_shared_path:         # local sync of LAL'S SharePoint client folder.
                           # LAL deliverables + profile ONLY. Nothing of theirs.
  matter_root_path:        # THEIR storage. Read during sweeps, never copied
                           # into lal_shared_path.
  knowledge_root_path:     # theirs
  template_root_path:      # theirs
  access_mode:             # per path: local_sync | connector — the sweeps
                           # run differently depending on which

stack:                     # Jotform declares, Phase 4 verifies
  pm_system:               # {{PM_SYSTEM}}
  dms:                     # {{DMS}}
  research_provider:       # {{RESEARCH_PROVIDER}}
  storage:                 # resolves the storage-agnostic connector
  connectors_live: []
  transcription:

staff:                     # Jotform authoritative — not observable in files
  - name:
    role:
    functions: []          # drafter | reviewer | approving_attorney |
                           # client_contact | intake
    approval_authority:

brand_voice:               # Sweep 1
  archetype:
  secondary_archetype:
  sentence_rhythm:
  vocabulary_preferred: []
  vocabulary_avoided: []
  client_address_mode:
  always_phrases: []
  never_phrases: []
  exemplar_sentences: []

user_voice:                # Sweep 2, one block per attorney
  - attorney:
    openings: {}           # by recipient type
    closings: {}
    formality_gradient: {}
    signature_block:
    characteristic_constructions: []
    bad_news_pattern:
    pushback_pattern:
    length_norms:
    avoids: []

format_spec:               # Sweep 3 — the highest-value block
  caption_block:
  page_setup:
  typography:
  heading_conventions:
  paragraph_numbering:
  signature_block:
  certificate_of_service:
  footer:
  exhibit_conventions:
  idiosyncrasies: []
  consistency_notes: {}
  per_buyer_masters_needed: []   # default empty — spec applied to LAL masters

workflow:                  # Sweep 4
  matter_types: []
  sequences: {}
  role_assignments: {}
  approval_points: []
  bottlenecks: []
  folder_taxonomy:
  naming_convention:       # pattern — file organizer adopts this, not the LAL default
  naming_compliance_notes:

knowledge:                 # Sweep 5
  inventory: []
  documented_processes: []
  firm_rules: []
  conflicts: []
  gaps: []
  contradicts_observed: []

templates:                 # Sweep 6
  inventory: []
  clause_library: {}       # tokenized
  stale: []
  missing_families: []
  competing_versions: []

jurisdiction:              # Jotform
  circuits: []
  counties: []
  judges: []
  divisions: []

conflicts:                 # Sweep 7
  - field:
    self_reported:
    observed:
    adopted:
    confirm_at_install:    # true | false

install:                   # Phase 8
  date:
  plugins_installed: []
  verification_matter:     # de-identified reference
  verification_result:
  open_items: []
```

---

## Token map

The installer substitutes these from the profile. Project schema is curly.

| Token | Source field |
|---|---|
| `{{FIRM_NAME}}` | `identity.firm_name` |
| `{{ATTORNEY_NAME}}` | `identity.attorney_names` |
| `{{BAR_NO}}` | `identity.bar_numbers` |
| `{{PM_SYSTEM}}` | `stack.pm_system` |
| `{{DMS}}` | `stack.dms` |
| `{{RESEARCH_PROVIDER}}` | `stack.research_provider` |
| `{{CLIENT_NAME}}` | runtime |
| `{{CASE_NO}}` | runtime |
| `{{JUDGE}}` | runtime |
| `{{OPPOSING_COUNSEL}}` | runtime |

## Delimiters — interchangeable

Both `{{TOKEN}}` and `[TOKEN]` resolve. Format masters carry bracket style,
content specs and this schema carry curly, and neither has to be converted.

**The rule that makes this safe: substitution matches the closed token list
above, in either delimiter. It never matches "any delimited word."**

That constraint is load-bearing, not tidiness. Bracketed text already carries a
different meaning across the library — drafting skills deliberately leave
`[PLACEHOLDER]` in a draft to mark something unconfirmed that a human is
supposed to fill in before filing. A substitution pass that grabs anything in
brackets would either blank those out or fill them with the wrong value, and
the failure is silent: the draft looks complete and is not.

So:
- `[FIRM_NAME]` — on the list, substituted
- `{{FIRM_NAME}}` — on the list, substituted
- `[HEARING DATE — CONFIRM WITH JA]` — not on the list, left exactly as-is
- `[PLACEHOLDER]` — not on the list, left exactly as-is

Adding a token means adding it to the list here. A token that appears in a
skill file but not in this schema does not resolve, which is the correct
failure — visible, not silent.

**Emit curly.** Anything newly written by a sweep or a content spec uses
`{{CURLY}}`. Bracket support exists so the existing format masters keep working
without a conversion pass, not as a second style to write in.

---

## What must never appear in this file

- Client names, matter names, case numbers from the buyer's files
- Copies of buyer documents
- Sales commentary or the Slack dossier
- Credentials of any kind

The profile is de-identified by construction. If a review finds any of the
above, the sweep that produced it gets re-run rather than the file getting
patched — a leak in the output means a leak in the process.


---

## Buyer-side additions (v1.1)

Where the profile lives on the firm's system: the firm's own storage (admin or
knowledge root) or the firm's Claude Project — never inside an installed skill
(installed plugins are read-only on the firm's side).

Two fields the buyer-side flow adds:

```yaml
paths:
  overlay_folder:          # where lal-firm-adaptation writes overlays
                           # default: "LAL OVERLAYS/" under the admin root
  reference_library_path:  # firm's downloaded copy of lal-reference-library
                           # (master guide, example bank, cleaned templates);
                           # skills reach it through the file connector

customizations:            # maintained by lal-customize
  - derivative:            # e.g. bj-lal-drafting-core
    base:                  # e.g. lal-drafting-core
    base_version:          # plugin version forked from
    route:                 # firm_repo | org_skill
    date:
```

Baked vs. runtime: install-time identity tokens are normally BAKED into the
firm's private marketplace repo by LAL before handoff. The profile remains the
runtime authority for paths, staff functions, overlay locations, and any token
the bake missed (which the installer reports to LAL as a gap).
