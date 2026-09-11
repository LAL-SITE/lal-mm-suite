---
name: lal-case-roadmap
description: "Case roadmap generator and updater. Fires when new documents appear at session start and at inflection points - versioned roadmap doc with current stage, next actions, and attorney flags."
---

## When to use this skill (full trigger reference)

{{FIRM_NAME}} Case Roadmap generator and updater. Triggers automatically at the start of any session when new documents are present in the project. Also triggers after retainer is signed and at any major case inflection point. Produces a versioned Word doc (Roadmap_v1, v2, v3...) saved to CLAUDE OUTPUT, AND updates the command center context panel. Covers all matter types and all {{FIRM_NAME}} service/scope models. Assesses scope of representation from retainer type, then generates a matter-type-specific roadmap with current stage, remaining stages, next actions, open issues, and attorney flags. Triggers on: "generate the roadmap," "update the roadmap," "new session," "retainer signed — build the roadmap," "case files updated," "where are we," "what's the roadmap," or any session open where project files have changed since last roadmap version.


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

# {{FIRM_NAME}} Case Roadmap Skill

## Purpose

This skill generates and maintains a living Case Roadmap for every {{FIRM_NAME}} matter.
The roadmap is the intelligence layer that drives the command center — it tells
staff where the case is, where it is going, what comes next, and what the
attorney needs to decide.

The roadmap is NOT a static checklist. It is a dynamic case document that
reflects the current state of the file based on documents present, stages
completed, scope of representation, matter type, resolution path, and
any open issues or red flags.

---

## When This Skill Runs

**Automatic triggers (run without being asked):**
- Session opens AND new documents are present in the project since the last
  roadmap version
- Retainer agreement is present but no roadmap exists yet (v1 generation)

**Manual triggers:**
- Any staff member says "update the roadmap," "generate the roadmap,"
  "where are we," "what's next," or "build the roadmap"
- Major inflection point occurs: resolution path changes, trial date set,
  mediation scheduled, client role changes, scope expands or narrows

**Who can run it:** Anyone — {{ROLE_INTAKE}}, {{ROLE_REVIEWER}}, {{ROLE_DRAFTER}}, {{ROLE_APPROVER}}, {{ROLE_APPROVER}}.

---

## Step 1 — Assess Scope of Representation

Before building the roadmap, identify the retainer type from the project files.
Map to the correct {{FIRM_NAME}} service model using this table:

| Retainer File / Label | Service Model | Attorney-Client? | Court Appearances? | Discovery Included? |
|---|---|---|---|---|
| Hourly Retainer — Full Legal Representation | **Full Rep (Hourly)** | YES | YES | YES |
| Flat Retainer — Limited Scope Representation | **Limited Scope (Flat Fee)** | YES | Only if checked in Scope Checklist | Only if checked |
| Limited Scope Hourly Retainer | **Limited Scope (Hourly)** | YES | Only if initialed in Scope Addendum | Only if initialed |
| limited-scope coaching Coaching Retainer | **DIY Coaching** | YES (advisory only) | NO — client self-represented | NO |
| Name Change Services Agreement | **Name Change (Flat Fee)** | YES | YES (hearing included) | N/A |
| Paralegal Services — Flat Fee | **Paralegal Services (Flat)** | NO — no atty-client relationship | NO | Only if selected |
| Paralegal Services — Hourly | **Paralegal Services (Hourly)** | NO — no atty-client relationship | NO | Only if selected |
| Parenting Plan Creation — Basic | **Parenting Plan Draft Only** | NO | NO | NO |
| Parenting Plan Creation — Attorney Review | **Parenting Plan + Atty Review** | YES (limited scope) | NO | NO |
| Child Support Strategy Session | **Strategy Session Only** | YES (advisory, limited) | NO | NO |
| Addendum to Flat Fee Agreement | **Scope Addendum** | Inherits from original | Per addendum terms | Per addendum terms |

**If no retainer is found:** Flag as [ATTORNEY REVIEW — No retainer located in project files. Roadmap scope cannot be confirmed.]

---

## Step 2 — Identify Matter Type

