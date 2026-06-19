# Documentation map

Who writes what:

- **Humans** author `product/`, `architecture/` (incl. ADRs), `design/`,
  `process/`.
- **Agents** write `memory/` every session, and add ADRs + feature specs as work
  demands.

| Path                     | Purpose                                          |
| ------------------------ | ------------------------------------------------ |
| `product/vision.md`      | Why it exists, who it serves, differentiation.   |
| `product/roadmap.md`     | Living, phase-based plan.                         |
| `architecture/overview.md` | System architecture + diagram.                 |
| `architecture/stack.md`  | Locked tech stack + versions.                    |
| `architecture/adr/`      | One Architecture Decision Record per decision.   |
| `design/`                | Design system (only if there is a UI).           |
| `process/workflow.md`    | The two lanes (vibe / spec) + shared invariants. |
| `process/conventions.md` | Naming / API shape / logging / errors / commits. |
| `process/security.md`    | Secrets, authz, input, dependencies, disclosure. |
| `process/definition-of-done.md` | Quality gates.                            |
| `process/automation.md`  | CI + hooks that enforce the gate.                |
| `process/ai-session-protocol.md` | Start/end-of-session ritual.             |
| `features/_template.md`  | Spec-before-code template.                       |
| `memory/`                | Living state: progress · context · decisions.    |
| `../skills/`             | Portable, tool-agnostic `SKILL.md` capabilities. |
