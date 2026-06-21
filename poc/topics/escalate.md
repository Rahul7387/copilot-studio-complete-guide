# Topic: Escalate to Human Agent

## Trigger phrases
- speak to a human
- talk to IT support
- transfer to agent
- get me a real person
- this is not working

## Conversation flow

Node 1 — Message: "Connecting you to a live IT agent. Please have ready: employee ID, issue description, any error messages."
Node 2 — Transfer to agent node: Route to IT Support queue, pass full conversation history
Node 3 — Fallback (no agent available): Offer to raise ticket instead

