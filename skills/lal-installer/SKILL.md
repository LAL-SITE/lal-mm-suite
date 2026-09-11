---
name: lal-installer
description: "Buyer-side installer. Use when installing or configuring a purchased LAL suite - verifies the org-wide plugin install, builds the Firm Profile, births the command center, runs verification."
---

# LAL Installer — Buyer-Side

## When to use this skill (full trigger reference)

Legal Authority Lab buyer-side installer. Ships in every suite. Use IMMEDIATELY when a firm is installing or configuring a purchased LAL suite. Triggers on: "install the suite," "run the installer," "set up our firm profile," "apply our firm settings," "configure the skills for our firm," "finish the install," "the firm profile is ready," "re-run the installer," or any request to personalize freshly installed LAL skills. Distinct from lal-install (LAL's internal engagement runbook, never shipped).

## How LAL suites are personalized (read first)

LAL skills arrive through the firm's **org-managed plugin marketplace** (a private
GitHub repo synced by the firm's Claude admin). Installed skills are
**read-only** on the firm's side — this installer never edits a skill file.
Personalization happens in two layers instead:

1. **The bake (LAL-side, already done).** Before handoff, LAL substitutes the
   install-time identity tokens ({{FIRM_NAME}}, {{ATTORNEY_NAME}}, {{BAR_NO}},
   {{PM_SYSTEM}}, {{DMS}}, {{RESEARCH_PROVIDER}}, addresses, roles) directly
   into the firm's private repo copy, from the intake questionnaire. If you can
   read a skill and see the firm's real name in it, the bake ran.
2. **The Firm Profile (runtime, this skill's job).** A single firm-config
   document living in the FIRM's own storage — the connected matter/admin
   folder or the firm's Claude Project — that every LAL skill consults for
   anything not baked: paths, staff roles, overlay locations, and any token
   still unresolved. Structure: `references/firm-profile-schema.md`.

## Step 1 — Verify the install

1. Confirm the LAL plugins the firm purchased appear as installed skills in
   this session. List what is present and what is missing.
2. If a purchased suite is missing, the fix is on the admin side, not here:
   the firm's Claude admin syncs the marketplace and sets the plugin to
   "Installed by default" (see the Buyer Runbook shipped with the repo).
   Report exactly which plugin is missing and stop the verification there —
   do not improvise a manual install.

## Step 2 — Locate or build the Firm Profile

Look for the firm-config file (Firm Profile) in the firm's storage or Project.

- **Profile found:** read it. List any fields with status `empty` or
  `inferred` and confirm the inferred ones with the user.
- **No profile:** gather the minimum set interactively, one block at a time —
  identity (firm name, attorneys, bar numbers, address, phone, email, website),
  stack (practice management system, document storage, research provider,
  upload portal), staff roles (who drafts, who reviews, who approves, who
  handles intake), and paths (matter root, template root, overlay folder,
  and the **LAL reference library** — the folder where the firm downloaded
  the `lal-reference-library` repository; if it isn't downloaded yet, point
  the user to the Buyer Runbook step and record the path once it exists).
  Write the answers into a new firm-config in the firm's storage so the next
  run reads instead of asks.
- **Check the bake.** Scan a sample of installed skills for unresolved
  install-time tokens. Any install-time token still showing `{{...}}` goes on
  the gap list with its resolved value from the profile — skills fall back to
  the Firm Profile at runtime for these, and the gap list goes to LAL so the
  next repo update bakes them. Never guess a value.
- Matter-level tokens ({{CLIENT_NAME}}, {{CASE_NO}}, {{JUDGE}},
  {{OPPOSING_COUNSEL}}, {{COUNTY}}, dates, amounts) belong to the attorney at
  draft time — they are never install-time gaps. Leave every
  `[CONFIRM LOCALLY: ...]` and `[PLACEHOLDER]` marker exactly as found.
- Solo/small-firm note: if the person running the installer is the attorney,
  their answers are authoritative; do not ask for anyone's approval.

## Step 3 — Birth the command center and verify

1. Initialize the command center per the installed `lal-command-center` skill
   (create its tracking structure in the firm's configured storage location).
2. Pick ONE real, active matter with the user. Run the suite's primary skill
   on it end to end (e.g., Discovery: intake prep on a real document batch;
   Drafting: one real notice through the QC gate).
3. Confirm: output lands in the firm's storage, filenames follow the firm's
   convention, the signature block renders with the firm's real identity, and
   the command center recorded the run.
4. Produce the **Install Report**: plugins verified, Firm Profile location,
   tokens confirmed baked, gaps remaining (and that they were sent to LAL),
   verification result, and what to do next — normally `lal-firm-adaptation`
   once storage is connected.

## Re-running and updates

- Safe to re-run any time the firm profile changes (new attorney, new PM
  system, new address). Update the Firm Profile document; skills read the
  current values at runtime immediately.
- A change to a BAKED value (firm name, attorney roster) also goes to LAL,
  which updates the firm's private repo — the org marketplace re-syncs and
  every seat gets the update. Nothing to reinstall by hand.
- A firm that wants to CHANGE how a shipped skill behaves routes to
  `lal-customize` — shipped skills are never edited; customizations become
  overlays or firm-prefixed derivative skills.

## What this skill does NOT do

- Never edits, patches, or rewrites any installed skill file (they are
  read-only by design)
- Does not gather brand voice or format specs (that is LAL's onboarding sweep)
- Does not touch matter-level tokens
- Does not install or uninstall plugins — the firm's Claude admin does that
  through the org marketplace
