# GENESIS.md — Reusable Project Bootstrap Protocol

> **Skeleton version: v0.5.0** — see `CHANGELOG.md` for what each version
> added; a fork records the version it started from in `docs/memory/context.md`.

> **Purpose.** Drop this single file into an empty (or early) repository and tell
> the agent: _"Follow `GENESIS.md`."_ The agent will **interview you** about
> the project you want, then generate a complete, sustainable, **agent-first
> governance foundation** (rules, memory bank, docs, ADRs, roadmap) tailored to
> your answers — without you having to re-explain the structure every time.
>
> This file is **fully project-agnostic**. It encodes _how_ a sustainable project
> is set up, not _what_ any specific project is. It contains no stack, vendor, or
> domain assumptions — every concrete choice comes from the interview.

---

## 0. Prime directive for the agent

You are the bootstrapping agent. Before writing **any** project file, you MUST:

1. **Read this entire file.**
2. **Detect the mode** (see §0.1): fresh empty repo, or a fork of the Genesis
   skeleton that already ships the agnostic scaffold.
3. **Run the Discovery interview** (§2) and get **explicit confirmation** (§3).
4. **Only then** generate / fill the governance foundation (§4) using the
   standards (§5).

### 0.1 Two modes

- **Mode A — fresh repo.** No skeleton present. Generate the full tree from §1.
- **Mode B — forked skeleton.** The repo already contains `AGENTS.md`, the
  `docs/` tree, the memory bank, and `ADR-0001`, with `{{...}}` placeholders and
  `<!-- GENESIS:FILL -->` markers. **Do not recreate these files.** Instead, after
  the interview: (1) replace every `{{...}}` placeholder and resolve every
  `GENESIS:FILL` block in place, (2) generate only the genuinely
  project-specific artifacts that can't be pre-made — vision/stack/roadmap
  *content*, design system (if a UI), additional ADRs (one per locked decision),
  the **project-type skills** researched for this stack (added under `skills/`),
  the MCP/tools table, the CI commands, and the tool-specific entry files
  (`.cursor/rules/…`, etc.) for the agents in use, (3) remove the Genesis banner
  from `AGENTS.md`, replace the meta
  `README.md`/`README.txt` placeholders with the real project identity, and
  rewrite `LICENSE` with the project's chosen license + owner (§2A). Mark
  Phase 0 done and update the memory bank. You can tell you are in Mode B if
  `AGENTS.md` exists and contains `{{` placeholders.

Hard behavior rules:

- **Do not scaffold blindly.** No governance files until the interview is confirmed.
- **Converse in the user's language** (any language) — but **every file you write
  into the repository is in the project's chosen language** (code, comments, docs,
  commit messages, UI copy). Pick that language with the user in the interview;
  once chosen, it is enforced everywhere in the repo.
- **Ask in small, focused batches.** Group related questions; always offer a
  sensible **default** so the user can say "defaults are fine" and move on.
- **Make no assumptions about the project's shape.** It may be a web app, a CLI,
  a library, a service, a data pipeline, a game — anything. Let the interview tell
  you. Skip any question group that doesn't apply.
- **Prefer Plan/Ask mode** for the interview (read-only). Switch to write/Agent
  mode only to generate files after confirmation.
- **Don't invent product facts.** If the user is vague, propose options and let
  them choose; record assumptions in the memory bank.
- **Commit only when the user explicitly asks.** Never auto-commit.

---

## 1. What you will produce (the end state)

A fresh repo with this governance skeleton. Names are conventional; adapt only if
the user asks. Trim parts that don't apply to the project's shape (e.g. drop
`design/` if there is no UI).

