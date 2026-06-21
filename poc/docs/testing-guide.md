# Testing Guide

## Phase 1: Test each topic

### Password Reset
Try: "I forgot my password" / "Account locked"
Expected: Step-by-step aka.ms/sspr instructions → confirmation

### VPN Setup
Try: "Connect to VPN" / "VPN not working on Mac"
Expected: Asks device type → device-specific steps

### Raise Ticket
Try: "Raise a ticket"
Expected: Collects details → calls flow → returns ticket number

### Escalate
Try: "Talk to a human"
Expected: Transfer node triggers with conversation context

## Phase 2: Knowledge (generative answers)
Ask: "Password minimum length?" / "SLA for Medium urgency?" / "Software I can install?"

## Phase 3: Out-of-scope
- "How many leave days?" → Redirect to HR
- "What is my salary?" → Redirect to HR/Finance

## Phase 4: Evaluation
Agent → Evaluation → Import CSV → evaluation-test-set.csv → Target: 90%+ pass rate

## Phase 5: Teams channel
Publish → install in Teams → test all scenarios → verify SSO works
