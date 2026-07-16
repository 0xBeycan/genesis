# Context

> Current working state and tribal knowledge for the next agent working on
> Genesis itself.

- **Stage:** v0.8.0 — the product skeleton lives in `templates/`; the root is
  Genesis's own workshop; `GENESIS.md` is the rewritten founder-interview
  protocol. Version: `CHANGELOG.md`.
- **Active constraints:** root files carry no placeholder syntax (CI-guarded);
  any `templates/` change ships with a `CHANGELOG.md` entry; no test runner
  here (docs-only repo) — verify guard/CI changes by running their commands
  locally.
- **Open questions:** the new protocol has not had a dogfood run yet —
  bootstrap a throwaway project end-to-end and feed friction back into
  `GENESIS.md`.
- **Hint for the next agent:** every rule has exactly one home — root
  `AGENTS.md` for the workshop, `templates/AGENTS.md` §3 for the product,
  `GENESIS.md` only for the interview/bootstrap process. Don't restate rules;
  point at them.
