# Naming Convention — Shipped Default and Configuration Surface

The naming convention is **configuration, not code.** This file ships one
working default and defines the full surface a buyer can change to express
their own convention. Nothing in the default is required.

---

## Part 1 — The shipped default

> **This is a DEFAULT.** It is one practice's convention, shipped so the skill
> works out of the box on day one. It is not a standard, not a requirement, and
> not a recommendation over a buyer's existing convention. If the buyer already
> has a convention that staff know, **configure that one instead.** A convention
> people already follow beats a better one they have to learn.

**Default pattern**

```
{{NAMING_PATTERN}} = <Party><SEP><Category><SEP><Source><SEP><Period>
```

Default settings:

| Setting | Token | Default value |
|---|---|---|
| Token order | `{{NAMING_PATTERN}}` | Party → Category → Source → Period |
| Separator | `{{NAMING_SEPARATOR}}` | underscore |
| Date format | `{{NAMING_DATE_FORMAT}}` | `MonYYYY`; ranges `MonYYYY-MonYYYY`; annual documents the year alone |
| Category vocabulary | `{{CATEGORY_VOCABULARY}}` | The set in `category-vocabulary.md` |
| Party token form | `{{NAMING_PARTY_TOKEN_FORM}}` | Party's first name. Never a last name alone. Never initials. |
| Unknown marker | `{{NAMING_UNKNOWN_MARKER}}` | `Unknown`, always paired with a flag naming which element is unconfirmed |
| Max length | `{{NAMING_MAX_LENGTH}}` | Unset — but see the length note below |
| Case style | `{{NAMING_CASE_STYLE}}` | Each token internally capitalised, no spaces inside a token |
| Version suffix | `{{NAMING_VERSION_SUFFIX}}` | Appended only on a genuine content collision |

**Token definitions, as defaulted**

- **Party** — the first name of the party whose document it is. Not the last
  name, not initials, not "Client" or "OP." Two parties who share a first name
  are a configuration question, not something to solve with an initial.
- **Category** — one value from the active `{{CATEGORY_VOCABULARY}}`. Never a
  free-text description.
- **Source** — the short name of the institution, employer, issuer, court, or
  sender. Shortened deliberately: the common short form rather than the full
  legal entity name with suffixes. If unconfirmed, `{{NAMING_UNKNOWN_MARKER}}`
  plus a flag.
- **Period** — the period the document covers, in `{{NAMING_DATE_FORMAT}}`.
  For a statement, the statement period. For an annual return or wage
  statement, the tax year. For a court document, the filing or entry date. For
  correspondence, the date sent.

**Default shape, with tokens rather than real values**

```
<FirstName>_<Category>_<ShortSource>_<Period>
```

**Length note.** Some storage and sync paths impose a total path-length limit.
Because folder depth varies by buyer, set `{{NAMING_MAX_LENGTH}}` to whatever
leaves headroom in the buyer's structure and shorten the Source token first
when a name exceeds it. Never shorten Category, and never drop Period.

---

## Part 2 — Configuration surface

Four dimensions are configurable, plus five secondary settings.

### 2.1 Token order — `{{NAMING_PATTERN}}`

Declare the pattern as an ordered list of the tokens below, joined by
`{{NAMING_SEPARATOR}}`.

| Token | Meaning | Required? |
|---|---|---|
| `Party` | Whose document it is, in `{{NAMING_PARTY_TOKEN_FORM}}` | Optional |
| `Category` | One value from `{{CATEGORY_VOCABULARY}}` | **Required in every configuration** |
| `Source` | Institution, employer, issuer, court, or sender | Optional |
| `Period` | Coverage period or document date | **Required in every configuration** |
| `Matter` | Matter identifier or number | Optional |
| `Producer` | Which side produced it | Optional |
| `Sequence` | Zero-padded counter | Optional |
| `Bates` | Bates or production number | Optional |
| `DocDate` | Filing, entry, or execution date, distinct from coverage period | Optional |
| `Status` | Draft / Executed / Filed / Served | Optional |

**Constraints.** `Category` and `Period` are required in every configuration —
they are what makes a filename sortable and auditable. A configuration that
omits either is rejected at install. Everything else is the buyer's choice.

**Sort behaviour.** Whichever token comes first determines how a folder listing
groups. Leading with `Party` groups by person; leading with `Category` groups
by document type; leading with `Period` or a date-first format gives
chronological order in any file browser. Choose deliberately — this is the
single most consequential configuration decision, because it decides what
staff see when they open a folder.

### 2.2 Category vocabulary — `{{CATEGORY_VOCABULARY}}`

A closed set. Full default set, financial and non-financial, in
`category-vocabulary.md`.

Rules that hold in every configuration:
- **Closed set.** Never free text. A document that fits no category is flagged,
  not described.
