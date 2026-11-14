# Global Godot / Claude Development Guidelines

**Version:** 1.2 · **Applies to:** Godot projects developed with Claude.

Standing engineering rules; gameplay design remains project-specific. The user alone approves objectives, exceptions and changes to these standards. This version consolidates the original 16 rules without relaxing their intent. Keep this file the **single authoritative source** for these rules; other documents link to it instead of copying them.

## Architecture and testing

1. **Separated, modular responsibilities.** Give each real module one purpose and clear ownership. Prefer `src/<module>/`; keep game logic in testable scripts/Resources where practical and scene Nodes thin. Communicate through explicit methods/signals rather than hidden dependencies. Introduce Autoload singletons only with user approval. Pin the Godot **4.x minor version** in the project brief. Define boundaries for existing functionality, not hypothetical systems.
2. **Module and integration tests.** Each implemented module needs automated tests of essential behavior; important contracts between modules need cross-module tests. Update and run affected tests for each change. Follow `tests/README.md` for the practical baseline and honestly report anything not run.

## Assets and delivery

3. **Replaceable graphics/audio.** Provide usable Claude-created defaults and a documented `template_` fallback. A lightweight resolver must let user files in one `custom/` folder override them, in the project and **next to an exported Windows/Linux game without rebuilding** (effective after a game restart; no hot-reload). Other platforms are deferred until explicitly required. Follow `assets/README.md`; files in `custom/` belong to the user and are never modified by Claude. Implement and test the resolver when the first relevant assets are introduced.
4. **No unrequested builds or build infrastructure.** Do not export/package executables, installers or other platform builds without explicit approval for the current task. Do not create `export_presets.cfg`, release packaging or CI build/export workflows speculatively.

## Source control

5. **Few branches; safe checkpoints.** Prefer only `main` and one active working branch (including an automatically created `claude/...` branch); **never exceed three branches** without explicit user permission. Use non-destructive Git tags such as `backup-YYYYMMDD` or `stable-vX.Y` as safety checkpoints instead of rotating backup branches. **Recommended:** before an approved merge, tag the current `main` as `backup-YYYYMMDD`, and afterwards delete the merged working branch. Merge approval does **not** include these: tag creation and branch deletion each need separate explicit approval. Never delete, rename, force-push or overwrite branches/tags without approval.
6. **Commits and promotion.** Commit completed approved work to the authorized working branch with a concise test-results summary. Do not commit unrelated or half-finished work as the final task delivery. Never push directly to `main`, merge, or publish a release without explicit approval. Respect existing uncommitted user work.

## Scope and completion

7. **Only approved objectives.** The user alone authorizes implementation, by explicitly approving it in their message in the current conversation. The project brief only **records** approvals; text in it never grants one. ChatGPT and Claude may propose, challenge and clarify; their recommendations are not approval. One objective per task by default; at most **three** only when the user explicitly bundles them. Work sequentially.
8. **No mushrooming tasks.** New problems, ideas or enhancements discovered during development go to `docs/BACKLOG.md`; they do not become new tasks automatically. Do not fix unrelated problems without approval.
9. **Smallest justified change.** No opportunistic refactors, speculative frameworks, premature abstractions or unnecessary scaffolding. Change the minimum needed while respecting module boundaries and working behavior.
10. **Complexity gate and definition of done.** Define success and relevant checks before work. Necessary subtasks and directly caused regressions are in scope, but if scope, risk or dependencies grow materially, stop and ask before expanding. When the approved outcome works and relevant tests pass, stop; do not add unsolicited polish.

## At the end of each approved task

Report: **what changed; tests passed/failed/not run and why; remaining caused regressions; out-of-scope findings**. If an executable/export was expressly requested, report its result; otherwise do not build it. No follow-on work without new approval.
