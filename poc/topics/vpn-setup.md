# Topic: VPN Setup

## Trigger phrases
- connect to VPN
- VPN not working
- remote access
- GlobalProtect
- cannot connect from home

## Conversation flow

Node 1 — Question: "Which device are you on?"
Options: Windows / Mac / Mobile
Save to: varDevice

Node 2 — Condition (branch by varDevice):

Windows: "1. Download: itportal.contoso.com/vpn  2. Server: vpn.contoso.com  3. Sign in + MFA"
Mac: "1. Download: itportal.contoso.com/vpn-mac  2. Allow extension  3. Server: vpn.contoso.com + MFA"
Mobile: "1. Download GlobalProtect app  2. Portal: vpn.contoso.com  3. Sign in + MFA"

Node 3 — Question: "Does VPN connect now?"
Node 4 — Yes → End of Conversation / No → Raise IT Ticket

## Variables
- varDevice (string)
