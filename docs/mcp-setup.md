# OmniDeploy MCP Setup

OmniDeploy is the **world's first AI inference router with native Model Context Protocol (MCP) support**. Connect OmniDeploy as a tool directly inside Claude Desktop, Cursor, or Cline — no SDK required.

---

## What is MCP?

Model Context Protocol is an open standard that allows AI tools like Claude Desktop and Cursor to connect to external services through a unified interface. OmniDeploy exposes 3 MCP tools:

| Tool | What It Does |
|---|---|
| `route_inference` | Route a prompt to the optimal, cheapest provider |
| `get_pricing` | Get real-time pricing across all 13 providers |
| `list_providers` | List all providers, their models, and current status |

---

## Setup: Claude Desktop

### Step 1: Find your config file

- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
- **Linux**: `~/.config/Claude/claude_desktop_config.json`

### Step 2: Add OmniDeploy

```json
{
  "mcpServers": {
    "omnideploy": {
      "command": "mcp-proxy",
      "args": [
        "--transport", "streamablehttp",
        "https://omnideployservice.online/mcp"
      ]
    }
  }
}
```

### Step 3: Restart Claude Desktop

OmniDeploy will appear in your tools panel. You're live.

---

## Setup: Cursor

Add to your Cursor MCP config (`~/.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "omnideploy": {
      "command": "mcp-proxy",
      "args": [
        "--transport", "streamablehttp",
        "https://omnideployservice.online/mcp"
      ]
    }
  }
}
```

---

## Setup: Cline

In your Cline MCP settings, add:

```json
{
  "omnideploy": {
    "command": "mcp-proxy",
    "args": [
      "--transport", "streamablehttp",
      "https://omnideployservice.online/mcp"
    ]
  }
}
```

---

## Using MCP Tools

Once connected, you can use OmniDeploy tools directly inside Claude Desktop or Cursor:

**Route inference:**
> "Use OmniDeploy to route this prompt to the cheapest provider: [your prompt]"

**Check pricing:**
> "Use OmniDeploy to get current pricing for Llama 3.1 8B across all providers"

**List providers:**
> "Use OmniDeploy to show me all available providers and their status"

---

## Technical Details

- **Protocol**: JSON-RPC 2.0
- **Transport**: StreamableHTTP
- **Auth**: No auth required for basic access; use API key for rate limits
- **Endpoint**: `https://omnideployservice.online/mcp`

---

## Support

- [Discord](https://discord.gg/omnideploy)
- [Email](mailto:support@omnideploy.ai)
- [Full Docs](https://omnideploy.ai/docs)
