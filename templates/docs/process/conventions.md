# Conventions

Keep only what applies to this project's stack; fill the stack-specific parts
during/after the interview.

## Naming & structure

- Small, single-responsibility files. No god classes.
- Domains don't import each other directly; shared contracts live in one place.
- {{stack-specific naming rules}}

## API shape (if applicable)

- Consistent success/error envelopes.
- Errors are typed and logged with context; never swallow them silently.
- {{realtime event naming, if any}}

## Logging & observability

How anyone (agent or human) understands what the running system did and why it
failed. The runner/library is stack-specific; the rules are not.

- **Structured logs** (key-value / JSON), not bare strings — machine-greppable.
- **Use levels deliberately:** `debug` (dev detail) · `info` (notable events) ·
  `warn` (recoverable) · `error` (needs attention). No `info`-spam in hot paths.
- **Never log secrets or PII** — no tokens, passwords, full payloads, emails.
  Redact at the boundary.
- **Correlate** related work with a request/trace id so one operation is followable
  end to end.
- **Errors carry context** — what was being done, with which inputs (redacted),
  and the cause. Never swallow an error silently.
- **Surface failures** — metrics/health/traces as the project grows
  ({{tooling, if any}}); deferred while pre-alpha but designed for, not bolted on.

## Authorization

- **Deny by default.** Grant explicitly. Details: `security.md`.

## Validation & config

- Validate input at boundaries. Configuration via env; never commit secrets.

## Testing

Tests are mandatory, not optional. The runner is stack-specific; the discipline
is not.

- **Pick a runner in Phase 1.** Every project configures a stack-appropriate test
  runner before feature work starts — `{{TEST_RUNNER}}`, chosen for the stack
  at bootstrap. Wire its command into `AGENTS.md` §6 and
  `.github/workflows/ci.yml`.
- **Test-first, both lanes.** Write a failing test (or executable acceptance
  check) before the code that satisfies it — in the vibe lane too. An agent has
  no gut feeling for regressions; the failing test is its feedback loop.
- **Behavior-changing code ships with a test.** Bug fix → a test that fails
  before the fix. New behavior → a test that pins it.
- **Levels** _(use what applies to the stack)_:
  - **Unit** — pure logic / single module, no I/O. The bulk of the suite.
  - **Integration** — module-to-module and real adapters (db, queue, HTTP).
  - **End-to-end / contract** — user-visible flows and public contracts.
- **Test behavior, not implementation.** Assert on observable outcomes and
  contracts so refactors don't break the suite.
- **Vendor isolation, contract-tested at two.** A vendor SDK is imported in
  exactly one module; when a second implementation arrives, every implementation
  is verified against the same contract test.
- **Coverage is a floor, not a goal:** {{COVERAGE_TARGET — default ≥80% on
  changed code}}. Don't chase 100%; cover the behavior that matters.
- **Keep the suite green and fast.** A red main branch blocks merges; no skipped
  or flaky tests left in.

## Commits & branches

- Convention: {{COMMIT_CONVENTION}} _(default: Conventional Commits)_.
- Branch naming: {{branch convention}}.
- **Commit only when the user asks.**
