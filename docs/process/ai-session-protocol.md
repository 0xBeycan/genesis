# AI session protocol

The ritual every agent (and human) follows so that work survives handoffs.
This file is the **canonical** copy — `AGENTS.md` §2 and `skills/wrap-session`
point here; if the ritual changes, change it here.

## Start of session

1. Read `AGENTS.md` (rules, stack, repo map).
2. Read `docs/memory/context.md` — current working state and tribal knowledge.
3. Read `docs/memory/progress.md` — what's done / in progress / next.
4. Read `docs/memory/decisions.md` — the "why" log.
5. Restate the immediate goal before touching anything.

## During the session

- Follow the `workflow.md` loop: READ → SPEC → TEST → PLAN → BUILD → VERIFY → RECORD → COMMIT.
- Open an ADR the moment an architecture/tech decision is made.
- Keep changes inside module boundaries; don't break contracts.
- **Keep `AGENTS.md` stable.** It is read (and prompt-cached) at the start of
  every session — churn there breaks the cache and re-bills the whole file.
  Session-to-session state belongs in the memory bank; change `AGENTS.md` only
  for real rule changes.

## End of session

1. Update `docs/memory/progress.md` — newest entry on top, dated, with the
   **Next step** clearly stated.
2. **Rotate `progress.md` when it grows:** past ~10 entries, move all but the
   newest 5 to `docs/memory/progress-archive.md` (same format, append at top).
   The archive is history; only `progress.md` is read every session.
3. Update `docs/memory/context.md` if the working state or open questions changed.
4. Append to `docs/memory/decisions.md` if a decision was locked (link the ADR).
5. **If a rule changed in `AGENTS.md` this session, re-sync the thin wrappers**
   (`CLAUDE.md`, `README.txt`, any `.cursor/rules/*` — and the `README.md` trees
   in the skeleton repo). Pointers that drift are worse than no pointers.
6. Run the Definition of Done gate for anything you're calling complete.
7. **Do not commit** unless the user asked.
