# Living Table: First Steps
### by COLTRAN Studios

Hands-first mixed-reality chess for Meta Quest 3. Align a physical board using four corners, play against an on-device chess opponent, and switch between physical-board overlays and a virtual board while retaining the game state.

## Test build

[Download Quest APK 0.1.30](https://github.com/MistaMischif/Living-Table-First-Steps/releases/tag/firststeps-v0.1.30).

Install the APK with Meta Quest Developer Hub or `adb install -r LivingTable-FirstSteps-0.1.30.apk`. Package: `com.livingtable.firststeps`. Requires a Quest configured for sideloading.

1. START, position the board, then CONTINUE.
2. Place four corners around the playable squares, excluding the frame.
3. Valid green geometry presents the standard pieces. PLAY starts you as White against AI.
4. In physical mode, move the virtual piece to the intended square and press MOVED IT to finish the turn. Move the physical AI piece as prompted, then press MOVED IT.
5. GO VIRTUAL retains an obstacle warning. REAL BOARD resumes immediately without alignment or scanning and hides the virtual board surface.

## Source and build

Public contest snapshot of version 0.1.30. Open with Unity 6000.3.9f1 and Android Build Support (SDK, NDK, OpenJDK). Package dependencies are declared in Packages/manifest.json. The Quest release entry point is `LivingTable.Editor.FirstStepsRelease.Build`; run Unity in batch mode with `-executeMethod LivingTable.Editor.FirstStepsRelease.Build`. Output: `Builds/LivingTable-FirstSteps-0.1.30.apk`.

Tests: `LivingTable.Editor.IntegratedFlowTests.Run` and `LivingTable.Editor.PhysicalFlowTests.Run` (batch mode without `-quit`; suites exit when finished). The source revision passed 117 integrated, 80 physical-flow and 50 end-to-end handoff checks. The published APK built successfully and was installed and launched on Quest. Three controlled Quest sleep/wake cycles passed with the same process and 3.29 MiB total graphics-memory growth. Live headset checkpoints verify physical → virtual → physical and continued play to ply 20, preserving exact game state. Two further suspend/resume pairs retained stable reported graphics allocation. MASTER OMEGA confirmed the full handoff and both manual visor wakes worked on November 4, 2026; this tested scope is founder-accepted. See [device evidence](releases/firststeps-0.1.30/DEVICE-TEST.md).

## Honest capability boundaries

- Chess opponent runs on-device. Optional conversational/vision services are separate self-hosted components under Services/FirstSteps; they require a reachable configured host.
- Turn-time camera recognition is disabled in this test build. Physical moves are user-confirmed, not camera-verified.
- Standard starting layout only in the simplified launch flow. Continue Game and Quick Play launch options have been removed.
- OpenXR is pinned to 1.17.1 to avoid the documented 1.18+ sleep/wake leak. Three controlled Quest cycles passed; this bounded test is not a guarantee against every crash.
- This snapshot has not been independently rebuilt after removing non-contest artwork. The APK is the verified 0.1.30 release, whose build excludes Candy Land resources.

Private development history, patent drafts, local generated build files, runtime credentials, and Candy Land artwork are excluded. Shared source code remains where required by the existing Unity architecture. Existing third-party notices and dependency terms remain applicable. No additional open-source licence is granted by making this contest snapshot public.