```
README.txt                         # NFO-style human + agent entry point → AGENTS.md
SECURITY.md                        # GitHub-visible pointer → docs/process/security.md
CHANGELOG.md                       # skeleton version history (fork may keep or delete)
AGENTS.md                          # SINGLE SOURCE OF TRUTH (rules, stack, repo map)
CLAUDE.md                          # thin wrapper → points to AGENTS.md (Claude Code; ships by default)
.cursor/rules/000-start-here.mdc   # Cursor entry (ships by default); Codex/Copilot/Gemini entries — generated on demand only when that tool is in use
docs/
  README.md                        # docs index / map
  product/
    vision.md                      # why it exists, who it serves, differentiation
    roadmap.md                     # living, phase-based plan
  architecture/
    overview.md                    # system architecture + diagram
    stack.md                       # locked tech stack + versions
    adr/                           # Architecture Decision Records (one per decision)
      0001-*.md ...
  design/                          # only if the project has a UI
    design-system.md               # tokens, components, performance budget
  process/
    workflow.md                    # the two lanes (vibe / spec) + shared invariants
    conventions.md                 # naming / API shape / logging / errors / commits
    security.md                    # secrets, authz, input, dependencies, disclosure
    definition-of-done.md          # quality gates
    ai-session-protocol.md         # start/end-of-session ritual
    automation.md                  # CI + hooks that enforce the gate
  features/
    _template.md                   # spec-before-code template
  memory/
    progress.md                    # done / in progress / next (AI writes every session)
    context.md                     # current working state / tribal knowledge
    decisions.md                   # short decision log (the "why", newest on top)
skills/                            # portable, tool-agnostic SKILL.md capabilities
  README.md _template/ wrap-session/ write-adr/ review-own-diff/ clean-code/
  write-tests/ ponytail/ caveman/
.github/workflows/ci.yml           # templated quality-gate CI (no-op until filled)
.gitignore .editorconfig ...       # ignores + baseline tooling config
```

> The **code** scaffold (apps/packages/build tooling) is a _later_ phase. This
> file's job is the **governance foundation** that every subsequent session reads.
> Put scaffolding into Phase 1 of the generated roadmap.

> **Already forked? (Mode B).** If you copied the Genesis repo, this entire tree
> already exists as a templated skeleton — you do **not** generate it from
> scratch. The interview just fills its `{{...}}` placeholders and adds the
> project-specific docs. See §0.1.

---

## 2. Discovery interview

Ask these as grouped batches. **Skip any group that doesn't apply** to the
project's shape. For every choice, propose a default and let the user confirm or
override — never decide a stack or vendor for them silently.

### A. Identity

- **Product name** and **codename/folder**.
- **One-sentence pitch** (what it is, in a single line).
- **Current status** (what stage the project is at right now).
- **License + copyright holder** (default: MIT, owned by the user/org). The
  skeleton ships `LICENSE` as MIT © the Genesis author — the fork's `LICENSE`
  must be rewritten with the project's own choice and owner (it carries no
  `{{...}}`, so the placeholder guard won't catch it).

### B. Product (vision)

