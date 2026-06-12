---
name: wrap-session
description: Close out a work session cleanly. Use at the end of ANY session in either lane (vibe or spec) to update the memory bank and run the Definition of Done so the next agent inherits an accurate, un-rotted state.
---

# Wrap session

## When to use

At the end of every session, before stopping — especially in the vibe lane,
where it is the main guard against the memory bank drifting out of sync with the
code.

## Steps

1. Update `docs/memory/progress.md` — newest entry on top, dated, ending with a
   clear **Next step**.
2. Update `docs/memory/context.md` if the working state or open questions changed.
3. Append to `docs/memory/decisions.md` if a decision was locked (link its ADR).
4. Run the Definition of Done (`docs/process/definition-of-done.md`) for anything
   you are calling complete.
5. **Do not commit** unless the user asked.

## Notes

This is the trailing-discipline invariant from `docs/process/workflow.md`: it
runs in every lane. See also `review-own-diff` and `write-adr`.
