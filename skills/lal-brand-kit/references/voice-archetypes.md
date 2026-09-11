# Voice Archetype Library

A taxonomy of professional registers observed in real Florida family law
correspondence. The installer picks **exactly one** archetype as
`{{VOICE_ARCHETYPE}}` — the practice's house register — and supplies
`{{VOICE_ALWAYS_PHRASES}}` and `{{VOICE_NEVER_PHRASES}}` of its own.

## How this library was built

Six archetypes, not a round number. Each one was derived from a distinct
register found in the correspondence specifications in this corpus —
`correspondence/*/**.spec.md`, `## Voice notes` sections. Those specs record
observed voice evidence from real sent mail and template libraries. They
contain no client identities and none is introduced here.

The evidence showed something more useful than a single house voice: the same
practice used **six materially different registers depending on who was being
written to and what the letter had to accomplish.** A warm client chase and a
bench transmittal were not the same voice with the tone dial moved — they had
different sentence lengths, different person, different attitudes toward
contractions, different rules about adjectives, and different definitions of a
defect. Those six are the archetypes below.

## How to choose

Read the "suits" line first. Most family law practices have a dominant
client-facing register (A or B) and inherit the other four from the audience
rather than choosing them. So:

- **Pick one archetype as the house register.** It governs client-facing
  output — the choice the buyer actually makes.
- **Archetypes C through F are audience-forced, not chosen.** When the reader
  is the bench, opposing counsel, a records custodian, or the reader of a
  money document, the audience selects the archetype regardless of house
  preference. The house archetype still supplies phrase banks and structural
  defaults.
- **Pick a register and hold it inside one document.** The most common
  observed defect is drifting from a warm register into a flat one mid-letter,
  or the reverse. Bookend warmth (rule 8 in the skill); do not interleave it.
- The eight voice rules in `lal-brand-kit.SKILL.md` §4.2 apply to every
  archetype. An archetype tunes register; it never suspends a rule.

---

## A — Warm Directive

**What it sounds like.** A capable person who likes you, has read your file,
and is telling you exactly what to do. Credit before correction: it names what
you sent, in detail, and what it made possible, before naming the gap. It
shrinks the ask linguistically even when the list is long. It acknowledges the
burden out loud once, then gets on with it.

**Sentences and diction.** Short paragraphs, two to four sentences.
Contractions throughout. Em dashes carry the explanatory clauses. Short
ALL-CAPS or `{{HEADING_CASE}}` section heads so the reader can scan — the same
heads reused across letters so clients learn the shape. Second person.
Imperative mood for instructions. Sentence fragments for emphasis, sparingly.
Selective ALL-CAPS inside body text for client-conduct instructions only.

**Always.**
- Name what arrived before naming what is missing.
- Give every ask a reason and a both-ways answer, so the reader can comply
  even with a negative.
- Minimise the miss: "one gap left," "that one statement."
- State the consequence once, in one short paragraph, then drop it.
- Commit to a reciprocal action at the close — say what the practice will do
  next, not only what the reader must do.
- Name the reader's emotional state at most once, early, then never again.
- Explain *why* a requirement exists, not only that it exists.
- Tell the reader what is needed **first**, rather than presenting the whole
  list as equally urgent.
- Time-box every forward commitment with a concrete interval.

**Never.**
- Escalating tone within a single letter.
- Repeating the consequence.
- Sympathy language past the first mention.
- Bare demands with no stated reason.
- "Please provide" with no reason and no alternative answer.
- Exclamation points in body copy.
- Predicting an outcome.
- Legalese, rule citations, or Latin.

**Suits.** Client emails and letters, document requests and chases, missed
deadline reminders, welcome and onboarding, status updates, guides,
explainers, roadmaps, newsletters. **This is the default house register for a
client-facing family law practice.**

**Salutation family for `{{CLOSING_SALUTATION}}`.** Warm and brief.

---

## B — Plain-Spoken Level

**What it sounds like.** A person setting the record straight with someone who
has every reason to distrust them. Radically plain. It is upfront about its own
position, names the emotional stake, and explicitly disclaims hostility. In
the source corpus this was the register used to write to an unrepresented
adverse party, and it was flagged as the highest-value voice in that lane —
because it is the hardest to fake and the easiest to get wrong.

**Sentences and diction.** Very short. Contraction-heavy. Second person.
Full-stop fragments used as paragraphs: "That's it." No citations, no Latin,
no defined terms, no numbered clauses. Concrete nouns over categories: "the
big stuff," not "material assets." First person singular where the writer is
taking a position personally.

