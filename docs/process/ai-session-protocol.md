# AI session protocol

The ritual every agent (and human) follows so that work survives handoffs.

## Start of session

1. Read `AGENTS.md` (rules, stack, repo map).
2. Read `docs/memory/context.md` — current working state and tribal knowledge.
3. Read `docs/memory/progress.md` — what's done / in progress / next.
4. Read `docs/memory/decisions.md` — the "why" log.
5. Restate the immediate goal before touching anything.

## During the session

- Follow the `workflow.md` loop: READ → SPEC → PLAN → BUILD → VERIFY → RECORD → COMMIT.
- Open an ADR the moment an architecture/tech decision is made.
- Keep changes inside module boundaries; don't break contracts.

## End of session

1. Update `docs/memory/progress.md` — newest entry on top, dated, with the
   **Next step** clearly stated.
2. Update `docs/memory/context.md` if the working state or open questions changed.
3. Append to `docs/memory/decisions.md` if a decision was locked (link the ADR).
4. Run the Definition of Done gate for anything you're calling complete.
5. **Do not commit** unless the user asked.
