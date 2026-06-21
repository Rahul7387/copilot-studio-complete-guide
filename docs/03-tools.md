# Tools — Deep Dive

Tools give agents the ability to take action — connect to APIs, trigger workflows, process text with AI.

## Where: Agent → Tools

## Types
| Tool | Description |
|---|---|
| Power Automate flow | Multi-step automation across 1,400+ connectors |
| Connector | Direct connection to popular SaaS platforms |
| Prompt | Single AI call for classification, summarization, extraction |
| Custom connector | Any REST API via OpenAPI spec |
| MCP server | Model Context Protocol — standardized tool interface |

## How routing works
The AI reads each tool's name and description to decide when to call it.
It automatically extracts inputs from conversation context.

## Best practices
- Write specific tool descriptions — the AI uses them for routing
- Set input validation and retry logic
- Test tools independently before connecting to the agent
- Apply least-privilege access — tools only access what they need
