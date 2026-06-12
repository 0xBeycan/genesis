# ADR-0002: Two-lane workflow (strict vibe + spec) with shared invariants

## Status

Accepted

## Context

The project starts solo and pre-alpha. Forcing full Spec-Driven Development —
spec-first plus pull-request review — from day one is ceremony for its own sake
when there is no second person to review a PR. But pure "vibe coding" rots: when
speed is the only goal, the memory bank stops being updated, boundaries erode,
and the process quietly breaks. We want speed early without paying for it later.

## Decision

Run work in **two lanes** that share one set of invariants:

- **Vibe lane** (`READ → BUILD → RECORD`) — default while solo/pre-alpha and for
  small/exploratory changes. Skips *upfront* ceremony (spec, plan, ADR-before,
  PR review), never the *trailing* discipline.
- **Spec lane** (`READ → SPEC → PLAN → BUILD → VERIFY → RECORD → COMMIT`) —
  default once work is load-bearing or there is a reviewer.

**Invariants hold in both lanes:** read+record the memory bank every session,
module boundaries, repo language, no secrets, commit only when asked. Full SDD +
PR-review ceremony becomes the default only **after alpha/beta**.

## Consequences

- Early work moves fast without abandoning the memory trail, so escalating a
  piece to the spec lane later just means writing its spec/ADR retroactively.
- Lane-switching is safe by construction: both lanes write the same memory bank
  and obey the same invariants.
- Contributors must consciously pick a lane and escalate on the defined triggers;
  the cost of the vibe lane is the discipline to still run `wrap-session`.
