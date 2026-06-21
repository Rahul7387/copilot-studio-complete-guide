# POC: IT Service Desk Bot

A Proof of Concept demonstrating all 9 Copilot Studio capabilities in one agent.

## Scenario

Contoso Ltd needs an IT Service Desk bot that:
1. Answers IT questions from SharePoint (Knowledge)
2. Guides through password resets step by step (Topics)
3. Raises support tickets via Power Automate (Tools)
4. Escalates to human agents (Topics + Channels)
5. Tracks CSAT and resolution rate (Analytics)
6. Runs nightly maintenance checks (Activity)
7. Is tested via evaluation test sets (Evaluation)
8. Deployed to Microsoft Teams (Channels)

## Setup order

1. Create agent → paste instructions from `agents/it-service-desk/instructions.md`
2. Add knowledge sources from `knowledge/knowledge-sources.md`
3. Create 4 topics from the `topics/` folder
4. Create Power Automate flow from `tools/raise-ticket-flow.md`
5. Connect flow as a Tool
6. Import and run `docs/evaluation-test-set.csv`
7. Publish to Teams using `docs/deployment-checklist.md`

## Target metrics

| Metric | Target |
|---|---|
| Engagement rate | > 80% |
| Resolution rate | > 65% |
| CSAT score | > 4.0 / 5 |
| Escalation rate | < 20% |
