# Decisions

> One short line per locked decision, newest on top, linking its ADR.

- GENESIS.md v2: single-mode, seven-phase, challenge-first founder interview;
  design phase with Claude Design handoff option; bootstrap ends with a green
  hello-world and a prepared first commit →
  [ADR-0008](../architecture/adr/0008-genesis-founder-interview.md)
- Product/workshop split: the skeleton lives in `templates/` (root = Genesis
  workshop); test-first both lanes; lane-bound specs; vendor isolation (SDK in
  one module); ADR threshold = rejected alternative; version single-sourced in
  `CHANGELOG.md` →
  [ADR-0007](../architecture/adr/0007-product-workshop-split.md)
- Dropped `caveman`: benchmarked +7% tokens / +3% cost vs baseline, so it cost
  more than it saved; `ponytail` is the sole always-on skill →
  [ADR-0006](../architecture/adr/0006-drop-caveman-skill.md)
- Cursor entry file + skill pointer ship by default (like Claude Code); other
  tools stay on-demand → `CHANGELOG.md` v0.5.0
- Governance hardening: progress rotation, canonical session ritual, skeleton
  versioning (`CHANGELOG.md`), native per-tool skill wiring, bootstrap
  placeholder guard, post-bootstrap `GENESIS.md` removal →
  [ADR-0005](../architecture/adr/0005-governance-hardening.md)
- Vendored `ponytail` (minimal-code discipline) + `caveman` (terse chat output)
  as always-on built-in skills; context-compression proxies (Headroom) rejected →
  [ADR-0004](../architecture/adr/0004-vendor-ponytail-caveman-skills.md)
- Test-first discipline with a stack-appropriate runner; tests are first-class,
  not optional →
  [ADR-0003](../architecture/adr/0003-test-first-discipline.md)
- Two-lane workflow (strict vibe + spec) with shared invariants; full SDD/PR
  ceremony deferred to post-alpha/beta →
  [ADR-0002](../architecture/adr/0002-two-lane-workflow.md)
- Adopted the Genesis agent-first governance model →
  [ADR-0001](../architecture/adr/0001-adopt-genesis-governance.md)
