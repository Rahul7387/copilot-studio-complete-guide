# Activity — Deep Dive

The Activity tab shows execution history of autonomous agent runs — background tasks and triggered workflows.

## Where: Agent → Activity

## What it shows
| Column | Description |
|---|---|
| Run history | All autonomous trigger executions with status |
| Run details | Step-by-step trace — inputs, tool calls, outputs |
| Knowledge source usage | What content was referenced per run |
| Status | Success / Failed / Running |
| Duration | How long each run took |
| Trigger | What caused the run |

## Trigger types
- Dataverse: new/updated row
- Scheduled: hourly, daily, weekly
- Power Automate trigger
- HTTP / API trigger
- Microsoft 365 events (new email, calendar event)

## Debugging with Activity
1. Open failed run
2. Review step-by-step trace — find failure point
3. Check tool call inputs/outputs
4. Check knowledge source references
5. Fix → re-test → verify next run succeeds

## Best practices
- Set email alerts for failed runs via Power Automate
- Review Activity weekly for autonomous agents in production
