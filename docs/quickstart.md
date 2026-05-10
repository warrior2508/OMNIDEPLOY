# OmniDeploy — Quick Start Guide

Get from zero to routing inference in under 5 minutes.

---

## Option 1: Instant API Key (Fastest — 30 seconds)

No signup. No card. Just your email.

```bash
curl -X POST omnideployservice.online/v1/agents/provision \
     -d '{"email":"you@startup.com"}'
```

Response:
```json
{
  "api_key": "omni_live_xxxxxxxxxxxx",
  "base_url": "https://omnideployservice.online"
}
```

### Use with Anthropic SDK

```python
from anthropic import Anthropic

client = Anthropic(
    api_key="omni_live_...",
    base_url="https://omnideployservice.online",
)

response = client.messages.create(
    model="claude-3-haiku-20240307",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Hello, OmniDeploy!"}],
)

print(response.content)
# Routed to cheapest provider automatically
```

### Use with OpenAI SDK

```python
from openai import OpenAI

client = OpenAI(
    api_key="omni_live_...",
    base_url="https://omnideployservice.online/v1",
)

response = client.chat.completions.create(
    model="llama-3.1-8b-instant",
    messages=[{"role": "user", "content": "Hello, OmniDeploy!"}],
)

print(response.choices[0].message.content)
```

---

## Option 2: MCP Setup (For Claude Desktop / Cursor / Cline)

### Step 1: Get your MCP config

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

### Step 2: Add to Claude Desktop

Open `~/Library/Application Support/Claude/claude_desktop_config.json` (macOS) or `%APPDATA%\Claude\claude_desktop_config.json` (Windows) and paste the config above.

### Step 3: Restart Claude Desktop

OmniDeploy appears as a tool. You can now use:
- `route_inference` — route a prompt to the cheapest provider
- `get_pricing` — get live pricing across all 13 providers
- `list_providers` — see provider status and capabilities

---

## Option 3: Dashboard Signup (Recommended for Teams)

1. Go to [omnideploy.ai/signup](https://omnideploy.ai/signup)
2. Create your account — free, no card needed
3. Get your API key from the dashboard
4. Connect your team members and set roles
5. Monitor usage and costs in real-time

---

## Supported Models

You can use any model from any of the 13 supported providers. OmniDeploy automatically selects the cheapest provider that supports your requested model.

```python
# These all work — OmniDeploy routes to the right provider
models = [
    "claude-3-haiku-20240307",      # → Anthropic
    "gpt-4o-mini",                   # → OpenAI
    "llama-3.1-8b-instant",          # → Groq (cheapest for Llama)
    "mixtral-8x7b-instruct",         # → Together / Fireworks
    "mistral-7b-instruct",           # → Mistral / DeepInfra
]
```

---

## Environment Variables

```bash
# .env
OMNIDEPLOY_API_KEY=omni_live_xxxxxxxxxxxx
OMNIDEPLOY_BASE_URL=https://omnideployservice.online
```

```python
import os
from anthropic import Anthropic

client = Anthropic(
    api_key=os.environ["OMNIDEPLOY_API_KEY"],
    base_url=os.environ["OMNIDEPLOY_BASE_URL"],
)
```

---

## What Happens to Each Request

1. Your request hits OmniDeploy's router
2. Router checks real-time pricing across all 13 providers
3. Selects cheapest provider meeting your latency policy
4. Forwards the request, returns the response
5. Logs cost, latency, and provider to your dashboard

Average p50 latency overhead: **< 20ms**

---

## Next Steps

- [API Reference →](https://omnideploy.ai/docs/api)
- [BYOC Setup (30% more credits) →](https://omnideploy.ai/docs/byoc)
- [MCP Full Guide →](https://omnideploy.ai/mcp-setup)
- [Pricing & Credits →](https://omnideploy.ai/pricing-faq)
- [Join Discord →](https://discord.gg/omnideploy)
