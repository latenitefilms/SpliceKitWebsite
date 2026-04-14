# Command Palette

Apple Intelligence for Final Cut Pro.

Hit **COMMAND+SHIFT+P** inside the modded FCP to open a VS Code-style command palette with fuzzy search across 100+ editing actions. Type what you want to do in plain English and Apple Intelligence (on-device LLM via FoundationModels) translates your intent into editing actions.

**Built-in commands include:**

- **Editing**: Blade, delete, cut/copy/paste, trim, nudge, compound clips, detach audio, lift/overwrite, create storylines
- **Playback**: Play/pause, frame stepping, go to start/end, loop, play selection, JKL-style controls
- **Color**: Color Board, Color Wheels, Color Curves, Hue/Saturation, auto-enhance, match color, balance color
- **Speed**: Normal, 2x/4x/8x/20x fast, 50%/25%/10% slow, reverse, freeze frame, hold frame
- **Markers**: Standard, to-do, and chapter markers with navigation
- **Effects & Transitions**: Browse, search, and apply any effect, transition, generator, or title by name
- **Audio**: Volume up/down, fade in/out, audio enhancements, **Remove Silences** (auto-detects and removes silent segments)
- **Scene Detection**: Analyze video for shot boundaries and automatically add markers or blade at every scene change
- **Transform**: Crop, distort, reframe, stabilize
- **Multicam**: Switch and cut angles 1-4, create multicam clips
- **Captions**: Add/import captions and subtitles
- **Ratings & Roles**: Favorite, reject, role assignment
- **View**: Zoom to fit, snapping, skimming, timeline index, inspector
- **Export**: Render, share selection, export FCPXML

**Natural language examples you can ask Apple Intelligence:**

- *"add markers every 5 seconds"*
- *"slow this clip to half speed"*
- *"add a cross dissolve"*
- *"color correct this clip"*
- *"blade at every scene change"*
- *"remove all the silences"*
- *"zoom to fit the timeline"*

The AI understands your intent, maps it to the right sequence of FCP actions, and executes them — all without leaving the keyboard.

**Remove Silences** uses Apple-native AVFoundation + Accelerate (vDSP) to analyze audio and detect silent segments. No ffmpeg or external dependencies. An options panel lets you configure the detection threshold, minimum silence duration, and padding. The audio analysis runs in the background with a processing indicator, then silences are bladed and ripple-deleted from the timeline.

**Scene Detection** uses histogram-based frame comparison via the Accelerate framework's vImage to detect cuts and shot changes. Configurable sensitivity and sample interval. Markers are inserted programmatically at exact timecodes — no playhead movement required — making it fast even on long sequences.
