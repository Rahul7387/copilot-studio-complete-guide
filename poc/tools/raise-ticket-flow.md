# Tool: Raise IT Support Ticket (Power Automate)

## Create in Power Automate

1. Power Automate → Create → Instant cloud flow
2. Name: Raise IT Support Ticket
3. Trigger: When Copilot Studio calls a flow

## Inputs

| Name | Type | Description |
|---|---|---|
| issueDescription | String | User's issue description |
| urgency | String | Low / Medium / High |
| employeeEmail | String | Employee's work email |

## Flow steps

Step 1 — ServiceNow: Create Record
Table: Incident | Map: Short description → issueDescription, Urgency → urgency

Step 2 — Return ticketNumber (e.g. INC0012345)

## Connect to Copilot Studio
Agent → Tools → Add a tool → Agent flow → Select this flow

Tool description:
"Creates a new IT support ticket in ServiceNow when an employee reports an issue that cannot be resolved through self-service steps."

## Alternative (no ServiceNow)
Replace with: Dataverse table / SharePoint list / Email to helpdesk
