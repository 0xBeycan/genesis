<!--
Auto-reminder of the gate. Delete rows that don't apply; don't delete the
section. Full definition: docs/process/definition-of-done.md
-->

## What & why

<!-- One paragraph: what this change does and why. Link the spec/ADR if any. -->

- Spec / feature: <!-- docs/features/<name>.md, or "n/a (vibe lane)" -->
- ADR (if a decision was made): <!-- docs/architecture/adr/####-*.md, or n/a -->

## Definition of Done

- [ ] **Spec** — `docs/features/<name>.md` is up to date (spec lane).
- [ ] **Code** — within module boundaries; comments explain "why"; repo language.
- [ ] **Contracts** — schemas/types exist before the code that depends on them.
- [ ] **Tests** — a stack-appropriate runner is configured; new/changed behavior
      has a test (written first in the spec lane); the whole suite passes.
- [ ] **Lint / Typecheck / Format** pass.
- [ ] **Security** — no secrets/PII committed or logged; authorization is
      deny-by-default; new deps vetted (`docs/process/security.md`).
- [ ] **Design** — respects the design system (if there is a UI).
- [ ] **Docs/memory** — `docs/memory/progress.md` updated; ADR added if a
      decision was made.
