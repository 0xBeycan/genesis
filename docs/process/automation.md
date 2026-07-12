# Automation — make the gate enforce itself

The Definition of Done is only real if something checks it. Wire these as the
stack solidifies (Phase 1+), so the gate doesn't depend on anyone remembering.

## CI

`.github/workflows/ci.yml` defines the quality gate (install · lint · typecheck ·
test · build). It **ships as a templated no-op triggered only by
`workflow_dispatch`** — safe to keep while the commands are placeholders. Once the
`{{...}}` commands are real (Phase 1), fill them **and** switch the trigger to
`push` / `pull_request` so the gate runs automatically. Replace with your
platform's CI if not GitHub.

## Local / pre-commit (optional)

A git pre-commit (or pre-push) hook can run lint + format + tests before code
leaves the machine — the same checks as CI, earlier. Use the stack's idiom
(e.g. husky + lint-staged + commitlint for JS/TS, `pre-commit` for Python).
Keep hooks fast; push the slow checks to CI.

## Cost hygiene (agent sessions)

- **Placeholder guard:** after the Genesis interview, enable the commented
  "No placeholders left" CI step so a half-filled `{{...}}` can't survive
  silently.
- **Model routing:** where the tool allows it, run trivial vibe-lane tasks
  (renames, small fixes, doc edits) on a cheaper/faster model and keep the
  strong model for architecture, debugging, and spec-lane work.
- **Fan out broad read-only searches** to sub-agents (`AGENTS.md` §10) instead
  of filling the main context with file dumps. A code-navigation MCP (e.g.
  Serena) reads at symbol level — prefer it over whole-file reads once the
  codebase grows.
- **Prompt-cache stability:** see `ai-session-protocol.md` — keep `AGENTS.md`
  churn-free; session state belongs in the memory bank.

## Maturity gates

- **Pre-alpha:** vibe lane is the default; CI may be a thin smoke check.
- **Alpha/beta and after:** spec lane + **PR review** become the default; CI is a
  required, blocking gate on the default branch.

> Automation enforces the invariants from `workflow.md`; it never replaces the
> end-of-session memory update (`skills/wrap-session`).
