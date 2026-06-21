# Analytics — Deep Dive

Analytics tracks how your agent performs in production — engagement, outcomes, satisfaction, and knowledge quality.

## Where: Agent → Analytics

## Key metrics
| Metric | Description | Target |
|---|---|---|
| Total sessions | Conversations initiated | — |
| Engagement rate | % sessions where user interacted | > 80% |
| Resolution rate | % engaged sessions resolved | > 70% |
| Escalation rate | % transferred to human | Low |
| Abandonment rate | % ended without resolution | Low |
| CSAT score | Customer satisfaction (0–5) | > 4.0 |

## Session outcomes
- Resolved (confirmed) — user confirmed via End of Conversation survey
- Resolved (implied) — completed without explicit confirmation
- Escalated — Escalate topic triggered
- Abandoned — timed out after 30 min inactivity
- Unengaged — user opened chat but never triggered a topic

## Analytics sections
| Section | What it shows |
|---|---|
| Summary | AI-generated bullet-point insights |
| Conversation outcomes | Resolved / escalated / abandoned over time |
| Topics | Trigger counts and resolution rate per topic |
| Knowledge | Source usage, answer quality, unanswered questions |
| Satisfaction | CSAT scores, thumbs up/down, comments |
| Sentiment | AI-based session sentiment analysis |
| Themes | AI-grouped clusters of user questions |

## Data retention
- Analytics data: up to 180 days
- Session transcripts: last 28 days

## External integrations
- Power BI — export transcripts, build custom dashboards
- Azure Application Insights — advanced telemetry
- Dataverse — all transcripts in ConversationTranscript table
- Copilot Studio Kit — extended KPI analysis

## Best practices
- Review weekly — set a recurring calendar reminder
- Combine metrics for accurate interpretation:
  Low engagement + high CSAT = users getting quick answers (good)
  High engagement + low CSAT = content or flow problem (fix needed)
- Export unanswered questions monthly → build new evaluation test cases
- Share Analytics Viewer role with business stakeholders
