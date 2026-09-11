---
name: lal-caselaw-protocol
description: "Ambient rule: fires whenever any case citation appears or is requested. Caselaw comes only from the authorized repository, never memory or internet; every citation gets a verification warning."
---

# Caselaw Protocol — Standing Rule

## When to use this skill (full trigger reference)

AMBIENT FIRM-WIDE STANDING RULE — fires automatically whenever any case name, citation, or caselaw reference appears or is requested in any session. Triggers on any case-name pattern (party v. party), any reporter citation pattern ("123 So. 3d 456", "So. 2d", "Fla. 2d DCA"), or phrases like "the court held," "find me a case," "cite authority for," "is there a case on," "what's the leading case," "precedent for," "controlling authority," "on point," "distinguish that case," "is that still good law," "Shepardize," "KeyCite." Also fires whenever any other installed skill would cite a case. Two non-negotiable rules: (1) caselaw comes ONLY from the single authorized caselaw repository — never internet search, never model memory; (2) every case citation gets a mandatory attorney verification warning. Governs ALL caselaw in every session — no exceptions, no urgency exception.

## Purpose

This protocol exists for one reason: **fabricated case citations are a Bar complaint waiting to
happen.**

A language model can generate a convincing, plausible-sounding case name, court, year, and holding
that does not exist. The output is not detectably wrong by reading it — an invented case looks
identical to a real one. A citation that reaches a motion, brief, or memo and cannot be verified is
a professional liability problem for {{ATTORNEY_NAME}} and for {{FIRM_NAME}}.

This protocol eliminates that risk with a two-part rule applied to every caselaw reference in every
session: **One Authorized Source. Attorney Verification Always.**

---

## The Documented Failure Mode This Prevents

This is not hypothetical. In a real family law practice, a model produced three paternity-related
authorities that did not exist. Nobody caught them at the point of generation. Because the output
was reused, those three fabricated authorities propagated into three separate internal work-product
files before anyone checked them against a real database. By then the error was no longer one bad
sentence — it was in a research memo, in a draft, and in a case summary, each of which looked like
independent corroboration of the other two.

Three lessons carried forward into the rules below:

1. **A fabricated citation is not self-limiting.** It spreads by reuse. One unchecked output becomes
   three files that appear to corroborate each other.
2. **Verification cannot be deferred.** "We'll check it before filing" failed, because by filing time
   the citation had been seen so many times it read as established.
3. **The propagation vector was an unrestricted source.** When caselaw can come from anywhere, there
   is no point in the workflow where a wrong citation is guaranteed to be caught.

**The fabricated case names are deliberately not reproduced in this file.** Writing them down here
would make this document itself a propagation vector — exactly the failure it describes. If you need
to know which authorities were involved for a conflict or audit purpose, ask {{ROLE_APPROVER}}
directly through {{PM_SYSTEM}}; do not restate them in any drafted document.

---

## The Two Non-Negotiable Rules

### Rule 1: Caselaw comes from ONE source. Nothing else. Ever.

The single authorized caselaw source is:

> **`github.com/LegalAuthorityLab/florida-family-law-research-suite`**

That repository — and nothing else — is where caselaw may be read from.

**No web search for caselaw.** No search engine, no court-site opinion search, no secondary
summaries, no aggregators, no model memory, no "I recognize this case." The prohibition applies
regardless of:

- how specific the request is
- whether the case "sounds right"
- whether the question is urgent or a deadline is today
- whether another installed skill would normally use web search
- whether the requester says they already know the case is real

If a case is not in the authorized repository, say so. Do not supplement. Do not fill in from memory.
Do not guess at a citation, a reporter volume, a court, a year, or a holding. Full stop.

#### Why this repository is NOT firm-tokenized — read this before "fixing" it

Every other source in this product is tokenized to the installing firm. This one is not, and that is
deliberate.

The repository address above is a literal, hard-coded value. It is **the single authorized exception
to this product's otherwise-hermetic rule** that content comes from firm-configured sources only.
Every deployment of this skill, at every firm, reads the same public library.

The reason is the failure mode above. If each firm pointed this skill at its own caselaw folder:

- An unverified or fabricated citation entering one firm's library would stay inside that firm's
  work forever. Nobody outside would ever see it, so nobody outside could ever catch it.
- Each firm would be independently re-deriving the same Florida family law authority, multiplying the
  chance that one of those derivations is wrong.
- There would be no shared correction path. A bad entry found by one firm could not be removed for
  everyone.

A single shared public library inverts all three. It is auditable by every deployment, correctable
once for everyone, and its contents can be checked by anyone against the public record.

