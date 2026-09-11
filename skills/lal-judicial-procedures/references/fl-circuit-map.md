# Florida Judicial Circuits — County Map and Starting URLs

**This file is a starting point to verify. It is never data to rely on.**

Use it for two things only: converting a county to its circuit number, and finding a starting point
for that circuit's official website. It deliberately contains **no** judge names, no division
assignments, no judicial-assistant contacts, and no officer procedures — those are exactly the facts
that go stale, and they are obtained by the live search in Step 2 of the skill, every time.

Treat every URL below as a starting point, not a guaranteed-current address. Always confirm it
resolves before relying on it. If it does not, **search for the circuit's current official site by
name — never guess at a replacement URL.** Circuit sites get restructured; a dead link here is
expected maintenance, not a sign the skill is broken.

County-to-circuit assignments are set by statute and are stable. Everything else on this page is not.

---

## All 20 circuits

| Circuit | Counties | Starting URL |
|---|---|---|
| 1st | Escambia, Okaloosa, Santa Rosa, Walton | firstjudicialcircuit.org |
| 2nd | Franklin, Gadsden, Jefferson, Leon, Liberty, Wakulla | search: "2nd judicial circuit Florida official site" |
| 3rd | Columbia, Dixie, Hamilton, Lafayette, Madison, Suwannee, Taylor | search: "3rd judicial circuit Florida official site" |
| 4th | Clay, Duval, Nassau | jud4.org |
| 5th | Citrus, Hernando, Lake, Marion, Sumter | circuit5.org |
| 6th | Pasco, Pinellas | jud6.org |
| 7th | Flagler, Putnam, St. Johns, Volusia | circuit7.org |
| 8th | Alachua, Baker, Bradford, Gilchrist, Levy, Union | circuit8.org |
| 9th | Orange, Osceola | ninthcircuit.org |
| 10th | Hardee, Highlands, Polk | jud10.flcourts.org |
| 11th | Miami-Dade | jud11.flcourts.org |
| 12th | DeSoto, Manatee, Sarasota | jud12.flcourts.org |
| 13th | Hillsborough | fljud13.org |
| 14th | Bay, Calhoun, Gulf, Holmes, Jackson, Washington | search: "14th judicial circuit Florida official site" |
| 15th | Palm Beach | 15thcircuit.com |
| 16th | Monroe | keyscourts.org |
| 17th | Broward | 17th.flcourts.org |
| 18th | Brevard, Seminole | flcourts18.org |
| 19th | Indian River, Martin, Okeechobee, St. Lucie | circuit19.org |
| 20th | Charlotte, Collier, Glades, Hendry, Lee | ca.cjis20.org |

**Circuits with no starting URL above (2nd, 3rd, 14th):** these are search entries on purpose rather
than a guessed address. Search by circuit name and confirm the result is the circuit's own site before
using it.

**Statewide fallback:** flcourts.gov publishes a circuit directory and links out to each circuit. Use
it when a circuit URL above is dead, and when a circuit publishes nothing usable at its own address.

---

## Where a county is not the whole answer

- **Multi-county circuits hold court in more than one courthouse,** and procedures, scheduling method,
  and remote-appearance practice can differ by courthouse within the same circuit. Resolving the
  circuit does not resolve the location.
  [CONFIRM LOCALLY: which courthouse the matter is assigned to and whether procedures differ there —
  with the judicial assistant]
- **Division numbering is circuit-specific and gets renumbered.** Never infer a division from a
  circuit, and never carry a division designation across circuits.
- **Some circuits publish procedures by division rather than by named officer.** If a search on the
  officer's name returns nothing, search the division.
- **County clerk practice is separate from court practice.** Filing mechanics, fees, cover sheets, and
  what gets filed versus only served are clerk questions.
  [CONFIRM LOCALLY: filing mechanics and required cover sheets — with the clerk of court in
  {{COUNTY}} County]

---

## Where to find what this file intentionally omits

| What you need | Where it comes from |
|---|---|
| Which officer is in which division right now | Live search, Step 2 query 2 — every time |
| An officer's motion practice, notice days, page limits | Live search, Step 2 queries 1 and 3 |
| Proposed order format and submission method | Live search, plus judicial assistant confirmation |
| Judicial assistant contact | The circuit's published directory; confirm by phone. **Never stored here.** |
| Scheduling method (UMC, portal, chambers) | Live search, plus judicial assistant confirmation |
| Remote/video appearance details | Live search, **plus mandatory 48-hour judicial assistant verification** |
| Standing and administrative orders | Live search, Step 2 query 4 |
| General magistrate procedure and objection/exception windows | Florida Family Law Rules of Procedure, plus circuit administrative order, plus the per-case order of referral |
| Mandatory disclosure obligations | Florida Family Law Rules of Procedure, plus any case management order in the matter |

---

## Rules that sit above every circuit

Statewide rules override circuit-level practice. Two categories to check whenever a circuit source
seems to impose something unusual:

- **Filing and signing obligations** are governed by the Florida Rules of General Practice and
  Judicial Administration, including the signer's obligations regarding the accuracy of authorities
  cited in a filing, and the availability of sanctions for a filing inconsistent with that
  representation. Where a circuit source appears to impose a **local** certification or disclosure
  requirement concerning the use of automated or generative tools, check whether a statewide
  administrative order has made the statewide approach exclusive and prohibited circuit-level
  variations — if so, the local requirement is superseded and should be flagged as such rather than
  applied. Report the current obligation as the statewide signing representation, not as a local form.
  ⚠️ VERIFY: confirm rule and current text before relying on this.
  [CONFIRM LOCALLY: whether any local certification requirement remains in force in this circuit —
  with the judicial assistant and with {{ROLE_APPROVER}}]
- **Non-automation standing orders are unaffected** by the above and still apply on their own terms.
  Federal court is outside this analysis entirely; individual federal judges maintain their own
  standing orders.
  ⚠️ VERIFY: confirm rule and current text before relying on this.

Both of these move. Verify at the time of use rather than trusting this paragraph's framing.

---

## How to maintain this file

1. Pick the circuit the firm actually appears in most.
2. Confirm the URL still resolves and still leads to a judge or division directory.
3. If it moved, replace the URL here and note the date you checked.
4. If the firm practices primarily in one circuit, build a notes file for it using the pattern in
   `circuit-starter-example.md`. Copy the pattern, not the example's content.
5. Do not add officer names, division assignments, or judicial-assistant contacts to this file, ever,
   no matter how convenient. That is the boundary that keeps the skill from quietly becoming a stale
   database.

Last structural build of this file: {{DATE}} of installation.
Last confirmed by a human: [CONFIRM LOCALLY: who checked these URLs and when — record it here]

This file should never be the last word on anything. It exists to save the skill a step, not to
replace Step 2 of the skill.