Determine matter type from the project files (petition, retainer, case notes,
or Case Launch Summary if present).

Supported matter types:
- Dissolution of Marriage — Contested
- Dissolution of Marriage — Uncontested
- Paternity / Parentage — Contested
- Paternity / Parentage — Uncontested
- Post-Judgment Modification (timesharing, support, alimony)
- Contempt & Enforcement
- Relocation (§61.13001)
- Injunction / Domestic Violence
- Name Change (Adult / Minor / Family)
- Adoption (Step-parent / Relative / Agency)
- Chapter 751 — Temporary Custody by Extended Family
- Guardian ad Litem Appointment
- limited-scope coaching Coaching (any matter type, self-represented)

If matter type cannot be determined from project files, ask before proceeding.

---

## Step 3 — Assess Current Case State

Scan all project documents and identify what exists. Use this to determine:

1. **Phases completed** — what documents confirm completion of each phase
2. **Current phase** — where the case sits right now
3. **Next required actions** — what must happen next based on scope + matter type
4. **Open issues** — unresolved legal, financial, or procedural issues
5. **Attorney flags** — anything requiring attorney decision or review
6. **Resolution path** — litigation / mediation / uncontested / hybrid

**Document → Stage mapping (universal):**

| Document Present In Project | Stage Confirmed |
|---|---|
| Signed retainer agreement | Intake & engagement complete |
| Intake questionnaire / client info forms | Client intake complete |
| Case analysis memo in CLAUDE OUTPUT | Initial legal analysis complete |
| Filed petition (in FILED DOCUMENTS) | Petition filed |
| Proof of service / affidavit of service | Service complete |
| Answer or counter-petition filed | Responsive pleading complete |
| Financial Affidavit — client | Client FA present |
| Financial Affidavit — opposing party | OP FA present |
| Mandatory disclosure documents | Disclosure initiated |
| Certificate of Compliance | Disclosure certified |
| FA cross-check chart in CLAUDE OUTPUT | FA cross-check complete |
| Income analysis memo in CLAUDE OUTPUT | Income analysis complete |
| Discovery gap chart in CLAUDE OUTPUT | Gap analysis complete |
| ED chart in CLAUDE OUTPUT | Equitable distribution charted |
| Alimony assessment memo in CLAUDE OUTPUT | Alimony analysis complete |
| CS worksheet in CLAUDE OUTPUT | Child support calculated |
| Notice of mediation | Mediation scheduled |
| Mediation report | Mediation concluded |
| MSA draft or signed MSA | Settlement reached |
| Proposed final judgment or signed FJ | Final judgment stage |
| Closing letter or post-judgment checklist | Case closing initiated |

---

## Step 4 — Build the Roadmap by Matter Type

Generate the roadmap using the correct template below. Adapt based on scope
of representation — if DIY Coaching, remove all firm action items and replace
with client coaching items. If Limited Scope, include only stages within scope
and clearly mark out-of-scope stages.

---

### ROADMAP TEMPLATE — DISSOLUTION OF MARRIAGE (CONTESTED / FULL REP)

**PHASE 1 — INTAKE, ENGAGEMENT & PLEADINGS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Lead intake & screening | {{ROLE_INTAKE}} | | |
| Conflict check & retainer execution | {{ROLE_INTAKE}} | | |
| Client intake forms & info gathering | {{ROLE_REVIEWER}} | | |
| Initial case analysis memo | {{ROLE_APPROVER}} | | |
| Petitioner or respondent strategy | {{ROLE_APPROVER}} | | |
| Draft initial pleadings (petition / answer / counter) | {{ROLE_APPROVER}} | | |
| Filing, service & deadline calendaring | {{ROLE_REVIEWER}} | | |
| Temporary relief (if needed) | {{ROLE_APPROVER}} | OPTIONAL | Only if emergency or contested issues cannot wait |

