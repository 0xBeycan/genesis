# Definition of Done

A change is **not done** until every applicable box is checked. This is a gate,
not a wish list.

- [ ] **Spec** — the feature has an up-to-date `docs/features/<name>.md`.
- [ ] **Code** — within module boundaries; comments explain "why"; repo language.
- [ ] **Contracts** — schemas/types exist before the code that depends on them.
- [ ] **Lint** passes.
- [ ] **Typecheck** passes (if the stack is typed).
- [ ] **Tests** pass (and cover the new behavior).
- [ ] **Format** applied.
- [ ] **Security** — no secrets committed; authorization is deny-by-default.
- [ ] **Design** — respects the design system (if there is a UI).
- [ ] **Docs/memory** — `docs/memory/progress.md` updated; ADR added if a
      decision was made.
