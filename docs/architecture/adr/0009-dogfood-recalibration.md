# ADR-0009: Dogfood recalibration — the build-first interview (v0.9.0)

## Status

Accepted — amends [ADR-0008](0008-genesis-founder-interview.md) (its
single-mode, challenge-first, green-materialize core stands).

## Context

First end-to-end dogfood run of the v0.8.0 protocol (2026-07-17; the
founder's real project, bootstrapped as a deliberate throwaway). The protocol
executed DREAM → MATERIALIZE and ended green — but the run produced 15
findings, and the founder's review of the materialized repo hardened the
biggest ones into policy. Their hypothesis "the old (≤v0.6) protocol
interviewed better" checked out **partially**: the old layer-walk and
options-form questioning were real losses; the new product/market depth,
freshness rule, and verified end state are real wins. Synthesize, don't
revert.

Key evidence (kept generic — the run's concrete product names stay out of the
skeleton by the agnosticism guardrail):

- A fresh fork may carry **no `.git`** at all, and the CI guard (`git grep`)
  sees only tracked files — two MATERIALIZE steps could not pass as written
  and needed mid-run repairs.
- Multi-surface projects broke the interview's coverage: one declared
  surface's stack was never asked, another's contents never interviewed —
  CONFIRM arrived before any per-surface scope existed, and the founder had
  to demand it.
- Free-prose question batches had replaced the old options idiom; the run was
  "correct but robotic" — a strong, current alternative to the founder's own
  default was never put on the table.
- Genesis's trace after materialize hit **five files** (adoption-seed ADR,
  `decisions.md`, `progress.md`, `context.md`, README footer) — the
  skeleton's own "one home per rule" promise, broken by its own bootstrap.
- The v0.8.0 rewrite lost the license step entirely: the fork landed with
  **no LICENSE**.
- The workshop's root entry files never mentioned `GENESIS.md`, steering a
  fresh fork session into workshop-maintainer mode.
- Smaller rot: FILL comments still cited the pre-rewrite lettered sections;
  Fill had no "enumerate remaining markers" step (one marker survived until
  the guard caught it); the template roadmap contradicted the protocol's
  Phase-0 definition; brownfield prototypes and registry-blocked name checks
  were uncovered.

## Decision

Recalibrate `GENESIS.md` + `templates/` as **v0.9.0**:

1. **Build-first spine.** The protocol's axis is building: surfaces → stack →
   design inputs → verified materialize. Challenge is counsel, never a
   filter; the only gate is the founder's yes at CONFIRM.
2. **Options, not essays.** Significant decisions are asked as option sets —
   labeled recommendation for *this* project first, 1–2 researched
   alternatives, always a "talk it through" escape — via the tool's native
   question UI when one exists. The form applies to **every** founder:
   non-technical ones get it in plain language with costs named, and the
   recommendation is the modern, proven choice for the project.
3. **Propose, don't transcribe.** Researched current alternatives and
   additive suggestions are required output of scoping and SHAPE & STACK,
   marked as proposals, never silently adopted.
4. **Per-surface scoping in PRODUCT** (every declared surface walked at
   roadmap-name level before CONFIRM; relations between surfaces included)
   and an **explicit UI-layer question** in SHAPE & STACK — a declared
   surface is never "decided at phase start".
5. **Claude Design return contract:** brief from the surface inventory →
   Claude Design returns `handoff.md` (design language + sample index) with
   sample HTML pages; pointer chain README → handoff → samples; every future
   feature builds component by component from `handoff.md`. `docs/design/` is
   created at MATERIALIZE, visual projects only — the skeleton ships none;
   the written README carries the canonical pointer and that build rule.
6. **MATERIALIZE resequenced (9 steps):** a git-baseline step opens it
   (`git init -b main` when `.git/` is missing; offer a fresh history when
   the skeleton's own history is present); `LICENSE` is written at Fill; Fill
   ends with a plain-grep marker enumeration; `git add -A` runs before the
   guard; deleting `GENESIS.md` also drops its guard exclusion and every
   remaining Genesis reference.
7. **Single-trace policy:** after materialize, Genesis is referenced only by
   `context.md`'s skeleton-version line. The adoption-seed ADR is deleted
   from `templates/` — a fork's ADR log opens at **0001** with the project's
   own first decision; the `decisions.md` seed, `progress.md` version mention,
   and README footer are gone.
8. **License restored:** license + copyright holder is an interview question;
   MATERIALIZE writes the file; the protocol warns the guard can't see it.
9. **Fork-mode pointer:** the workshop's `CLAUDE.md`, `AGENTS.md`, prompt
   hook, and Cursor rule open with "forked to start a project? read
   `GENESIS.md` first".
10. Housekeeping from the findings: template roadmap Phase 0 carries the
    hello-world + CI boxes bootstrap completes; FILL comments cite the new
    phase names; `write-tests` got its missing FILL marker; an existing
    prototype becomes a named port phase (location → `AGENTS.md` §11);
    name quick-checks note that registry APIs answer where websites block
    plain fetches.

A same-day founder review of the applied draft tightened three more points:

11. **Understand, don't vet.** DREAM asks only what the project is: the
    idea, the first user, the pain, the founder's own differentiation, and
    how technical they are. The first-users-discovery, stakes, and budget
    questions and the bootstrap reality scan are gone — market research
    happens during development (spec lane) to diversify and decide features,
    and `vision.md`'s Market table ships as an empty living form.
12. **Plan-mode interview.** The agent enters the tool's read-only/plan mode
    itself for the interview and leaves it only on CONFIRM's yes; a tool
    without such a mode falls back to the write-nothing discipline.
13. **Fresh history is the rule, not an offer:** skeleton history present →
    `rm -rf .git && git init -b main`; the upstream trail lives in the
    skeleton's `CHANGELOG.md`. The same review also cleared the "Phase 1"
    residue (`AGENTS.md` §3, `conventions.md` §Testing, `automation.md`) —
    the runner and real CI commands land at bootstrap — and fixed the
    workshop README's fork-order drift.

**Rejected alternatives:** reverting to the old protocol wholesale (loses the
product/market depth, the freshness rule, and the green end state); keeping
ADR-0008's "no menus" rejection as-is (a labeled recommendation with a default
resolves choice paralysis without hiding the alternatives); keeping the README
attribution line (overruled by strict single-home); shipping a `LICENSE`
template file (license text varies with the choice — an interview question
plus a write step stays agnostic); shipping a `docs/design/README.md`
template (a non-visual fork would have to prune a directory that never
applied — created per-project at MATERIALIZE instead, keeping ADR-0008's
rejection intact); keeping the bootstrap reality scan and the
stakes/budget/first-users questions (the run's report had praised the scan —
overruled: the protocol's job is to build the project, not vet it; the
scan's value moves to development-time feature research).

## Consequences

- Fork ADR logs carry only the project's own decisions; upstream tracking
  rides solely on `context.md`'s version line — cherry-picks still work,
  badge-hunting greps stay clean.
- The interview grows where it pays (per-surface scoping, options form) and
  shrinks where it doesn't (DREAM is four questions); the bootstrap can no
  longer end without git history, a license, or with unresolved markers.
- The design handoff is now a contract, not a suggestion — future features
  have a canonical component source.
- v0.9.0 itself needs a validation run: the founder plans to re-bootstrap the
  same real project from a fresh fork as its actual start.
