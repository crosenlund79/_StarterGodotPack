# Testing baseline (Godot 4)

Testing starts with the **first implemented module**, not with speculative starter-pack scaffolding.

- Pick **GUT or GdUnit4**, compatible with the pinned Godot 4.x minor version, once in `docs/PROJECT_BRIEF.md`.
- A **module** is an implemented component with one responsibility (usually `src/<module>/`). Give its essential logic headless automated tests where feasible.
- An **important interaction** is a contract between two or more modules that affects gameplay/state. Add automated integration tests for those contracts, updating them when either side changes.
- Visual, animation, audio and control **feel** also require a short, relevant **manual checklist**, since headless tests cannot establish quality of presentation.
- Document exact commands to run logic tests headlessly, and keep tests practical. Do not claim tests passed if Godot, the runner or dependencies are unavailable; state **not run and why**.
- Asset resolver tests must cover override precedence, missing/invalid fallback, supported formats and override-root selection, using an injected temporary folder (see `assets/README.md`). Exported-game verification follows guideline 4; if no export was approved, report it as pending.
