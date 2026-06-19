# Skills

A **skill** is a portable, tool-agnostic capability: a folder containing a
`SKILL.md` file with YAML frontmatter (`name`, `description`) and a Markdown
body, optionally bundling scripts or reference files alongside it. The agent
only loads a skill's `description` until it decides the skill is relevant, then
reads the full body — *progressive disclosure*.

`SKILL.md` is supported across Claude Code, Codex CLI, Cursor, Gemini CLI,
Copilot (agent mode), Cline, Roo Code, Goose, and more — so a skill written here
is **not locked to one agent**.

## Layout

```
skills/
  _template/SKILL.md     # copy this to start a new skill
  <skill-name>/SKILL.md  # one folder per skill (+ optional scripts/, refs/)
```

## Built-in (general, project-agnostic)

These ship with the Genesis skeleton and apply to any project:

- **`wrap-session`** — the end-of-session ritual: update the memory bank, run the
  Definition of Done. The rot-guard for the vibe lane.
- **`write-adr`** — scaffold a numbered ADR from the template.
- **`review-own-diff`** — self-review a change against the Definition of Done
  before declaring it done.
- **`clean-code`** — general code-quality rules (small single-responsibility
  files, naming, error handling, "why" comments, no god classes).
- **`write-tests`** — drive a change with tests: turn acceptance criteria into a
  failing test first, pin behavior/contracts, keep the suite green.

## Project-specific (added after the interview)

Once the stack and project type are known, the agent should **research and add
skills that fit this project** — from public skill registries or the web — as
new folders here (e.g. a framework's conventions, a testing approach, an API
client pattern). Keep each skill small, single-purpose, and in the repo language.

> Adding a non-trivial skill is a decision: note it in `docs/memory/decisions.md`
> (and an ADR if it changes how the project is built).
