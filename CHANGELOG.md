# Changelog — Genesis skeleton

Versions of the **skeleton itself**, so a forked project knows what it diverged
from and can cherry-pick upstream improvements. Forks: keep this file as-is (or
delete it); your own history lives in `docs/memory/progress.md`.

## v0.6.0 — 2026-07-16

- **`caveman` skill removed**
  ([ADR-0006](docs/architecture/adr/0006-drop-caveman-skill.md), partially
  supersedes ADR-0004). Ponytail's benchmark ran caveman as a terse-prose
  control: **+7% tokens, +3% cost, +2% time** vs the no-skill baseline — it cost
  more than it saved, because agentic sessions are input-token-dominated and
  compressing chat prose touches a rounding error. `ponytail` is now the sole
  always-on skill; it already cuts LOC by more than double what caveman did.
  Forks wanting terse output can re-vendor upstream.

## v0.5.0 — 2026-07-12

- **Cursor ships by default** alongside Claude Code:
  `.cursor/rules/000-start-here.mdc` (alwaysApply pure pointer — read order,
  always-on skills, end-of-session checklist). `AGENTS.md` §7, `GENESIS.md`
  §1/§4/§F, `skills/README.md` §Wiring, and `README.md` updated to match.
- Bootstrap ritual clarified: forks **reset `progress.md`** to their own first
  entry (skeleton maintenance history stays upstream); `decisions.md` keeps the
  inherited skeleton-decision lines; `LICENSE` is rewritten with the fork's
  own license + owner (new interview §A question — no `{{...}}`, so the guard
  can't catch it). Interview now suggests a code-navigation
  MCP (e.g. Serena) post-scaffold and stack-idiom pre-commit hooks (husky /
  `pre-commit`).

## v0.4.0 — 2026-07-11

- Governance hardening ([ADR-0005](docs/architecture/adr/0005-governance-hardening.md)):
  `progress.md` rotation rule, canonical session ritual (`ai-session-protocol.md`)
  with wrappers deduplicated, thin-wrapper re-sync step, prompt-cache stability
  rule, post-interview placeholder guard, `GENESIS.md` post-bootstrap removal,
  skeleton versioning (this file), native per-tool skill wiring in the interview,
  a post-interview prune step (delete non-applicable sections instead of leaving
  empty templates), root `SECURITY.md`, `.claude/settings.local.json` ignored.

## v0.3.0 — 2026-07-11

- Vendored `ponytail` (minimal-code discipline) and `caveman` (terse chat
  output) as always-on built-in skills
  ([ADR-0004](docs/architecture/adr/0004-vendor-ponytail-caveman-skills.md)).

## v0.2.0 — 2026-06-19

- Test-first discipline baked in ([ADR-0003](docs/architecture/adr/0003-test-first-discipline.md));
  `skills/write-tests/`; `docs/process/security.md`; logging conventions;
  PR template with the DoD checklist.

## v0.1.0 — 2026-06-13

- Initial skeleton: `AGENTS.md`, `GENESIS.md` protocol, docs tree, memory bank,
  built-in skills, templated CI, ADR-0001/0002.
