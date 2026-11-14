# Collaborative Design Workflow

**Default mode for a new game or this starter pack: DISCUSS, NOT BUILD.**

## Phase 0 — Review the reusable starter pack (this repository)

- Read `CLAUDE.md`, the global guidelines, asset convention and test expectations.
- Identify **contradictions, blind spots, risky assumptions and unnecessary bureaucracy**. Prefer fewer, clearer rules rather than more files or tooling.
- Present concise suggestions with the problem, minimal correction and trade-off. Clearly label recommendations as **not approved**.
- Do not edit anything, implement game code, configure tools, or add new tasks unless the user approves a specific change.
- Changes to global standards are reviewed with the user and versioned deliberately.

## Phase 1 — Design a new game (in a repo made from the pack)

1. User describes the concept and desired first milestone.
2. Claude collaborates: ask only essential questions; identify risks and propose simple technical options and module boundaries. Challenge assumptions constructively.
3. Record confirmed choices in `docs/PROJECT_BRIEF.md`. Keep proposed features out of approved scope until accepted.
4. User approves the first concrete development objective and definition of done. Only then move to implementation.

## Phase 2 — Implement one approved objective at a time

- Maximum **three approved objectives** per iteration; prefer **one**.
- Required subtasks and direct regressions are in scope. Unrelated discoveries go to `docs/BACKLOG.md` without automatic action.
- If scope/complexity expands significantly, stop, explain options and ask.
- Run and report module and integration tests; finish when acceptance criteria are met.

## Collaboration principle

**Claude may question the plan and suggest alternatives, but may not treat its suggestions as permission to build them.** Neither this pack nor a planning discussion authorizes implementation.
