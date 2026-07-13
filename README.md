# Genesis

**A reusable, project-agnostic bootstrap protocol that turns an empty repository into an agent-first, sustainable project foundation.**

Genesis is two things:

1. **A protocol** ([`GENESIS.md`](./GENESIS.md)) — point your coding agent at it and it **interviews you** about the project you want, then fills in a complete governance foundation tailored to your answers.
2. **A ready-made skeleton** — the project-agnostic parts that every project needs regardless of the answers (`AGENTS.md`, the `docs/` tree, the memory bank, ADR-0001) already ship in this repo as templates. **Fork it and you start with the structure already in place.**

You never have to re-explain your project's structure again. Every future session just reads `AGENTS.md` and the memory bank, and continues from where the last one left off.

---

## Why does this exist?

Building software with AI agents (and sharing it with human teammates) breaks down when context lives only in someone's head — or in a chat that scrolls away. Genesis solves this by establishing a durable, on-disk **single source of truth** the first time you start a project, designed for the reality that:

> _"Today an AI works on this, tomorrow a human, next week another team."_

Instead of re-describing your stack, conventions, and decisions every session, you bootstrap once and let the structure carry the context forward.

## What it produces

After the interview, the agent scaffolds a governance skeleton like this:

```
README.txt                  # NFO-style entry point → AGENTS.md
AGENTS.md                   # SINGLE SOURCE OF TRUTH (rules, stack, repo map)
CLAUDE.md  .cursor/rules/   # thin per-tool wrappers → point to AGENTS.md
docs/
  product/                  # vision + living, phase-based roadmap
  architecture/             # overview, locked stack, ADRs (one per decision)
  design/                   # design system (only if there's a UI)
  process/                  # workflow, conventions, definition-of-done, session protocol
  features/                 # spec-before-code template
  memory/                   # progress · context · decisions (the AI writes these every session)
skills/                     # portable, tool-agnostic SKILL.md capabilities
.github/                    # templated quality-gate CI + PR template
```

> The **code** scaffold (apps, packages, build tooling) is a later phase. Genesis's job is the **governance foundation** that every subsequent session reads first.

## Two ways to start

**Mode A — fresh repo:** drop `GENESIS.md` into an empty repo and the agent generates the whole governance tree from scratch.

**Mode B — fork this repo (recommended):** the skeleton is already here, so you skip straight to filling it in.

```bash
# Use this repository as a template, then:
git clone <your-fork> my-project && cd my-project
```

Then, in your coding agent of choice:

> Follow `GENESIS.md`.

The agent detects that the skeleton already exists and:

1. **Runs the discovery interview** — focused, grouped questions about identity, product vision, tech stack, architecture constraints, design, process/tooling, and roadmap. Every choice has a sensible default; any group that doesn't apply is skipped.
2. **Confirms** — summarizes your decisions as a compact spec and waits for an explicit "yes".
3. **Fills the skeleton in place** — replaces every `{{...}}` placeholder and `<!-- GENESIS:FILL -->` block, writes the project-specific docs (vision, stack, roadmap phases), opens one ADR per locked decision, and updates the memory bank.

The protocol is **fully project-agnostic**: it encodes _how_ a sustainable project is set up, not _what_ any specific project is. No stack, vendor, or domain assumptions are baked in — every concrete choice comes from your interview.

## Core principles

Genesis bakes these non-negotiable standards into every project it bootstraps:

- **Single source of truth + thin wrappers** — one canonical `AGENTS.md`; every other tool file just points to it.
- **Language policy** — the repo is written in one chosen language; the conversation can be any language.
- **Memory bank + session protocol** — read memory at the start of a session, update it at the end. The trail you leave is the next agent's starting point.
- **Spec before code** — every feature starts from a spec file.
- **ADR for every decision** — architecture and tech choices are traceable and reversible-by-supersession, never silent.
- **Provider independence** — external vendors sit behind adapters; nothing is hardcoded to one vendor.
- **Module boundaries** — domains don't import each other; shared contracts live in one place.
- **Definition of Done is a gate** — lint, typecheck, tests, format, docs, and a memory update every time.
- **Commit only when asked** — never auto-commit.

## What's in the box

Everything below ships pre-built as templates, so a fork starts with the
structure already in place:

```
GENESIS.md                  # the bootstrap protocol (interviews you, fills the skeleton)
AGENTS.md                   # SINGLE SOURCE OF TRUTH (rules, stack, repo map)
CLAUDE.md                   # thin wrapper → points to AGENTS.md (Claude Code)
.cursor/rules/              # thin wrapper → points to AGENTS.md (Cursor)
.claude/skills/             # skill wiring for Claude Code (symlinks into skills/)
README.txt                  # NFO-style entry point for humans & agents
SECURITY.md                 # reporting channel + pointer to the full policy
.gitignore  .editorconfig   # baseline tooling config
docs/
  README.md                 # docs map (who writes what)
  product/                  # vision + living, phase-based roadmap
  architecture/             # overview, locked stack, ADRs (+ ADR-0001, ADR template)
  process/                  # workflow, conventions, definition-of-done, session protocol
  features/                 # spec-before-code template
  memory/                   # progress · context · decisions (the AI writes these every session)
skills/                     # built-in skills: wrap-session · write-adr · review-own-diff
                            #   clean-code · write-tests · ponytail · caveman
.github/                    # quality-gate CI (templated) + PR template with the DoD
CHANGELOG.md                # skeleton versions — what a fork diverged from
```

Project-specific files (design system, entry files for further tools like
Codex / Copilot / Gemini) are added by the interview only when they apply.

### Works with

Genesis ships with the **Claude Code** (`CLAUDE.md` + `.claude/skills/` wiring) and **Cursor** (`.cursor/rules/000-start-here.mdc`) entry files by default. It's tool-agnostic, so the interview generates a matching entry file for any other agent you actually use — Codex, Copilot, Gemini, and others — on demand.

---

## License

[MIT](./LICENSE) © Genesis. Fork it, adapt it, build on it.
