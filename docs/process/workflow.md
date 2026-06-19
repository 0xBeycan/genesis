# Workflow

This project runs in **two lanes**. Both share the same non-negotiable
invariants, so you can switch between them at any time **without breaking the
structure or losing progress**. That is the whole point: speed is optional,
discipline is not.

## The two lanes

### 🏍️ Vibe lane (strict vibe) — default early / solo / exploratory

```
READ → BUILD → RECORD
```

Fast and low-ceremony, but **not** sloppy. You skip the *upfront* paperwork
(no spec, no plan, no ADR-before-code, no PR review) — you do **not** skip the
*trailing* discipline. `RECORD` is mandatory every session.

Use it when: prototyping, solo work, small/reversible changes, the project is
pre-alpha and there is no one to review a PR anyway.

### 🏛️ Spec lane (ceremony) — load-bearing / team / post-alpha

```
READ → SPEC → TEST → PLAN → BUILD → VERIFY → RECORD → COMMIT
```

1. **READ** — `AGENTS.md` + memory bank.
2. **SPEC** — write/update `docs/features/<name>.md` first.
3. **TEST** — turn the spec's acceptance criteria into a failing test before the
   code (test-first); see `conventions.md` §Testing.
4. **PLAN** — outline the change; open an ADR for any architecture/tech decision.
5. **BUILD** — implement within module boundaries until the test goes green.
6. **VERIFY** — run the Definition of Done gate.
7. **RECORD** — update the memory bank.
8. **COMMIT** — only when asked; {{COMMIT_CONVENTION}} _(default: Conventional Commits)_.

> Full **Spec-Driven Development** (spec-first + **PR review** ceremony) becomes
> the default **after alpha/beta**, when there is a team or a reviewer. Before
> that, the vibe lane is the default — opening a PR to review your own solo work
> is just ceremony for its own sake.

## Invariants — true in BOTH lanes (never skipped)

These are what make lane-switching safe:

1. **READ at start, RECORD at end.** The memory bank is updated every session,
   in any lane. This is the rot-guard.
2. **Module boundaries** hold; shared contracts in one place.
3. **Repo language** only; comments explain "why".
4. **Behavior-changing code ships with a test** that lands in the same change
   (test-first in the spec lane; may follow the code in the vibe lane).
5. **No secrets, no large artifacts** committed.
6. **Commit only when asked.**

## Switching lanes

- **Vibe → Spec (escalate)** the moment work becomes load-bearing. Triggers:
  an architecture/tech decision, a new dependency, a public API/contract, a
  security-sensitive change, or "others will now build on this." To escalate,
  write the spec/ADR *retroactively* — the memory bank already has the trail.
- **Spec → Vibe (relax)** for throwaway spikes and exploration branches.
- Switching never corrupts state because both lanes write to the **same memory
  bank** and obey the **same invariants**.
