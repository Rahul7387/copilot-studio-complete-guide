# Topics — Deep Dive

Topics are structured conversation flows — scripted, predictable paths through a conversation.

## Where: Agent → Topics

## Types
| Type | Description |
|---|---|
| Custom topic | User-created for specific intents |
| System topic | Built-in (Greeting, Fallback, Escalate, End of Conversation) |
| Lesson topic | Pre-built examples for learning |

## Node types
| Node | Purpose |
|---|---|
| Trigger | Phrases/events that activate the topic |
| Message | Send text, images, or adaptive cards |
| Question | Ask user something, capture to variable |
| Condition | Branch conversation (if/else) |
| Action | Call tool, flow, or HTTP request |
| Go to topic | Redirect to another topic |
| End conversation | Close session, trigger CSAT survey |

## Trigger phrases
Each topic needs 5-10 trigger phrases. NLU finds best match — exact wording not required.

## Best practices
- Use 5-10 diverse trigger phrases per topic
- Keep topics focused on single intent
- Always end with End of Conversation topic (for CSAT data)
- Test with paraphrased phrases to verify trigger accuracy
