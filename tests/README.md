# Testing baseline (Godot 4)

Testing starts with the **first implemented module**, not with speculative starter-pack scaffolding.

- Pick **GUT or GdUnit4**, compatible with the pinned Godot 4.x minor version, once in `docs/PROJECT_BRIEF.md`.
- A **module** is an implemented component with one responsibility (usually `src/<module>/`). Give its essential logic headless automated tests where feasible.
- An **important interaction** is a contract between two or more modules that affects gameplay/state. Add automated integration tests for those contracts, updating them when either side changes.
- Visual, animation, audio and control **feel** also require a short, relevant **manual checklist**, since headless tests cannot establish quality of presentation.
- Document exact commands to run logic tests headlessly, and keep tests practical. Do not claim tests passed if Godot, the runner or dependencies are unavailable; state **not run and why**.
- Asset resolver tests must cover external/project/fallback priority and invalid/missing files (see `assets/README.md`). An actual exported-game check is necessary to confirm runtime overrides, but **never initiate an export** without explicit approval; report verification pending if not approved.

No automated executable/installer building or unrequested CI/export infrastructure.
