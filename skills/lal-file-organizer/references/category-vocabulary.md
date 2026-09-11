# Category Vocabulary and Routing

The default `{{CATEGORY_VOCABULARY}}` — a closed set covering the **whole
matter**, not discovery alone — plus the category → folder routing table.

> **This is a DEFAULT.** Replace or extend it to match the buyer's practice.
> Every rule about how the vocabulary behaves (closed set, one value per
> document, additions approved not invented) holds regardless of the values.

---

## Part 1 — Financial and disclosure categories

These twelve are grounded in Florida's family law mandatory-disclosure
categories.

> ⚠️ VERIFY: confirm rule and current text before relying on this.
> Florida Family Law Rule of Procedure 12.285 governs mandatory disclosure in
> family law matters and enumerates the categories of financial documents a
> party must produce. The rule and its category list are amended from time to
> time. Confirm the current text, the current category list, the current time
> periods, and which categories apply to the specific proceeding type before
> relying on any mapping below.

| Category value | What it covers |
|---|---|
| `CheckingStatement` | Checking or savings account statements |
| `BrokerageStatement` | Brokerage or investment account statements |
| `TaxReturn` | Personal income tax returns and attached schedules |
| `BusinessTaxReturn` | Business or entity income tax returns |
| `W2` | Annual wage and tax statements |
| `1099` | Any form in the 1099 series |
| `K1` | Partnership, S-corporation, or trust income statements |
| `Paystub` | Pay stubs and periodic wage statements |
| `InsuranceDoc` | Life and health insurance documents |
| `Deed` | Deeds, titles, and instruments of ownership |
| `LoanApplication` | Loan and credit applications and supporting financial statements |
| `CreditCardStatement` | Credit card statements |
| `MortgageStatement` | Mortgage and home-equity statements |
| `LoanStatement` | Auto, student, and personal loan statements |
| `LiabilityDoc` | Other liability documents |
| `AccountStatement` | Other account statements not covered above |
| `RetirementStatement` | Retirement, pension, and deferred-compensation statements |
| `BusinessFinancial` | Business financial statements, ledgers, profit-and-loss records |

`[CONFIRM LOCALLY: which disclosure categories apply to this proceeding type and what time periods are required — with {{ROLE_APPROVER}}]`

**A category is not a legal conclusion.** Assigning `CheckingStatement` says
what a document is. It says nothing about whether disclosure is complete,
timely, or sufficient. Those are legal judgments and route out.

---

## Part 2 — Whole-matter categories

The source this product derives from handled discovery documents only. Core
handles the whole matter, so the vocabulary extends across every document class
a family law matter contains.

### Court documents — filed by either side

| Category value | What it covers |
|---|---|
| `Petition` | Initiating petitions |
| `Response` | Answers, responses, counterpetitions |
| `Motion` | Motions of any kind |
| `MotionResponse` | Responses and replies to a motion |
| `Memorandum` | Memoranda of law and legal argument |
| `FinancialAffidavit` | Sworn financial affidavits |
| `CertOfCompliance` | Certificates of compliance with disclosure obligations |
| `CertOfService` | Certificates and proofs of service |
| `ProposedOrder` | Proposed orders submitted for signature |
| `Stipulation` | Stipulations and joint filings |
| `Withdrawal` | Substitution or withdrawal of counsel documents |
| `CourtFiling` | Filed documents not covered above |

### Orders and notices

| Category value | What it covers |
|---|---|
| `Order` | Signed orders |
| `Judgment` | Final judgments and decrees |
| `NoticeOfHearing` | Notices setting or cancelling a hearing |
| `NoticeOfFiling` | Notices of filing |
| `NoticeOther` | Other notices, including unavailability |
| `Subpoena` | Subpoenas issued or received |

### Discovery instruments — distinct from the records they produce

| Category value | What it covers |
|---|---|
| `Interrogatories` | Interrogatories served or received |
| `InterrogatoryAnswers` | Answers to interrogatories |
| `RequestForProduction` | Requests for production |
| `ProductionResponse` | Written responses to requests for production |
| `RequestForAdmission` | Requests for admission |
| `AdmissionResponse` | Responses to requests for admission |
| `DeficiencyLetter` | Discovery deficiency correspondence |
| `PrivilegeLog` | Privilege and objection logs |
| `DepositionTranscript` | Deposition transcripts and errata |

### Correspondence

| Category value | What it covers |
|---|---|
| `ClientLetter` | Letters and email to or from the client |
| `CounselLetter` | Correspondence with opposing counsel |
| `BenchLetter` | Correspondence with the court or judicial staff |
| `ThirdPartyLetter` | Correspondence with custodians, providers, experts, vendors |
| `StatusUpdate` | Periodic client status communications |

### Reports and agreements

| Category value | What it covers |
|---|---|
| `ExpertReport` | Expert and evaluator reports |
| `EvaluationReport` | Social investigations, evaluations, assessments |
| `MediationReport` | Mediation reports and mediator communications |
| `SettlementAgreement` | Executed marital settlement and related agreements |
| `ParentingPlan` | Parenting plans, proposed and executed |
| `SupportWorksheet` | Support guideline worksheets and calculations |

### Engagement, billing, and administration

| Category value | What it covers |
|---|---|
| `EngagementAgreement` | Retainer and engagement agreements |
| `Invoice` | Invoices and billing statements |
| `TrustRecord` | Trust and client-funds records |
| `Identification` | Identity and verification documents |
| `Authorization` | Releases, consents, authorizations |
| `IntakeRecord` | Intake forms, questionnaires, consultation records |

