# ADR-0008: GENESIS.md v2 — the founder-interview protocol

## Status

Accepted — amended by [ADR-0009](0009-dogfood-recalibration.md) after the
first dogfood run: the question form (options, not prose batches), the fork
trace (single home; no adoption-seed ADR), and the ADR numbering changed.

## Context

The old protocol predated the `templates/` split ([ADR-0007](0007-product-workshop-split.md))
and had accumulated exactly the failures the 2026-07-16 external review named:
an intake-form interview with zero push-back ("mush in, mush out"), a
dual-mode design whose Mode-A generation guide drifted from the shipped
skeleton, a second copy of the golden rules, a web-app-shaped layer checklist
with a TypeScript lecture inside a "no stack assumptions" file, and no
questions for deployment, package identity, data model, secrets, or budget.
It also carried a version string (the direct cause of the v0.5.0/v0.6.0
header drift) and, after ADR-0007, actively contradicted the recalibrated
product rules.

The user's vision: the protocol should act as a founding CTO (with a product
and market streak) — first understand the dream, handle technical and
non-technical founders alike, search the web when freshness matters, cover the
design process (including a Claude Design handoff), scaffold a running
hello-world, and leave the repo first-commit-ready.

## Decision

Rewrite `GENESIS.md` from scratch as a **single-mode, seven-phase
founder-interview protocol**: DREAM → PRODUCT → SHAPE & STACK → DESIGN → PLAN
→ CONFIRM → MATERIALIZE.

- **Single mode.** The protocol only brings the `templates/` skeleton to life;
  it never generates the tree from prose (the old Mode A is gone — the class
  of drift it caused cannot recur).
- **Challenge-first.** Vague answers get narrowed, bloated MVPs get forced to
  the one proving flow, risky picks get evidence-based push-back; overrules
  are honored and recorded.
- **Adaptive register.** Technical founders state picks and get challenged
  only on real conflicts; non-technical founders get one plain-language
  recommendation with costs — never a menu. Active web search is required for
  freshness-sensitive picks, reality scans, and pricing.
- **Assumption ledger.** "I don't know" answers become recorded assumptions in
  `context.md`, never silent decisions.
- **Design phase for every project.** Visual layers choose a design source:
  founder-provided (Figma/brand), agent-defined design language, or a **Claude
  Design handoff** (a tailored brief saved as `docs/design/brief.md`; returned
  assets indexed by `docs/design/README.md`). Non-visual shapes get an
  **Interface UX** section in `conventions.md` (command/endpoint shape, output
  modes, error style, exit codes) — `docs/design/` exists only for visual
  layers.
- **Bootstrap ends green.** MATERIALIZE sweeps the workshop (keeping
  `GENESIS.md` until last for resumability), moves `templates/` to the root,
  fills every placeholder/FILL block, scaffolds a runnable hello-world with
  one passing smoke test and real CI commands, verifies test + guard locally,
  and prepares — but does not execute — the first commit.
- **The protocol carries no content that lives elsewhere:** no version string
  (`CHANGELOG.md` owns it), no standards copy (`templates/AGENTS.md` §3 owns
  the rules), no tree (`templates/` is the tree), no per-file generation guide
  (each FILL comment documents itself).

**Rejected alternatives:** keeping two modes (a prose generation guide is a
second skeleton that drifts); governance-only bootstrap (contradicts the
hello-world requirement and leaves CI meaningless); option menus for
non-technical founders (choice paralysis without knowledge); pre-writing MVP
feature specs at bootstrap (launders interview guesses into authoritative
specs); a `docs/design/` directory for non-visual shapes (directory inflation
for a section-sized concern).

## Consequences

- The protocol shrank from ~440 to ~250 lines while gaining the design phase,
  the hello-world scaffold, and the non-technical path; everything cut was a
  duplicate of something the skeleton already owns.
- Interview quality now depends on enforcing the challenge-first rules, not on
  the founder's precision.
- Claude Design is referenced as an optional handoff; if it is unavailable the
  agent-defined design language is the fallback — no hard dependency.
- The first real test is a dogfood run: bootstrap a sample project end-to-end
  and feed friction back into this file.
