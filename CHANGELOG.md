# Changelog — Genesis skeleton

Versions of the **skeleton itself**, so a forked project knows what it diverged
from and can cherry-pick upstream improvements. Forks: keep this file as-is (or
delete it); your own history lives in `docs/memory/progress.md`.

## v0.9.0 — 2026-07-17

- **Dogfood recalibration**
  ([ADR-0009](docs/architecture/adr/0009-dogfood-recalibration.md)): the
  first end-to-end run of the v0.8.0 protocol (a real project, bootstrapped
  as a throwaway) fed 15 findings back into the product; a same-day founder
  review tightened the result. The interview is now **build-first**: DREAM
  shrinks to understanding the project (idea, first user, pain, the founder's
  own differentiation, technicality) — the first-users-discovery, stakes, and
  budget questions and the bootstrap reality scan are gone; market research
  happens during development (spec lane) to diversify and decide features,
  and `vision.md`'s Market table ships as an empty living form. The agent
  runs the interview in the tool's plan/read-only mode (entered by itself)
  and the only gate is CONFIRM's yes. Significant decisions are asked as
  **option sets** for **every** founder — labeled recommendation first
  (modern, proven tooling), 1–2 researched alternatives, a "talk it through"
  escape; the tool's native question UI when it has one; plain language and
  named costs for non-technical founders — and the agent must **propose, not
  transcribe**: current alternatives and additive suggestions are required
  output, marked as proposals. PRODUCT walks **every declared surface** at
  roadmap-name level (UI → menus/pages/flows · API/SDK → exported surface ·
  service → routes/jobs) before CONFIRM; SHAPE & STACK asks the UI layer
  explicitly and restores the **license + copyright holder** question the
  v0.8.0 rewrite had lost (forks were landing unlicensed — MATERIALIZE now
  writes `LICENSE`).
- **MATERIALIZE resequenced** into nine steps: a fresh-history baseline opens
  it (`git init -b main` when `.git/` is missing — a fresh fork may have
  none; the skeleton's own history is deleted and re-inited, so the fork
  opens with its own first commit); Fill ends with a plain-grep **marker
  enumeration** (a marker once survived the fill pass and only the guard
  caught it); `git add -A` moves ahead of the local guard run (`git grep` is
  blind to untracked files); deleting `GENESIS.md` also drops its `ci.yml`
  exclusion. The Claude Design path gained a **return
  contract**: `handoff.md` (design language + sample index) plus sample HTML
  pages land in `docs/design/`, pointer chain README → handoff → samples, and
  every future feature builds component by component from `handoff.md`. The
  directory itself is created at MATERIALIZE, visual projects only — the
  skeleton still ships none.
- **Single-trace policy:** after materialize, Genesis is referenced only by
  `context.md`'s skeleton-version line. The adoption-seed ADR left
  `templates/` (a fork's ADR log opens at 0001 with the project's own first
  decision), and the `decisions.md` seed line, `progress.md` version mention,
  and README "bootstrapped with" footer are gone (v0.8.0 let the footer stay
  — overruled).
- Template fixes from the run: roadmap Phase 0 now carries the hello-world +
  CI boxes bootstrap completes (ticked at MATERIALIZE); FILL comments cite
  the new phase names instead of the pre-rewrite lettered sections;
  `write-tests` got its missing FILL marker; an existing prototype becomes a
  named **port phase** with its location recorded as an `AGENTS.md` §11
  gotcha; package-name quick-checks note that registry APIs answer where
  websites block plain fetches. The founder review's sweep also cleared the
  "Phase 1" residue the report missed — `AGENTS.md` (§3 test rule, §5 repo-map
  comment), `conventions.md` §Testing, `automation.md`, `security.md`, and
  the CI template's header now say the runner, repo map, and real CI commands
  land **at bootstrap**.
- **Workshop:** root `CLAUDE.md`/`AGENTS.md`, the prompt hook, and the Cursor
  rule now open with "forked to start a project? Read `GENESIS.md` first" — a
  fork session was being steered into workshop-maintainer mode. The README's
  fork walkthrough now matches the real order (sweep → move → fill) and notes
  the plan-mode interview.

## v0.8.0 — 2026-07-16

