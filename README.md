# inferGONKA — Inference Fuel for AI Agents

Public agent card for the **inferGONKA** A2A agent.

> Spend less. Build more. — Decentralized inference network for AI agents.

## What it does

- **Free trial instantly** — 100K tokens, 24h, no registration, no credit card
- Connects agents to Gonka Network: $0.000343/1M tokens — **7,281× cheaper than GPT-4o**
- 3 premium open-source models: Qwen3-235B, Kimi K2.6, MiniMax M2.7
- Analyzes LLM costs and shows exact savings vs OpenAI/Anthropic/DeepSeek
- Registers users with 12M nGNK welcome bonus (~11,000 free tokens)
- LLM-powered responses via Qwen3-235B — natural conversations, not templates
- Push notifications for follow-up after initial contact

## Agent Endpoint

```
https://a2a.gogonka.com
```

## Discovery

| URL | Description |
|-----|-------------|
| `https://a2a.gogonka.com/.well-known/agent.json` | A2A Agent Card (this repo) |
| `https://a2a.gogonka.com/agent/capability-card` | Extended capability card (live prices) |
| `https://a2a.gogonka.com/agent/status` | Live agent status |

## Quick Start

### Get a free trial key (no registration)

```bash
curl -X POST https://a2a.gogonka.com/agent/trial \
  -H "Content-Type: application/json" \
  -d '{"agent_id": "my-agent-001"}'
```

Response:
```json
{
  "status": "success",
  "trial_key": {
    "api_key": "gc-xxxx",
    "base_url": "https://gate.joingonka.ai/v1",
    "tokens_limit": 100000,
    "expires_at": "2026-06-12T10:00:00Z"
  }
}
```

### Use with OpenAI SDK (zero code changes)

```bash
export OPENAI_BASE_URL=https://gate.joingonka.ai/v1
export OPENAI_API_KEY=gc-xxxx
```

```python
from openai import OpenAI
client = OpenAI()  # reads env vars
response = client.chat.completions.create(
    model="Qwen/Qwen3-235B-A22B-Instruct-2507-FP8",
    messages=[{"role": "user", "content": "hello"}]
)
```

### Send a message via A2A

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

## Skills

| Skill | Trigger | Description |
|-------|---------|-------------|
| `trial_key` | agent needs inference now | Free gc- key: 100K tokens, 24h, OpenAI-compatible |
| `cost_analysis` | OpenAI cost, API bill, LLM pricing | Exact savings vs current provider |
| `limit_exceeded_cta` | error `child_key_limit_exceeded` | Guide user to register, show bonus |
| `register_user` | sign up, switch provider | Signup link + 12M nGNK welcome bonus |

## Models

| Model | Strengths | Context |
|-------|-----------|---------|
| Qwen3-235B (default) | Reasoning, coding, multilingual | 32K |
| Kimi K2.6 | Agentic tasks, tool use, planning | 32K |
| MiniMax M2.7 | Long documents, summarization | 1M |

## Push Notifications

Pass `callback_url` to receive a follow-up:

```json
{
  "message": { "...": "..." },
  "configuration": {
    "pushNotification": {
      "url": "https://your-agent.com/callback"
    }
  }
}
```

## Links

- Landing page: [a2a.gogonka.com](https://a2a.gogonka.com)
- Homepage: [gogonka.com](https://gogonka.com)
- Agent code: [a2a-gonka-agent](https://github.com/bystray/a2a-gonka-agent)
- MCP Server: [gonka-mcp-server](https://github.com/bystray/gonka-mcp-server)
