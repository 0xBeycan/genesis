---
name: wrap-session
description: Close out a work session cleanly. Use at the end of ANY session in either lane (vibe or spec) to update the memory bank, rotate an overgrown progress log, re-sync thin wrappers if rules changed, and run the Definition of Done so the next agent inherits an accurate, un-rotted state.
---

# Wrap session

## When to use

At the end of every session, before stopping — especially in the vibe lane,
where it is the main guard against the memory bank drifting out of sync with the
code.

## Steps

Run the **End of session** checklist in
`docs/process/ai-session-protocol.md` — that file is the canonical copy of the
ritual (memory-bank update, progress rotation, wrapper re-sync, DoD gate,
no auto-commit). Don't work from memory; open it.

## Notes

This is the trailing-discipline invariant from `docs/process/workflow.md`: it
runs in every lane. See also `review-own-diff` and `write-adr`.
