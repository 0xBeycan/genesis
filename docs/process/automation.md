# Automation — make the gate enforce itself

The Definition of Done is only real if something checks it. Wire these as the
stack solidifies (Phase 1+), so the gate doesn't depend on anyone remembering.

## CI

`.github/workflows/ci.yml` runs the quality gate (install · lint · typecheck ·
test · build) on push and pull requests. It ships as a templated no-op; fill the
`{{...}}` commands once they exist. Replace with your platform's CI if not GitHub.

## Local / pre-commit (optional)

A git pre-commit (or pre-push) hook can run lint + format + tests before code
leaves the machine — the same checks as CI, earlier. Keep hooks fast; push the
slow checks to CI.

## Maturity gates

- **Pre-alpha:** vibe lane is the default; CI may be a thin smoke check.
- **Alpha/beta and after:** spec lane + **PR review** become the default; CI is a
  required, blocking gate on the default branch.

> Automation enforces the invariants from `workflow.md`; it never replaces the
> end-of-session memory update (`skills/wrap-session`).
