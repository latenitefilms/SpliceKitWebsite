# Release Notes

### 3.1.149

**🎉 Released:**
- 17th April 2026

**🥳 New Features:**
- Native Blackmagic RAW (BRAW) playback in Final Cut Pro — import, preview, and edit .braw files from URSA Cine / BMPCC / Pocket 4K/6K cameras without transcoding. Works with every codec variant we've seen in the wild (braw, brxq, brst, brvn) including URSA Cine 17K. Playback runs through the Blackmagic RAW SDK with zero-copy Metal decode and realtime framerates at 6K+.

---

### 3.1.148

**🎉 Released:**
- 16th April 2026

**🔨 Improvements**
- Automatically expose Apple's AUSoundIsolation effect on startup so Voice Isolation stays available in the audio effects browser across launches.

---

### 3.1.147

**🎉 Released:**
- 16th April 2026

**🐞 Bug Fix:**
- Fix OTIO and FCPXML import reliability: preserve source in-points, normalize media URLs, avoid library-picker fallbacks, and import projects through the in-process pipeline.

---

### 3.1.146

**🎉 Released:**
- 16th April 2026

**🐞 Bug Fix:**
- Fix an Audio Mixer bug that could cause a major performance drop after adding audio bus effects. Mixer polling now avoids repeated effect-stack mutations while keeping bus effects attached to their roles.

---

### 3.1.145

**🎉 Released:**
- 16th April 2026

**🔨 Improvements**
- Audio Mixer: managed role-bus effects, solo/mute controls, FX menu, state mirroring, diagnostics.

---

### 3.1.144

**🎉 Released:**
- 16th April 2026

**🔨 Improvements**
- Transcript Editor diagnostics, timestamp mapping fixes, speaker cleanup, and faster pause deletion.

---

### 3.1.143

**🎉 Released:**
- 15th April 2026

**🔨 Improvements**
- Add song cut workflow for beat-synced video assembly from sequence-backed sources. Fix cumulative frame drift in FCPXML builds, fix connected song alignment, add half-beat pairing rule, add sequence name substring matching, resolve timeline clips to browser equivalents for native insertion.

---

### 3.1.142

**🎉 Released:**
- 15th April 2026

**🐞 Bug Fix:**
- Fix audio mixer clip discovery for nested compound clips and storylines, handle deduplication, caption panel visibility guard

---

### 3.1.141

**🎉 Released:**
- 15th April 2026

**🐞 Bug Fix:**
- Fix Remove All Keyframes command: recursive discovery of keyframe targets across child clips, effect stacks, and audio channels

---

### 3.1.14

**🎉 Released:**
- 15th April 2026

**🥳 New Features:**
- **All-new Audio Mixer UI:** role-colored faders with gradient strips, segmented LED meters with clipping detection, per-fader automation arming, real-time volume during playback, keyframe management

---

### 3.1.13

**🎉 Released:**
- 14th April 2026

**🐞 Bug Fix:**
- Mixer metering works without Audio Meters panel, CALayer tree search for mini transport meters.

---

### 3.1.12

**🎉 Released:**
- 14th April 2026

**🔨 Improvements**
- Live audio metering in mixer panel, Final Cut Pro role colors, keyframed volume support.

---

### 3.1.11

**🎉 Released:**
- 14th April 2026

**🐞 Bug Fix:**
- Fix transcript editor missing connected clips (`FFAnchoredClip` URL resolution), mixer panel, caption enhancements, CloudContent diagnostic logging, patcher launch monitoring.

---

### 3.1.10

**🎉 Released:**
- 14th April 2026

**🐞 Bug Fix:**
- Fix CloudKit crash on Final Cut Pro 12.2+, patcher diagnostic logging to `~/Library/Logs/SpliceKit/patcher.log`, comprehensive startup diagnostics in `dylib`, disable spring-loaded blade.

---

### 3.1.9

**🎉 Released:**
- 14th April 2026

