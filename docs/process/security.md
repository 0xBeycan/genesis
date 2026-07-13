# Security

Baseline security expectations for every change. Stack-specific tooling is filled
in Phase 1; the principles below hold from day one. The detailed companion to the
**Security** line in `definition-of-done.md` and the **deny-by-default** rule in
`conventions.md`.

## Secrets

- **Never commit secrets.** No keys, tokens, passwords, or `.env` files in git
  (`.gitignore` already blocks `.env*`, `*.pem`, `*.key`). Provide a
  `.env.example` with empty/placeholder values when env vars exist.
- **Secrets come from the environment / a secret manager,** never from source.
- **Never log a secret or PII** — see `conventions.md` §Logging & observability.
- If a secret leaks, **rotate it first**, then scrub history.

## Authorization & input

- **Deny by default.** Grant access explicitly; the absence of a rule means "no".
- **Validate and sanitize everything crossing a boundary** — request input, file
  contents, env, third-party responses. Trust nothing from the edge.
- **Parameterize queries / escape output;** never build queries or markup by
  string concatenation of untrusted input.
- **Least privilege** for tokens, DB roles, and service accounts.

## Dependencies & supply chain

- **Commit the lockfile** so builds are reproducible.
- **Pin / constrain versions;** review what a new dependency pulls in before
  adding it. Prefer fewer, well-maintained deps.
- **Automated vulnerability + update checks** (e.g. {{Dependabot / Renovate /
  audit command}}) wired into CI once the stack exists.
- **License check** — confirm new deps' licenses are compatible with the project.

## Reporting a vulnerability

- The reporting channel lives in the root `SECURITY.md` (the file GitHub's
  Security tab surfaces) — that is the single fill-in; don't duplicate it here.
  Do **not** open a public issue for an unpatched vulnerability.

## Review

- Security-sensitive changes (auth, crypto, input handling, new dependency,
  anything touching secrets) escalate to the **spec lane** and get an extra pass —
  see `skills/review-own-diff`.