- **`GENESIS.md` rewritten from scratch as a founder-interview protocol**
  ([ADR-0008](docs/architecture/adr/0008-genesis-founder-interview.md)):
  single mode (brings `templates/` to life; the old Mode-A generation path is
  gone), seven challenge-first phases (DREAM → PRODUCT → SHAPE & STACK →
  DESIGN → PLAN → CONFIRM → MATERIALIZE) that adapt to technical and
  non-technical founders, require web search where freshness matters, and
  record unknowns in an assumption ledger. The design phase offers three
  sources — founder-provided, agent-defined, or a Claude Design handoff brief
  saved under `docs/design/` — and non-visual shapes get an Interface-UX
  section in `conventions.md`. Bootstrap now ends with a running hello-world,
  one passing smoke test, real CI commands, a locally verified guard, and a
  prepared-but-unexecuted first commit. The protocol carries no version
  string, no standards copy, no tree, and no per-file guide — `templates/`
  and its FILL comments are the single source. A CTO walkthrough then
  tightened the sequence — the skeleton version is noted before the sweep,
  the Claude Design brief is written at MATERIALIZE (never mid-interview),
  and `GENESIS.md` is deleted *before* the first commit is staged — and added
  a first-ten-users question, on-demand market-brief depth, name-availability
  checks, §11 gotcha seeding, and a broken-run resume rule. An agent-eye
  simulation of post-bootstrap life then added `vision.md`'s living **Market**
  table (seeded by the reality scan; post-MVP competitor deep-dives update it
  in the spec lane), a change-both-together warning on `AGENTS.md` §6 ↔
  `ci.yml` commands, and a size trigger (~120 lines) on the progress-rotation
  rule.
- New built-in skill: **`ideate`** — a procedural diverge-then-converge step
  for decisions with real design freedom (fix constraints → 3–5 genuinely
  different options incl. a wildcard → converge → record rejects via the ADR
  threshold). On-demand, never always-on: it opens the option space that
  `ponytail` then minimizes, so the two chain instead of clashing.
  `GENESIS.md` points at it for design direction and open names. Portfolio
  rule added to `skills/README.md`: a skill earns its slot only when its
  absence produces a named, recurring failure.
- Tool name-drops removed from the protocol and process docs (the same rot
  class as the old TypeScript lecture): MCP servers are wired only for a
  **named need**, with current options researched at wiring time — never on
  day one; pre-commit hook managers are verified by a quick search when set
  up. `AGENTS.md` §9 stays the agnostic registry. A follow-up sweep cleared
  the remaining incidental examples too (runner-name lists in placeholder
  hints, an npm/setup-node comment in the CI template, a scanner-name hint in
  `security.md`) — placeholders now carry no suggested answers.

## v0.7.0 — 2026-07-16

- **Product/workshop split**
  ([ADR-0007](docs/architecture/adr/0007-product-workshop-split.md)): the
  entire skeleton now lives in **`templates/`** — `AGENTS.md`, `CLAUDE.md`,
  the docs tree, memory seeds, skills, tool wiring, and CI. A fork's bootstrap
  fills the placeholders, moves `templates/` to the repo root, and deletes the
  workshop files. The root became Genesis's own workshop: a minimal dev
  `AGENTS.md`, a real memory bank (template seed text moved into the product),
  and live CI — no placeholder syntax outside `templates/`, and a `templates/`
  change without a CHANGELOG entry fails.
- **Process recalibration** (same ADR): test-first in **both** lanes (vibe:
  `READ → TEST → BUILD → RECORD`); specs are lane-bound (vibe work records to
  `progress.md`); **vendor isolation** (SDK imported in exactly one module;
  adapter + contract test with the second implementation) replaces day-0
  adapters; ADR threshold = a rejected live alternative; the shared invariants
  live once, in `AGENTS.md` §3.
- Guard hardening: the product's CI ships **active** (inert inside
  `templates/`, arms on the bootstrap move), also matches unresolved
  fill-markers, and now covers the memory bank; CI TODO steps no longer carry
  placeholder braces. `README.txt` became `templates/README.md` (rename dance
  gone). The version lives **only** in this file. Dead upstream URL fixed
  (`0xBeycan`). The PR template points at the DoD instead of copying it.
  ADR-0006's stray tool-syntax tail removed. Stack tables (`AGENTS.md` §4,
  `stack.md`) ship as empty forms — the interview writes one row per layer the
  project actually has, so no project shape is pre-assumed. The commit
  convention has one home (`conventions.md`); the docs map's ADR wording
  matches the new threshold.

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
