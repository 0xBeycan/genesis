---
name: write-adr
description: Record an architecture or tech decision as a numbered ADR. Use whenever a live alternative is rejected, or a locked choice would tempt a future undo — a stack/library pick, a boundary, a vendor swap, a job/event model, or superseding a past decision.
---

# Write an ADR

## When to use

The moment a decision rejects a live alternative, or locks something a future
session would be tempted to undo — in either lane. In the vibe lane this may
happen *after* the code; write it retroactively. Routine, single-option
decisions need only a `docs/memory/decisions.md` line, not an ADR.

## Steps

1. Copy `docs/architecture/adr/_template.md` to
   `docs/architecture/adr/NNNN-<short-title>.md`, using the next free number.
2. Fill `Status` (usually `Accepted`), `Context`, `Decision`, `Consequences`.
3. If this supersedes an earlier ADR, set the old one's status to
   `Superseded by ADR-NNNN` — never edit an accepted ADR's decision silently.
4. Add a one-line entry to `docs/memory/decisions.md` linking the new ADR.

## Notes

Keep it short — forces and trade-offs, not an essay. See `wrap-session`.