**PHASE 2 — DISCOVERY & FINANCIAL ANALYSIS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Discovery intake prep ({{UPLOAD_PORTAL}} / folder organization) | {{ROLE_DRAFTER}} | | |
| Stage 2 — Case summary memo | {{ROLE_DRAFTER}} | | |
| Stage 3 — Client FA preliminary review | {{ROLE_DRAFTER}} | | |
| Stage 4 — Client FA cross-check (docs vs. FA) | {{ROLE_DRAFTER}} | | |
| Stage 5 — Income analysis | {{ROLE_DRAFTER}} | OPTIONAL | Required if income is variable, disputed, or complex |
| Stage 6 — OP FA preliminary review | {{ROLE_DRAFTER}} | | |
| Stage 6X — OP discovery review | {{ROLE_DRAFTER}} | | |
| Stage 7 — Discovery gap analysis (both parties) | {{ROLE_DRAFTER}} | | |
| Stage 8 — Equitable distribution chart | {{ROLE_DRAFTER}} | | |
| Stage 8B — Mediation equalizer chart | {{ROLE_DRAFTER}} | OPTIONAL | Run before mediation |
| Alimony assessment (§61.08) | {{ROLE_APPROVER}} | | Required if marriage 3+ years or alimony claimed |
| Child support worksheet (§61.30) | {{ROLE_DRAFTER}} | | Required if minor children |
| Advanced discovery (interrogatories / RFPs / subpoenas) | {{ROLE_APPROVER}} | OPTIONAL | Required if income or assets disputed |
| Motion practice (temp relief, compel, etc.) | {{ROLE_APPROVER}} | OPTIONAL | As needed |

**PHASE 3 — RESOLUTION & CLOSING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Settlement strategy memo | {{ROLE_APPROVER}} | | |
| Mediation preparation package | {{ROLE_APPROVER}} | | |
| Mediation session | {{ROLE_APPROVER}} | | |
| MSA drafting (if settled) | {{ROLE_APPROVER}} | | |
| Proposed final judgment | {{ROLE_APPROVER}} | | |
| Final judgment review & submission | {{ROLE_APPROVER}} | | |
| Post-judgment closing checklist | {{ROLE_REVIEWER}} | | |
| Closing letter to client | {{ROLE_REVIEWER}} / {{ROLE_APPROVER}} | | |

---

### ROADMAP TEMPLATE — DISSOLUTION OF MARRIAGE (UNCONTESTED)

**PHASE 1 — INTAKE & PLEADINGS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Intake & conflict check | {{ROLE_INTAKE}} | | |
| Retainer execution | {{ROLE_INTAKE}} | | |
| Client intake forms | {{ROLE_REVIEWER}} | | |
| MSA drafting (parties already agreed) | {{ROLE_APPROVER}} | | |
| Parenting plan drafting (if children) | {{ROLE_APPROVER}} | | |
| Petition for dissolution (simplified if no children) | {{ROLE_APPROVER}} | | |
| Filing & service coordination | {{ROLE_REVIEWER}} | | |

**PHASE 2 — DISCLOSURE (MINIMAL)**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Financial affidavits (both parties) | {{ROLE_DRAFTER}} | | Mandatory even in uncontested matters |
| Mandatory disclosure (both parties) | {{ROLE_DRAFTER}} | | Rule 12.285 — waiver must be signed if bypassed |
| Certificate of compliance | {{ROLE_DRAFTER}} | | |

**PHASE 3 — FINAL JUDGMENT & CLOSING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Proposed final judgment | {{ROLE_APPROVER}} | | |
| Hearing scheduling (if required) | {{ROLE_REVIEWER}} | | |
| Final judgment entry | {{ROLE_REVIEWER}} | | |
| Post-judgment closing checklist | {{ROLE_REVIEWER}} | | |
| Closing letter | {{ROLE_REVIEWER}} / {{ROLE_APPROVER}} | | |

---

### ROADMAP TEMPLATE — PATERNITY (CONTESTED / FULL REP)

**PHASE 1 — INTAKE & PLEADINGS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Intake & conflict check | {{ROLE_INTAKE}} | | |
| Retainer execution | {{ROLE_INTAKE}} | | |
| Initial case analysis | {{ROLE_APPROVER}} | | Confirm: establishment, modification, disestablishment, relocation, or 751 |
| Petition for paternity / parentage | {{ROLE_APPROVER}} | | |
| UCCJEA affidavit (if children involved) | {{ROLE_APPROVER}} | | |
| Filing, service & deadline calendar | {{ROLE_REVIEWER}} | | |

