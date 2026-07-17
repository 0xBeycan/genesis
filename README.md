# Genesis

**A reusable, project-agnostic bootstrap protocol that turns an empty
repository into an agent-first, sustainable project foundation.**

Genesis is two things:

1. **A product** — the governance skeleton in [`templates/`](./templates/):
   a canonical `AGENTS.md`, thin per-tool wrappers, a docs tree with a memory
   bank, portable skills, and a templated quality-gate CI. Everything a
   project starts with, shipped as templates.
2. **A protocol** — [`GENESIS.md`](./GENESIS.md): point a coding agent at it
   in your fork. It interviews you like a founding CTO — understands the idea,
   challenges the scope, picks the stack (searching the web when freshness
   matters), covers the design process — then moves the skeleton to the repo
   root, scaffolds a running hello-world with a passing test and real CI, and
   leaves the first commit prepared.

Everything outside `templates/` is the **workshop**: how Genesis itself is
developed.

## Why

Building software with AI agents (and sharing it with human teammates) breaks
down when context lives only in someone's head — or in a chat that scrolls
away. Genesis establishes a durable, on-disk **single source of truth** once,
so no session ever re-explains the project:

> _"Today an AI works on this, tomorrow a human, next week another team."_

## Layout

```
templates/     ← THE PRODUCT: the complete skeleton a fork receives
GENESIS.md     ← the bootstrap protocol (interview → fill → move)
CHANGELOG.md   ← the product's version history (single source of the version)
AGENTS.md      ← rules for developing Genesis itself (this repo)
docs/          ← Genesis's own memory bank + ADRs
.github/       ← live CI: no placeholder syntax outside templates/;
                 a templates/ change requires a CHANGELOG entry
```

## How a fork starts

1. Use this repository as a template (or fork it).
2. Tell your coding agent: **"Follow `GENESIS.md`."**
3. It interviews you in plan/read-only mode, then — on your explicit yes —
   sweeps the workshop files, moves `templates/` to the repo root, fills the
   placeholders, and scaffolds a verified hello-world, leaving your project's
   own foundation with the first commit prepared.

From then on, every session just reads `AGENTS.md` + the memory bank and
continues where the last one left off.

## Rules

All product rules live in [`templates/AGENTS.md`](./templates/AGENTS.md) —
nothing is summarized here, on purpose. Rules for working on Genesis itself:
[`AGENTS.md`](./AGENTS.md).

### Works with

Claude Code and Cursor ship pre-wired. The skeleton is tool-agnostic; the
interview generates an entry file for any other agent (Codex, Copilot,
Gemini, …) on demand.

## License

[MIT](./LICENSE) © Genesis — for this repo itself. Your fork's license is
your own choice.
