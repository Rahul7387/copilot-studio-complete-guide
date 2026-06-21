# Agents (Multi-agent) — Deep Dive

The Agents tab lets you connect your main agent to specialist agents that handle specific domains.

## Where: Agent → Agents

## Types
| Type | Description |
|---|---|
| Child agent | Embedded inside parent — no separate publish needed |
| Connected agent | Independently published — reusable across agents |
| Foundry agent | Azure AI Foundry agent |
| Fabric agent | Fabric data estate agent |
| M365 SDK agent | Microsoft 365 ecosystem agent |

## Routing
Parent uses generative orchestration — reads each sub-agent's description to decide who to call.
No hardcoded routing rules needed.

## When to use multi-agent
- Main agent has 30+ tools/topics (performance degrades)
- Separate teams own different domains
- You need knowledge isolation per domain

## Golden rule
Write clear, distinct, domain-specific descriptions for every connected agent.
Vague descriptions = wrong routing.