**PHASE 2 — DISCOVERY & FINANCIAL ANALYSIS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Discovery intake prep | {{ROLE_DRAFTER}} | | |
| Financial affidavits (both parties) | {{ROLE_DRAFTER}} | | |
| FA preliminary & cross-check | {{ROLE_DRAFTER}} | | |
| Income analysis | {{ROLE_DRAFTER}} | OPTIONAL | Required if income disputed |
| Child support worksheet (§61.30) | {{ROLE_DRAFTER}} | | Required |
| Parenting plan — contested provisions | {{ROLE_APPROVER}} | | |
| Advanced discovery | {{ROLE_APPROVER}} | OPTIONAL | If timesharing or income disputed |

**PHASE 3 — RESOLUTION & CLOSING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Settlement strategy | {{ROLE_APPROVER}} | | |
| Mediation preparation | {{ROLE_APPROVER}} | | |
| Mediation session | {{ROLE_APPROVER}} | | |
| Parenting plan finalization | {{ROLE_APPROVER}} | | |
| Proposed final judgment of paternity | {{ROLE_APPROVER}} | | |
| Post-judgment closing checklist | {{ROLE_REVIEWER}} | | |

---

### ROADMAP TEMPLATE — POST-JUDGMENT MODIFICATION

**PHASE 1 — INTAKE & PLEADINGS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Intake — identify modification path | {{ROLE_INTAKE}} / {{ROLE_APPROVER}} | | Paths: timesharing, support, alimony, parental responsibility, relocation |
| Prior order review & substantial change analysis | {{ROLE_APPROVER}} | | Confirm statutory basis before filing |
| Retainer execution | {{ROLE_INTAKE}} | | |
| Supplemental petition for modification | {{ROLE_APPROVER}} | | |
| Filing & service | {{ROLE_REVIEWER}} | | |

**PHASE 2 — DISCOVERY & ANALYSIS**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Updated FA & cross-check | {{ROLE_DRAFTER}} | | |
| Income analysis & CS recalculation | {{ROLE_DRAFTER}} | | Required if support modification |
| Alimony modification analysis (§61.08 2023) | {{ROLE_APPROVER}} | OPTIONAL | If alimony is at issue |
| Parenting evidence collection | {{ROLE_APPROVER}} | OPTIONAL | If timesharing modification |
| Discovery (income / cohabitation / parenting) | {{ROLE_APPROVER}} | OPTIONAL | As needed |

**PHASE 3 — RESOLUTION & CLOSING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Settlement strategy | {{ROLE_APPROVER}} | | |
| Mediation preparation | {{ROLE_APPROVER}} | | |
| Mediation session | {{ROLE_APPROVER}} | | |
| Supplemental final judgment | {{ROLE_APPROVER}} | | |
| Post-judgment closing checklist | {{ROLE_REVIEWER}} | | |

---

### ROADMAP TEMPLATE — CONTEMPT & ENFORCEMENT

**PHASE 1 — INTAKE & STRATEGY**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Intake — identify violations | {{ROLE_INTAKE}} / {{ROLE_APPROVER}} | | Movant or respondent? Identify order violated |
| Prior order review | {{ROLE_APPROVER}} | | Four-element contempt analysis |
| Retainer execution | {{ROLE_INTAKE}} | | |
| Motion for contempt / enforcement | {{ROLE_APPROVER}} | | Or response / defense if respondent |
| Filing & service | {{ROLE_REVIEWER}} | | |

**PHASE 2 — HEARING PREPARATION**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Evidence collection | {{ROLE_REVIEWER}} / {{ROLE_APPROVER}} | | Violations log, payment records, communications |
| Judicial procedures check | {{ROLE_APPROVER}} | | Judge-specific contempt hearing requirements |
| Proposed order with purge conditions | {{ROLE_APPROVER}} | | |

