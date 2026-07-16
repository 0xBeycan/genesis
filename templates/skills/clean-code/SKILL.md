---
name: clean-code
description: General, language-agnostic code-quality rules. Use while writing or refactoring any code in this repo to keep files small, names clear, errors handled, and boundaries respected — the baseline that keeps the vibe lane from rotting.
---

# Clean code (general)

## When to use

Always, while writing or changing code — independent of stack or lane.

## Rules

- **Small, single-responsibility files.** No god classes/functions. If it does
  two unrelated things, split it.
- **Names say intent.** Prefer clear over clever; no cryptic abbreviations.
- **Respect module boundaries.** Domains don't import each other; shared
  contracts live in one place.
- **Handle errors explicitly.** Type them where the stack allows; log with
  context; never silently swallow.
- **Validate at boundaries.** Trust nothing crossing an edge (input, config, IO).
- **Comments explain "why", not "what".** In the repo language only.
- **No dead code, no commented-out blocks.** Delete it; git remembers.
- **Deny by default** for anything authorization-related.

## Notes

This is the always-on baseline. Project-type skills (added after the interview)
layer stack-specific conventions on top — they refine these rules, never relax
them.

`ponytail` is the always-on sibling: this skill governs the **shape** of the
code, `ponytail` governs **how much** of it exists. They apply together.
