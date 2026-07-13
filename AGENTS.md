# AGENTS.md — Single Source of Truth

> This is the **canonical** rules file for this repository. Every other agent
> entry file (`CLAUDE.md`, `.cursor/rules/*`, etc.) is a thin pointer to this
> one. **If a rule changes, change it here** — others reference it, never
> duplicate.
>
> Scaffolded from the [Genesis](https://github.com/BeycanDeveloper/genesis)
> skeleton. Fields written as `{{...}}` and blocks marked `<!-- GENESIS:FILL -->`
> are completed during the Genesis interview (see `GENESIS.md`). Remove this
> banner once the project is set up.

## 0. Language policy (mandatory)

The repository is written in **{{REPO_LANGUAGE}}** _(default: English)_. All
code, comments, docs, commit messages, and UI copy use this single language.
Conversation with the user may be in any language.

## 1. Project in one sentence

{{ONE_SENTENCE_PITCH}}

## 2. Session protocol

**At the start of every session**, read in this order:

1. This file (`AGENTS.md`)
2. `docs/memory/context.md` — current working state
3. `docs/memory/progress.md` — done / in progress / next
4. `docs/memory/decisions.md` — the "why" log

**At the end of every session**, update `docs/memory/progress.md` (and
`context.md` / `decisions.md` when relevant). Full ritual in
`docs/process/ai-session-protocol.md`.

## 3. Golden rules

- **Single source of truth:** this file. Thin wrappers everywhere else.
- **Spec before code:** every feature starts from `docs/features/<name>.md`.
- **ADR for every architecture/tech decision:** `docs/architecture/adr/`.
- **Provider independence:** external vendors sit behind interfaces/adapters.
- **Module boundaries:** domains don't import each other; shared contracts live
  in one place. Small, single-responsibility files.
- **Tests are first-class:** every project picks a stack-appropriate test runner
  in Phase 1 and keeps it green. Behavior-changing code ships with tests; in the
  spec lane, write the test first. Details: `docs/process/conventions.md` §Testing.
- **Definition of Done is a gate:** `docs/process/definition-of-done.md`.
- **Two lanes, shared invariants:** work runs in a **vibe** or a **spec** lane
  (`docs/process/workflow.md`). The memory bank, module boundaries, repo
  language, secret-safety, and commit-on-demand hold in **both** — so switching
  lanes never breaks structure or progress.
- **Comments explain "why", not "what"** — in the repo language only.

### NEVER

- Write a language other than {{REPO_LANGUAGE}} into the repo.
- Commit secrets (`.env`, keys) or large binaries / build artifacts.
- Hardcode a single external vendor.
- Build a contract-dependent part before its contract exists.
- Break module boundaries.
- Ship behavior-changing code with no test for it.
- Auto-commit without being asked.

## 4. Tech stack

<!-- GENESIS:FILL — from the interview. Detailed companion: docs/architecture/stack.md -->

| Layer              | Choice    | Notes |
| ------------------ | --------- | ----- |
| Language / runtime | `{{...}}` |       |
| Frontend / UI      | `{{...}}` |       |
| Backend / services | `{{...}}` |       |
| Data layer         | `{{...}}` |       |

## 5. Repo map

<!-- GENESIS:FILL — target structure once the code scaffold lands (Phase 1) -->

## 6. Commands

<!-- GENESIS:FILL — fill once the scaffold exists -->

| Command     | What it does |
| ----------- | ------------ |
| `{{...}}`   | install      |
| `{{...}}`   | dev / run    |
| `{{...}}`   | test         |
| `{{...}}`   | lint         |
| `{{...}}`   | build        |

## 7. Tool-specific entry files & commands

- `CLAUDE.md` → points here (Claude Code; ships by default).
- `.cursor/rules/000-start-here.mdc` → points here (Cursor; ships by default).

<!-- GENESIS:FILL — add Codex / Copilot / Gemini entries as used -->

**Slash commands** are optional, **tool-specific** wrappers (Claude Code:
`.claude/commands/`, Cursor: its own format, etc.) that user-trigger a ritual —
e.g. `/wrap`, `/adr`, `/feature` — usually mapping to a skill in `skills/`. They
are **not** pre-generated. The agent **asks the user**, based on the tool
currently in use, whether to create them, and generates only what the user wants.
This stays the user's standing decision — they can ask for (or drop) commands for
any tool at any time later.

## 8. Skills

Portable, tool-agnostic capabilities live in `skills/` (see `skills/README.md`).
Built-in general skills: `wrap-session`, `write-adr`, `review-own-diff`,
`clean-code`, `write-tests`, `ponytail` (minimal code — always on), `caveman`
(terse chat output — always on). Project-specific skills are researched and
added after the interview based on the stack/project type.

Skills are also **wired natively per tool in use** so descriptions load lazily
instead of depending on this section being read — pre-wired in the skeleton for
the default tools (§7), added on demand for any other tool. Per-tool mechanism:
`skills/README.md` §Wiring.

## 9. MCP & external tools

<!-- GENESIS:FILL — which MCP servers / external tools this repo wires up -->

| Tool / MCP server | Purpose | Notes |
| ----------------- | ------- | ----- |
| `{{...}}`         |         |       |

> The same MCP server serves every agent, but **each tool reads its own config
> file** (Claude Code: root `.mcp.json` · Cursor: `.cursor/mcp.json` · others:
> their own) — wire it per tool in use, and keep this table as the one place
> that lists them.

## 10. Agent orchestration

<!-- GENESIS:FILL — only if multi-agent work is used. Sub-agent definition files
are tool-specific and generated on demand like slash commands (§7), never
pre-generated (Claude Code: `.claude/agents/` · Cursor: `.cursor/agents/`). -->

- **When to fan out:** broad read-only search / independent parallel subtasks.
- **Roles:** {{e.g. planner vs builder vs reviewer — define if used}}.
- **Boundaries:** sub-agents obey the same invariants (§3); results are merged by
  the lead agent, which owns the memory-bank update.

## 11. Non-obvious patterns / gotchas

<!-- GENESIS:FILL — the highest-signal section. Capture the things an agent would
get wrong without being told: surprising constraints, footguns, "always do X
before Y", load-bearing files, things that look unused but aren't. Add to this
list whenever you discover one. -->

- {{...}}
