# How To Use

This page explains how to setup and use **SpliceKit**.

If you run into any problems the best place for support is the [FCP Cafe Discord](https://ltnt.tv/discord).

---

## Installation

Make sure you have **Final Cut Pro v12** (lifetime/perpetual) and/or **Final Cut Pro Creator Studio v12** (subscription) installed.

Download the latest **SpliceKit** `DMG` from the [website](https://github.com/elliotttate/SpliceKit/releases/latest).

Open the `DMG` and drag **SpliceKit** into your **Applications** folder:

![](/static/installation-01.png)

Launch **SpliceKit** from your **Applications** folder.

![](/static/installation-02.png)

Pick the version of Final Cut Pro you want to use and click **Continue**:

![](/static/installation-03.png)

SpliceKit will "patch" Final Cut Pro:

![](/static/installation-04.png)

You will be prompted with:

![](/static/installation-05.png)

Click **Allow**.

SpliceKit has now "patched" Final Cut Pro and it's ready to go!

Click **Launch FCP** to launch the "patched" Final Cut Pro:

![](/static/installation-06.png)

---

## Sections

Sections bar for timeline song structure, add default transition to all clips command, fuzzy search stop-word handling.

https://www.youtube.com/watch?v=plirvqHe6o0

---

## Transcript Editor — Text-Based Video Editing

[![Transcript Editor Demo](https://img.youtube.com/vi/JxxDSH4Ly0I/maxresdefault.jpg)](https://www.youtube.com/watch?v=JxxDSH4Ly0I)

> Click a word to jump the playhead. Select words and press Delete to remove video segments. Drag words to reorder clips. All changes apply directly to the FCP timeline.

Powered by **NVIDIA Parakeet TDT 0.6B** (on-device via FluidAudio) with v3 multilingual (25 languages) as the default engine and v2 English-optimized as an option. Speaker diarization identifies who's speaking. All clips are transcribed in a single batch process for speed.

---

## Command Palette — Apple Intelligence for Final Cut Pro

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

---

## Controlling SpliceKit Externally

### Python Client (Interactive REPL)

```bash
python3 Scripts/splicekit_client.py
```

```
splicekit> version
splicekit> classes FFAnchored
splicekit> methods FFPlayer
splicekit> props FFAnchoredSequence
splicekit> super FFAnchoredSequence
splicekit> ivars FFLibrary
```

### Direct TCP

```bash
echo '{"jsonrpc":"2.0","method":"system.version","id":1}' | nc 127.0.0.1 9876
```

### MCP Server

First, create a Python virtual environment for the MCP server and install the `mcp` package:

```bash
python3 -m venv ~/.venvs/splicekit-mcp
~/.venvs/splicekit-mcp/bin/python -m pip install --upgrade pip mcp
```

Use the virtual environment's Python as the MCP `command`.

Point MCP at the server script inside the installed SpliceKit app bundle:

```json
{
  "mcpServers": {
    "splicekit": {
      "command": "/Users/yourname/.venvs/splicekit-mcp/bin/python",
      "args": ["/Applications/SpliceKit.app/Contents/Resources/mcp/server.py"]
    }
  }
}
```

The MCP server connects to the SpliceKit bridge running inside Final Cut Pro on `127.0.0.1:9876`, so the modded Final Cut Pro must be running.