# Collaborative Design Workflow

**Default state: DISCUSS, NOT BUILD.** Global work constraints live in `docs/GODOT_CLAUDE_GUIDELINES.md`.

## Responsibilities and approval

- **User:** Owns creative vision and is the **only approval authority** for features, tasks, changes to standards, exceptions and merges.
- **ChatGPT:** Helps brainstorm, document decisions and propose scoped tasks. Its plans are **not authorization**.
- **Claude Code:** Checks the actual repository, challenges feasibility and suggests minimal designs; implements only explicitly approved work. Its plans are **not authorization**.
- **`docs/PROJECT_BRIEF.md`:** Single shared handoff record for confirmed decisions, proposed ideas and current approved objective. No second task template or parallel source of truth.

## Steps

1. **Review / design.** User describes concept or asks for pack review; assistants propose approaches and trade-offs without implementing.
2. **Confirm.** Record *only user-confirmed* decisions in the brief and label pending ideas as proposals.
3. **Authorize.** User explicitly approves the next objective and acceptance criteria. An assistant must not infer approval from text it previously wrote into the brief.
4. **Implement.** Claude checks repository state, changes only the approved scope, tests affected modules/interfaces and reports any out-of-scope discoveries without acting on them.
5. **Review.** User decides whether the result is accepted or needs an approved correction; no self-generated follow-on tasks.

For a new game, begin with the smallest valuable objective. For this master pack, review documentation changes before promotion to `main`.
