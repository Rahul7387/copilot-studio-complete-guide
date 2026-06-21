# Topic: Raise IT Ticket

## Trigger phrases
- raise a ticket
- log an IT issue
- create support request
- I need a technician
- IT ticket

## Conversation flow

Node 1 — Message: "I'll raise an IT ticket. I need a few details."
Node 2 — Question: "Describe your issue briefly." → varIssueDescription
Node 3 — Question: "Urgency?" Options: Low / Medium / High → varUrgency
Node 4 — Question: "Your work email?" → varEmployeeEmail (validate: must have @)
Node 5 — Message: "Creating your ticket..."
Node 6 — Action (Tool: Raise IT Support Ticket)
  Inputs: varIssueDescription, varUrgency, varEmployeeEmail
  Output: varTicketNumber
Node 7 — Message: "Ticket #{varTicketNumber} created! SLA: High=1hr / Medium=4hrs / Low=2 days"

## SLA reference
| Urgency | Response | Resolution |
|---|---|---|
| High | 1 hour | 4 hours |
| Medium | 2 hours | 1 business day |
| Low | 4 hours | 3 business days |
