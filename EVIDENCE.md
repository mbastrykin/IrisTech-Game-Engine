# IrisTech — Public Evidence Register

> This document distinguishes **what the public showcase visibly demonstrates** from **what is described but cannot yet be independently verified**. It is documentation, not a substitute for the private engine source or a benchmark report.

**Reference snapshot:** [5 November 2026 showcase update](https://github.com/mbastrykin/IrisTech-Game-Engine/commit/d7d69b853375b0b148280d3c1707e2872b47b37a).  
**Evidence review:** 23 November 2026.  
**Publication scope:** The public repository contains a README and screenshots. It does not publish the engine source code.

## Evidence levels

- **Visual evidence:** A screenshot shows an observable result or interface. It does not, on its own, establish the algorithm, runtime, build reproducibility, or performance.
- **Recorded demonstration:** A continuous, identifiable capture can show a feature operating end-to-end; none is currently hosted in this repository.
- **Reproducible artifact:** A downloadable, versioned demo plus instructions can be exercised by a reviewer; none is currently published as a GitHub Release.
- **Instrumented result:** A benchmark, test log or trace with environment, build identifier and method allows results to be assessed; none is currently published here.
- **Implementation claim:** A feature described in the README but not demonstrable from public artifacts. The engine source remains private.

## What is publicly inspectable now

| Area | Available evidence | What it establishes | What it does **not** establish |
| --- | --- | --- | --- |
| Editor and scene graph | [Hierarchy & Play Mode screenshot](screenshots/hierarchy-play-mode.png), [earlier editor screenshot](screenshots/scene-editor.png) | Viewport, scene hierarchy, editing panels and visible controls | Correct hierarchy operations, scene serialization, or isolated Play Mode state |
| Real-time rendering | [Dark Castle](screenshots/dark-castle-editor.png), [lighting test](screenshots/lighting-and-shadows.png) | Rendered scene, materials and lighting/shadow appearance | Specific shadow algorithms, frame time, or compatibility across backends |
| Forest/stress scene | [Forest scene](screenshots/forest-stress-scene.png) | A forest development scene | Quantitative rendering throughput, scene size or stable FPS |
| Tetrahedral Cage work | [Forest debug overlay](screenshots/forest-debug-overlay.png) | Geometry/debug visualization relevant to cage experiments | Barycentric binding correctness, before/after deformation, regression-test results or GPU path |
| Android driving game | [Rain](screenshots/pedal-to-the-medal-android-rain.png), [daytime](screenshots/pedal-to-the-medal-daytime-highway.png), [traffic](screenshots/pedal-to-the-medal-traffic-streak.png), [hillside](screenshots/pedal-to-the-medal-hillside-road.png), [city](screenshots/pedal-to-the-medal-city-streets.png), [rainy downhill](screenshots/pedal-to-the-medal-rainy-downhill.png), [rainy traffic](screenshots/pedal-to-the-medal-rainy-traffic.png), [run summary](screenshots/pedal-to-the-medal-run-summary.png) | Screenshots presented as gameplay, showing environment variety, HUD, touch controls and results UI | Verified device execution, APK identity, FPS, engine-only rendering or implementation of game logic |
| Audio / Lua / Jolt Physics | README descriptions | Intended or reported subsystems | Working integration, behavioral correctness or test coverage |
| Windows/Android packaging | README descriptions | Reported build workflows | One-project build reproducibility, installer operation or Android runtime integrity |

**Evidence boundary:** The screenshots are real files in this showcase; their presence is not equivalent to independent testing of the private engine. Descriptions such as “experimental” are kept experimental until a repeatable result is published.

## Recommended proof package — publication checklist

The following are **requested future evidence**, not existing validated results. Add them only after capturing and verifying the actual run.

### P0 — continuous end-to-end demonstrations

1. **Windows editor (uncut, 2–3 minutes):** show launch and version/build ID; open a project; select an entity, change its transform and hierarchy; save; reload to show persistence; enter and exit Play Mode; show a separate game player launch if available. Keep the application UI visible.
2. **Android on physical hardware (uncut):** show the phone/device model and OS version, launch the installed Pedal to the Medal APK, demonstrate touch steering/braking, environment change and run-summary UI. Publish the APK version/build ID and SHA-256 of the exact build shown; do not publish signing credentials.
3. **Tetrahedral Cage behavior:** show cage wireframe, bound mesh, before/after deformation, then a moving cage with visible mesh response. Capture the same test input with CPU path and, only if verified, the GPU experiment. Include the test case name and expected outcome.

**Acceptance:** an outside viewer can connect each recording to a stated feature and to a distinct version/build. A cinematic edit alone is weaker proof than an uncut technical demonstration.

### P1 — reproducible build and validation results

4. **Build evidence:** publish redacted Windows and Android build/install logs with toolchain versions, command or UI action used, build timestamp, commit/build ID, success/failure status and resulting binary SHA-256. If an installer or APK cannot be shared, say so clearly rather than implying public download availability.
5. **Regression tests:** publish a test summary for the available deforming, Lua runtime and scene-hierarchy test suites. Include the exact tested build, test names, pass/fail/skip counts and platform. Do not print private source code.
6. **Performance report:** publish raw measurements (CSV preferred) and a short methodology for at least one representative scene. Use repeated runs with fixed settings and distinguish CPU from GPU timings.

Suggested data columns (leave blank rather than invent a value):

| Build ID | Platform/device | GPU | Scene | Resolution | Quality | Run | Avg FPS | Frame time p50 ms | Frame time p95 ms | Frame time p99 ms | Draw calls | Triangles | CPU frame ms | GPU frame ms |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| *not published* | | | | | | | | | | | | | |

For mobile testing, also record OS, graphics backend, thermal/power state, cold/warm run, battery/charging status and sustained performance after several minutes. Record both baseline and changed build when claiming an optimization. FPS without device, settings, scene and methodology is not a reliable performance claim.

### P2 — make specific claims traceable

7. **One-page architecture diagram:** show only public component boundaries — editor, ECS/scene graph, renderer, Lua, audio, physics, runtime and Windows/Android packaging. Avoid exposing private source layout.
8. **Claim-to-evidence cross-references:** attach the relevant timestamp within a demonstration, validation log or benchmark to every high-value claim. When proof is unavailable, label the claim **documented / unverified publicly**.
9. **Cross-platform comparison:** capture the same reproducible test scene on Windows and Android and list intentional differences. This is stronger evidence than two unrelated screenshots.

## Publication integrity and confidentiality

- Do not expose private source code, repository paths, credentials, API keys, signing files, personal machine paths or customer/project secrets.
- Separate **current verified behavior** from **experimental work** and future goals.
- Identify each screenshot, video, APK or benchmark by the build from which it was captured. Preserve original output; do not use mockups as proof of engine behavior.
- A public README can document a closed-source engine. It should not imply that the public showcase alone verifies internal algorithm implementations.
