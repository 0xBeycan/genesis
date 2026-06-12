---
name: review-own-diff
description: Self-review a change before declaring it done. Use after finishing an edit and before wrap-session — checks the diff against the Definition of Done and the golden rules, catching boundary breaks, secrets, and missing specs/ADRs.
---

# Review your own diff

## When to use

After building, before calling anything complete — in either lane. This is the
cheapest place to catch the problems the vibe lane tends to create.

## Steps

1. Read the actual diff (don't review from memory).
2. Check against the Definition of Done (`docs/process/definition-of-done.md`).
3. Check the golden rules: module boundaries intact? no secrets? repo language?
   contract exists before the code that needs it? comments explain "why"?
4. If the change became load-bearing, escalate to the spec lane: write the
   spec/ADR retroactively (see `write-adr`).
5. Fix what you found, then run `wrap-session`.

## Notes

Be honest about findings — report what's still broken rather than smoothing over
it. A failing check named out loud is worth more than a green claim.
