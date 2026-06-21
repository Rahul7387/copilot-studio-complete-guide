# Instructions — Deep Dive

Instructions are the system-level prompt defining your agent's identity, behavior, tone, and rules.
They are read before every user message. Think of them as the agent's job description.

## Where: Agent → Overview → Instructions

## What to include
- The agent's role and purpose
- Tone and style (formal, friendly, concise)
- What the agent SHOULD and SHOULD NOT do
- How to handle ambiguous queries
- Escalation rules
- Domain limits

## Best practices
- Be specific — vague instructions = inconsistent behavior
- Explicitly list what the agent should NOT do
- Test instruction changes in the test panel before publishing
- Update instructions when the agent's scope changes

## Common mistakes
- Instructions too short ("Be a helpful assistant") — not specific enough
- No boundary rules — agent answers everything, including out-of-scope queries
- Conflicting instructions — agent gets confused and behaves unpredictably
