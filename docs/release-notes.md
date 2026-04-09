# Release Notes

### 3.1.4

**🎉 Released:**
- 8 Apr 2026

**🔨 Improvements**
- Improves social caption insertion and relaunch restore. Fixes title placeholder recovery on restart, preserves caption placement on reload, and tightens word highlighting behavior.

---

### 3.1.3

**🎉 Released:**
- 8 Apr 2026

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

**Bug Fixes:**
- Fix Lua RPC main thread deadlock: `sk.rpc()` no longer forces every call through main thread, preventing soft deadlocks during polling loops
- Fix caption engine override: caption generation now uses the user's configured transcription engine instead of forcing FCP Native
- Fix parakeet-transcriber build for updated FluidAudio API (`AsrManager.initialize` → `loadModels`, new model version enum variants)
- Caption script is now non-blocking for long clips with transcript reuse
---

### 3.1.2

**🎉 Released:**
- 7 Apr 2026

**What's New:**
- Added local App Store receipt validation for Creator Studio subscriptions before launch.
- Shows an alert when no valid subscription is found.

---

### 3.1.1

**🎉 Released:**
- 7 Apr 2026

**What's New:**
- Added support fixes for Final Cut Pro Creator Studio.
- Fixed subscription validation and a CloudKit crash on ad-hoc signed builds.

---

### 3.1.0

**🎉 Released:**
- 6 Apr 2026

**What's New:**
- Added configurable J/L playback speed ladders instead of Final Cut Pro’s fixed shuttle progression.
- Added menu and API controls for custom playback ladders.
- Added MCP playback speed controls and current-rate reporting.
- Preserved original K+L and K+J single-frame stepping behavior.

---

### 3.0.2

**🎉 Released:**
- 6 Apr 2026

**What's New:**
- Improved Final Cut Pro discovery so SpliceKit can find non-standard app locations automatically.
- Added a manual “Browse for Final Cut Pro...” fallback.
- Fixed a launch crash caused by a missing log panel class in the dylib build.
- Fixed incorrect version display when Final Cut Pro is installed outside the default path.

---

### 3.0.1

**🎉 Released:**
- 5 Apr 2026

**What's New:**
- Fixed Sparkle showing false update prompts on the latest version.
- Bundled the pre-built `parakeet-transcriber` in the DMG for easier setup.
- Improved Parakeet error messages and skipped clips shorter than 0.5s.
- Deployed helper tools into the SpliceKit tools folder during deployment and added more detailed logging.

---

### 3.0.0

**🎉 Released:**
- 5 Apr 2026

**What's New:**
- Rebranded FCPBridge as **SpliceKit**.
- Introduced a new wizard-style patcher app, DMG distribution, and app icon.
- Renamed the Final Cut Pro menu item to **Enhancements**.
- Removed hardcoded user-specific paths and standardized tool locations.
- Existing users need to re-patch because the framework name changed.

---

### 2.8.4

**🎉 Released:**
- 4 Apr 2026

**What's New:**
- Added effect browser favorites support through Final Cut Pro’s built-in favorites API.
- Exposed Final Cut Pro internal debug and diagnostics tools through MCP presets.
- Fixed patcher signing to preserve Apple framework signatures.
- Added crash prevention for unsafe trim selectors and fixed the `retimeHold` action mapping.

---

### 2.8.3

**🎉 Released:**
- 2 Apr 2026

**What's New:**
- Added effect dragging to empty timeline space to create named adjustment clips.
- Included a toggle for this behavior in the FCPBridge menu.

---

### 2.8.2

**🎉 Released:**
- 2 Apr 2026

**What's New:**
- Added support for Final Cut Pro Creator Studio with auto-detection and an edition picker.
- Added adjustment clip creation when dragging effects into empty timeline space.

---

### 2.8.1

**🎉 Released:**
- 2 Apr 2026

