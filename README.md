# Godot / Claude Project Starter Pack — v1.1 (Pilot)

A **reusable set of engineering rules**, not a Godot game or a ready-made framework. This repository is where we test and improve the starter pack collaboratively with Claude before reusing it in new game repositories.

## What is in the pack?

| Path | Purpose |
| --- | --- |
| `CLAUDE.md` | Automatically loaded project instructions and preflight |
| `docs/GODOT_CLAUDE_GUIDELINES.md` | Approved global development standards (16 rules + task budget) |
| `docs/DESIGN_WORKFLOW.md` | Design-first collaboration, review and approval gates |
| `docs/PROJECT_BRIEF.md` | Copy-specific game decisions, empty until a game is approved |
| `docs/TASK_TEMPLATE.md` | Optional compact task definition |
| `docs/BACKLOG.md` | Deferred findings; **not** implementation authorization |
| `assets/README.md` | User-overridable Claude graphics/audio convention |
| `tests/README.md` | Module and cross-module test expectations |
| `.gitignore` | Standard local Godot, Claude and build ignores |

## Test the pack in its own repository

1. Create a **new empty GitHub repository** for the starter pack (no generated README or `.gitignore`).
2. Extract the ZIP and upload/commit its **contents, preserving folders**. Do **not** upload only the ZIP.
3. Open Claude Code in the repository root. Run `/context all` and check that `CLAUDE.md` and its imported rules are present in memory.
4. Send the first review prompt below. **Claude must only review and propose**, not change files.
5. Discuss changes; approve only specific edits; commit a reviewed version (e.g. `v1.1` / `v1.2`).
6. Once stable, optionally enable **Settings → Template repository** in GitHub. For new projects use **Use this template → Create a new repository**, taking the default branch only.

### First message to Claude (copy/paste)

> This repository is our reusable Godot/Claude starter pack, **not a game**. Read `CLAUDE.md` and all referenced guidance. Review the pack for contradictions, missing practical safeguards, unnecessary complexity, and points that might cause scope creep. Check in particular: modularity, module/integration testing, three-branch policy, explicit-only EXE/installer builds, user-replaceable graphics/audio, and collaborative design approval. **Review only: do not edit files, create branches, scaffold a Godot project or implement anything.** Return a concise prioritized list of findings, with minimal proposed changes and trade-offs. Wait for approval.

## Reuse for an actual game

Create a new repository from the template (or extract the ZIP into an empty repository), then fill `docs/PROJECT_BRIEF.md` with the agreed premise, scope, and first objective. Claude Code should design collaboratively before building anything. An undecided field is not permission to invent a decision.

**Important limitations:** `CLAUDE.md` is a set of instructions, **not technical enforcement**. The override folders are a **contract**, not a working asset loader; implement/test resolution when the first real assets are created. Tests are similarly implemented with actual modules, not included as speculative scaffolding. Do not introduce automatic builds, hooks or packages without approval.

**Version control:** New versions of the master pack do not automatically update existing games; review and apply changes deliberately. This pack does not create or rotate Git branches.