- **One value per document.** A document spanning two categories is flagged for
  `{{ROLE_APPROVER}}` to assign.
- **Additions are a configuration change,** proposed in the audit summary and
  applied by `{{ROLE_APPROVER}}` — never invented mid-run.
- Every category must map to exactly one destination folder in the routing
  table. A vocabulary value with no destination is an install-time error.

### 2.3 Date format — `{{NAMING_DATE_FORMAT}}`

| Option | Single | Range | Sorts chronologically? |
|---|---|---|---|
| `MonYYYY` | month abbreviation + year | `MonYYYY-MonYYYY` | No |
| `YYYY-MM` | year-month | `YYYY-MM_YYYY-MM` | Yes |
| `YYYYMMDD` | full date, no delimiter | `YYYYMMDD-YYYYMMDD` | Yes |
| `YYYY-MM-DD` | full date, delimited | `YYYY-MM-DD_YYYY-MM-DD` | Yes |
| `YYYY` | year only | `YYYY-YYYY` | Yes |

Choose one and apply it to every document. Mixed formats inside one matter
destroy sort order and are the most common convention failure.

For annual documents — tax returns, annual wage and income statements — the
year alone is correct regardless of the chosen format. Configure
`{{NAMING_DATE_FORMAT_ANNUAL}}` if the buyer wants a different form there.

If a date cannot be confirmed from the document's content, use
`{{NAMING_UNKNOWN_MARKER}}` and flag. **Never infer a date from a folder name,
a filesystem timestamp, or an adjacent document.**

### 2.4 Separator — `{{NAMING_SEPARATOR}}`

| Option | Note |
|---|---|
| Underscore | Survives every context. Safe default. |
| Hyphen | Safe, but collides visually with hyphens inside date ranges |
| Space | Legible, but breaks in URLs, scripts, and some sync paths |

Constraints in every configuration:
- One separator character, used only between tokens — never inside a token.
- Never a character reserved by a filesystem or forbidden by a storage
  provider. Excluded in all configurations: `/ \ : * ? " < > |`
- No leading or trailing separator, no doubled separator where an optional
  token is empty. Collapse cleanly.
- Do not use the same character as the intra-range delimiter in
  `{{NAMING_DATE_FORMAT}}`.

### 2.5 Secondary settings

| Token | What it controls |
|---|---|
| `{{NAMING_PARTY_TOKEN_FORM}}` | First name / first + last initial / role label / matter-party code |
| `{{NAMING_UNKNOWN_MARKER}}` | The literal used for an unconfirmed element. Must be visually obvious in a folder listing — its whole job is to be noticed. |
| `{{NAMING_MAX_LENGTH}}` | Total filename length ceiling; Source shortens first |
| `{{NAMING_CASE_STYLE}}` | Internal capitalisation per token; applied consistently |
| `{{NAMING_VERSION_SUFFIX}}` | Applied only on genuine content collision, never as a general versioning scheme |

---

## Part 3 — Configuration worksheet

The installer fills this once. It is the whole convention.

```
{{NAMING_PATTERN}}            = <ordered token list; must include Category and Period>
{{NAMING_SEPARATOR}}          = <one character>
{{NAMING_DATE_FORMAT}}        = <one option from 2.3>
{{NAMING_DATE_FORMAT_ANNUAL}} = <optional override for annual documents>
{{CATEGORY_VOCABULARY}}       = <default set, or the buyer's own>
{{NAMING_PARTY_TOKEN_FORM}}   = <form>
{{NAMING_UNKNOWN_MARKER}}     = <literal>
{{NAMING_MAX_LENGTH}}         = <integer or unset>
{{NAMING_CASE_STYLE}}         = <style>
{{NAMING_VERSION_SUFFIX}}     = <form>
```

## Part 4 — Install-time validation

Reject the configuration and ask again if any of these fails:

- [ ] `Category` present in `{{NAMING_PATTERN}}`.
- [ ] `Period` present in `{{NAMING_PATTERN}}`.
- [ ] `{{NAMING_SEPARATOR}}` is a single character and not filesystem-reserved.
- [ ] `{{NAMING_SEPARATOR}}` differs from the date-range delimiter.
- [ ] `{{NAMING_DATE_FORMAT}}` is one option, applied everywhere.
- [ ] Every value in `{{CATEGORY_VOCABULARY}}` maps to exactly one destination
      folder.
- [ ] `{{NAMING_UNKNOWN_MARKER}}` is set and visually conspicuous.
- [ ] No configured value contains `Click here to enter text.` or `XXXXXXXX`.
- [ ] No configured value contains a storage path, drive letter, site name,
      tenant name, or URL.
- [ ] The buyer has confirmed whether they are adopting the default or
      supplying their own — and knows the default is a default.