### Internal work product

| Category value | What it covers |
|---|---|
| `Tracker` | Document and deadline trackers |
| `AuditSummary` | Output of this skill |
| `QCMemo` | Quality-control memoranda |
| `InternalNote` | Internal notes and case memoranda |

### Reference

| Category value | What it covers |
|---|---|
| `ReferenceMaterial` | Rules, forms, procedural references |
| `ClientGuide` | Client-facing guides and explainers |

---

## Part 3 — Routing table

Two axes. Origin selects the top-level folder; category selects the subfolder.

### Financial and disclosure categories

Destination: the discovery folder for the **producing party** under
`{{PARTY_FOLDER_SCHEME}}`, then the subfolder below.

| Category | Default subfolder |
|---|---|
| `CheckingStatement` | Checking Statements |
| `BrokerageStatement` | Brokerage Accounts |
| `RetirementStatement` | Brokerage Accounts |
| `TaxReturn` | Tax Returns |
| `BusinessTaxReturn` | Business Tax Returns |
| `BusinessFinancial` | Business Tax Returns |
| `W2`, `1099`, `K1` | Annual Income Documents |
| `Paystub` | Recent Paychecks |
| `InsuranceDoc` | Life and Health Insurance Documents |
| `Deed` | Deeds |
| `LoanApplication` | Loan Applications |
| `CreditCardStatement` | Credit Cards |
| `MortgageStatement`, `LoanStatement`, `LiabilityDoc` | Other Liabilities |
| `AccountStatement` | Other Account Statements |

The twelve default subfolder names above are the `{{SUBFOLDER_SET_FINANCIAL}}`
default. Buyers commonly rename them; the routing survives renaming because
routing is category-to-slot, and the slot label is configuration.

### Whole-matter categories

| Category group | Default destination |
|---|---|
| `Petition`, `Response`, `Motion`, `MotionResponse`, `Memorandum`, `FinancialAffidavit`, `CertOfCompliance`, `CertOfService`, `Stipulation`, `Withdrawal`, `CourtFiling` | Filed folder for the filing side — **only if the face of the document shows it was filed and accepted** |
| the same categories, unfiled | Drafts |
| the same categories, rejected or returned | Filed, Not Accepted |
| `ProposedOrder` | Drafts until entered |
| `Order`, `Judgment` | Orders |
| `NoticeOfHearing`, `NoticeOfFiling`, `NoticeOther` | Notices |
| `Subpoena` | Notices |
| `Interrogatories`, `InterrogatoryAnswers`, `RequestForProduction`, `ProductionResponse`, `RequestForAdmission`, `AdmissionResponse`, `DeficiencyLetter`, `PrivilegeLog` | Discovery folder for the party who **served** the instrument |
| `DepositionTranscript` | Reports and Agreements |
| `ClientLetter`, `CounselLetter`, `BenchLetter`, `ThirdPartyLetter`, `StatusUpdate` | Correspondence |
| `ExpertReport`, `EvaluationReport`, `MediationReport`, `SettlementAgreement`, `ParentingPlan`, `SupportWorksheet` | Reports and Agreements |
| `EngagementAgreement`, `Invoice`, `TrustRecord`, `Identification`, `Authorization`, `IntakeRecord` | Billing and Retainer |
| `Tracker`, `AuditSummary`, `QCMemo`, `InternalNote` | Notes |
| `ReferenceMaterial`, `ClientGuide` | Research and Education |

**Routing rules that override the table**

1. **Filed status is read off the document, never off its current folder.** A
   clerk stamp, e-filing header, or entry date makes it filed. Absence makes it
   a draft, however polished.
2. **Discovery instruments route by who served them; produced records route by
   who produced them.** These are different questions and get different
   answers.
3. **An executed agreement supersedes its drafts in location, not in
   existence.** File the executed copy in Reports and Agreements; leave drafts
   in Drafts. Never delete a draft.
4. **A document with two plausible destinations is flagged, not split.** One
   document, one destination, chosen by `{{ROLE_REVIEWER}}`.
5. **A category with no configured destination is an install-time error.** At
   run time it means the vocabulary and folder configuration have drifted apart
   — stop, flag it to `{{ROLE_APPROVER}}`, and leave the document in place.
6. **No document is ever routed to a different matter.** A document that
   appears to belong elsewhere is flagged in place.

---

## Part 4 — Vocabulary governance

- Closed set. Free text is never a category.
- One category per document.
- Additions and renames are configuration changes: proposed in the audit
  summary, applied by `{{ROLE_APPROVER}}`, never invented mid-run.
- Every value maps to exactly one destination.
- Retiring a value requires deciding what happens to documents already carrying
  it. Do not retire a value in the middle of a run.
- Every rule or statute reference in this file or in any output derived from it
  carries `⚠️ VERIFY: confirm rule and current text before relying on this.`
  **No case law.**

## Part 5 — Gaps, not fabrications

- Proceeding types this default vocabulary does not specifically cover:
  post-judgment enforcement instruments beyond generic motions, appellate
  documents, and interstate or registration proceedings. These are **unbuilt,
  not absent by design.** If a buyer needs them, add categories through the
  governance process above rather than forcing an existing value.
- Time periods and applicability of disclosure categories vary by proceeding
  type and by local practice, and are not encoded here.
  `[CONFIRM LOCALLY: applicable disclosure categories and time periods — with {{ROLE_APPROVER}}, per the {{CIRCUIT}} circuit, {{COUNTY}} county, and the assigned division]`
