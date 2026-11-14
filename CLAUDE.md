# Claude Code — Godot Project Starter Instructions

This repository may be **the reusable starter pack itself**, not yet a game. Never infer permission to build a game from the presence of these files. Rules are standing instructions; new features, architecture, rule changes, and implementation require explicit user approval.

@docs/GODOT_CLAUDE_GUIDELINES.md
@docs/PROJECT_BRIEF.md
@docs/DESIGN_WORKFLOW.md

## First: establish the mode

- **Starter-pack review:** If asked to review or refine this reusable pack, assess the documents and their practicality. Do not create Godot files, scaffolding, branches, tests, assets, or revised rules unless explicitly approved. Make a concise list of issues, concrete fixes and trade-offs. Wait for approval before editing.
- **Project design:** If a game concept is being discussed but no development objective is approved, collaborate on the design only. Ask/identify essential decisions, propose the smallest sensible architecture, and distinguish agreed requirements from suggestions. Do not implement.
- **Approved implementation:** Only when explicitly requested, follow the scope and definition of done in the project brief / current task.

## Mandatory preflight before changes

1. Read the imported rules and relevant file conventions (`assets/README.md`, `tests/README.md` when applicable).
2. Inspect repository status, tracked/untracked work, current branches, modules and existing tests. Do not overwrite user work or change branches without approval. Report conflicts with the three-branch rule rather than deleting or renaming anything.
3. Restate approved objective(s) (maximum three, preferably one), acceptance criteria, and impact. If a task grows substantially, stop and obtain approval before expanding it.

## During approved implementation

- Make the smallest modular change; add/update module tests and affected cross-module tests.
- Record unrelated findings in `docs/BACKLOG.md`, never implement them automatically.
- Follow `assets/README.md` for replaceable art/audio; keep `template_` fallbacks.
- Never export a Windows EXE or build an installer unless **explicitly requested in that task**.

## Finish and stop

Report briefly: changed files/behavior, tests run and results, known regressions, deferred findings. Once approved acceptance criteria pass, stop; do not opportunistically improve anything else.
