# How This Skill Works (Plain English)

## What a "skill" is

A skill is a folder of instructions that tells the assistant how to handle a specific kind of task the
same way every time — the way a well-run firm has a standard procedure for a specific kind of file.
The assistant reads the folder, follows the process whenever the topic comes up, and does not have to
be re-taught in every conversation.

This skill's job: whenever a judge, general magistrate, hearing officer, division, or Florida county
comes up, go look up that officer's **current** procedures on the actual court website — live, every
time — instead of guessing or relying on what it remembers.

## Why "live lookup, never cached" matters here specifically

The assistant's training data has a cutoff date. Judges rotate between divisions. Judges retire, lose
elections, and get reassigned mid-case. Divisions get renumbered. Standing orders get replaced.
Judicial assistants change. Remote-appearance links get reissued.

An answer from memory about "what that judge requires" may be describing a judge who is no longer in
that division, or a procedure that was replaced two years ago — and **there is no way to tell from the
answer alone that it is stale.** It reads exactly like a current answer.

This skill removes the choice. The search is mandatory, not optional. The officer's procedures are
never treated as a fact already known.

**It searches again even if you asked about the same judge earlier in the same conversation.** That
looks redundant and is not. Procedures pages get updated without notice, and "I already looked this
up" is precisely the assumption that produces a missed requirement.

## This skill needs live web search — and that is a real dependency

Most of this product works from firm-configured sources. This skill is one of only two parts that
reach out live, and it does so by design, because the facts change faster than any file can be
maintained.

If live search is not available in a session, the skill should say so up front rather than answering
anyway. What you should then expect from it: the circuit and county mapping, the general rule
framework, and the checklist structure — with every officer-specific detail marked as unverified. What
you should **not** accept from it in that state: a confident statement about what a particular judge
requires.

It only uses official Florida sources — the state courts site, individual circuit court sites, the Bar,
and the Legislature. Not blogs, not listserv summaries, not judge-analytics products, not the firm's
own old notes.

## What is in `references/`, and why it is not "cheating"

Three files, none of which contains a judge's requirements as a stored fact:

1. **`fl-circuit-map.md`** — the 20 Florida circuits, which counties fall in each, and a starting-point
   website per circuit. It saves a step. It does not tell the assistant what any officer requires. It
   deliberately holds no officer names, no division assignments, and no judicial-assistant contacts.
2. **`circuit-starter-example.md`** — a worked example of the note-taking pattern, using one circuit
   purely as an illustration. The circuit shown is an example, not the firm's home jurisdiction. Copy
   the pattern for whichever circuit you actually appear in.
3. **`how-this-works.md`** — this file.

Every one of these is **a starting point to verify, never data to rely on.** The live search runs
regardless of what any of them says. If a reference file and a live search disagree, the live search
wins and the reference file gets corrected.

## Why no names are stored

You will notice the reference files never record a judge's or judicial assistant's name. Two reasons,
both practical:

1. **Names go stale faster than anything else in the file,** and a stale name looks current.
2. **A judge's name written next to a client matter re-identifies the matter.** A file that says which
   judge is handling which case is a confidentiality exposure that a circuit map is not.

The assistant may name the officer in a session response, because that came from a live search you can
check. It does not write the name into a reusable file.

## What good use of this skill looks like

- You mention a judge's name or a division, and it searches before saying anything about procedures —
  even if you asked about that judge earlier in the conversation.
- It tells you **what it found, where it found it, and when it verified it** — and flags anything that
  looks old, undated, or uncertain.
- When two sources disagree, it shows you both and says which is more recent, instead of quietly
  picking one.
- When it finds nothing, it says so and tells you what it searched — rather than producing a plausible
  answer to fill the space.
- Anything it cannot verify comes back to you as `[CONFIRM LOCALLY: ...]` with who to ask, not as an
  assumption.
- You still call chambers to confirm anything time-sensitive. A remote hearing link always carries a
  48-hour verification flag, no matter how authoritative the source looked — that is the single most
  common way an appearance gets missed.

## What this skill is not

- **Not a substitute for calling chambers.** It flags that step; it does not replace it.
- **Not a guarantee the court's own page is current.** Courts update their procedures pages on their
  own schedule, and some do not.
- **Not a database of judges.** It is a process. If it ever starts answering from a stored list, that
  is a defect.
- **Not legal advice about what to file.** It is a research step that feeds your own judgment.
- **Not a source of case law.** Case citations are handled by a separate protocol. This skill deals in
  statutes, rules, and administrative orders only, each carrying its own verify marker.

## Who does what

| Step | Owner |
|---|---|
| Runs the search, produces the summary and checklist | The assistant, working with {{ROLE_DRAFTER}} |
| Confirms anything marked `[CONFIRM LOCALLY: ...]` | {{ROLE_DRAFTER}}, by phone or portal |
| Reviews the output before it advances | {{ROLE_REVIEWER}} |
| Approves, signs, and files | {{ROLE_APPROVER}} |
| Time and activity logged | {{PM_SYSTEM}}, before the session closes |

Files are reached and saved through the session's file connector and land in {{DMS}} — never a local
path or a mapped drive.
