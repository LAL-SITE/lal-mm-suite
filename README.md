# LAL Mastermind — AI Paralegal Skills

**Publisher:** Legal Authority Lab — legalauthoritylab.com
**Plugin name:** `lal-mm-ai-paralegal-skills`
**Version:** 1.0.0
**Audience:** enrolled members of the Legal Authority Lab Mastermind program

This is a reduced, "starter" edition of the full Legal Authority Lab Florida
family law skill suites: one basic path through a case — intake,
financial-discovery intake, core drafting with prefiling QC, case roadmap,
and case closing — plus the Core Foundation layer every LAL suite depends
on. It is provided as part of your Mastermind enrollment. See `LICENSE` for
the terms.

## What's included — 24 skills

**Core Foundation (16 skills)** — installer, file connector, start-case,
command center, brand kit, correspondence, caselaw protocol, help, file
organizer, judicial procedures, Florida ethics, document intake rules,
draft versioning, exemplar library, filing status rules, integrity rules.

**Financial Discovery — intake only (1 skill)** — `lal-financial-intake`.
This is the intake step only, not the full discovery pipeline (no tracker,
QC gates, deep-scan, or ED chart — those ship with the full Financial
Discovery Core suite).

**Drafting — Core (5 skills)** — `lal-drafting-core`, `lal-finalize-draft`,
`lal-output-standards`, `lal-pleading-standard`, `lal-prefiling-qc`. Basic
notices, motions, and proposed orders with the firm's prefiling QC gate.
Advanced drafting (dissolution, modification, paternity, injunctions) ships
with the full Drafting Advanced suite.

**Roadmap & Case Management (2 skills)** — `lal-case-roadmap`,
`lal-case-closing`. Tracks case status through a controlled close with an
attorney-approval hard stop.

## What's NOT included

Mediation & settlement, GAL, research, contempt/enforcement, name change,
prenup/postnup, and trial systems are not part of this edition, nor are
`lal-customize` (skill forking) and `lal-firm-adaptation` (overlay
learning) — those ship with a full suite license. Every skill in this
edition degrades gracefully if a full-suite skill it can optionally hand off
to isn't installed; nothing here errors on a missing suite, it just stops at
the edge of what's included.

## Installing

1. In Claude (Cowork), go to your plugin/skill install settings and upload
   the zip for this edition as a plugin (folder structure: this repo's root
   `.claude-plugin/plugin.json` plus its `skills/` folder — do not unzip and
   re-zip only the `skills/` folder, the plugin manifest must stay at the
   zip's top level alongside it).
2. In a new conversation, say **"Run the LAL installer."** It verifies the
   install, builds your Firm Profile (your firm name, attorneys, bar
   numbers, systems — stored in your own document storage, never inside the
   skills), and initializes your matter command center.
3. Download the companion **LAL Mastermind Reference Sources** zip into your
   own document storage and tell the installer where you put it — skills
   that cite reference material (brand kit, correspondence, caselaw
   protocol, drafting, financial intake) look for it there.

## Reference sources

Ships as a separate zip, `lal-mm-reference-sources-v1.0.0.zip`, indexed
against exactly the 24 skills above (see its own `INDEX.md`). Keeping
references out of this plugin zip keeps plugin sync fast, matching the
convention used across every Legal Authority Lab suite.

## Support

Questions about this edition go through the Mastermind program, not general
LAL suite support.