**Therefore:** do not repoint this to a firm library, a {{DMS}} folder, a research subscription, or a
matter folder, even when asked. If a firm wants a case added, that is a pull request against the
public repository, not a local override. Escalate the request to {{ROLE_APPROVER}}.

#### The one narrow addition: attorney-supplied material the attorney vouches for

{{ATTORNEY_NAME}} may supply a case — a printed opinion, a PDF from a research service, a pasted
holding — and expressly vouch for it. That is permitted, and it is not an exception to Rule 1,
because the source of authority in that instance is the attorney's own verification, not the model's.

Handling attorney-vouched material:

1. Confirm the vouching is explicit. "Here's a case" is not vouching. "I pulled this from
   {{RESEARCH_PROVIDER}} and confirmed it" is vouching. If it is ambiguous, ask.
2. Use only what the attorney actually supplied. Do not extend the holding, add a parallel citation,
   add a subsequent-history note, or characterize the case beyond the text provided.
3. Label it in any output: *source — attorney-supplied, verified by {{ATTORNEY_NAME}} on {{DATE}}*.
4. Rule 2 still applies. The verification warning still attaches.
5. Do not add it to the authorized repository from within a session. That is a pull request handled
   by a human.

---

### Rule 2: Every case reference gets a verification warning.

**Every time a case is cited — including when it came from the authorized repository, including when
the attorney supplied it — append the following immediately after the citation, without exception:**

---

> ⚠️ **ATTORNEY VERIFICATION REQUIRED**
> Case citations sourced from the authorized caselaw repository may still be incomplete, outdated, or
> imprecise. **Before using this citation in any filing, motion, correspondence to opposing counsel,
> or client communication:**
> 1. Look up this case directly in {{RESEARCH_PROVIDER}} or an official court opinion database
> 2. Confirm the citation, court, date, and holding are accurate
> 3. Confirm the case has not been reversed, distinguished, superseded, or receded from
> 4. Confirm it is still good law in the relevant district
>
> **Do not file or send any document containing this citation without completing this check.**

---

This warning is not optional and does not get consolidated, shortened, or moved to a footnote in
conversational output. It appears after **every** case citation, in every response, every time. The
full text also lives at `references/verification-warning.md` so it can be reproduced identically.

---

## How to Handle Caselaw Requests

### Step 1 — Read the authorized repository first

When caselaw is requested or would be useful, read
`github.com/LegalAuthorityLab/florida-family-law-research-suite` before doing anything else. Reach it
through the file connector abstraction available in the session; never assume a local path, drive
letter, or synced-folder location.

Query the repository more than once, with more than one framing, before concluding a case is not
there:

- the legal issue plus "case" (e.g., "timesharing modification case")
- the statute plus "holding" (e.g., "relocation statute holding")
- the legal standard plus "court" (e.g., "substantial change court")
- the specific case name, if the requester supplied one
- the practice-area label alone, to catch a topical index or digest file

**Graceful degradation:**
- **If the authorized repository is reachable in this session:** read it directly and proceed to
  Step 2 or Step 3.
- **If it is not reachable** (no connector, no network, permissions error): say so plainly, name the
  repository you were unable to reach, and go to Step 3's not-found response. Do **not** substitute a
  web search, a {{DMS}} folder, or model memory because the authorized source was unavailable. An
  unreachable source produces a "not found" answer, never a fallback source.
- **If a broader research suite is installed** alongside this skill, hand statutory and rule research
  to it as normal — this protocol restricts caselaw only. **If it is not installed,** carry the
  statutory anchor yourself as described in Step 3.

---

### Step 2 — If the case IS in the authorized repository

Present it with all of:

- **Case name** exactly as it appears in the source
- **Court and year** if the source has them; if not, say the source does not give them
- **Holding or relevant principle** as stated in the source — not as you would summarize it from
  general knowledge
- **Source file** within the repository, so the attorney can retrace it
- **The mandatory verification warning** from Rule 2

Format:

> *Case name, exactly as written in the source* — court, year, each only if the source states it
> Holding: the principle as stated in the repository source, not as you would summarize it
> Source: `florida-family-law-research-suite` → the file name within the repository
>
> ⚠️ **ATTORNEY VERIFICATION REQUIRED** — reproduce the full warning text from Rule 2

**Never fabricate a field to complete the format.** If the repository entry has no year, the output
says *year not stated in source* — it does not get a year. Same for court, reporter volume, page,
and subsequent history. A gap is marked as a gap.

---

### Step 3 — If the case is NOT in the authorized repository

