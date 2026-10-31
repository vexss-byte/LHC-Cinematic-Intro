# Reference pack implementation coverage

"Implemented" below means a corresponding code path exists in this repository. It does not mean the feature has passed full dedicated-server and multi-client runtime testing.

| Requirement | Current state | Notes |
|---|---|---|
| Register member names | Implemented | Add/remove/list/clear/online commands |
| Up to 40 members | Basic validation | Add and online commands enforce 40 |
| Automatic numbering | Implemented | Uses member list order |
| Full intro | Implemented foundation | Opening, approach, per-member show, load-out |
| Single-member preview | Implemented | `/lhc play member <name>` |
| Title reveal | Partial | Title/subtitle packets and loading overlay |
| Cinematic camera | Partial | Client camera mixin for approach/member shots |
| Independent virtual camera without spectator mode | Not implemented | Viewers are currently moved to an anchor and set to spectator |
| Member number/name HUD | Implemented | Lower-left card |
| Per-member quote/subtitle | Not implemented | No per-member quote field or payload yet |
| Bossbar progress | Implemented | Current member and progress |
| Multiple walk styles | Partial | 10 algorithmic movement styles |
| Multiple poses | Partial | 8 pose patterns; not 40 editable presets |
| Custom position per member | Not implemented | Shared entrance and center only |
| Stage entrance and center | Implemented | Set with `/lhc setentrance` and `/lhc setcenter` |
| Per-member particle profile | Not implemented | Shared procedural FX |
| Fireworks and particle FX | Partial | Basic gold/mixed fireworks and poof/dust |
| Per-member audio profile | Not implemented | Fixed sound cues |
| Group-lineup finale | Not implemented | Current full intro uses load-out |
| Outro camera scene | Not implemented | No dedicated outro sequence |
| Viewer restoration on stop/end | Partial | Position, rotation and gamemode are stored/restored |
| Resync for join-in-progress | Not implemented | Only the initial viewer set receives state |
| Pause/resume | Not implemented | Play and stop only |
| World border/build-height checks | Not implemented | Validate stage before running on production server |
| GitHub Actions build | Implemented | Workflow builds with Java 25 and Gradle 9.8.2 |
| Dedicated server/multi-client testing | Pending | Must be tested in a real 26.3 environment |

## Priorities

1. Add per-member profile data: display name, quote, entrance/final position, pose ID, FX profile, and sound profile.
2. Implement the bottom quote card and synchronized message transitions.
3. Add a group-lineup finale and dedicated outro camera shot.
4. Replace spectator-based viewing with an isolated virtual camera.
5. Add late-join resynchronization and pause/resume state handling.
6. Validate stage positions against dimension, world border, and build height.
7. Run dedicated-server tests with multiple clients and document the results.
