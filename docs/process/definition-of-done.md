# Definition of Done

A change is **not done** until every applicable box is checked. This is a gate,
not a wish list.

- [ ] **Spec** — the feature has an up-to-date `docs/features/<name>.md`.
- [ ] **Code** — within module boundaries; comments explain "why"; repo language.
- [ ] **Contracts** — schemas/types exist before the code that depends on them.
- [ ] **Lint** passes.
- [ ] **Typecheck** passes (if the stack is typed).
- [ ] **Tests** — a stack-appropriate runner is configured; new/changed behavior
      has a test (written first in the spec lane); the whole suite passes.
- [ ] **Format** applied.
- [ ] **Security** — no secrets/PII committed or logged; authorization is
      deny-by-default; new deps vetted (`docs/process/security.md`).
- [ ] **Design** — respects the design system (if there is a UI).
- [ ] **Docs/memory** — `docs/memory/progress.md` updated; ADR added if a
      decision was made.
