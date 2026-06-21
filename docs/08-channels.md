# Channels — Deep Dive

Channels are where you deploy your agent so users can interact with it.

## Where: Agent → Channels

## Supported channels
| Channel | Audience | Notes |
|---|---|---|
| Microsoft Teams | Internal employees | SSO; publish to Teams app store |
| SharePoint | Intranet users | One-click; permissions inherited |
| Microsoft 365 Copilot | M365 users | Native M365 extension |
| Demo website | Demos | Quick shareable link |
| Custom website | Public/internal web | Embed via iframe or Direct Line SDK |
| WhatsApp | Global customers | Requires WhatsApp Business Account |
| Facebook | Social media | Requires Facebook App |
| Telephony / Voice | Call centers | Real-time NLU + IVR |
| Azure Bot Service | Custom channels | Slack, Telegram, Line, and more |

## Authentication options
- No auth — public bots
- Azure AD (Entra ID) — SSO for internal users
- Custom OAuth — any OAuth 2.0 provider
- Manual auth — user provides credentials in chat

## Teams deployment
1. Agent → Channels → Teams → Turn on
2. Customize manifest (name, icon, description)
3. Submit for admin approval or install directly
4. Optionally pin in Teams sidebar

## Best practices
- Choose channels where users already work
- Use SSO for internal agents to avoid login friction
- Test each channel separately — adaptive cards not supported everywhere
- Use demo website for stakeholder demos before full deployment