**PHASE 3 — RESOLUTION**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Hearing | {{ROLE_APPROVER}} | | |
| Order on contempt | {{ROLE_APPROVER}} | | |
| Compliance monitoring | {{ROLE_REVIEWER}} | | If purge conditions imposed |

---

### ROADMAP TEMPLATE — NAME CHANGE

**PHASE 1 — INTAKE & FILING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Intake — identify type | {{ROLE_INTAKE}} | | Adult / minor / family / restoration / complex |
| Retainer execution | {{ROLE_INTAKE}} | | Flat fee per selected tier |
| Document collection | {{ROLE_REVIEWER}} | | ID, birth cert, residency proof, prior orders |
| Petition drafting | {{ROLE_APPROVER}} | | Master petition — one document for all types |
| Filing | {{ROLE_REVIEWER}} | | E-portal — confirm acceptance and judge assignment |

**PHASE 2 — BACKGROUND CHECK & HEARING PREP**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Fingerprinting & FDLE/FBI compliance | {{ROLE_REVIEWER}} | | Verify completion before scheduling hearing |
| Hearing scheduling | {{ROLE_REVIEWER}} | | Remote or in-person per judge |
| Client hearing prep | {{ROLE_APPROVER}} | | ID and residency proof confirmed |

**PHASE 3 — FINAL JUDGMENT & CLOSING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Final judgment | {{ROLE_APPROVER}} | | Must match petition allegations exactly |
| Certified copies | {{ROLE_REVIEWER}} | | |
| Post-judgment record update instructions | {{ROLE_REVIEWER}} | | |

---

### ROADMAP TEMPLATE — DIY COACHING (ANY MATTER TYPE)

> NOTE: Client is self-represented. Firm does NOT file, appear, or contact opposing counsel.
> All roadmap actions are COACHING items — client executes, firm advises.

**PHASE 1 — ENGAGEMENT & STRATEGY**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Intake & retainer execution | {{ROLE_INTAKE}} | | $1,500 initial retainer — no payment plan |
| Initial strategy session | {{ROLE_APPROVER}} | | Case assessment and options analysis |
| Procedural roadmap for client | {{ROLE_APPROVER}} | | What client must do, in what order, by when |

**PHASE 2 — COACHING THROUGH CASE STAGES**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Document review and coaching sessions | {{ROLE_APPROVER}} | | Billed at $300/hr against retainer |
| Drafting assistance (client files) | {{ROLE_APPROVER}} | | Firm drafts, client reviews and files |
| Hearing coaching | {{ROLE_APPROVER}} | | Pre-hearing prep session — client appears alone |
| Mediation coaching | {{ROLE_APPROVER}} | | Pre-mediation strategy session |

**PHASE 3 — RESOLUTION COACHING**

| Stage | Owner | Status | Notes |
|---|---|---|---|
| Settlement review | {{ROLE_APPROVER}} | | Attorney reviews proposed terms — advisory only |
| Final document review | {{ROLE_APPROVER}} | | Before client submits final judgment |
| Post-resolution guidance | {{ROLE_APPROVER}} | | Explain what happens next, what client must do |

---

### ROADMAP TEMPLATE — LIMITED SCOPE (FLAT FEE OR HOURLY)

> NOTE: Roadmap includes ONLY stages within the signed scope checklist or
> scope selection addendum. All out-of-scope stages are marked [OUT OF SCOPE —
> client responsible] and are NOT included in firm's task list.
>
> ALWAYS reference the scope checklist from the retainer when building this roadmap.
> Do not assume any stage is in scope unless expressly checked or initialed.

Build from the applicable full-rep roadmap above, then:
1. Review scope checklist / addendum
2. Mark each stage as IN SCOPE, OUT OF SCOPE, or ATTORNEY DECISION NEEDED
3. Flag any stages where client assumes responsibility
4. Flag any gaps where out-of-scope tasks could affect client's rights

---

## Step 5 — Roadmap Output Structure

Every roadmap document must contain the following sections in this order:

