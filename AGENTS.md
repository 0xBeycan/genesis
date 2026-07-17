# AGENTS.md — Genesis development

Rules for working on **this repo**: the Genesis skeleton itself. The product
lives in [`templates/`](./templates/) — everything there ships to forks;
everything outside it is our workshop. **Forked to start a project? Read
[`GENESIS.md`](./GENESIS.md) first — these workshop rules are not for you.**

## Session protocol

- **Start:** read this file, then `docs/memory/` (context → progress →
  decisions).
- **End:** update `docs/memory/progress.md` (and `context.md` /
  `decisions.md` when relevant). Keep entries short.

## Rules

- The repo is written in **English**; chat may be any language.
- **The product is `templates/`.** Any change inside it is a product change
  and ships with a `CHANGELOG.md` entry (version bump) — CI enforces this.
- **One home per rule.** A rule lives in exactly one file; everything else
  points to it. Product rules: `templates/AGENTS.md` §3. Workshop rules: this
  file. Sole exception: wrappers and hooks may repeat the safety-net
  reminders (the always-on skill; the templates-change → CHANGELOG rule; the
  fork → `GENESIS.md` pointer).
- **The version lives only in `CHANGELOG.md`.**
- **ADR threshold:** open an ADR (`docs/architecture/adr/`) when a live
  alternative was rejected or a decision would tempt a future undo; every
  locked decision gets a line in `docs/memory/decisions.md`.
- **No test runner here** (docs-only repo, deliberate): verify guard/CI
  changes by running their commands locally before pushing.
- **Skills:** the product's skills are our skills — `.claude/skills/*`
  symlinks into `templates/skills/`, wiring only the ones that apply to a
  docs-only repo (`ponytail`, `clean-code`, `write-adr`, `ideate`); `ponytail`
  is always on. The rest reference product-only process files and stay
  unwired here.
- Commit only when asked. Never commit secrets.

## NEVER

- Write placeholder syntax outside `templates/` — history files (ADRs,
  `CHANGELOG.md`) may quote it; CI encodes exactly those exemptions.
- Change `templates/` without a `CHANGELOG.md` entry.
- Duplicate a rule instead of pointing at it.
- Auto-commit without being asked.
