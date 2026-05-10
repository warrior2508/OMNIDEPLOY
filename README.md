<div align="center">

### 🌍 World's First AI Inference Router with Native MCP Support

<img src="https://omnideploy.ai/logo.png" alt="OmniDeploy" width="120" />

# OmniDeploy

**The inference router built for agents.**

Drop-in for the Anthropic and OpenAI SDKs. Routes every call across 13 providers to the cheapest one meeting your latency policy. The world's first AI inference router with native MCP support.

[![Status](https://img.shields.io/badge/Status-Live%20in%20Production-brightgreen)](https://omnideploy.ai)
[![MCP Native](https://img.shields.io/badge/MCP-Native-00FF94)](https://omnideploy.ai/mcp-setup)
[![Providers](https://img.shields.io/badge/Providers-13-blue)](https://omnideploy.ai)
[![INR Billing](https://img.shields.io/badge/Billing-INR%20via%20Razorpay-blue)](https://omnideploy.ai/signup)
[![License](https://img.shields.io/badge/License-Proprietary-orange)](LICENSE)

[Website](https://omnideploy.ai) • [Docs](https://omnideploy.ai/docs) • [MCP Setup](https://omnideploy.ai/mcp-setup) • [Pricing](https://omnideploy.ai/#pricing) • [Discord](https://discord.gg/omnideploy)

</div>

---

## What is OmniDeploy?

OmniDeploy is an **agent-native AI inference router** — the first with native [Model Context Protocol (MCP)](https://modelcontextprotocol.io) support. One URL change in your existing Anthropic or OpenAI SDK, and every inference call automatically routes to the cheapest provider across 13 options.

No new SDK to learn. No lock-in. Just cheaper, faster AI.

```python
# Before OmniDeploy
from anthropic import Anthropic
client = Anthropic(api_key="your-anthropic-key")

# After OmniDeploy — one line change, 40-60% cheaper
from anthropic import Anthropic
client = Anthropic(
    api_key="omni_live_...",
    base_url="https://omnideployservice.online",
)

# Everything else stays exactly the same
resp = client.messages.create(
    model="llama-3.1-b-instant",
    max_tokens=200,
    messages=[{"role": "user", "content": "Hello"}],
)
# 200 OK · routed → groq · 290ms · $0.000038
```

---

## Why OmniDeploy?

| Problem | Without OmniDeploy | With OmniDeploy |
|---|---|---|
| API costs | Paying OpenAI rates for everything | Auto-routed to cheapest provider per call |
| Multi-provider setup | Separate SDKs, keys, logic | Single unified API |
| Agent tooling | No native MCP | First router with native MCP |
| India billing | USD only, no GST | INR via Razorpay, GST compliant |
| Provider lock-in | Locked to one provider | Switch anytime, zero friction |
| Setup time | Hours of configuration | 30 seconds, email only |

---

## Features

### ⚡ Drop-In SDK Compatibility
Change one line. Works with the Anthropic Messages API and OpenAI Chat Completions. No migration. No refactoring. Zero switching cost.

### 🔀 Intelligent Inference Routing
Routes across **13 providers** — Groq, Together, Fireworks, Cerebras, Anthropic, OpenAI, SambaNova, DeepInfra, Mistral, Cohere, Perplexity, AI21, HuggingFace — to whichever is cheapest for your latency policy.

### 🤖 MCP Native (World First)
OmniDeploy is the **first inference router with native Model Context Protocol support**. Connect directly inside Claude Desktop, Cursor, or Cline without any SDK.

3 MCP tools available:
- `route_inference` — route a prompt to the optimal provider
- `get_pricing` — get real-time pricing across providers
- `list_providers` — list all active providers and status

### 🔑 Programmatic Agent Provisioning
Spin up API keys programmatically. No signup, no password, 30 seconds.

```bash
curl -X POST omnideployservice.online/v1/agents/provision \
     -d '{"email":"you@startup.com"}'

# { "api_key": "omni_live_…", "base_url": "https://omnideployservice.online" }
```

### 💰 Cost Optimization — Live Calculator
Companies save an average of **$50,000/year** by switching. Some save over **$500,000/year**.

- Real-time cost comparison across all 13 providers
- Automatic routing to cheapest option meeting your SLA
- No markup on pass-through costs (BYOC tier)

### 🇮🇳 INR Billing — India First
Pay in Indian Rupees. Razorpay integration live. Supports UPI, Cards, NetBanking, and Wallets. **GST compliant** — the only AI inference platform built for Indian teams.

### 📊 Real-Time Dashboard
- Live cost & latency monitoring
- Usage analytics per model and provider
- Team members, roles, and audit log
- Request breakdown by provider

### 🔧 BYOC — Bring Your Own Cloud
Connect your own cloud credentials. Get **30% higher credit limits**, zero usage markup, and priority support. Your data stays in your infrastructure.

### 🔒 Enterprise Security
- SOC 2 Type II
- GDPR compliant
- ISO 27001
- EU AI Act ready
- End-to-end encryption
- Role-based access control
- Full audit logs

---

## Getting Started

### Option 1 — Sign Up (Recommended for Teams)

Full dashboard, usage analytics, INR billing.

[→ Sign up free at omnideploy.ai](https://omnideploy.ai/signup)

### Option 2 — Connect via MCP (For Agent Builders)

Add OmniDeploy as a tool inside Claude Desktop or Cursor in 60 seconds.

```json
// claude_desktop_config.json
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

[→ Full MCP setup guide](https://omnideploy.ai/mcp-setup)

### Option 3 — Instant API Key (For Developers in a Hurry)

Email only. No password, no card, 30 seconds.

```bash
curl -X POST omnideployservice.online/v1/agents/provision \
     -d '{"email":"you@startup.com"}'
```

Then use with Anthropic SDK:

```python
from anthropic import Anthropic

client = Anthropic(
    api_key="omni_live_...",         # key from provisioning
    base_url="https://omnideployservice.online",
)
```

Or with OpenAI SDK:

```python
from openai import OpenAI

client = OpenAI(
    api_key="omni_live_...",
    base_url="https://omnideployservice.online/v1",
)
```

---

## Supported Providers

| Provider | Status |
|---|---|
| Groq | ✅ Live |
| Together AI | ✅ Live |
| Fireworks AI | ✅ Live |
| Cerebras | ✅ Live |
| Anthropic | ✅ Live |
| OpenAI | ✅ Live |
| SambaNova | ✅ Live |
| DeepInfra | ✅ Live |
| Mistral | ✅ Live |
| Cohere | ✅ Live |
| Perplexity | ✅ Live |
| AI21 | ✅ Live |
| HuggingFace | ✅ Live |

---

## Pricing

| Plan | Price | Credits | Best For |
|---|---|---|---|
| **Free** | ₹0/month | 1,000 credits | Testing & hobby projects |
| **Pro** | ₹2,499/month (~$30) | 5,000 credits + grace | Growing teams |
| **Enterprise** | ₹9,999/month (~$120) | 50,000 credits base | Large organizations |

**BYOC users get:** 30% higher limits · No usage markup · Priority support

**Smart billing:**
- Free → Hard limit (stops at 1,000 credits)
- Pro → Soft limit + grace period (alerts before throttling)
- Enterprise → Metered invoice (₹0.80/credit overage)

Payment via Razorpay — UPI · Cards · NetBanking · Wallets

[→ View full pricing & FAQ](https://omnideploy.ai/#pricing)

---

## Platform

| Feature | Description |
|---|---|
| [Genome](https://omnideploy.ai/genome) | Behavioral intelligence layer — learns from your usage patterns |
| [Terminal](https://omnideploy.ai/terminal) | CLI-first interface for power users |
| [Marketplace](https://omnideploy.ai/marketplace) | Pre-built integrations and agent templates |
| [Carbon](https://omnideploy.ai/carbon) | Carbon-aware routing for sustainable AI |

---

## Roadmap

- [x] Multi-provider inference routing (13 providers)
- [x] Anthropic SDK drop-in
- [x] OpenAI SDK drop-in
- [x] Native MCP support (world first)
- [x] Programmatic agent provisioning
- [x] INR billing via Razorpay
- [x] BYOC support
- [x] Real-time cost & latency dashboard
- [x] Team roles & audit log
- [x] SOC 2 / GDPR / ISO 27001
- [ ] CLI tool (`omnideploy` command)
- [ ] GitHub Actions integration
- [ ] Model versioning & A/B testing
- [ ] Kubernetes operator
- [ ] Sovereign cloud deployments
- [ ] Volume discount API

---

## Documentation

- [Quick Start Guide](https://omnideploy.ai/docs)
- [API Reference](https://omnideploy.ai/docs/api)
- [MCP Setup](https://omnideploy.ai/mcp-setup)
- [BYOC Setup](https://omnideploy.ai/docs/byoc)
- [Pricing FAQ](https://omnideploy.ai/pricing-faq)
- [Security & Compliance](https://omnideploy.ai/security)
- [Changelog](https://omnideploy.ai/changelog)

---

## Competitive Landscape

| | OmniDeploy | OpenRouter | Portkey | LiteLLM |
|---|---|---|---|---|
| MCP Native | ✅ | ❌ | ❌ | ❌ |
| INR Billing | ✅ | ❌ | ❌ | ❌ |
| Auto cost routing | ✅ | ❌ | ❌ | ❌ |
| Behavioral intelligence | ✅ | ❌ | ❌ | ❌ |
| Anthropic SDK drop-in | ✅ | ✅ | ✅ | ✅ |
| Agent provisioning | ✅ | ❌ | ❌ | ❌ |
| Providers | 13 | 50+ | 15+ | 100+ |
| Self-hostable | ❌ | ❌ | ✅ | ✅ |

---

## Support

- **Email**: support@omnideploy.ai
- **Twitter/X**: [@omnideploy](https://twitter.com/omnideploy)
- **LinkedIn**: [linkedin.com/company/omnideploy](https://linkedin.com/company/omnideploy)
- **Discord**: [Join our community](https://discord.gg/omnideploy)

---

## About

OmniDeploy is built in India, for the world. We believe AI infrastructure should be invisible — routed, optimized, and governed automatically so builders can focus on what they're building.

**Founded**: 2024 · **Location**: Mumbai, India · **Stage**: Public Beta

> TCP/IP made the internet possible.  
> Linux made cloud computing possible.  
> OmniDeploy makes the AI economy possible.

---

<div align="center">

**Ready to cut your AI costs by 40-60%?**

[Get Started Free →](https://omnideploy.ai/signup) · [Connect via MCP →](https://omnideploy.ai/mcp-setup)

No credit card required · 1,000 free requests/month · Cancel anytime

</div>
