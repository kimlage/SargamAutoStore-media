# SargamAutoStore 1.0.0 — local workload measurements

Measured on September 25, 2026: Apple M3 Max, 36 GiB RAM, macOS, Valheim 1.0.15, Unity 6000.0.75f1, BepInEx 5.4.23.5. Local singleplayer, 1920×1080. Isolated profile: SargamAutoStore plus a private measurement helper; other gameplay mods were absent. Bloom, depth of field, motion blur and chromatic aberration were enabled during this measurement.

## Results

| Workload | Units stored | Elapsed | Mod Update mean | Mod Update p95 | Mod Update maximum | Sampled frames |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| Idle, 32 loaded chests | 0 | 8.008 s | 0.034 ms | 0.062 ms | 0.164 ms | 720 |
| Ground, round 1 | 1,024 | 0.500 s | 1.828 ms | 2.406 ms | 3.201 ms | 32 |
| Ground, round 2 | 1,024 | 0.599 s | 1.907 ms | 2.125 ms | 5.714 ms | 32 |
| Ground, round 3 | 1,024 | 0.367 s | 1.711 ms | 1.860 ms | 1.927 ms | 25 |

Every workload reached the expected destination: 32 item types, 32 native chests, 32 units added per chest. Native in-memory inventory and independently loaded saved ZDO inventory agreed on quantities and types. No production error counter increased. All 32 receiving-chest highlight effects were active concurrently during each workload.

## Method

The private fixture creates 32 seeded, player-built chests on a temporary stepped deck. Each receives only its existing exact item type. Chest range is 32 m; player activity range is 64 m. Signs are disabled. Work limits are the normal 24 entries per frame and 1.5 ms cooperative budget. Destination glow uses the normal 1.5-second duration and HUD feedback remains enabled.

After an eight-second idle sample, the helper creates 1,024 single-unit drops per round, waits two seconds for settling, and enables automatic collection. Creation and settling are outside the measured interval. Valheim may merge nearby drops, so this is **1,024 units**, not a claim that 1,024 separate objects remain when timing begins. The same production scheduler used during normal play performs all transfers. The first workload is included, but this is a warmed game session following the functional demo, not a cold-start benchmark.

A Harmony prefix/postfix measures wall time spent in the production plugin's `Update`, including its scheduler, feedback and highlight maintenance. It excludes later Unity rendering/physics and the private helper's work. The 1.5 ms setting is a cooperative scheduler target, not a hard ceiling for the full Update; one native game call or other Update work can exceed it. The observed maximum was 5.714 ms. No screenshots were captured during timed samples.

The CSV also includes whole-game frame p50/p95; those are not CPU time attributable to this mod. Idle was 11.094/13.478 ms; the three active rounds were 15.673/19.709, 18.490/22.005 and 14.667/21.049 ms. This is a small local sample without a mod-disabled baseline or other gameplay mods, not an FPS guarantee or a multiplayer/Windows/Linux certification. Hardware, world density, native drop merging and other mods can change the result substantially.

## Data

- [Summary CSV](benchmark.csv)
- [Idle samples](idle-samples.csv)
- [Round 1 samples](ground1024-r1-samples.csv)
- [Round 2 samples](ground1024-r2-samples.csv)
- [Round 3 samples](ground1024-r3-samples.csv)

Sample CSV columns are `plugin_update_ms,whole_frame_ms` (no header). Quantiles use the nearest-rank method. Only sanitized numeric measurements are public; raw game logs, saves and private inventory backups are excluded.
