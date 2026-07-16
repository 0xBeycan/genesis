# ADR-0007: Product/workshop split and process recalibration

## Status

Accepted — partially supersedes [ADR-0002](0002-two-lane-workflow.md),
[ADR-0003](0003-test-first-discipline.md),
[ADR-0004](0004-vendor-ponytail-caveman-skills.md), and
[ADR-0005](0005-governance-hardening.md) (each carries a note).

## Context

An external review (2026-07-16, verified file-by-file) traced this repo's
recurring failures to two roots:

1. **Enumeration drift.** The same rule restated in many files disagrees over
   time: the vibe-lane test rule existed in five places with two meanings,
   README.md carried two different file trees, and the v0.6.0 bump missed
   GENESIS.md's version header the day it happened.
2. **Dual identity.** Every root file was simultaneously the product (a fork's
   template) and Genesis's own working file: the memory bank carried template
   seed text, the placeholder guard had to exempt it, agents got template
   placeholders injected into their own sessions, and Genesis could not run a
   meaningful CI on itself.

Also due for recalibration: the unconditional spec rule contradicted the vibe
lane by design; day-0 provider independence cost three artifacts per vendor
and conflicted with ponytail's no-single-impl-abstraction rule; and "one ADR
per locked decision" was minting ceremony ADRs.

## Decision

1. **The product lives in `templates/`** — the complete skeleton a fork
   receives (`AGENTS.md`, `CLAUDE.md`, `README.md`, `SECURITY.md`, the docs
   tree with memory seeds, `skills/`, tool wiring, CI). Everything outside is
   the workshop for developing Genesis, with its own minimal `AGENTS.md` and a
   real memory bank. Bootstrap = interview → fill placeholders → move
   `templates/` to the repo root → delete the workshop files.
2. **Test-first in both lanes.** Vibe lane: `READ → TEST → BUILD → RECORD`.
   Rationale: a human can feel a regression; an agent can't — the failing test
   is its only feedback loop.
3. **Spec is lane-bound.** Spec-lane work starts from `docs/features/`;
   vibe-lane work records intent and outcome in `progress.md`. The DoD box
   reflects the lane.
4. **Vendor isolation replaces day-0 adapters.** A vendor SDK is imported in
   exactly one module; interface/adapter + contract test arrive with the
   second implementation. Ponytail's carve-out exception is retired.
5. **Shared invariants have one home:** `AGENTS.md` §3; `workflow.md` and the
   wrappers point there.
6. **ADR threshold:** a rejected live alternative (or an undo-tempting
   decision). Every locked decision still gets a `decisions.md` line.
7. **Version single-source:** `CHANGELOG.md` only. Root CI fails any diff that
   touches `templates/` without touching `CHANGELOG.md`.
8. **Guards live and total.** Root CI (push/PR): no placeholder syntax outside
   `templates/` (memory bank included; historical quoting was reworded), with
   `docs/architecture/adr`, `CHANGELOG.md`, and `GENESIS.md` exempt as
   history/protocol. The product's CI ships **active** inside `templates/` —
   inert until the bootstrap move, armed automatically after it — and its
   guard also matches unresolved fill-markers.
9. **Clean ADR inheritance.** Genesis's ADRs stay here; the product ships a
   seed ADR-0001 referencing this repo and the skeleton version.
10. **Skills single-sourced** in `templates/skills/`; this repo consumes them
    via `.claude/skills/` symlinks (dogfood); a fork lands with root `skills/`
    plus the same symlink wiring.

**Rejected alternatives:** keeping the dual-identity layout; a self-arming
guard condition (unnecessary once the product CI is inert by location);
shipping all upstream ADRs into forks (duplication); spec-always (kills the
vibe lane's purpose); day-0 adapters (an interface designed against one
implementation is redesigned at the second anyway); `.claude/skills/` as the
skills' real home (canonical layer inside one vendor's dotdir);
`.github/README.md` for the meta README (GitHub-specific rendering — a
`templates/` dir works on any host).

## Consequences

- Root files carry no placeholders, so CI on this repo is green-and-meaningful
  for the first time; "update one place, miss the other" version drift is
  mechanically blocked.
- Forks start cleaner: their own ADR directory, their own memory, one `mv`
  instead of a rename dance — and the old `README.txt`/WordPress collision is
  gone.
- ADR-0002/0003/0004/0005 are split-status: read them together with this ADR.
- `GENESIS.md` predates the split: its top note marks it stale pending a
  ground-up rewrite (tracked in `docs/memory/context.md`).
- The vibe lane gets slightly heavier (test before code, always) — accepted:
  the speed the lane keeps is the skipped ceremony, not skipped feedback.
