# ADR-0003: Test-first discipline with a stack-appropriate runner

## Status

Accepted

## Context

The skeleton left testing implicit: CI had a `Test` slot, the Definition of Done
had a "tests pass" checkbox, and `conventions.md` had a `## Testing` placeholder —
but nothing **required** a project to configure a test runner or to drive design
with tests. Read as "as applicable", testing read as optional, so a forked
project could ship behavior with no test and still pass every gate. We want every
project bootstrapped from Genesis to inherit testing as a first-class discipline,
without hardcoding a single runner (provider independence still holds — the runner
is a stack choice).

## Decision

- **Every project configures a stack-appropriate test runner in Phase 1**
  (Vitest/Jest, pytest, `go test`, …) and wires its command into `AGENTS.md` §6
  and `.github/workflows/ci.yml`. A project is never set up without one.
- **Test-first in the spec lane.** The loop gains a `TEST` step
  (`READ → SPEC → TEST → PLAN → BUILD → VERIFY → RECORD → COMMIT`): turn the
  spec's acceptance criteria into a failing test before the code. This refines
  the spec-lane loop from [ADR-0002](0002-two-lane-workflow.md).
- **Behavior-changing code ships with a test** as a shared invariant of *both*
  lanes — test-first in the spec lane, may follow the code in the vibe lane, but
  lands in the same change either way.
- **Tests assert behavior and contracts, not implementation;** each
  provider-independent adapter gets a contract test. Coverage is a floor
  (default ≥80% on changed code), not a target.

## Consequences

- The interview now always asks about the test runner and levels; the Definition
  of Done and `conventions.md` §Testing enforce it.
- Refactors stay safe because the suite pins behavior, not internals.
- Slight upfront cost per change (writing the test), paid back by a green,
  trustworthy suite that lets later agents and humans change code with confidence.
- The vibe lane keeps its speed: the test may follow the code there, so long as
  it ships together.
