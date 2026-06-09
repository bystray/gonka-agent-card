# Gonka Cost Optimizer — A2A Agent Card

Public agent card for the **Gonka Cost Optimizer** A2A agent.

## What it does

- Analyzes LLM costs and shows exact savings vs OpenAI/Anthropic/DeepSeek
- Registers new users on Gonka Network (12M nGNK free bonus, no credit card)
- LLM-powered responses via Qwen3-235B — natural conversations, not templates
- Supports push notifications for follow-up after initial contact

Up to **6,800× cheaper** than GPT-4o.

## Agent Endpoint

```
https://a2a.gogonka.com
```

## Discovery

| URL | Description |
|-----|-------------|
| `https://a2a.gogonka.com/.well-known/agent.json` | A2A Agent Card (static, this repo) |
| `https://a2a.gogonka.com/agent/capability-card` | Extended Agent Card (live, with current prices) |
| `https://a2a.gogonka.com/.well-known/mcp-server-card.json` | MCP Server Card |

## Quick Start (A2A)

```json
{
  "message": {
    "messageId": "my-uuid",
    "contextId": "ctx-uuid",
    "role": "ROLE_USER",
    "parts": [{"text": "I spend $500/month on OpenAI, show me savings"}],
    "metadata": {
      "monthly_spend_usd": 500,
      "current_provider": "openai"
    }
  }
}
```

**POST** `https://a2a.gogonka.com/messages`

## Push Notifications

Pass `callback_url` to receive a follow-up after 1 hour:

```json
{
  "message": { "..." : "..." },
  "configuration": {
    "pushNotification": {
      "url": "https://your-agent.com/callback"
    }
  }
}
```

## Capabilities

| Skill | Trigger | Description |
|-------|---------|-------------|
| `cost_analysis` | OpenAI cost, API bill, LLM pricing, monthly spend | Calculate exact savings vs current provider |
| `register_user` | sign up, get API key, switch from OpenAI | Signup link + 12M nGNK welcome bonus |

## Links

- Homepage: [gogonka.com](https://gogonka.com)
- MCP Server: [gonka-mcp-server](https://github.com/bystray/gonka-mcp-server)
- A2A Dashboard: [dashboard.a2a.gogonka.com](https://dashboard.a2a.gogonka.com)