- **Problem** it solves (the #1 pain).
- **Solution** approach (the core mechanism / unfair advantage).
- **Target users** (who, technical level).
- **Differentiation** (why this over alternatives).
- **MVP scope** vs **out-of-scope (for now)**.

### C. Tech stack

Walk only the layers the project actually needs. For each, ask the user's
preference; if they have none, propose options suited to their ecosystem and let
them pick. Possible layers (not a checklist to force):

- **Project type & repo shape** — single package or multi-package workspace? Which
  workspace/build tooling fits the chosen ecosystem?
- **Language(s) / runtime(s).**
- **Frontend / UI** (if any) — framework, styling.
- **Backend / services** (if any) — framework.
- **Data layer** — database/store + how migrations are managed (if any).
- **Background work** — queue / scheduler / jobs (if any long-running work).
- **Realtime / messaging** (if needed).
- **Auth / identity** (if needed).
- **Billing / payments** (if needed).
- **Storage** — files/assets/blobs (if needed).
- **Heavy/external compute or third-party APIs** — a separate runtime "world"?
- Pin **versions** where it matters (record in `stack.md`).
- **Choose modern, non-deprecated tooling defaults — don't carry legacy ones.**
  When pinning a compiler/runtime config, avoid options already deprecated and
  slated for removal. _Example (TypeScript):_ don't use `moduleResolution: "node"`/
  `"node10"` or `baseUrl` — both are removed in TS 7.0. Use `moduleResolution:
  "bundler"` (bundled libs/apps) or `"nodenext"` (Node services), and express
  path aliases via `paths` (relative, no `baseUrl`). Carrying a legacy default
  into a fresh project just schedules a forced migration later.

> For every layer that depends on an **external vendor**, default to **provider
> independence**: put it behind an interface/adapter so it can be swapped. Confirm
> with the user which dependencies are pluggable vs. deliberately fixed.

### D. Architecture constraints

- **Separate worlds / boundaries?** Are there parts in a different language,
  runtime, repo, or image with a hard boundary between them? Define it.
- **Sync vs async** — should long operations be **job-based + event-driven**
  (queue + push) rather than blocking? (Recommended whenever long work exists.)
- **Module boundaries** — should domains avoid importing each other directly, with
  shared contracts living in one place? (Recommended for anything non-trivial.)
- **Single-source-of-truth rules** — is there a piece of state that must be the
  one authority for something? Name it.
- **Contract-first rules** — is there anything that must not be built before its
  contract/schema/spec exists? Name it.
- **Performance expectations** — are there latency/throughput targets or budgets
  worth stating up front (e.g. an endpoint's p95, a job's runtime)? Stack-specific
  and optional, but ask early; record any that the user names. (UI projects also
  get a perf budget in the design system — §E.)

### E. Design (only if there is a UI)

- Brand feel / tone (let the user describe it).
- Need a **design system** (tokens + components + performance budget)?
- Marketing/landing surface? Rendering mode.
- Accessibility + motion expectations.

### F. Process & tooling

- **Repo language policy** — which single language is written into the repo?
  (Conversation can be any language; the repo is one.)
- **Which agents/tools** will read the repo (Claude Code, Cursor, Codex, Copilot,
  Gemini, ...)? Generate the matching entry file for each one in use.
- **Default lane** — the workflow has a **vibe** and a **spec** lane sharing the
  same invariants (`docs/process/workflow.md`). Default to **vibe** while
  solo/pre-alpha; confirm when the spec lane + PR review takes over (alpha/beta).
- **Skills** — the built-in general skills (`wrap-session`, `write-adr`,
  `review-own-diff`, `clean-code`, `write-tests`, `ponytail`, `caveman`) ship
  already; `ponytail` (minimal code) and `caveman` (terse chat output) are
  always-on baselines ([ADR-0004](docs/architecture/adr/0004-vendor-ponytail-caveman-skills.md)).
  Ask whether to **research and add project-type skills** (from skill
  registries / the web) for the chosen stack, into `skills/`.
- **Skill wiring (per tool in use)** — `skills/` stays the single source, but
  each agent tool discovers skills natively so descriptions load lazily
  (progressive disclosure) instead of relying on the agent reading `AGENTS.md`
  §8 voluntarily. Claude Code (`.claude/skills/` symlinks) and Cursor
  (`.cursor/rules/000-start-here.mdc` names the always-on skills and points at
  `skills/`) ship pre-wired in the skeleton — keep both in sync when skills are
  added/removed. Other tools — their native skill/rule location, pointing at
  `skills/`, generated on demand for tools actually in use.
- **Slash commands** — optional, **tool-specific** ritual wrappers (`/wrap`,
  `/adr`, `/feature`, lane-switch), one set per agent in use, mapping to the
  `skills/`. **Do not pre-generate them.** Based on the tool the user is
  currently working in, **ask** whether to create command files; generate only
  what they want, in that tool's format. This stays the user's standing decision
  — offer it again later, on demand.
- **MCP / external tools** to wire (if any) → fill `AGENTS.md` §9. Worth
  suggesting: a code-navigation MCP (e.g. **Serena** — LSP-based, symbol-level
  reads instead of whole files; token-efficient once real code exists — wire it
  post-scaffold and re-index as the code grows).
- **Multi-agent orchestration** — will sub-agents/parallel roles be used? If so,
  fill `AGENTS.md` §10 and generate sub-agent definition files for the tools in
  use (Claude Code: `.claude/agents/`, Cursor: `.cursor/agents/` — near-identical
  markdown + YAML-frontmatter format), with roles drawn from the interview
  (stack, boundaries). **Do not pre-generate them** — same on-demand rule as
  slash commands; generic roles are already covered by each tool's built-in
  agents. Otherwise leave §10 out.
- **Commit convention** (e.g. Conventional Commits) + branch naming.
- **Commit-on-demand** rule (recommended: never commit unless asked).
- **Testing (always ask — not optional).** Which **test runner** fits the chosen
  stack (Vitest/Jest, pytest, `go test`, …)? Confirm the levels that apply
  (unit / integration / e2e), a coverage floor, and that **test-first** holds in
  the spec lane. A project is never set up without a configured runner; record
  the command in `AGENTS.md` §6 and `.github/workflows/ci.yml`.
- **Quality gates** for Definition of Done (lint, typecheck, tests, format — as
  applicable). Fill the CI commands in `.github/workflows/ci.yml` once known.
  Offer local pre-commit hooks in the stack's idiom (e.g. husky + lint-staged +
  commitlint for JS/TS, `pre-commit` for Python) — fast checks locally, slow
  ones in CI (`docs/process/automation.md`).
