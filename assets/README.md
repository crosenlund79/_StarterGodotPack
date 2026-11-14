# Replaceable graphics and audio — runtime override contract

**Approved behavior: Option B.** Users must be able to replace Claude-created graphics/audio by dropping files into one documented folder, **including next to an exported Windows/Linux game, without rebuilding**. The game must keep working when an override is absent or invalid. This document defines the contract; the starter pack does not include a speculative Godot loader.

## One override layout

```
custom/graphics/player.png      # user override (graphics)
custom/audio/footstep.ogg       # user override (audio)
```

For a logical asset `player` or `footstep`, use this order:

1. **User override** in `custom/graphics/` or `custom/audio/` under the override root (below).
2. **Claude fallback** packaged with the game, e.g. `res://assets/graphics/template_player.png` or `res://assets/audio/template_footstep.ogg`.

A missing or invalid override falls back to the `template_` asset. Map by logical name, not a fixed full filename; an override may use any **supported** extension for its type. Subfolders under `custom/graphics/` and `custom/audio/` mirror the fallback folder structure.

**Override root** — computed in one place and passed to the resolver:

- **Editor / development:** the project's `custom/` folder (`ProjectSettings.globalize_path("res://custom")`). Never use the editor executable's location.
- **Exported Windows/Linux game:** `custom/` next to the executable (`OS.get_executable_path().get_base_dir()`).
- **Tests:** a temporary folder supplied by the test.
- **macOS and other platforms:** deferred. Do not implement until a project explicitly requires that platform and records the decision in `docs/PROJECT_BRIEF.md`.

`custom/.gdignore` must exist so Godot neither imports nor packs override files; all overrides use the same runtime-loading code path in the editor and in exports. To use overrides with an exported game, the user places (copies) their `custom/` folder next to the executable.

## Ownership

Files in `custom/` belong to the user. Claude never adds, modifies, renames or deletes files there (other than the template's `.gdignore` and `.gitkeep` placeholders). Claude-created assets live only under `res://assets/` with the `template_` prefix and remain in source control and in exports.

## Small resolver, not a modding system

- Introduce a **single asset-resolution entry point** (for example `get_texture("player")`, `get_audio("footstep")`) when the first approved feature needs art or sound. Callers do not hardcode asset paths.
- **Supported override formats:** **PNG** for graphics; **OGG Vorbis** for audio. **WAV** only if the pinned Godot 4.x version supports runtime WAV loading — check that version's class reference; do not hand-write a WAV parser.
- Load external files with Godot runtime loading (e.g. `Image.load_from_file` + `ImageTexture.create_from_image`, `AudioStreamOggVorbis.load_from_file`), not `load()`/`ResourceLoader`. Use `FileAccess.file_exists()` for overrides and `ResourceLoader.exists()` for packaged fallbacks.
- **Valid** means: the file exists, has a supported extension and decodes successfully. Further checks (dimensions, duration, etc.) require approval. On an invalid override, emit a warning (`push_warning`) and use the fallback; never crash.
- **No hot-reload or file watching.** Each asset is resolved once (at startup or first use) and cached for the session. **Override changes take effect after restarting the game.**
- Test: override precedence, fallback when missing, fallback when invalid, each supported format, and the override-root selection (using an injected test folder). When a Windows/Linux export is explicitly requested, verify overrides against the **actual exported build** by changing a file in `custom/` and restarting without rebuilding; otherwise mark this verification as pending, not passed.

Don't add empty artwork, a generalized plugin framework, or an automatic export just to satisfy this document. Add working assets and the resolver when a real approved gameplay task first needs them.