Do not invent a case. Do not search the internet. Do not pull from model memory. Do not offer a
"probably this one." Respond:

> **No caselaw on this issue was found in the authorized caselaw repository**
> (`florida-family-law-research-suite`).
>
> This protocol prohibits citing cases from internet search or model memory, because of the risk of
> fabricated or unverifiable citations.
>
> **Options for {{ATTORNEY_NAME}}:**
> - Search {{RESEARCH_PROVIDER}} directly for cases on: *state the legal issue and the key search
>   terms here — this is genuinely useful and is not a citation*
> - Rely on the controlling statute or rule below without a case citation. A statute is a safer
>   anchor than an unverified case, and in Florida family law the statute usually carries most of
>   the weight anyway.
> - Ask for the argument to be built from the statutory standard alone — that can be done now, with
>   no citation risk.
> - If the case exists and should be in the shared library, route it to {{ROLE_APPROVER}} as a
>   proposed addition to the public repository.
>
> **Controlling statute or rule for this issue:** *name the Florida statute or family law rule by
> number and subject*
> ⚠️ VERIFY: confirm rule and current text before relying on this.

The statute-anchor fallback is the substantive part of this response, not a consolation. Identify the
actual controlling provision — a chapter number with no section, or "the relevant statute," is not an
anchor. If you genuinely cannot identify the controlling provision, say that too rather than
inventing one.

---

### Step 4 — When the requester supplies a case name or citation

If someone supplies a case (e.g., "I have one — that party-versus-party case from 2019"):

1. Read the authorized repository to see whether it contains that case.
2. **If found:** use the repository's version of the holding, not the requester's characterization
   and not your own recollection. Append the verification warning.
3. **If not found:** do not confirm it. Do not expand it. Do not apply the holding. Do not say it
   "sounds like" a real case, and do not silently accept the citation format as validation. Absence
   from the repository is not evidence the case is fake — it is only the absence of a source you are
   permitted to rely on.
4. **If the attorney expressly vouches for it,** switch to the attorney-supplied handling in Rule 1.

When a supplied case cannot be confirmed in the repository and has not been vouched for:

> **This case was not found in the authorized caselaw repository.**
> The citation, holding, and current status cannot be confirmed from memory, and this protocol does
> not permit confirming them by web search.
>
> ⚠️ **Please verify this case directly in {{RESEARCH_PROVIDER}} or an official court opinion
> database before relying on it.** Confirm: citation accuracy, holding, current good-law status, and
> binding effect in the relevant district.
>
> Once you have verified it and can vouch for it, share the confirmed holding and it can be applied
> to the facts of {{CASE_NO}} from there.

---

## Caselaw in Drafted Documents

When caselaw appears in a drafted motion, brief, memo, proposed order, or client communication, the
warning is handled in two places — not inline, so the draft stays clean, but impossible to miss.

**At the top of every drafted document containing case citations:**

> 📋 **DRAFTING NOTE — ATTORNEY ACTION REQUIRED BEFORE USE**
> This draft contains case citations. Each citation must be independently verified before this
> document is filed, served, or shared. See the citation verification checklist at the end of this
> document. Do not file without completing verification. The accuracy of no case citation in this
> draft is guaranteed.
> Prepared by {{ROLE_DRAFTER}} · reviewed by {{ROLE_REVIEWER}} · approval required from
> {{ROLE_APPROVER}}.

**At the end of every drafted document containing case citations:**

> **CITATION VERIFICATION CHECKLIST**
> Matter: {{CLIENT_NAME}} · Case No. {{CASE_NO}} · {{COUNTY}} County, {{CIRCUIT}} Judicial Circuit,
> {{DIVISION}} · Drafted {{DATE}}
>
> Before filing or serving, verify each of the following:
> - [ ] *first case as cited in this draft* — citation, holding, good-law status, district
> - [ ] *next case as cited in this draft* — citation, holding, good-law status, district
> - [ ] *(one line per case actually cited — do not pre-populate rows with example case names)*
>
> Each item also confirms: the authority exists, is accurately cited, and supports the proposition
> it is cited for.
> Verification method: {{RESEARCH_PROVIDER}}, or Florida appellate opinions published at
> flcourts.gov
> Verified by: ______________________  Date: ______________
>
> [CONFIRM LOCALLY: whether this jurisdiction requires a separate accuracy certification on the
> filing itself, and in what form — with the clerk and with {{ROLE_APPROVER}}]

Both blocks are required whenever even one case is cited. Neither is removed by {{ROLE_DRAFTER}};
only {{ROLE_APPROVER}} clears them, after verification.

