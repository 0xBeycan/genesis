# ADR-0004: Vendor ponytail and caveman as built-in skills

## Status

Accepted

## Context

Every agent session pays two recurring costs: **over-built code** (speculative
abstractions, unnecessary dependencies, boilerplate — more tokens to generate,
more code to maintain) and **verbose chat output** (filler, pleasantries,
narration — pure output-token waste). Two proven MIT-licensed upstreams attack
exactly these layers:

- [ponytail](https://github.com/DietrichGebert/ponytail) (~80k★) — a
  "lazy senior dev" decision ladder that questions whether code needs to exist
  before writing it. Upstream agentic benchmarks: ~54% fewer lines of code,
  ~20% cheaper, ~27% faster, with safety/validation/accessibility preserved.
- [caveman](https://github.com/JuliusBrussee/caveman) — terse chat-output
  rules. Upstream measurement: ~65% fewer output tokens with technical content
  kept exact.

Both upstreams ship per-tool plugin formats (Claude Code plugin, `.cursor/rules`,
hooks, MCP). Genesis already has a portable, tool-agnostic skill layer
(`skills/`) that every agent inherits through `AGENTS.md` — so the rules belong
there, **in the repo**, inherited by every project forked from the skeleton,
with no per-machine or per-tool installation.

Context-compression tools (e.g. Headroom) were evaluated for the same goal and
**not** adopted: they are machine-level proxies/wrappers, not repo artifacts;
realistic gains for coding agents are ~15–20%; and interposing a compression
proxy risks provider prompt-cache hits and answer quality. Revisit only if
context costs become a measured problem.

## Decision

- **Vendor the distilled rulesets** as `skills/ponytail/` and `skills/caveman/`,
  always-on baselines alongside `clean-code`. No upstream hooks, plugins, or
  scripts are vendored — rules only; per-tool slash-command wrappers stay
  optional and on-demand (`AGENTS.md` §7).
- **Division of labor:** `clean-code` governs the *shape* of code · `ponytail`
  governs *how much* code exists · `caveman` governs *chat output*. No existing
  rule became redundant; the skills cross-reference each other instead.
- **Genesis adaptations (upstream rules reconciled, not copied blindly):**
  1. Ponytail's "one assert self-check, no frameworks" testing rule is
     **overridden** by the test-first discipline
     ([ADR-0003](0003-test-first-discipline.md)); YAGNI applies to test scope,
     never to whether the test exists.
  2. Ponytail's "no abstraction with one implementation" yields to the
     provider-independence golden rule: external vendors stay behind adapters.
  3. Caveman **never compresses repository files** — code, docs, memory bank,
     commits stay normal prose in the repo language (`AGENTS.md` §0).
  4. Caveman's wenyan (classical Chinese) intensity levels were trimmed.

## Consequences

- Every forked project inherits less generated code and cheaper sessions by
  default; agents other than Claude Code (Cursor, Codex, Gemini, …) get the
  same behavior because skills are plain markdown read via `AGENTS.md`.
- Caveman default-on makes chat curt; any project can soften it (request
  `lite`) or drop the skill folder in its fork — that is a per-project
  decision, no ADR needed there.
- Vendored copies drift from upstream; syncing is a manual, deliberate act —
  re-check upstream occasionally and re-reconcile through this ADR's
  adaptation list.
- Both vendored files carry MIT attribution to their upstream repos.
