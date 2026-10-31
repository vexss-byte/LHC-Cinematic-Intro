# Build and test

## Automated build

GitHub Actions workflow: `.github/workflows/build.yml`.

- Triggers: push to main, pull request, or manual workflow dispatch.
- Runner: Ubuntu latest.
- Java: Temurin 25.
- Gradle: 9.8.2.
- Build command: `gradle build --stacktrace`.
- Artifact: `laper-hardcore-intro-jar`, containing JAR files from `build/libs/`.

To download the JAR:
1. Open the repository's **Actions** tab.
2. Select the latest **Build LHC Cinematic Intro** run.
3. Wait for the run to complete successfully.
4. Download `laper-hardcore-intro-jar` from the Artifacts section.

## Manual test checklist

- Start a dedicated Minecraft 26.3 server with Fabric Loader and Fabric API.
- Join using at least two clients with this mod installed.
- Configure center and entrance in the same dimension.
- Run the full intro and a single-member preview.
- Stop during loading, approach, walk-in, and pose phases.
- Disconnect a viewer during the sequence.
- Verify camera, HUD, sound, and particles on all clients.
- Verify viewer position, rotation, and gamemode are restored.
- Test with the maximum supported 40 names.

A successful Java/Gradle build is not proof of visual parity with the reference video; runtime tests remain necessary.