**Always.**
- "I want to be upfront with you" — declare position before making an ask.
- State what the document is *about*, in one sentence, in ordinary words.
- Disclaim hostility explicitly where hostility could reasonably be assumed.
- Name options with descriptive names, not abstract letters, and follow each
  with a one-line plain-English summary of its practical effect.
- Tell the reader plainly that they may get their own counsel.
- Reason before ask, always.

**Never.**
- Rule numbers, statute numbers, or formal citation format.
- Defined terms in quotes.
- Any adjective about the reader.
- Anything that reads as a threat.
- Anything that reads as legal advice to the reader.

**Suits.** Letters to unrepresented parties, plain-language explainers, DIY
and self-help material, intake-stage communications, social captions, public
educational content. **Also the right house register for a practice whose
brand promise is clarity and de-jargoning.**

`[CONFIRM LOCALLY: what a communication to an unrepresented adverse party may and may not contain — with {{ROLE_APPROVER}}]`

---

## C — Neutral Procedural

**What it sounds like.** Nothing. Deliberately. The letter delivers a document
or asks a logistical question and gets out. The enclosing sentence does the
whole job; everything else is identification, position, format and thanks.
Neutrality here is a drafting rule, not a tone preference — a characterising
adjective is treated as a defect.

**Sentences and diction.** Two paragraphs typical, four maximum. No
contractions in the formal form. Passive-to-the-court construction: the
practice does not put itself at the head of the sentence. Third person for the
court throughout; direct address only in the single questions line. Factual
bullets carry dates. Issue lists carry no adjectives.

**Always.**
- One-line identification of the matter and the writer's role.
- Every request phrased so it is answerable with a yes, a no, or a date.
- Ask what the division or clerk requires rather than assuming a practice.
  This is the single most repeated move in the source lane.
- Attach a `[CONFIRM LOCALLY: ...]` marker at every point where format or
  procedure varies by circuit, county, division, judge, or clerk.
- Plain thanks at the close.

**Never.**
- Argument, prediction, or persuasion of any kind.
- Adjectives about any party or position.
- Assuming a format the division has not confirmed.
- Colour bar, CTAs, or service badges. This register's documents are
  brand-silent.

**Register note.** In informal scheduling email the register loosens markedly
— contractions, one-line messages, time-of-day greetings, plain thanks — but
the substance stays purely logistical. Treat that as the same archetype in a
lighter form, not a different archetype.

**Suits.** Bench and judicial-assistant correspondence, scheduling and
coordination email, transmittal and cover letters, notices, clerk
correspondence, calendar requests.

`[CONFIRM LOCALLY: submission format, courtesy-copy expectations, and whether a separate filed notice is required — with {{ROLE_APPROVER}}, per {{CIRCUIT}}, {{COUNTY}}, division, and {{JUDGE}}]`

---

## D — Anchored Adversarial

**What it sounds like.** Immovable and scrupulously fair. It concedes first,
fully, and without hedging, then states disagreement as a position plus a
basis. Its most distinctive move is answering an aggressive position by
applying the other side's own logic symmetrically rather than rejecting it.
Where the other side has asserted something outside the record, it requests
written confirmation instead of arguing.

**Sentences and diction.** Measured, medium-length, declarative. No
contractions. Two-clause disagreement formula: "My client does not agree to X,
as Y" — no adjectives. Enumerated computations. Clock times on hard deadlines.
Every substantive assertion anchored to a rule, a statute, or a specific
identified document.

**Always.**
- Open with a one-sentence representation statement, even where counsel plainly
  knows it.
- State the agreed items before the not-agreed items.
- Anchor each assertion to a rule, statute, or named document — each carrying
  `⚠️ VERIFY: confirm rule and current text before relying on this.`
- Show the computation: state the method so the number is checkable, number
  the lines, attach the schedule.
- Label exactly one figure as authorised, and only one.
- Give every deadline a concrete date, a clock time where the deadline is
  hard, and a named consequence.
- State reciprocity explicitly in courtesy correspondence.
- Request written confirmation rather than disputing an off-record assertion.

**Never.**
- Case law. Rules and statutes only.
- Any characterisation of the other side's motive or competence.
- A conclusion without its basis in the same sentence.
- A number without its method.
- Emotional register of any kind.

**Suits.** Opposing counsel correspondence, negotiation and settlement
transmittals, courtesy and extension letters, deficiency notices to counsel,
scheduling disputes.

---

## E — Protective Declarative

**What it sounds like.** The money voice. Formal, declarative, and
typographically emphatic in exactly the places that protect the practice. It
grants a courtesy and fences it in the same breath: the waiver is given,
priced as a loss, limited to one time, and stripped of future credit value —
all inside one passage. Where archetype A puts a softener on every ask, this
register puts emphasis on every protection.

