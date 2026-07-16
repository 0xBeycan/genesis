# ADR-0005: Governance hardening — rotation, versioning, wiring, drift guards

## Status

Accepted — amended by [ADR-0007](0007-product-workshop-split.md): the version's
single source is now `CHANGELOG.md` alone, and the bootstrap-guard design is
superseded by the `templates/` split (live root CI; the product's CI ships
active, inert by location).

## Context

A full audit of the skeleton (2026-07-11) found no structural excess but four
systemic risks: (1) `docs/memory/progress.md` grows unboundedly and is read
every session, so the memory bank slowly becomes the most expensive read;
(2) thin wrappers that *summarize* rules instead of just pointing had already
drifted (missing test rule in `CLAUDE.md`/`README.txt`, stale trees in
`README.md`, the session ritual copied verbatim in three places); (3) skills
relied on the agent voluntarily reading `AGENTS.md` §8 — no tool discovered
them natively, so no progressive disclosure; (4) forks had no way to know which
skeleton version they diverged from, and nothing guarded against half-filled
`{{...}}` placeholders surviving the interview.

## Decision

- **Memory rotation:** past ~10 entries in `progress.md`, all but the newest 5
  move to `docs/memory/progress-archive.md`. Only `progress.md` is read every
  session; the archive is history.
- **One canonical ritual:** `docs/process/ai-session-protocol.md` owns the
  session ritual; `AGENTS.md` §2 and `skills/wrap-session` point to it instead
  of copying it. Wrappers carry pointers, not content — and the end-of-session
  checklist gains a **wrapper re-sync step** for whenever `AGENTS.md` rules
  change.
- **Prompt-cache stability rule:** `AGENTS.md` changes only for real rule
  changes; session-to-session state goes to the memory bank (protects provider
  prompt caching of the start-of-session read set).
- **Native skill wiring per tool** (generated on demand, like entry files):
  Claude Code `.claude/skills/` symlinks, a Cursor `.cursor/rules` pointer,
  etc. — `skills/` stays the single source; tools get lazy, description-only
  loading.
- **Skeleton versioning:** root `CHANGELOG.md` tracks skeleton versions;
  `GENESIS.md` carries the current version; a fork records the version it
  started from in `context.md`.
- **Bootstrap guards** in the GENESIS §6 ritual: a `grep '{{'` placeholder
  check (plus a commented CI step to enable post-interview), and **deleting
  `GENESIS.md`** after bootstrap (it lives upstream; keeping it is an explicit
  decision).
- **Housekeeping:** root `SECURITY.md` pointer (GitHub-visible),
  `.claude/settings.local.json` ignored, `README.txt` slimmed to a pure
  pointer (read order only, no rule summaries).

## Consequences

- Session-start reads stay flat (~3k tokens) instead of growing with project
  age; the skills' always-on cost drops to descriptions-only where wiring is in
  place.
- Less duplicated prose means fewer places to drift — the remaining wrappers
  are one-line pointers plus the re-sync habit.
- Upstream skeleton improvements become consumable by forks (compare versions
  via `CHANGELOG.md`, cherry-pick).
- Rotation adds one small judgment call to `wrap-session`; the archive file is
  append-only history and never read by default.
