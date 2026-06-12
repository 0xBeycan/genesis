# ADR-0001: Adopt the Genesis agent-first governance model

## Status

Accepted

## Context

This project will be worked on by AI agents, humans, and possibly multiple teams
over time. Context that lives only in chat histories or someone's head does not
survive handoffs, and re-explaining the project's structure every session is
wasteful and error-prone. A durable, on-disk source of truth is needed before
any feature work begins.

## Decision

Adopt the Genesis governance foundation:

- A canonical `AGENTS.md` as the single source of truth, with thin tool wrappers
  (`CLAUDE.md`, etc.) that only point to it.
- A memory bank (`docs/memory/`) read at the start of every session and updated
  at the end.
- Spec-before-code (`docs/features/`), one ADR per architecture/tech decision,
  provider independence via adapters, enforced module boundaries, and a
  Definition-of-Done gate.

## Consequences

- Every session begins by reading the memory bank and ends by updating it.
- Decisions are recorded as numbered ADRs and superseded, never edited silently,
  so the project's history of "why" stays traceable.
- A small amount of upfront ceremony is accepted in exchange for long-term
  continuity, faster onboarding, and safe AI/human handoffs.
