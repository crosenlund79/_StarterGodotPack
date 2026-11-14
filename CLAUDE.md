# Claude Code — Godot Project Instructions

This repository may be the reusable starter pack, **not a game**. Read the linked rules before planning or editing. A suggestion, roadmap entry, or assistant-generated plan is never authorization.

@docs/GODOT_CLAUDE_GUIDELINES.md
@docs/PROJECT_BRIEF.md
@docs/DESIGN_WORKFLOW.md

## Identify the mode

- **Starter-pack review:** Inspect the documentation, identify contradictions and practical issues, and propose minimal changes. Review only unless the user approves edits.
- **Game design:** Discuss concepts, risks and module boundaries. Distinguish proposals from user-approved choices. Do not implement.
- **Approved task:** Proceed only when the user explicitly approves the objective in their message or explicitly confirms an objective in `docs/PROJECT_BRIEF.md`. Merely finding text in that file does not confer approval.

## Before an approved change

1. Verify repository identity and current branch; check for uncommitted work. Do not overwrite others' changes. Respect the branch and commit policy in the guidelines.
2. Read relevant conventions in `assets/README.md` and `tests/README.md`.
3. Confirm the approved objective, boundaries and acceptance criteria from `docs/PROJECT_BRIEF.md` / the user's message. A new task needs fresh user authorization, not an old approved objective.
4. If requirements conflict or the work is materially larger than expected, stop and ask instead of expanding scope.

## Implement, verify, stop

- Make the smallest necessary modular changes. Add or update relevant module and integration tests; use manual checks for visual/feel/audio work.
- Record unrelated findings in `docs/BACKLOG.md`; do not implement them.
- Apply the `template_` fallback and runtime external override contract in `assets/README.md` when working with graphics or audio.
- Never create exports, executables, installers, export presets or build automation without explicit current-task approval.
- End with a brief report: change, tests run/pass/fail/not runnable, regressions, deferred findings. Commit finished approved work on the authorized working branch, not directly to `main`; never merge into `main` without explicit approval.