**Sentences and diction.** Declarative, never imperative. No contractions. No
em-dash asides. ALL-CAPS section heads. A bold run-in `Important:`.
Capitalised status lines. Selective capitalised negation inside a sentence,
placed only on the clause that limits an obligation. Every figure on its own
line.

**Always.**
- Show the arithmetic: fees, credits, payments, balances each on their own
  line. Nothing netted silently.
- Copy fee and scope language verbatim from the executed agreement.
- State the status explicitly rather than letting the reader infer it.
- Grant, then fence — in one passage, never in two.
- Land the typographic emphasis only on protective sentences. Emphasis
  elsewhere dilutes it.
- Close with the scope fence: no further work unless a new written agreement
  is signed.
- State a consequence as the reader's responsibility, not as the practice's
  regret.

**Never.**
- Contractions or warmth in the operative blocks.
- Summarising or recalculating a figure that appears in an executed document.
- Apologising for a fee, a balance, or a limit.
- Escalating or repeating within the document.
- Inventing a rate, a cadence, or a credit. Missing figures are marked gaps.

**Suits.** Fee and billing correspondence, invoices and statements, trust and
retainer accountings, closing statements, waiver letters, disengagement for
non-payment, scope-limitation notices.

**Register note.** Warmth is bookended here too — thanks at the top, warmth at
the bottom, flat arithmetic between. The register does not shift when the news
is bad; there is no separate "bad exit" voice.

---

## F — Institutional Limiting

**What it sounds like.** Authority speaking, not a person. Every paragraph
either grants or limits. It never says "I think"; it says "I am required to."
Polite-but-immovable in its softer form: it opens with a social courtesy, then
pivots entirely to authority, invites the reader to consult their own counsel,
and observes in the next sentence that the requirement is clear regardless.

**Sentences and diction.** Flat. First person singular for the office's own
authority and obligations. Bold run-in heads. Bare imperatives for
preservation and suspension instructions. Dense enumeration. Zero relationship
language. One concession only — a paragraph tailoring cost or burden. In its
hardest form it becomes instrument-voice rather than letter-voice: decimal-
numbered clauses, `shall`, defined terms in quotes on first use, drafted to be
signed or served rather than read.

**Always.**
- State the source of authority and its scope in the first paragraph.
- Say what will not be disclosed, alongside what is required.
- State the reason for the contact before the ask.
- Give a compliance path and, where burden is real, a cost-tailoring
  paragraph.
- Invite the reader to consult counsel — then restate the requirement.
- Use "without further delay" rather than a softened deadline where the
  authority is already clear.

**Never.**
- Warmth, hedging verbs, or relationship language.
- Explaining methodology to a collateral contact who did not ask.
- Any characterisation of a party.
- Brand colour, CTAs, or badges. Instrument-voice documents are brand-silent
  and are routed to the filings standard when they will be filed or served.

**Suits.** Preservation and suspension notices, records requests to
custodians, collateral contact letters, appointment-notification letters,
subpoena cover correspondence, releases and consents.

`[CONFIRM LOCALLY: service method, custodian requirements, and whether the document must be filed rather than sent — with {{ROLE_APPROVER}}]`

---

## Distinctions at a glance

| | Person | Contractions | Paragraph length | Adjectives on a party | Emphasis lands on | Predicts |
|---|---|---|---|---|---|---|
| A Warm Directive | 2nd / 1st plural | Yes | 2–4 sentences | Never | The next action | Never |
| B Plain-Spoken Level | 2nd / 1st singular | Heavy | 1–3 sentences, fragments | Never | Honesty of position | Never |
| C Neutral Procedural | 3rd (court) | Formal: no. Email: yes | 1–3 sentences | Defect | Nothing | Never |
| D Anchored Adversarial | 1st singular / 3rd | No | 3–5 sentences | Defect | The anchor and the arithmetic | Never |
| E Protective Declarative | 1st plural / passive | No | 2–4 sentences | Never | Protective clauses only | Never |
| F Institutional Limiting | 1st singular (office) | No | Enumerated clauses | Never | The limit | Never |

Every archetype forbids prediction and forbids adjectives characterising a
party. Those two are corpus-wide, not archetype-specific.

## Gaps — do not fabricate

- No archetype here is derived from post-judgment enforcement or appellate
  correspondence; the source corpus did not contain enough of either to
  characterise a register. If a buyer needs one, treat it as unbuilt and flag
  it, rather than stretching D to cover it.
- Salutation and sign-off wording is install-time
  (`{{CLOSING_SALUTATION}}`). The library records which family fits which
  archetype but supplies no phrasing of its own.
- Archetype selection does not authorise content. Legal analysis, strategy,
  and outcome assessment stay out of every archetype and route to the
  practice's legal skills.
