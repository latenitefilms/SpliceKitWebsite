# MCP Server

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

---

## Python Client

There's also an Interactive REPL:

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

---

## Direct TCP

You can also connect via Direct TCP:

```bash
echo '{"jsonrpc":"2.0","method":"system.version","id":1}' | nc 127.0.0.1 9876
```