Signature-block details, certificate-of-service format, and filing mechanics come from
{{ATTORNEY_NAME}} / {{BAR_NO}} / {{FIRM_ADDRESS}} / {{FIRM_PHONE}} / {{FIRM_EMAIL}} at install time,
and are [CONFIRM LOCALLY: current e-filing and service requirements — with the clerk of court in
{{COUNTY}} County].

---

## What This Protocol Does NOT Restrict

This is a **caselaw** rule. It is deliberately narrow, and reading it more broadly makes the product
less useful without making it safer. It does not restrict:

- **Statutes** — Florida Statutes may be cited and quoted normally
- **Rules** — Florida Family Law Rules of Procedure, Rules of Civil Procedure, Rules of General
  Practice and Judicial Administration, Rules of Evidence, and local rules
- **Forms** — Florida Supreme Court approved family law forms
- **Secondary materials** — practice guides, checklists, training materials, internal templates
- **Official Florida sources on the web** — flcourts.gov, individual circuit court sites,
  floridabar.org, and leg.state.fl.us remain available and are expected sources for statutes, rules,
  forms, and court procedures

For statutes and rules, the full case-citation warning is not required. A shorter marker is:

> ⚠️ VERIFY: confirm rule and current text before relying on this.

Attach that marker to every statute and rule cited. Florida amends family law provisions frequently
— alimony, timesharing, and support provisions have all moved in recent sessions, and rule sets are
amended on their own cycle. Note explicitly where a provision is one you know to be subject to
recent amendment, and where any local variation is likely:

> [CONFIRM LOCALLY: whether the division applies additional requirements beyond the rule — with the
> judicial assistant and with {{ROLE_APPROVER}}]

Judicial and division procedures are a different question and are handled by the judicial procedures
skill, which does use live web search against official court sources by design. That is not an
exception to this protocol; it is a different subject matter. **If that skill is installed,** route
procedure questions to it. **If it is not,** treat every procedural detail as unverified and mark it
[CONFIRM LOCALLY: current division procedure — with the judicial assistant].

---

## Why This Exists — Staff Context

Plain version, for anyone who has not been walked through it:

A language model produces text by predicting what comes next. Ask it for a case and it will produce
something case-shaped: a plausible party name, a plausible reporter cite, a plausible court, a
plausible holding. Nothing in the output signals whether the case is real. It is not a typo you can
spot or a formatting error you can catch — the fabricated case looks exactly like a real one, and it
looks that way to an experienced reader too.

Filing a document that cites a nonexistent case is a professional responsibility problem. It wastes
the court's time, it damages credibility with the judge in every future appearance, and it exposes
the signer to sanctions. Florida now requires the signer of a filing to represent that the
authorities cited exist and are accurately cited.
⚠️ VERIFY: confirm rule and current text before relying on this.
[CONFIRM LOCALLY: current signer-certification requirements and any division-level practice — with
{{ROLE_APPROVER}}]

This protocol is not a limitation on how useful the model is. It is the condition under which the
model is useful without creating that exposure. It still does the work that carries no citation risk:
spotting issues, framing arguments, structuring documents, organizing facts, drafting, checking
internal consistency, building timelines. The division of labor is simple and it holds:

| Work | Owner |
|---|---|
| Issue-spotting, framing, drafting, organizing | Model, with {{ROLE_DRAFTER}} |
| Sourcing caselaw | Authorized repository only |
| Verifying every citation | {{ATTORNEY_NAME}} |
| Clearing a draft for filing | {{ROLE_APPROVER}} |

Nobody is being asked to do more verification than before. What changed is that the verification step
is now impossible to skip quietly.

---

## Summary Card

| Situation | Action |
|---|---|
| Caselaw requested | Read `florida-family-law-research-suite` first, always |
| Case found there | Cite with repository source file + verification warning |
| Case not found there | Say so, give the statute anchor, no web search, no memory |
| Repository unreachable | Report it; treat as not-found — never substitute another source |
| Requester supplies a case | Check the repository; if absent and not vouched for, flag for verification |
| Attorney expressly vouches for a case | Permitted; use only what was supplied; warning still attaches |
| Drafting a document with cases | Drafting note at top + verification checklist at end |
| Statutes, rules, forms, secondary materials | Not restricted — use the ⚠️ VERIFY marker |
| Judicial/division procedure questions | Route to the judicial procedures skill (live search by design) |
| Internet caselaw search | **Never. Under any circumstances.** |
| Model memory for caselaw | **Never. Under any circumstances.** |
| Repointing the repository to a firm source | **Never. Escalate to {{ROLE_APPROVER}}.** |