- **Non-obvious patterns** — capture any known footguns/gotchas into `AGENTS.md`
  §11 (highest-signal section); keep adding to it as they're discovered.
- **Task tracking** — start with an in-repo markdown roadmap, move to issues later?

### G. Roadmap

- Break the work into **phases** (Phase 0 = governance, Phase 1 = scaffold, then
  feature phases). Confirm the phase ordering and what "done" means per phase.

---

## 3. Confirm before generating

Summarize everything back to the user as a compact spec:

- Identity + one-sentence pitch
- Stack table (layer → choice)
- Architecture constraints + which dependencies are behind adapters
- Phase list for the roadmap
- Tooling/agent entry files to generate
- Repo language policy

Then ask: **"Shall I generate the governance foundation with these decisions?"**
Generate only after an explicit yes. Apply any corrections first.

---

## 4. Generate the governance foundation

Create the tree from §1. Guidance per file:

- **`AGENTS.md` (canonical).** The single source of truth. Suggested sections, in
  order: `0` Language policy (mandatory) · `1` Project in one sentence · `2`
  Session protocol (read-at-start / update-at-end) · `3` Golden rules + a **NEVER**
  list · `4` Tech stack summary table · `5` Repo map (target structure) · `6`
  Commands (fill once the scaffold exists) · `7` Sections/menus (if applicable) ·
  `8` Tool-specific files. State clearly: _"If a rule changes, update only this
  file; others reference it."_

- **`CLAUDE.md`.** Thin. Points to `AGENTS.md`, restates the language policy and
  the end-of-session ritual, lists the "Never" summary. No duplicated detail.

- **`.cursor/rules/000-start-here.mdc`.** Ships by default (like `CLAUDE.md`).
  Front-matter `alwaysApply: true` + `description`. A pure pointer: read-order
  list, always-on skills (`ponytail`, `caveman`), end-of-session checklist
  pointer — no duplicated rule content. This is what auto-injects the protocol
  into Cursor.

- **`README.txt`.** NFO/ASCII-art entry point for humans and agents. Restates the
  read-order, the golden rules, and how auto-reading is guaranteed across tools.

- **`docs/README.md`.** The docs map + "who writes what" (humans write
  product/architecture/design/process; AI writes memory/ every session, plus ADRs
  and feature specs as needed).

- **`docs/product/vision.md` + `roadmap.md`.** From interview §B and §G. Roadmap
  uses `[ ] todo · [~] in progress · [x] done`, marks Phase 0 as done at the end
  of bootstrap, and notes "Continuous (every phase)" rules.

- **`docs/architecture/overview.md` + `stack.md`.** Architecture diagram +
  locked stack with versions. `stack.md` is the detailed companion to AGENTS §4.

- **`docs/architecture/adr/`.** Open **one ADR per locked decision** from the
  interview (governance model, each stack choice, provider-independence rules,
  job/event model, contract-first rules, design system, task tracking, ...).
  ADR format: `Status` (Proposed/Accepted/Superseded) · `Context` · `Decision` ·
  `Consequences`. Number them `0001`, `0002`, ... When a decision changes later,
  open a **new** ADR and mark the old one `Superseded` — never edit silently.

- **`docs/design/design-system.md`** (only if there is a UI). Tokens, components,
  performance budget, accessibility, brand.

- **`docs/process/*`.**
  - `workflow.md` — the loop: `READ → SPEC → TEST → PLAN → BUILD → VERIFY → RECORD → COMMIT`.
  - `conventions.md` — naming, project structure, API shape (success/error
    envelopes), logging & observability, errors, realtime events, authorization
    (deny-by-default), validation/config, testing, commits & branches. Include
    only what applies.
  - `security.md` — secrets handling, authorization, input validation,
    dependency/supply-chain hygiene, vulnerability disclosure.
  - `definition-of-done.md` — the quality-gate checklist (code, contracts, design,
    security, docs/memory, UX).
  - `ai-session-protocol.md` — the start/during/end ritual in detail.

- **`docs/features/_template.md`.** Spec-before-code template: status, problem,
  scope, **input contract** (if applicable), flow, acceptance criteria, out-of-scope.

