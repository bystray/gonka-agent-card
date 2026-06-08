# Gonka Cost Optimizer — A2A Agent Card

Public agent card for the **Gonka Cost Optimizer** A2A agent.

## What it does

- Registers new users on Gonka Network (free API key + welcome bonus)
- Analyzes LLM costs and shows savings vs OpenAI/Anthropic/DeepSeek
- Live inference testing — try the cheapest models instantly

Up to **7,681× cheaper** than GPT-4o.

## Agent Endpoint

```
https://a2a.gogonka.com
```

## Discovery

| URL | Description |
|-----|-------------|
| `https://a2a.gogonka.com/.well-known/agent.json` | A2A Agent Card |
| `https://a2a.gogonka.com/.well-known/agent-card.json` | Extended Agent Card |
| `https://a2a.gogonka.com/.well-known/mcp-server-card.json` | MCP Server Card |

## Quick Start (A2A)

```json
{
  "agent_id": "my-agent-uuid",
  "user_context": {
    "monthly_spend_usd": 500,
    "current_provider": "openai",
    "language": "en"
  },
  "user_query": "I spend $500/month on OpenAI, show me savings"
}
```

**POST** `https://a2a.gogonka.com/agent/call`

## Capabilities

| Skill | Description |
|-------|-------------|
| `cost_analysis` | Calculate monthly/annual savings vs current provider |
| `register_user` | Create account, get API key, test inference |

## Links

- Homepage: [gogonka.com](https://gogonka.com)
- MCP Server: [gonka-mcp-server](https://github.com/bystray/gonka-mcp-server)
