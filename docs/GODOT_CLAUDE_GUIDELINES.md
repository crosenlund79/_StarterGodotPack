# Global Godot / Claude Development Guidelines

**Status:** Adopted · **Version:** 1.0 · **Applies to:** All Godot projects developed with Claude.

These are standing engineering rules. Follow them in every iteration unless the user explicitly approves an exception. Project-specific gameplay and art direction remain separate. Improve these guidelines only through review with the user after practical experience; do not silently weaken or expand them.

## Architecture and ownership

1. **Separation of responsibilities.** Give each system a clear purpose and ownership of its data/behavior. Avoid overlapping responsibilities and hidden dependencies.
2. **Modular from the start.** Prefer cohesive, independently maintainable modules with clear interfaces. In existing projects, improve boundaries only where the approved task requires it; do not initiate a wholesale rewrite.
3. **Tests per module.** Every module must have an automated suite covering its essential behavior. Add or update relevant tests when changing a module.
4. **Cross-module tests.** Maintain automated integration tests for important interactions and contracts between modules. Run the relevant unit and integration tests for each change; report what passed, failed, or could not run.

## Source control and delivery

5. **Three branches maximum.** Keep at most three branches: `current` (active), `backup` (previous safety point), and `older-backup` (older safety point). Do not create extra feature, experimental, or release branches. If an existing repository uses different names or has more branches, report this and obtain approval before renaming, deleting, or rotating anything. Never discard user work to enforce the limit.
6. **No automatic EXE/installer builds.** Do not export, package, or generate a Windows EXE or installer unless the user explicitly asks for it in the current task. Do not configure automatic EXE/installer creation as a side effect. Testing and ordinary source checks remain allowed.
7. **Replaceable graphics and audio.** Claude supplies working default artwork and sound. The user can replace either by adding files in documented override folders using matching logical asset names, without code changes. If an override is missing or invalid, retain a reliable fallback to the Claude-supplied `template_` asset. Do not overwrite user assets. Apply the same approach to existing projects when assets are touched or when explicitly requested.

## Scope and task control

8. **Only approved scope.** Implement only the features, fixes, and changes explicitly requested. Suggestions are not authorization.
9. **No cascading tasks.** Discoveries made during a task do not automatically become new tasks. Record unrelated findings and ask before acting on them.
10. **No opportunistic refactoring.** Do not redesign working systems merely because an alternative looks cleaner. Refactor only what is necessary for the approved objective.
11. **Complexity checkpoint.** If an objective proves substantially larger, riskier, or more interconnected than expected, stop before expanding the work. Explain the cause, options, and tradeoffs; await a decision.
12. **One objective at a time.** Work sequentially on clearly defined, approved development objectives; do not start parallel feature work.
13. **No speculative engineering.** Do not create frameworks, abstractions, settings, general-purpose tooling, or scaffolding for hypothetical future needs.
14. **Backlog, not implementation.** Log newly noticed bugs, improvements, and opportunities as concise findings for later review. Do not fix unrelated issues without approval.
15. **Smallest reasonable change.** Modify the minimum necessary code and assets while preserving module boundaries and existing behavior.
16. **Explicit definition of done.** Before work, identify the requested outcome and relevant tests. When the outcome works, applicable tests pass, and no caused regressions remain, stop. Report the result without adding extra polish or features.

## Iteration limits and allowed exceptions

- **Maximum three approved development objectives per iteration; prefer one.** Required subtasks do not count as separate objectives if they are strictly necessary to deliver an approved objective.
- **Fix regressions caused by the current work** within the same task. If fixing them would cause a major scope expansion, apply the complexity checkpoint.
- **Failures unrelated to the task** are reported, not quietly added to scope.
- **Do not delete, rename, force-push, or replace branches or user-authored assets** without explicit approval.

## End-of-task report (brief)

State: **what changed; tests run and results; any unresolved issue or out-of-scope finding; whether an EXE/installer was explicitly requested and produced.** Do not create further tasks from this report.

**Operating principle:** *Build what's needed. Test what you've built. Preserve what works. Report what you've discovered. Then stop.*
