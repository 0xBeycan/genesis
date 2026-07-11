# Progress

> Newest entry on top. Each entry: what changed + the **Next step**.

## 2026-07-11 — Vendor ponytail + caveman skills (less code, fewer tokens)

- Vendored two MIT upstreams as always-on built-in skills, distilled to their
  rulesets (no hooks/plugins): `skills/ponytail/` (the "does this need to
  exist" ladder — YAGNI → reuse → stdlib → native → dep → one line → minimum)
  and `skills/caveman/` (terse chat output, ~65% fewer output tokens; never
  compresses repo files). Recorded in
  [ADR-0004](../architecture/adr/0004-vendor-ponytail-caveman-skills.md).
- Reconciled with existing governance instead of copying blindly: ponytail's
  minimal self-check rule is overridden by test-first (ADR-0003); its
  no-single-impl-abstraction rule yields to provider independence; caveman got
  a hard repository-file boundary; wenyan levels trimmed.
- No existing rules turned out redundant — division of labor documented:
  `clean-code` = shape of code, `ponytail` = amount of code, `caveman` = chat
  output. Cross-references added in `clean-code`.
- Updated the skill lists in `AGENTS.md` §8, `GENESIS.md` §1 tree + interview
  §F (also added the previously missing `write-tests` there), `skills/README.md`.
- Evaluated and rejected context-compression proxies (Headroom): machine-level,
  ~15–20% realistic gain for coding agents, provider-cache/quality risk —
  rationale in ADR-0004.
- **Next step:** run the Genesis interview to fill `{{...}}`, or revisit issue
  templates/CODEOWNERS if/when a second contributor joins.

## 2026-06-19 — Close governance gaps (security, logging, PR template, CI doc)

- Added `docs/process/security.md` (secrets, authz, input, dependency/supply-chain
  hygiene, vuln disclosure) and a **Logging & observability** section in
  `conventions.md` (structured logs, levels, no secrets/PII in logs, correlation).
- Added `.github/pull_request_template.md` with the DoD checklist embedded (user
  reviews even solo, so PRs are kept).
- Fixed `automation.md` doc drift: it claimed CI runs on push/PR while `ci.yml` is
  `workflow_dispatch`-only — now states the template runs on dispatch and you
  switch the trigger when commands are filled (no CI trigger added per decision).
- Added a stack-agnostic **performance/SLO** question to the interview (GENESIS §D);
  fixed a duplicate `workflow.md` line in the §1 tree.
- Added `skills/write-tests/` so the test-first discipline has a ritual; wired
  `security.md` into `docs/README.md`, the DoD, and GENESIS §1/§4.
- Deliberately skipped (per decision): CI auto-trigger, CHANGELOG (progress.md
  covers it pre-release), data-layer process doc (DB+migration questions suffice),
  `.env.example` (created per project), slash commands (agent-agnostic).
- **Next step:** run the Genesis interview to fill `{{...}}`, or revisit issue
  templates/CODEOWNERS if/when a second contributor joins.

## 2026-06-19 — Bake test-first discipline into the skeleton

- Testing was implicit (a CI slot + a DoD checkbox + a placeholder) and read as
  optional. Made it first-class across the governance: `AGENTS.md` golden rule +
  NEVER, `GENESIS.md` interview §F + standards §5 + NEVER, the `workflow.md` loop
  (`READ → SPEC → TEST → PLAN → BUILD → VERIFY → RECORD → COMMIT`) and its
  invariants, `definition-of-done.md`, and a real `conventions.md` §Testing.
- Recorded the decision in [ADR-0003](../architecture/adr/0003-test-first-discipline.md)
  (refines the spec-lane loop from ADR-0002); runner stays a stack choice.
- **Next step:** consider a `skills/write-tests/` skill and adding `push`/`pull_request`
  triggers to `ci.yml`; otherwise run the Genesis interview to fill `{{...}}`.

## {{DATE}} — Phase 0: governance foundation (from Genesis skeleton)

- Forked the Genesis skeleton: `AGENTS.md`, `CLAUDE.md`, `README.txt`, the
  `docs/` tree, the memory bank, the `skills/` tree, CI scaffold, and
  ADR-0001/0002 are in place.
- Workflow is **two-lane** (strict vibe + spec); vibe is the pre-alpha default.
- **Next step:** run the Genesis interview (`GENESIS.md`) to fill the `{{...}}`
  placeholders, choose the default lane + which skills to seed + MCP/CI, and
  generate the project-specific docs, then start Phase 1 (scaffold).