**🐞 Bug Fixes:**
- Fix patcher signing on macOS 15.7.3 — the patcher was applying only 1 entitlement (cs-disable-library-validation) instead of the full set needed for ad-hoc signing. This caused the re-signed app to launch unsigned on some systems, triggering a CloudKit crash (EXC_BREAKPOINT in CloudContentCatalog.updateCatalogAndRegistry()). Now applies all 4 required entitlements including explicit app-sandbox=false to prevent CloudKit entitlement validation failures. Fixed across all patcher paths: GUI app (initial patch + update), shell script, and entitlements.plist. (Fixes #23)

**📄 Documentation:**
- Added plain-English explainer — What Is SpliceKit? covers what it is, how it works, and whether it's safe, written for non-technical users. Linked from the top of the README.

---

### 3.1.8

**🎉 Released:**
- 14th April 2026

**🐞 Bug Fixes:**
- **Transcript persistence across projects** — switching projects no longer shows stale transcript from previous project; added `transcript.clear` RPC endpoint
- **addTodoMarker fixed** — was returning "No responder handled"; now uses direct sequence method
- **Silence detection** — was returning 0 silences on clips with obvious pauses; improved threshold algorithm and added start-to-start interval detection
- **Timeline duration** — was reporting 0.000s; now falls back to summing spine clip durations
- **add_markers_at_times offset** — now accounts for timeline start offset (e.g. 01:00:00:00)

**🥳 New Features:**
- **OpenTimelineIO import/export** — universal timeline exchange with DaVinci Resolve, Premiere Pro, Avid (`.otio`, `.edl`, `.aaf`)
- **Native OTIO-to-FCPXML converter** — frame-exact conversion with canonical SMPTE timebases
- **Compound clip drilling** — `get_timeline_clips` now exposes `isCompound`, `nestedItemCount`, and `include_nested` parameter
- **Batch editing tools** — `apply_transition_to_all_clips`, `batch_apply_effect`, `batch_color_correct`
- **Expanded command palette** — full categorized action lists, comprehensive AI capabilities prompt
- **Lua example** — `shuffle_clips.lua` script

---

### 3.1.7

**🎉 Released:**
- 12th April 2026

**🔨 Improvements**
- Sections bar for timeline song structure, add default transition to all clips command, fuzzy search stop-word handling. Watch [video[(https://youtu.be/plirvqHe6o0).

---

### 3.1.6

**🎉 Released:**
- 10th April 2026

**🔨 Improvements**
- Dual timeline workflow updates, cross-window drag and copy, secondary window controls, and browser sizing/layout fixes.

---

### 3.1.5

**🎉 Released:**
- 10th April 2026

**🔨 Improvements**
- Improves patcher update detection and rebuild/update flows, fixes bundled Parakeet packaging for updates, and reduces patched-app signing friction by removing unnecessary debug entitlements.

---

### 3.1.4

**🎉 Released:**
- 8 April 2026

**🔨 Improvements**
- Improves social caption insertion and relaunch restore. Fixes title placeholder recovery on restart, preserves caption placement on reload, and tightens word highlighting behavior.

---

### 3.1.3

**🎉 Released:**
- 8 April 2026

**Apple Intelligence+ (Agentic Mode):**
- New **Apple Intelligence+** engine in the Command Palette — an agentic AI mode powered by Apple's on-device FoundationModels framework with tool-calling capabilities
- Apple Intelligence+ can read your timeline, seek to specific times, blade/cut clips, add markers, apply effects, execute menu commands, and repeat actions at intervals — all from a natural language prompt
- 6 built-in tools: **edit** (timeline actions), **seek** (playhead positioning), **clips** (read timeline state), **repeat_action** (batch operations like "blade every 5 seconds"), **effect** (apply effects), **menu** (execute any Final Cut Pro menu command)
- Timeline-aware context: Apple Intelligence+ automatically knows your project name, duration, clip count, frame rate, and playhead position
- Smart pattern detection: phrases like "cut every 3 seconds" or "add markers every 10 seconds" are intercepted for fast direct execution
- Three AI engines selectable from the Command Palette dropdown: **Apple Intelligence** (basic), **Gemma 4** (local MLX), and **Apple Intelligence+** (agentic with tools) — Apple Intelligence+ is now the default
- Engine preference persists across sessions via `NSUserDefaults`

**Lua Scripting Engine:**
- Embedded Lua 5.4 VM running directly in FCP's process (zero latency)
- `sk` module with 25+ actions: `sk.blade()`, `sk.seek()`, `sk.clips()`, `sk.rpc()`, `sk.eval()`
- REPL panel (`CONTROL+OPTION+L`) for interactive scripting
- Live coding: save `.lua` files to `~/Library/Application Support/SpliceKit/lua/auto/`
- 8 built-in menu scripts (timeline report, remove silences, blade every 5s, balance color, cross dissolves, generate captions, export XML, screenshot viewer)
- 25+ example scripts (podcast producer, music video editor, conform tool, batch export, and more)
- MCP tools: `lua_execute`, `lua_execute_file`, `lua_reset`, `lua_watch`, `lua_state`

**Social Captions (Improved):**
- Uses Final Cut Pro's built-in Basic Title — works on all Final Cut Pro installations, no custom templates needed
- Word-by-word karaoke highlighting via per-word `<text-style>` colouring
- Auto-transcribe: generates captions without manual transcription step
- Drop shadow on all caption text for readability
- Lower-third positioning via Motion channel hierarchy
- Screen freeze hides temp project switch (seamless UX)
- `reloadMicaDocument` fix: no more greyed-out text or Inspector crashes

**Default Spatial Conform Type (PR #22):**
- Override default spatial conform (Fit/Fill/None) for new timeline clips
- Menu: `Enhancements > Options > Default Spatial Conform`
- Options panel dropdown + Command Palette cycling
- Bridge API: `set_bridge_option_value("defaultSpatialConformType", "fill")`

**🐞 Bug Fixes:**
- Fix Lua RPC main thread deadlock: `sk.rpc()` no longer forces every call through main thread, preventing soft deadlocks during polling loops
- Fix caption engine override: caption generation now uses the user's configured transcription engine instead of forcing FCP Native
- Fix parakeet-transcriber build for updated FluidAudio API (`AsrManager.initialize` → `loadModels`, new model version enum variants)
- Caption script is now non-blocking for long clips with transcript reuse
---

### 3.1.2

**🎉 Released:**
- 7 April 2026

**🔨 Improvements**
- Added local App Store receipt validation for Creator Studio subscriptions before launch.
- Shows an alert when no valid subscription is found.

---

### 3.1.1

**🎉 Released:**
- 7 April 2026

**🐞 Bug Fixes:**
- Added support fixes for Final Cut Pro Creator Studio.
- Fixed subscription validation and a CloudKit crash on ad-hoc signed builds.

---

### 3.1.0

**🎉 Released:**
- 6 April 2026

**🔨 Improvements**
- Added configurable J/L playback speed ladders instead of Final Cut Pro’s fixed shuttle progression.
- Added menu and API controls for custom playback ladders.
- Added MCP playback speed controls and current-rate reporting.
- Preserved original K+L and K+J single-frame stepping behavior.

---

### 3.0.2

**🎉 Released:**
- 6 April 2026

**🔨 Improvements**
- Improved Final Cut Pro discovery so SpliceKit can find non-standard app locations automatically.
- Added a manual “Browse for Final Cut Pro...” fallback.

**🐞 Bug Fixes:**
- Fixed a launch crash caused by a missing log panel class in the dylib build.
- Fixed incorrect version display when Final Cut Pro is installed outside the default path.

---

### 3.0.1

**🎉 Released:**
- 5 April 2026

**🔨 Improvements**
- Bundled the pre-built `parakeet-transcriber` in the DMG for easier setup.
- Improved Parakeet error messages and skipped clips shorter than 0.5s.
- Deployed helper tools into the SpliceKit tools folder during deployment and added more detailed logging.

**🐞 Bug Fixes:**
- Fixed Sparkle showing false update prompts on the latest version.

---

### 3.0.0

**🎉 Released:**
- 5 April 2026

**🔨 Improvements**
- Rebranded FCPBridge as **SpliceKit**.
- Introduced a new wizard-style patcher app, DMG distribution, and app icon.
- Renamed the Final Cut Pro menu item to **Enhancements**.
- Removed hardcoded user-specific paths and standardized tool locations.
- Existing users need to re-patch because the framework name changed.

---

### 2.8.4

**🎉 Released:**
- 4 April 2026

**🔨 Improvements**
- Added effect browser favorites support through Final Cut Pro’s built-in favorites API.
- Exposed Final Cut Pro internal debug and diagnostics tools through MCP presets.
- Fixed patcher signing to preserve Apple framework signatures.
- Added crash prevention for unsafe trim selectors and fixed the `retimeHold` action mapping.

**🐞 Bug Fixes:**

---

### 2.8.3

**🎉 Released:**
- 2 April 2026

**🔨 Improvements**
- Added effect dragging to empty timeline space to create named adjustment clips.
- Included a toggle for this behavior in the FCPBridge menu.

---

### 2.8.2

**🎉 Released:**
- 2 April 2026

**🔨 Improvements**
- Added support for Final Cut Pro Creator Studio with auto-detection and an edition picker.
- Added adjustment clip creation when dragging effects into empty timeline space.

---

### 2.8.1

**🎉 Released:**
- 2 April 2026

**🔨 Improvements**
- Improved Parakeet error messages with download progress and network, disk, memory, and Xcode CLT diagnostics.
- Expanded the command palette to 120+ entries.

---

### 2.8.0

**🎉 Released:**
- 2 April 2026

**🔨 Improvements**
- Added full MCP control with universal menu access and dialog handling.
- Added effect parameter read/write support for opacity, transform, crop, and volume.
- Expanded timeline actions to 200+ operations.
- Improved playhead monitoring, tool selection, and modal-safe dispatch.

---

### 2.7.0

**🎉 Released:**
- 2 April 2026

**🔨 Improvements**
- Added batch export to export timeline clips individually to a folder with one initial destination prompt.
- Added `batch_export()` and `set_timeline_range()` MCP tools.
- Added absolute `startTime` and `endTime` positions for timeline clips.
- Used swizzling and range controls to automate Final Cut Pro’s export pipeline.

---

### 2.6.1

**🎉 Released:**
- 1 April 2026

**🔨 Improvements**
- Fixed Parakeet in the release patcher by embedding transcriber source in the patcher app bundle.
- Added handling for read-only app bundles by copying sources to a writable temp directory before building.

---

### 2.6.0

**🎉 Released:**
- 1 April 2026

**🔨 Improvements**
- Made Parakeet v3 Multilingual the default transcription engine, with Parakeet v2 still available.
- Added batch transcription with shared model loading, source deduplication, and concurrent diarization.
- Fixed installation issues caused by hardcoded paths and improved binary deployment.
- Cleaned up logs, sockets, repo files, and patcher resources.

---

### 2.5.0

**🎉 Released:**
- 1 April 2026

**🔨 Improvements**
- Added Sparkle auto-update support to the patcher.
- Fixed “Browse Titles...” so titles insert correctly as connected clips.
- Made NVIDIA Parakeet the default transcription engine.
- Added speaker diarization and improved transcript/playhead sync after edits.

---

### 2.4.0

**🎉 Released:**
- 1 April 2026

**🔨 Improvements**
- Added NVIDIA Parakeet transcription as the default engine.
- Added speaker diarization for Parakeet and Apple Speech.
- Added speaker renaming in the transcript UI.
- Improved transcript/playhead sync, long-audio stability, authorization flow, and progress updates.

---

### 2.3.0

**🎉 Released:**
- 1 April 2026

**🔨 Improvements**
- Added a VS Code-style command palette inside Final Cut Pro.
- Added Apple Intelligence integration for natural-language editing commands.
- Added silence detection and removal using Apple-native audio analysis.
- Added scene detection with configurable marking and blading actions.
- Improved timeline state, playhead positioning, and media path resolution.

---

### 2.2.0

**🎉 Released:**
- 1 April 2026

**🔨 Improvements**
- Fixed live playhead sync for transcript highlighting during playback.
- Moved patcher shell commands off the main thread to prevent beachballing.
- Removed the git dependency by switching downloads to `curl`.
- Fixed button overflow and clean Cmd+Q shutdown.

---

### 2.1.0

**🎉 Released:**
- 31 March 2026

**🔨 Improvements**
- Added a transcript editor for text-based video editing inside Final Cut Pro.
- Added word-level transcription, click-to-seek, delete-to-ripple-delete, and drag-to-reorder.
- Added toolbar, menu bar, and keyboard shortcut integration.
- Added a self-contained signed patcher app.
- Added MCP tools for opening, reading, deleting, and moving transcript words.

---

### 2.0.0

**🎉 Released:**
- 31 March 2026

**🔨 Improvements**
- Introduced **FCPBridge 2.0.0** with direct programmatic control of Final Cut Pro via injected dylib and MCP server.
- Added 28 MCP tools, 40+ timeline actions, JSON-RPC access, object handles, KVC property access, and FCPXML generation/import.
- Added patcher app support for copying, injecting, re-signing, and launching a modded Final Cut Pro build.
- Verified the system with 30 passing tests across editing, playback, color, effects, and timeline analysis.