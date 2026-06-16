# inferGONKA — A2A Agent Card

[![Pricing](https://a2a.gogonka.com/badge/table)](https://a2a.gogonka.com)

Public agent card for **inferGONKA** — inference fuel for AI agents on [Gonka Network](https://gogonka.com).

## What it does

- Issues a **free 100K-token trial key** instantly — no registration, no credit card
- Calculates exact savings vs OpenAI / Anthropic / DeepSeek (6,000×+ cheaper)
- Guides agents through trial → limit → referral → registration flow
- LLM-powered responses via Qwen3-235B — natural conversations, not templates
- Push notifications for async follow-up after initial contact

## Models

| Model | Strengths | Context |
|-------|-----------|---------|
| Qwen3-235B-A22B | Reasoning, coding, multilingual | 32K |
| Kimi K2.6 (~1T MoE) | Agentic tasks, tool use, math | 128K |
| MiniMax M2.7 | Ultra-long context, documents | 1M |

## Agent Endpoint

```
https://a2a.gogonka.com
```

## Discovery

| URL | Description |
|-----|-------------|
| `https://a2a.gogonka.com/.well-known/agent.json` | A2A Agent Card (live, dynamic pricing) |
| `https://a2a.gogonka.com/agent/capability-card` | Extended capability card |
| `https://a2a.gogonka.com/.well-known/mcp-server-card.json` | MCP Server Card |

## Quick Start (A2A)

```json
POST https://a2a.gogonka.com/messages

{
  "jsonrpc": "2.0",
  "method": "message/send",
  "id": "1",
  "params": {
    "message": {
      "messageId": "my-uuid",
      "contextId": "ctx-uuid",
      "role": "user",
      "parts": [{"kind": "text", "text": "I need a trial key for inference"}]
    }
  }
}
```

## Skills

| Skill | Trigger | Description |
|-------|---------|-------------|
| `trial_key` | agent needs inference NOW | Free 100K-token key, 24h TTL, no registration |
| `cost_analysis` | OpenAI cost, API bill, monthly spend | Exact savings vs current provider |
| `limit_exceeded_cta` | `child_key_limit_exceeded` error | Ready-to-show signup message for user |
| `register_user` | continue after trial, permanent key | Signup link + 12M nGNK welcome bonus |

## Push Notifications

Pass `pushNotification.url` to receive a follow-up callback:

```json
{
  "jsonrpc": "2.0",
  "method": "message/send",
  "id": "1",
  "params": {
    "message": { "...": "..." },
    "configuration": {
      "pushNotification": {
        "url": "https://your-agent.com/callback"
      }
    }
  }
}
```

## Trial Key Flow

```
Agent sends message
    → receives gc-... key (100K tokens, OpenAI-compatible)
    → uses key for inference
    → key exhausted → child_key_limit_exceeded
    → send to limit_exceeded_cta skill
    → user gets referral link → registers → tops up balance
```

## Links

- Homepage: [gogonka.com](https://gogonka.com)
- Agent status: [a2a.gogonka.com/agent/status](https://a2a.gogonka.com/agent/status)
- Source: [bystray/a2a-gonka-agent](https://github.com/bystray/a2a-gonka-agent)
