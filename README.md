# Laper Hardcore Cinematic Intro

Fabric mod project for **Minecraft Java 26.3**. The aim is to recreate the LAPER HARDCORE member-introduction sequence from the supplied video: title reveal, cinematic camera shots, one-by-one member showcases, HUD information, particles, fireworks, and finale.

## Build

- Minecraft: 26.3
- Java: 25
- Fabric Loader: 0.20.1
- Fabric API: 0.165.0+26.3
- Fabric Loom: 1.19-SNAPSHOT
- Gradle CI: 9.8.2

The build workflow is in `.github/workflows/build.yml`. It runs for pushes, pull requests, or manually from the **Actions** tab. After a successful run, download the `laper-hardcore-intro-jar` artifact.

## Install

1. Install Fabric Loader for Minecraft 26.3.
2. Put the built mod JAR in the `mods` folder.
3. Install the same mod on each client that should receive the custom camera and HUD effects. Keep Fabric API installed on the server and clients.
4. Give an operator permission to run the `/lhc` commands.

## Stage setup and quick start

1. Stand at the center of the showcase stage and run `/lhc setcenter`.
2. Stand at the entrance where each member should appear and run `/lhc setentrance`.
3. Add names with `/lhc members add <name>`, or populate from online players with `/lhc members online`.
4. Run `/lhc play intro`.

The stage center and entrance must be in the same dimension. The current implementation supports up to 40 registered names.

## Commands

| Command | Description |
|---|---|
| `/lhc setcenter` | Save the showcase center at your current position |
| `/lhc setentrance` | Save the member entrance at your current position |
| `/lhc play intro` | Start the complete intro for online viewers |
| `/lhc play member <name>` | Preview one member for yourself |
| `/lhc stop` | Stop the show and restore viewers |
| `/lhc members add <name>` | Add a member name |
| `/lhc members remove <name>` | Remove a member name |
| `/lhc members list` | List registered members |
| `/lhc members clear` | Clear the member list |
| `/lhc members online` | Replace the list with online player names (up to 40) |
| `/lhc time walk <seconds>` | Set walk-in duration (2–60 seconds) |
| `/lhc time pose <seconds>` | Set pose duration (2–60 seconds) |
| `/lhc test loading` | Test the loading overlay |
| `/lhc test firework` | Test the fireworks |

Configuration is stored in `config/laperhardcore.json`.

## Project structure

- `src/main/java/com/laper/lhc`: server-side show timeline, stage/member handling, particles and payloads.
- `src/main/java/com/laper/lhc/client`: cinematic camera and HUD.
- `src/main/java/com/laper/lhc/mixin`: client camera/look hooks.
- `src/main/resources`: Fabric mod metadata and mixin configuration.
- `.github/workflows/build.yml`: automated build.
- `docs/`: video analysis, spec coverage, and build notes.

## Reference fidelity and limitations

This is a working source foundation, not a claim that every part of the reference pack is complete. The current implementation has a title/loading opening, camera approach and member shots, number/name HUD, a bossbar, 10 movement patterns, 8 pose patterns, basic fireworks/particles/sounds, and stage center/entrance setup.

Still outstanding against the full reference: individual per-member quote/subtitle profiles, configurable individual positions/FX/audio, a dedicated group-lineup finale, true spectator-independent viewer camera mode, robust resync for clients joining mid-show, pause/resume, and full multi-client runtime testing. The current source moves viewers to a camera anchor and switches them to spectator while the cinematic camera hook is active; it is not yet the requested fully independent virtual-camera system.

See [VIDEO-REFERENCE.md](docs/VIDEO-REFERENCE.md) and [SPEC-COVERAGE.md](docs/SPEC-COVERAGE.md) before treating any not-yet-implemented item as complete.
