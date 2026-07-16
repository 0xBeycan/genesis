---
name: ideate
description: Open the option space before committing to a decision with real design freedom — a product/feature angle, a name, a design-language direction, an architecture fork with several viable shapes, or a debugging dead-end. Generate genuinely different options, score them against fixed constraints, converge to one, record the rejects. Use when the first idea is about to win by default, or the user asks for alternatives / "more creative". Not for code style — boring code wins (ponytail).
---

# Ideate — diverge before you converge

An agent's default failure is that the first workable idea wins. This skill is
the antidote: a short, deliberate divergence step *before* a commitment —
never instead of one.

## When to use

Decisions with real design freedom: a product or feature angle, a name, a
design-language direction, an architecture fork with several viable shapes, a
debugging dead-end. Also whenever the user asks for alternatives.

When **not** to use: implementation style (boring wins — `ponytail`),
decisions already constrained to one viable shape, reversible trivia.

## Steps

1. **Fix the constraints first.** What MUST hold (from `AGENTS.md`, the
   vision, the budget)? Constraints are not options — write them down.
2. **Generate 3–5 genuinely different options** — different shapes, not
   variants of one; include one deliberate wildcard from outside the obvious
   pattern. Search the web if the space is unfamiliar.
3. **Score against the constraints and goals** — one line per option, honest
   costs included.
4. **Converge to ONE.** Say why it wins, in a sentence.
5. **Record the rejects:** a `docs/memory/decisions.md` line; an ADR when the
   fork was real (`write-adr`). Rejected alternatives are the highest-signal
   part of the record.

## Notes

- Division of labor: `clean-code` = the *shape* of code · `ponytail` = the
  *amount* of code · `ideate` = the *option space* before the commitment.
  They chain, never clash: ideate picks the what; ponytail minimizes the how.
- Diverge on the WHAT, stay boring on the HOW.
- Time-boxed: this is a step, not a session. If the options don't
  meaningfully differ, say so and move on — forced variety is noise.
