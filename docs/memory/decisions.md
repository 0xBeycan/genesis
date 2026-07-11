# Decisions

> One short line per locked decision, newest on top, linking its ADR.

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
