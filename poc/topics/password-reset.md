# Topic: Password Reset

## Trigger phrases
- forgot my password
- reset password
- account is locked
- cannot log in
- password expired

## Conversation flow

Node 1 — Message:
"I can help you reset your password. Follow these steps:"

Node 2 — Message (numbered steps):
"1. Open: aka.ms/sspr
2. Enter your work email address
3. Choose verification method (phone / email / authenticator)
4. Complete the verification
5. Set new password (minimum 12 characters)"

Node 3 — Question: "Were you able to reset your password?"
Save to: varPasswordResetSuccess (Boolean)

Node 4 — Condition:
- Yes → success message → End of Conversation
- No → "I'll raise a ticket for you." → Raise IT Ticket topic

## Variables
- varPasswordResetSuccess (Boolean)
