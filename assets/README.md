# Replaceable graphics and audio — runtime override contract

**Approved behavior: Option B.** Users must be able to replace Claude-created graphics/audio by dropping files into documented folders, **including after a desktop game is exported, without rebuilding**. The game must keep working when the override is absent or invalid. This document defines the contract; the starter pack does not include a speculative Godot loader.

## Paths and precedence

For a logical asset `player` or `footstep`, use this order:

1. **External override** next to the exported desktop executable, e.g. `custom/graphics/player.png` or `custom/audio/footstep.ogg` (resolved relative to `OS.get_executable_path().get_base_dir()`, not `res://`).
2. **Project override** during development or built into a game, e.g. `res://assets/graphics/custom/player.png` or `res://assets/audio/custom/footstep.ogg`.
3. **Claude fallback** packaged with the game, e.g. `res://assets/graphics/template_player.png` or `res://assets/audio/template_footstep.ogg`.

A missing/broken candidate should move to the next candidate. Use consistent logical names and subfolders, and preserve user-supplied assets. An override may use a different **supported** audio extension from the fallback; map by logical name rather than fixed full filename.

## Small resolver, not a modding system

- Introduce a **single asset-resolution entry point** (for example `get_texture("player")`, `get_audio("footstep")`) when the first approved feature needs art or sound. Callers do not hardcode `template_` asset paths.
- Supported external formats initially: **PNG** for graphics; **OGG Vorbis or WAV** for audio. Validate file existence, decoding and basic suitability before using it. Avoid `load()`/`ResourceLoader` for raw, unpacked external files; use Godot 4 runtime file loading. Use `ResourceLoader.exists()` for packaged assets and `FileAccess.file_exists()` for external ones as appropriate.
- Fallbacks are always kept in project source control and bundled in exports. Do not delete or overwrite user replacements. Handle invalid/missing overrides gracefully; report a warning rather than crashing.
- In the editor, never derive the project override folder from the **editor executable** location; use project paths. For exported desktop builds, use the executable folder. For platforms that cannot access executable-adjacent files, document a `user://` override folder instead, retaining no-rebuild replacement where accessible.
- Test external priority, project priority, missing and invalid overrides, supported formats, and fallback. When a desktop export is explicitly requested, verify overrides against the **actual exported build** by changing a file without rebuilding; otherwise mark this verification as pending, not passed.

Don't add empty artwork, a generalized plugin framework, or an automatic export just to satisfy this document. Add working assets and the resolver when a real approved gameplay task first needs them.
