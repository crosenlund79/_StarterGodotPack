# Godot / Claude Starter Pack — v1.2 (Review Candidate)

> Label stays "Review Candidate" until the user approves promotion to `main`; then change it to "v1.2" here and in `docs/GODOT_CLAUDE_GUIDELINES.md`.

Reusable **development instructions and design conventions** for future Godot 4 projects; this is **not a game, a functioning asset loader, or an implemented test framework**. We improve this pack with the user, ChatGPT and Claude before promoting a reviewed version to `main`.

## Contents

| File | Responsibility |
| --- | --- |
| `CLAUDE.md` | Claude's entry point, preflight and work modes |
| `docs/GODOT_CLAUDE_GUIDELINES.md` | Single authority for engineering, source control, scope and delivery rules |
| `docs/DESIGN_WORKFLOW.md` | User / ChatGPT / Claude decision and handoff process |
| `docs/PROJECT_BRIEF.md` | Single record for each game's design and approved current objective |
| `docs/BACKLOG.md` | Deferred observations, never implicit authorization |
| `assets/README.md` | Runtime art/audio override contract (`template_` fallbacks) |
| `custom/` | User-owned override folder (`graphics/`, `audio/`); `.gdignore` keeps Godot from importing/packing it |
| `tests/README.md` | Module, integration, manual and environment test expectations |
| `.gitignore` | Editor-generated, local and binary artifacts ignored by default |

## Pilot this master pack

1. Review the rules and check for gaps or needless complexity with Claude Code in **review-only mode**.
2. Approve changes explicitly. Keep review edits on a working branch, then inspect and merge to `main` only after approval.
3. When stable, optionally mark `_StarterGodotPack` as a **GitHub template repository**.
4. For a new project, choose **Use this template**, then complete `docs/PROJECT_BRIEF.md` and hold a design review **before any game code**.

### Starter review prompt

> This is the `_StarterGodotPack` reusable template, not a game. Read `CLAUDE.md` and all referenced guidance. Review for contradictory rules, real Godot 4 pitfalls, unnecessary complexity and scope creep. Propose minimal improvements with trade-offs. Do not edit files, create branches, generate game code or export a build without my explicit approval.

## Reuse in a game repository

- **Replace this README with the game's README.** Preserve `CLAUDE.md`, the rules and relevant conventions; fill out `docs/PROJECT_BRIEF.md` only with user-confirmed decisions.
- `src/<module>/`, automated tests and the minimal asset resolver are introduced when an approved game objective needs them—not prebuilt speculatively in this template.
- The runtime override behavior (Windows/Linux, effective after restarting the game) is required in games that use replaceable assets. This documentation **does not itself implement that loader**; the first relevant implementation must test it.
- Template updates do **not** automatically flow into existing games. Review changes case by case.

**Operating principle:** Build what's needed. Test it. Preserve what works. Report what was discovered. Then stop.
