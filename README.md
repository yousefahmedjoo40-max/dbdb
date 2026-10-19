# Strange Decisions - Steve chase + jumpscares (Forge 1.16.5)

See the chat message for the full explanation. Quick start:

1. Create a GitHub repository and upload **everything in this folder** (keep `.github/workflows/build.yml`).
2. Open the **Actions** tab -> the *Build* workflow runs automatically on every push.
3. When it is green, open the run -> **Artifacts** -> `strangedecisions-jar` -> your `.jar` is inside.
   (Push a tag like `v1.0.0` to also get a GitHub Release with the jar attached.)

Put the jar in `.minecraft/mods` with Forge 1.16.5 (36.2.x).

## Commands (op level 2)
- `/strangedecisions chase start [player]` / `chase stop [player]`
- `/strangedecisions jumpscare <peek|portrait|second|prison> <sound true|false> [player]`

## Jumpscares (with / without sound)
| id       | image                      | default sound | when |
|----------|----------------------------|---------------|------|
| peek     | jumpscare_peek.png         | silent        | countdown reaches 150 |
| portrait | jumpscare_portrait.png     | scream        | countdown reaches 70 |
| second   | jumpscare_second.png       | scream        | chase climax (then music plays to its natural end) |
| prison   | jumpscare_prison.png       | silent        | after the music ends (follow-up "ending") |

All of it is configurable in `config/strangedecisions-common.toml` (per-image `enabled` and `sound`).

## Assets (src/main/resources/assets/strangedecisions)
- `sounds/jumpscare_scream.ogg` - the shared scream, unmodified
- `sounds/chase_music.ogg` - chase music
- `sounds/ending_music.ogg` - OPTIONAL, not supplied (skipped automatically)
- `textures/gui/jumpscare_*.png`, `textures/entity/steve_stalker.png`

The Gradle task `verifyAssets` fails the build if a required asset is missing.
