---
name: write-adr
description: Record an architecture or tech decision as a numbered ADR. Use whenever a choice is made that future readers would ask "why?" about — a stack/library pick, a boundary, a provider-independence rule, a job/event model, or superseding a past decision.
---

# Write an ADR

## When to use

The moment an architecture/tech decision is locked — in either lane. In the
vibe lane this may happen *after* the code; write it retroactively.

## Steps

1. Copy `docs/architecture/adr/_template.md` to
   `docs/architecture/adr/NNNN-<short-title>.md`, using the next free number.
2. Fill `Status` (usually `Accepted`), `Context`, `Decision`, `Consequences`.
3. If this supersedes an earlier ADR, set the old one's status to
   `Superseded by ADR-NNNN` — never edit an accepted ADR's decision silently.
4. Add a one-line entry to `docs/memory/decisions.md` linking the new ADR.

## Notes

Keep it short — forces and trade-offs, not an essay. See `wrap-session`.
