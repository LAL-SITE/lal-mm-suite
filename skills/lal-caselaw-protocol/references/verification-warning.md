# Verification Warning — Canonical Text

This file holds the exact warning text used by `lal-caselaw-protocol.SKILL.md`. It exists so the
warning is reproduced identically every time instead of being paraphrased. **Do not shorten,
summarize, soften, or move any of these blocks to a footnote.** Reproduce them verbatim.

The authorized caselaw source referenced throughout is, and is only:

> `github.com/LegalAuthorityLab/florida-family-law-research-suite`

That value is deliberately not tokenized. See the "not firm-tokenized" section of the skill for why,
and the flagged discrepancy note at the end of the skill for an open naming question.

---

## Block 1 — The mandatory case-citation warning

Attach after **every** case citation, in every response, every time — including citations that came
from the authorized repository, and including cases the attorney supplied and vouched for.

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

## Block 2 — Statute and rule marker

Statutes, rules, and forms are **not** restricted by the protocol and do not take Block 1. They take
this one-line marker instead, attached to each provision cited:

> ⚠️ VERIFY: confirm rule and current text before relying on this.

Add a local-practice flag wherever the provision is one that divisions commonly supplement:

> [CONFIRM LOCALLY: whether the division imposes requirements beyond the rule — with the judicial
> assistant and with {{ROLE_APPROVER}}]

---

## Block 3 — Not-found response

Use when the issue has no supporting authority in the authorized repository, **and** when the
repository could not be reached at all. An unreachable source yields a not-found answer — never a
substitute source.

> **No caselaw on this issue was found in the authorized caselaw repository**
> (`florida-family-law-research-suite`).
>
> This protocol prohibits citing cases from internet search or model memory, because of the risk of
> fabricated or unverifiable citations.
>
> **Options for {{ATTORNEY_NAME}}:**
> - Search {{RESEARCH_PROVIDER}} directly for cases on: *state the legal issue and the key search
>   terms — this is genuinely useful and is not a citation*
> - Rely on the controlling statute or rule below without a case citation
> - Ask for the argument to be built from the statutory standard alone
> - Route the case to {{ROLE_APPROVER}} as a proposed addition to the shared public repository
>
> **Controlling statute or rule for this issue:** *the Florida statute or family law rule, by number
> and subject*
> ⚠️ VERIFY: confirm rule and current text before relying on this.

Identify the actual controlling provision. If you cannot, say so — never invent one to fill the slot.

---

## Block 4 — Unconfirmed case supplied by the requester

Use when someone supplies a case that is not in the authorized repository and has not been expressly
vouched for by the attorney.

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

## Block 5 — Drafting note, top of document

Required at the top of any drafted document containing at least one case citation.

> 📋 **DRAFTING NOTE — ATTORNEY ACTION REQUIRED BEFORE USE**
> This draft contains case citations. Each citation must be independently verified before this
> document is filed, served, or shared. See the citation verification checklist at the end of this
> document. Do not file without completing verification. The accuracy of no case citation in this
> draft is guaranteed.
> Prepared by {{ROLE_DRAFTER}} · reviewed by {{ROLE_REVIEWER}} · approval required from
> {{ROLE_APPROVER}}.

---

## Block 6 — Citation verification checklist, end of document

Required at the end of the same document. One line per case actually cited. Do **not** pre-populate
rows with example or placeholder case names.

> **CITATION VERIFICATION CHECKLIST**
> Matter: {{CLIENT_NAME}} · Case No. {{CASE_NO}} · {{COUNTY}} County, {{CIRCUIT}} Judicial Circuit,
> {{DIVISION}} · Drafted {{DATE}}
>
> Before filing or serving, verify each of the following:
> - [ ] *first case as cited in this draft* — citation, holding, good-law status, district
> - [ ] *next case as cited in this draft* — citation, holding, good-law status, district
>
> Each item also confirms: the authority exists, is accurately cited, and supports the proposition it
> is cited for.
> Verification method: {{RESEARCH_PROVIDER}}, or Florida appellate opinions published at flcourts.gov
> Verified by: ______________________  Date: ______________
>
> [CONFIRM LOCALLY: whether this jurisdiction requires a separate accuracy certification on the
> filing itself, and in what form — with the clerk and with {{ROLE_APPROVER}}]

---

## Block 7 — Attorney-vouched source label

When {{ATTORNEY_NAME}} supplies a case and expressly vouches for it, label it in output. Block 1
still attaches.

> Source: attorney-supplied — verified and vouched for by {{ATTORNEY_NAME}} on {{DATE}}.
> Used as supplied; holding not extended, and no parallel citation or subsequent history added.

Ambiguous vouching is not vouching. Ask before treating material this way. Nothing supplied in a
session is added to the shared repository from within a session — that is a human pull request.

---

## Notes on token use in these blocks

- Install-time tokens: `{{FIRM_NAME}}` `{{ATTORNEY_NAME}}` `{{BAR_NO}}` `{{FIRM_ADDRESS}}`
  `{{FIRM_PHONE}}` `{{FIRM_EMAIL}}` `{{PM_SYSTEM}}` `{{DMS}}` `{{RESEARCH_PROVIDER}}`
  `{{UPLOAD_PORTAL}}` `{{ROLE_DRAFTER}}` `{{ROLE_REVIEWER}}` `{{ROLE_APPROVER}}` `{{ROLE_INTAKE}}`
- Draft-time tokens, also curly: `{{CLIENT_NAME}}` `{{CASE_NO}}` `{{JUDGE}}` `{{OPPOSING_COUNSEL}}`
  `{{COUNTY}}` `{{CIRCUIT}}` `{{DIVISION}}` `{{DATE}}`
- `{{RESEARCH_PROVIDER}}` resolves to whatever research service the firm actually subscribes to. Never
  name a vendor literally in output — a firm without that subscription is being told to do something
  it cannot do.
- Never emit `Click here to enter text.` or `XXXXXXXX`. An unknown value is either a token, a
  `[CONFIRM LOCALLY: ...]` flag, or an explicit statement that the value is not known.
- Storage-agnostic: reach the repository and any firm file only through the session's file connector
  abstraction. Never assume a local path, drive letter, or synced-folder location.