- **`docs/memory/*`.** Initialize:
  - `progress.md` — first entry dated, "Phase 0 governance foundation created",
    plus the Next step (usually Phase 1 scaffold). Newest on top.
  - `context.md` — current stage, active constraints, assets on hand, open
    questions, a "hint for the next agent".
  - `decisions.md` — one short line per locked decision, linking to its ADR.

- **Ignores + tooling.** `.gitignore`, `.editorconfig`, formatter/linter config
  as appropriate to the stack. **Never** commit secrets; provide a `.env.example`
  if env vars exist.

---

## 5. Non-negotiable standards (carry these to every project)

These are the principles that make a project sustainable for "today an AI,
tomorrow a human, next week another team". Bake them into the generated docs:

1. **Single source of truth + thin wrappers.** One canonical `AGENTS.md`; every
   other tool file is a pointer that stays in sync automatically.
2. **Language policy.** The repo is one language; chat is free.
3. **Memory bank + session protocol.** Read memory at start, update it at end.
   The trail you leave is the next agent's starting point.
4. **Spec before code.** Every feature starts from `docs/features/<name>.md`.
5. **ADR for every architecture/tech decision.** Decisions are traceable and
   reversible-by-supersession, never silent.
6. **Provider independence.** External vendors sit behind interfaces/adapters
   (Strategy/Adapter); no single vendor is hardcoded.
7. **Job-based + event-driven** for long work — queue + push, no blocking/polling
   (when the domain has long-running jobs).
8. **Module boundaries / no spaghetti.** Domains don't import each other; shared
   contracts live in one place. Small, single-responsibility files. No god classes.
9. **Test-first, always tested.** Every project configures a stack-appropriate
   test runner in Phase 1; behavior-changing code ships with a test (written
   first in the spec lane). Tests assert behavior/contracts, not implementation.
10. **Definition of Done is a gate.** Lint + typecheck + tests + format + docs +
    memory update, every time (as applicable to the stack).
11. **Respect the design system** (if there is a UI): tokens/components, stylish
    but fast.
12. **Conventional Commits** (or the chosen convention), and **commit only when
    the user asks.**
13. **Comments explain "why", not "what".** Repo language only.

> **NEVER:** write the wrong language into the repo · commit secrets (`.env`,
> keys) · commit large binaries/build artifacts · hardcode a single external
> vendor · build a contract-dependent part before its contract exists · break
> module boundaries · ship behavior-changing code with no test · auto-commit
> without being asked.

---

## 6. End-of-bootstrap ritual

After generating the foundation:

1. **Reset `docs/memory/progress.md`** to the project's own first entry
   ("Phase 0 governance foundation from the interview" + Next). The skeleton's
   maintenance entries are upstream history — they live in the Genesis repo and
   `CHANGELOG.md`, not in the fork's memory. `docs/memory/decisions.md` is
   different: **keep** the inherited skeleton-decision lines (their ADRs ship
   in the fork) and add the interview decisions on top.
2. Make sure **`docs/memory/decisions.md`** lists every locked decision → ADR.
3. Mark **Phase 0** done in the roadmap; leave Phase 1 (scaffold) as the next step.
4. **Prune what doesn't apply** — delete, don't leave empty templates: `design/`
   if there is no UI, the API-shape block in `conventions.md` for non-API
   projects, unused `stack.md` rows, `AGENTS.md` §9 if no MCP/external tools
   and §10 if single-agent, non-applicable DoD lines. An empty section costs
   tokens every session and tells the next agent nothing; git remembers if the
   shape changes later.
5. **Placeholder guard:** run `grep -rn '{{' --include='*.md' .` (ignore
   `_template` files and `CHANGELOG.md`) — resolve every leftover, then enable
   the commented "No placeholders left" step in `.github/workflows/ci.yml`.
6. **Record the skeleton version** (the `v*` at the top of this file /
   `CHANGELOG.md`) in `docs/memory/context.md`, so the fork knows what it
   diverged from.
7. **Delete `GENESIS.md`** — the protocol's job is done and it lives upstream;
   ~20KB of bootstrap instructions has no reader after Phase 0. If the user
   prefers to keep it, note that choice in `docs/memory/decisions.md`.
8. Summarize to the user: what was created, the locked decisions, and the
   recommended next step. **Do not commit** unless asked.

> From here on, every future session just reads `AGENTS.md` + the memory bank and
> continues — the structure never needs to be re-explained. That is the whole point.