```
{{FIRM_NAME}} CASE ROADMAP
[Matter Name] | [Matter Type] | [Version: vN] | [Date]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

SCOPE OF REPRESENTATION
Service Model: [Full Rep / Limited Scope / DIY Coaching / etc.]
Retainer Type: [Hourly / Flat Fee / Addendum / etc.]
Attorney-Client Relationship: [Yes / No]
Court Appearances: [Yes / No / Per Scope Checklist]
Discovery Included: [Yes / No / Partial — see scope]

MATTER OVERVIEW
Matter Type: [Dissolution Contested / Paternity / Modification / etc.]
Client Role: [Petitioner / Respondent / Mother / Father / Movant / etc.]
Resolution Path: [Litigation / Mediation / Uncontested / TBD]
Discovery Level: [Full / Partial / Minimal / None]
Children: [Yes — N minor child(ren) / No]
Case No.: [If known]
County: [If known]

CURRENT STATUS
Current Phase: [Phase 1 / 2 / 3]
Current Stage: [Name of active stage]
Last Updated: [Date]
New Documents Since Last Version: [List any new files detected]

COMPLETED STAGES
[Checked list of confirmed-complete stages based on documents present]

ACTIVE STAGES — NEXT 30 DAYS
[3–5 prioritized actions with owner and deadline if known]

REMAINING STAGES
[Full roadmap table for current matter type — status updated]

OPEN ISSUES
[Unresolved legal, financial, or procedural issues that affect the roadmap]

ATTORNEY FLAGS
[Items requiring attorney decision, review, or sign-off before proceeding]

GAPS & RISKS
[Any missing documents, unaddressed deadlines, or scope gaps that could
affect the client's rights or the case timeline]
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CONFIDENTIAL — ATTORNEY WORK PRODUCT — DRAFT FOR REVIEW
{{FIRM_NAME}}
```

---

## Step 6 — Versioning & Output

**Naming convention:**
`[ClientLastName]_Case_Roadmap_v[N]_[YYYY-MM-DD].doc`

Example: `Smith_Case_Roadmap_v3_2026-05-12.doc`

**Save location:** CLAUDE OUTPUT folder in the client's {{DMS}} matter folder.

**Version increment rules:**
- v1 — generated at retainer signing (first session with retainer present)
- v2+ — generated any time new documents are detected at session open, or
  when manually triggered at a major inflection point

**Always note what changed** in the "New Documents Since Last Version" field
so staff and attorneys can see at a glance what triggered the update.

---

## Step 7 — Command Center Context Block

In addition to the Word doc, output a structured JSON block that the command
center can read to update the interface. This block should be clearly labeled
and placed at the END of the response (after the roadmap narrative), formatted
as follows:

```json
{
  "client": "[Client Name]",
  "matterType": "[dissolution|paternity|modification|contempt|namechange|adoption|751|relocation|gal|injunction]",
  "serviceModel": "[Full Rep|Limited Scope Flat|Limited Scope Hourly|DIY Coaching|Paralegal Flat|Paralegal Hourly|Name Change|Strategy Session Only]",
  "clientRole": "[Petitioner|Respondent|Mother|Father|Movant|Respondent|Petitioner|N/A]",
  "resolutionPath": "[litigation|mediation|uncontested|tbd]",
  "discoveryLevel": "[full|partial|minimal|none]",
  "currentPhase": "[p1|p2|p3]",
  "currentStage": "[stage label]",
  "completedStages": [array of stage IDs confirmed complete],
  "redFlags": "[any attorney flags or urgent items — empty string if none]",
  "roadmapVersion": "[vN]",
  "lastUpdated": "[YYYY-MM-DD]"
}
```

---

## Non-Negotiables

- Nothing in the roadmap authorizes any action without attorney sign-off
- Scope of rep is assessed from the ACTUAL retainer — never assumed
- Limited scope and DIY matters must clearly mark what is OUT OF SCOPE
- Every roadmap includes the attorney flags section — never omit even if empty
- The roadmap is versioned — never overwrite, always increment
- Output saves to CLAUDE OUTPUT folder — always note this in the response
- If retainer type is ambiguous or missing, flag before proceeding

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

