# CLAUDE.md

This is a **thin wrapper**. The single source of truth is
**[`AGENTS.md`](./AGENTS.md)** — read it first.

- **Language policy:** the repo is written in {{REPO_LANGUAGE}} _(default
  English)_; chat can be any language.
- **Start of session:** read `AGENTS.md`, then
  `docs/memory/context.md`, `progress.md`, `decisions.md`.
- **End of session:** update `docs/memory/progress.md`
  (see `docs/process/ai-session-protocol.md`).

**Never:** wrong repo language · commit secrets/artifacts · hardcode one vendor ·
build before the contract exists · break module boundaries · ship behavior
changes without tests · auto-commit without being asked.
