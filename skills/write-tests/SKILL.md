---
name: write-tests
description: Drive a change with tests. Use whenever you add or change behavior — to turn acceptance criteria into a failing test first (spec lane), or to pin new/fixed behavior with a test that ships in the same change (vibe lane). The how-to companion to the test-first golden rule.
---

# Write tests

## When to use

Any time behavior changes — a new feature, a bug fix, a refactor that needs a
safety net. Test-first in the spec lane; the test may follow the code in the vibe
lane, but lands in the same change either way. See `conventions.md` §Testing and
[ADR-0003](../../docs/architecture/adr/0003-test-first-discipline.md).

## Steps

1. **Find the behavior.** What observable outcome or contract should hold? For a
   bug, reproduce it as a failing assertion first.
2. **Pick the level** — unit / integration / e2e-contract, per the level guide
   in `conventions.md` §Testing.
3. **Write the test against behavior, not implementation** — assert outcomes
   and contracts, not internals (adapter → contract test; rules in
   `conventions.md` §Testing).
4. **Watch it fail** for the right reason (red) before writing the code.
5. **Implement** the smallest change that makes it pass (green).
6. **Run the whole suite** — no skipped or flaky tests left behind.

## Notes

- The runner is stack-specific ({{Vitest/Jest · pytest · go test · …}}); its
  command lives in `AGENTS.md` §6 and `.github/workflows/ci.yml`.
- Tests are part of the Definition of Done — run `review-own-diff` and
  `wrap-session` before calling a change complete.
