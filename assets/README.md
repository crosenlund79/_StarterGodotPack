# Replaceable assets: required contract

Claude must create working default graphics and audio, and every game must implement a **folder-based resolver** for user replacements. These folders alone do not implement replacement behavior; implement and test the resolver when the first relevant assets are introduced.

## Naming example

- `assets/graphics/template_player.png` — Claude-supplied fallback.
- `assets/graphics/custom/player.png` — user replacement, takes precedence.
- `assets/audio/template_footstep.wav` — Claude-supplied fallback.
- `assets/audio/custom/footstep.wav` — user replacement, takes precedence.

Nested folders may mirror the fallback folder structure. Maintain one documented naming convention per project; use matching logical names with a `template_` prefix only on fallbacks.

Resolver behavior: prefer a valid override, otherwise use the matching `template_` asset. Missing/broken override files must not crash gameplay. Never overwrite or delete user replacements. Keep original Claude assets in source control. Include tests for override precedence, fallback, and missing files. Add art/audio files only when the approved task actually needs them.