**What's New:**
- Improved Parakeet error messages with download progress and network, disk, memory, and Xcode CLT diagnostics.
- Expanded the command palette to 120+ entries.

---

### 2.8.0

**🎉 Released:**
- 2 Apr 2026

**What's New:**
- Added full MCP control with universal menu access and dialog handling.
- Added effect parameter read/write support for opacity, transform, crop, and volume.
- Expanded timeline actions to 200+ operations.
- Improved playhead monitoring, tool selection, and modal-safe dispatch.

---

### 2.7.0

**🎉 Released:**
- 2 Apr 2026

**What's New:**
- Added batch export to export timeline clips individually to a folder with one initial destination prompt.
- Added `batch_export()` and `set_timeline_range()` MCP tools.
- Added absolute `startTime` and `endTime` positions for timeline clips.
- Used swizzling and range controls to automate Final Cut Pro’s export pipeline.

---

### 2.6.1

**🎉 Released:**
- 1 Apr 2026

**What's New:**
- Fixed Parakeet in the release patcher by embedding transcriber source in the patcher app bundle.
- Added handling for read-only app bundles by copying sources to a writable temp directory before building.

---

### 2.6.0

**🎉 Released:**
- 1 Apr 2026

**What's New:**
- Made Parakeet v3 Multilingual the default transcription engine, with Parakeet v2 still available.
- Added batch transcription with shared model loading, source deduplication, and concurrent diarization.
- Fixed installation issues caused by hardcoded paths and improved binary deployment.
- Cleaned up logs, sockets, repo files, and patcher resources.

---

### 2.5.0

**🎉 Released:**
- 1 Apr 2026

**What's New:**
- Added Sparkle auto-update support to the patcher.
- Fixed “Browse Titles...” so titles insert correctly as connected clips.
- Made NVIDIA Parakeet the default transcription engine.
- Added speaker diarization and improved transcript/playhead sync after edits.

---

### 2.4.0

**🎉 Released:**
- 1 Apr 2026

**What's New:**
- Added NVIDIA Parakeet transcription as the default engine.
- Added speaker diarization for Parakeet and Apple Speech.
- Added speaker renaming in the transcript UI.
- Improved transcript/playhead sync, long-audio stability, authorization flow, and progress updates.

---

### 2.3.0

**🎉 Released:**
- 1 Apr 2026

**What's New:**
- Added a VS Code-style command palette inside Final Cut Pro.
- Added Apple Intelligence integration for natural-language editing commands.
- Added silence detection and removal using Apple-native audio analysis.
- Added scene detection with configurable marking and blading actions.
- Improved timeline state, playhead positioning, and media path resolution.

---

### 2.2.0

**🎉 Released:**
- 1 Apr 2026

**What's New:**
- Fixed live playhead sync for transcript highlighting during playback.
- Moved patcher shell commands off the main thread to prevent beachballing.
- Removed the git dependency by switching downloads to `curl`.
- Fixed button overflow and clean Cmd+Q shutdown.

---

### 2.1.0

**🎉 Released:**
- 31 Mar 2026

**What's New:**
- Added a transcript editor for text-based video editing inside Final Cut Pro.
- Added word-level transcription, click-to-seek, delete-to-ripple-delete, and drag-to-reorder.
- Added toolbar, menu bar, and keyboard shortcut integration.
- Added a self-contained signed patcher app.
- Added MCP tools for opening, reading, deleting, and moving transcript words.

---

### 2.0.0

**🎉 Released:**
- 31 Mar 2026

**What's New:**
- Introduced **FCPBridge 2.0.0** with direct programmatic control of Final Cut Pro via injected dylib and MCP server.
- Added 28 MCP tools, 40+ timeline actions, JSON-RPC access, object handles, KVC property access, and FCPXML generation/import.
- Added patcher app support for copying, injecting, re-signing, and launching a modded Final Cut Pro build.
- Verified the system with 30 passing tests across editing, playback, color, effects, and timeline analysis.