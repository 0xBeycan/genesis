# ADR-0006: Drop the caveman skill

## Status

Accepted — partially supersedes [ADR-0004](0004-vendor-ponytail-caveman-skills.md)
(the `caveman` half only; `ponytail` stands unchanged).

## Context

[ADR-0004](0004-vendor-ponytail-caveman-skills.md) vendored `caveman` as an
always-on baseline on the strength of its upstream claim: ~65% fewer output
tokens with technical content kept exact. That number is real but measures the
wrong layer for this repo's use.

Ponytail's own benchmark (Claude Code, Haiku 4.5, 12 tasks) ran `caveman` as a
terse-prose control arm against a no-skill baseline:

| vs no-skill baseline       | LOC  | tokens | cost | time | safe |
| -------------------------- | ---- | ------ | ---- | ---- | ---- |
| ponytail                   | -54% | -22%   | -20% | -27% | 100% |
| caveman (terse-prose ctrl) | -20% | **+7%**| **+3%** | **+2%** | 100% |

Caveman is *net negative* on tokens, cost, and time. The mechanism is
straightforward: in an agentic coding session the overwhelming majority of
tokens are input (file reads, tool results), so compressing chat prose touches
a rounding error of the total — while the skill's own always-on instructions
are added to every prompt. The output-token saving is real and irrelevant at
this scale.

Its remaining benefit, less generated code, overlaps `ponytail`, which cuts LOC
by more than double (-54% vs -20%) and cuts every other metric too. Nothing
marginal is left. The one honest argument for keeping it — output readability —
points the other way: compressed prose is harder to read, and this repo's
audience is humans reviewing agent work.

## Decision

- **Remove `skills/caveman/`**, its `.claude/skills/` symlink, and its
  `.cursor/rules` mention. `ponytail` remains the sole always-on skill via the
  `UserPromptSubmit` hook in `.claude/settings.json`.
- Chat output follows normal prose rules; brevity stays a matter of judgment
  (say less), not mechanical compression (say it in fewer articles).
- ADR-0004's caveman-specific adaptations (no compression of repo files, no
  wenyan levels) are moot and retired with the skill.

## Consequences

- One less always-on instruction block per prompt, and chat output that reads
  normally. No measured cost regression: the skill was costing tokens, not
  saving them.
- ADR-0004 is now split-status: its ponytail half is live, its caveman half is
  superseded here. Read the two together.
- A fork that wants terse output can re-vendor from
  [upstream](https://github.com/JuliusBrussee/caveman) (MIT) — a per-project
  call, no ADR needed there.
- Precedent worth keeping: an upstream's headline metric is measured on the
  upstream's workload. Check that the layer it optimizes is a layer this repo
  actually spends on before adopting it.
</content>
</invoke>
