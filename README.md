# 🤖 Microsoft Copilot Studio — Complete Reference Guide

[![Microsoft Copilot Studio](https://img.shields.io/badge/Microsoft-Copilot%20Studio-0078D4?style=flat&logo=microsoft)](https://copilotstudio.microsoft.com)
[![Power Platform](https://img.shields.io/badge/Power-Platform-742774?style=flat&logo=microsoft)](https://powerplatform.microsoft.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A comprehensive reference guide covering every core concept in Microsoft Copilot Studio — Instructions, Knowledge, Tools, Agents, Topics, Activity, Evaluation, Channels, and Analytics — plus a fully working POC: the **IT Service Desk Bot**.

---

## 📋 Table of Contents

- [What is Copilot Studio?](#-what-is-copilot-studio)
- [Core Concepts](#-core-concepts)
  - [1. Instructions](#1-instructions)
  - [2. Knowledge](#2-knowledge)
  - [3. Tools](#3-tools)
  - [4. Agents](#4-agents)
  - [5. Topics](#5-topics)
  - [6. Activity](#6-activity)
  - [7. Evaluation](#7-evaluation)
  - [8. Channels](#8-channels)
  - [9. Analytics](#9-analytics)
- [POC: IT Service Desk Bot](#-poc-it-service-desk-bot)
- [Folder Structure](#-folder-structure)
- [Contributing](#-contributing)

---

## 🌟 What is Copilot Studio?

Microsoft Copilot Studio is a low-code platform for building AI-powered conversational agents. It coordinates language models with instructions, knowledge sources, topics, tools, and triggers to accomplish business goals — without requiring deep coding expertise.

An agent built in Copilot Studio can:
- Understand natural language and respond conversationally
- Answer questions from connected knowledge sources (SharePoint, websites, files)
- Take action via tools (Power Automate flows, APIs, connectors)
- Route complex queries to specialist agents
- Publish across multiple channels (Teams, web, WhatsApp, voice)
- Be monitored and improved via built-in analytics and evaluations

---

## 🧩 Core Concepts

---

### 1. Instructions

**What they are:**
Instructions are the system-level prompt that defines your agent's identity, behavior, tone, scope, and rules. They are the first thing the AI reads before processing any user message. Think of instructions as the agent's "job description."

**Where to find them:**
`Agent → Overview tab → Instructions section`

**What to include:**
- The agent's role and purpose
- Tone and communication style (formal, friendly, concise)
- What the agent SHOULD and SHOULD NOT do
- How to handle ambiguous queries
- Escalation behavior
- Domain boundaries (e.g., "only answer IT questions")

**Example instructions:**
```
You are the IT Service Desk Bot for Contoso Ltd.

Your role is to help employees resolve common IT issues quickly and efficiently.

You help with:
- Password resets and account lockouts
- VPN setup and connectivity
- Software installation requests
- Hardware issues
- Raising IT support tickets

Tone: Professional, clear, and step-by-step. Use numbered steps for technical guidance.

Rules:
1. Never attempt to answer HR or Finance questions — refer to the relevant department.
2. For security incidents (phishing, data breach), escalate immediately and do not attempt to resolve.
3. Always confirm the resolution at the end of every interaction.
4. If you cannot resolve an issue in 3 steps, offer to raise a ticket.
```

**Best practices:**
- Be specific — vague instructions lead to inconsistent behavior
- Set clear "do not do" rules to prevent scope creep
- Update instructions when the agent's domain expands
- Test the effect of instruction changes in the test panel before publishing

---

### 2. Knowledge

**What it is:**
Knowledge sources are the information repositories your agent uses to answer user questions. Instead of manually creating a topic for every possible question, you connect the agent to existing content and the AI generates accurate, grounded responses automatically.

**Where to find it:**
`Agent → Knowledge tab`

**Supported knowledge source types:**

| Source | Description |
|---|---|
| **Public website** | Crawls and indexes any public URL |
| **SharePoint** | Connects to SharePoint sites, pages, and document libraries |
| **Files** | Upload PDFs, Word docs, Excel files, PowerPoint, text files |
| **File collection** | Group multiple related files as a single named knowledge source |
| **Dataverse** | Query structured enterprise data from Dataverse tables |
| **Azure AI Search** | Connect to an existing Azure AI Search index |
| **Bing Custom Search** | Scoped web search using a Custom Configuration ID |
| **OneNote** | Reference OneNote pages from Microsoft 365 |
| **Outlook / Teams** | Use emails and Teams messages as knowledge (Microsoft 365) |

**How it works:**
When a user asks a question, the agent searches all connected knowledge sources, retrieves the most relevant content, and generates a grounded, conversational answer — citing the source if needed.

**Generative answers vs topics:**
- Knowledge sources power **generative answers** — AI answers any question from connected content without manual topic authoring
- Topics provide **structured, scripted conversation flows** for predictable paths
- Both can work together in the same agent

**Best practices:**
- Connect authoritative, up-to-date sources — the agent is only as good as its knowledge
- Use file collections to group related documents (e.g., "IT Policies")
- Regularly review unanswered questions in Analytics to find knowledge gaps
- Add SharePoint metadata filters to improve retrieval precision
- Avoid uploading duplicate content — it confuses the retrieval model

---

### 3. Tools

**What they are:**
Tools give your agent the ability to take action — not just answer questions. A tool is any capability that connects the agent to external systems, APIs, data sources, or AI processes. Tools are how agents move from "conversational assistant" to "autonomous agent."

**Where to find them:**
`Agent → Tools tab`

**Types of tools:**

| Tool type | Description | Use when |
|---|---|---|
| **Connector** | 1,400+ prebuilt connectors (Salesforce, ServiceNow, Jira, etc.) | Connecting to popular SaaS platforms |
| **Power Automate flow** | Trigger automated multi-step workflows | Complex actions involving multiple systems |
| **Prompt** | Single-turn AI call for classification, summarization, extraction | Processing text with AI logic |
| **Custom connector** | Connect to any REST API via OpenAPI spec | Internal or niche APIs |
| **MCP server** | Model Context Protocol — standardized tool interface | Cross-platform agent integration |
| **Agent flow** | Multi-step agent-native automation | Autonomous tasks triggered by the agent |

**How tools work with generative orchestration:**
The AI reads each tool's name and description to decide when to call it. It automatically extracts required inputs from the conversation context and asks the user if any input is missing.

**Example tool: Raise IT ticket**
```
Tool name: Raise IT Support Ticket
Description: Creates a new IT support ticket in ServiceNow when an employee reports an issue that cannot be resolved through self-service.
Inputs: Issue description (string), Urgency (Low/Medium/High), Employee email (string)
Output: Ticket number (string)
```

**Best practices:**
- Write descriptive tool names and descriptions — the AI uses them for routing decisions
- Set input validation and retry logic for user-provided values
- Use "Dynamically fill with AI" for inputs the AI can infer from context
- Test tools individually before connecting them to the agent
- Apply least-privilege access — tools should only access what they need

---

### 4. Agents

**What they are:**
In Copilot Studio, "Agents" refers to the multi-agent capability — connecting your main agent to other specialist agents. This enables complex workflows to be broken into modular, focused sub-agents that collaborate to solve problems.

**Where to find it:**
`Agent → Agents tab`

**Types of agent connections:**

| Type | Description | Best for |
|---|---|---|
| **Child agent** | Lightweight sub-agent embedded inside the parent | Single team, quick modularization |
| **Connected agent** | Independently published Copilot Studio agent | Separate teams, reuse across agents |
| **Microsoft Foundry agent** | Agent built on Azure AI Foundry | Advanced AI scenarios |
| **Microsoft Fabric agent** | Agent connected to Fabric data estate | Enterprise analytics and data |
| **M365 Agents SDK agent** | Agent built with Microsoft 365 SDK | Microsoft 365 ecosystem integration |

**How orchestration works:**
The parent agent uses **generative orchestration** — it reads each connected agent's description to decide which one to delegate to. No hardcoded routing rules needed.

**When to use multi-agent:**
- Your main agent has 30+ tools, topics, or actions (performance degrades)
- Different teams own different domains independently
- You need domain-specific knowledge isolation
- You want to reuse specialist agents across multiple parent agents

**Routing rule:**
The parent agent's AI uses each sub-agent's **description** to route. Write clear, distinct, domain-specific descriptions for every agent.

---

### 5. Topics

**What they are:**
Topics are structured conversation flows — scripted, predictable paths through a conversation. They are the building blocks of classic agent behavior. A topic defines what triggers it (trigger phrases), what nodes execute (messages, questions, conditions, actions), and how it ends.

**Where to find them:**
`Agent → Topics tab`

**Types of topics:**

| Type | Description |
|---|---|
| **Custom topic** | User-created topics for specific intents (FAQs, workflows, forms) |
| **System topic** | Built-in topics (Greeting, Fallback, Escalate, End of Conversation) |
| **Lesson topic** | Pre-built example topics to learn authoring patterns |

**Node types in a topic:**

| Node | Purpose |
|---|---|
| **Trigger** | Defines phrases/events that activate the topic |
| **Message** | Sends text, images, videos, or adaptive cards to the user |
| **Question** | Asks the user something and captures the response into a variable |
| **Condition** | Branches the conversation based on variable values (if/else) |
| **Action** | Calls a tool, Power Automate flow, or HTTP request |
| **Go to topic** | Redirects to another topic |
| **Variable management** | Set, clear, or manipulate conversation variables |
| **Send adaptive card** | Display rich interactive UI cards |
| **End conversation** | Ends the session and optionally triggers a CSAT survey |

**Trigger phrases:**
Each custom topic needs 5–10 trigger phrases — natural language phrases the user might say to activate the topic. The NLU model finds the best match, so exact phrasing isn't required.

```
Topic: Password Reset
Trigger phrases:
- forgot my password
- can't log in to my account
- reset password
- account is locked
- password expired
```

**Best practices:**
- Use 5–10 diverse trigger phrases per topic — cover different ways users phrase the same intent
- Keep topics focused on a single intent
- Always end with the End of Conversation topic for CSAT tracking
- Use variables to personalize responses (user name, department, ticket number)
- Test trigger accuracy by trying paraphrased phrases in the test panel

---

### 6. Activity

**What it is:**
The Activity tab shows the execution history of **autonomous agent runs** — triggered workflows and background tasks. While Analytics covers conversational usage, Activity covers what your agent did when operating autonomously (without a user actively chatting).

**Where to find it:**
`Agent → Activity tab`

**What Activity shows:**

| Section | Description |
|---|---|
| **Run history** | List of all autonomous trigger executions with status |
| **Run details** | Step-by-step trace of each run — inputs, tool calls, outputs |
| **Knowledge source usage** | Which knowledge sources were referenced in each run |
| **Status** | Success / Failed / Running for each execution |
| **Duration** | How long each run took |
| **Trigger** | What event caused the run (scheduled, Dataverse event, Power Automate, etc.) |

**Types of triggers that appear in Activity:**
- Dataverse row changes (new record, updated record)
- Scheduled triggers (run every hour, daily, weekly)
- Power Automate triggers
- HTTP / API triggers
- Microsoft 365 event triggers (new email, calendar event)

**How to use Activity for debugging:**
1. Open a failed run → click into it
2. Review the step-by-step trace — find where the failure occurred
3. Check tool call inputs/outputs — identify if the wrong data was passed
4. Check knowledge source references — verify the right content was retrieved
5. Fix the issue in the agent → re-test → verify next run succeeds

**Best practices:**
- Set up email notifications for failed runs (via Power Automate)
- Review Activity weekly for autonomous agents in production
- Use knowledge source analysis in Activity to refine what the agent reads

---

### 7. Evaluation

**What it is:**
Evaluation is Copilot Studio's built-in quality assurance system. It lets you create test sets — collections of questions and expected answers — and run them against your agent systematically. This replaces manual "poke and hope" testing with structured, repeatable benchmarks.

**Where to find it:**
`Agent → Evaluation tab`

**Core concepts:**

| Concept | Description |
|---|---|
| **Test set** | A collection of test cases (questions + expected answers) |
| **Test case** | A single question with its expected response |
| **Evaluation run** | Running a test set against the current agent version |
| **Pass / Fail** | Whether the agent's response matches the expected answer |
| **Score** | Percentage of test cases that passed |

**4 ways to create test sets:**
1. **Auto-generate** — Copilot Studio generates test cases from your existing topics and knowledge
2. **CSV import** — Upload a spreadsheet of questions and expected answers
3. **Test canvas capture** — Conversations in the test panel are saved as test cases
4. **Manual entry** — Add individual test cases by hand

**CSV format for import:**
```csv
question,expected_answer
"How do I reset my password?","Visit the self-service portal at portal.contoso.com/reset"
"What is the VPN address?","vpn.contoso.com using GlobalProtect client"
"How long does hardware replacement take?","3-5 business days after ticket approval"
```

**Running evaluations:**
- Run manually from the Evaluation tab
- Trigger automatically via Power Automate connector
- Run via Power Platform REST API (for CI/CD integration)
- Compare multiple agent versions side by side

**What to evaluate regularly:**
- After every significant instruction change
- After adding new knowledge sources
- After updating topics
- After changing tools or their descriptions
- Before every production release

**Best practices:**
- Build test sets that cover happy paths, edge cases, and out-of-scope queries
- Include intentionally failing cases to verify the agent doesn't hallucinate
- Target 90%+ pass rate before publishing to production
- Review failed cases to understand why — use them to improve instructions or knowledge

---

### 8. Channels

**What they are:**
Channels are the platforms and surfaces where you deploy your agent so users can interact with it. You build the agent once in Copilot Studio and publish it to any supported channel.

**Where to find them:**
`Agent → Channels tab`

**Supported channels:**

| Channel | Audience | Notes |
|---|---|---|
| **Microsoft Teams** | Internal employees | Publish to Teams app store; SSO supported |
| **SharePoint** | Intranet users | One-click deployment; permissions auto-inherited |
| **Microsoft 365 Copilot** | M365 Copilot users | Native extension of M365 Copilot experience |
| **Demo website** | Testing and stakeholder demos | Quick shareable link; no auth by default |
| **Custom website** | Public or internal web | Embed via iframe or Direct Line SDK |
| **WhatsApp** | Global customers | Requires WhatsApp Business Account |
| **Facebook** | Social media users | Requires Facebook App registration |
| **Telephony / Voice** | Call center | Real-time voice with NLU; supports IVR |
| **Azure Bot Service** | Any custom channel | Slack, Telegram, Line, Kik, and more |
| **Email** | Inbox-triggered workflows | Autonomous agents processing emails |

**Authentication options per channel:**
- **No authentication** — anyone with the link can chat (demo/public bots)
- **Azure AD (Entra ID)** — Microsoft 365 SSO for internal users
- **Custom OAuth** — Any OAuth 2.0 provider
- **Manual authentication** — User provides credentials during conversation

**Teams deployment steps:**
1. Agent → Channels → Microsoft Teams → Turn on
2. Customize the Teams app manifest (name, icon, description)
3. Submit to admin for approval OR install directly for your org
4. Optionally pin the bot in Teams sidebar

**Best practices:**
- Choose channels based on where your users already work — don't force behavior changes
- Use SSO (Azure AD) for internal agents to avoid login friction
- For voice channels, tune silence detection and speech sensitivity settings
- Test each channel separately — behavior can vary (adaptive cards not supported everywhere)
- Use the demo website for quick stakeholder demos before full deployment

---

### 9. Analytics

**What it is:**
Analytics is the built-in dashboard that tracks how your agent is performing in production. It covers user engagement, conversation outcomes, topic performance, knowledge effectiveness, user satisfaction, and AI-generated insights. Data is available for up to 180 days.

**Where to find it:**
`Agent → Analytics tab`

**Key metrics:**

| Metric | Description | Target |
|---|---|---|
| **Total sessions** | Number of conversations initiated | — |
| **Engaged sessions** | Sessions where the user actively interacted | High |
| **Engagement rate** | % of sessions that became engaged | > 80% |
| **Resolution rate** | % of engaged sessions that were resolved | > 70% |
| **Escalation rate** | % of sessions transferred to a human | Low |
| **Abandonment rate** | % of sessions that ended without resolution | Low |
| **CSAT score** | Average customer satisfaction (0–5 scale) | > 4.0 |
| **Thumbs up / down** | Per-response feedback from users | High positive ratio |

**Session outcomes:**
- **Resolved (confirmed)** — User confirmed their issue was solved via End of Conversation survey
- **Resolved (implied)** — Session completed without explicit confirmation
- **Escalated** — User or agent triggered the Escalate topic / Transfer to agent
- **Abandoned** — Session timed out without resolution (30-minute inactivity)
- **Unengaged** — User opened the chat but never triggered a topic

**Analytics sections:**

| Section | What it shows |
|---|---|
| **Summary (AI-generated)** | Bullet-point AI summary of key insights and trends |
| **Conversation outcomes** | Stacked chart of resolved / escalated / abandoned over time |
| **Topics** | Which topics triggered most, resolution rate per topic |
| **Knowledge** | Knowledge source usage, answer quality, unanswered questions |
| **Satisfaction** | CSAT scores, thumbs up/down reactions, user comments |
| **Sentiment (preview)** | AI-based analysis of overall session sentiment |
| **Agents** | Call volume and success rates for connected child agents |
| **Themes** | AI-grouped clusters of user questions for pattern discovery |

**Unanswered questions:**
Copilot Studio automatically tracks questions the agent couldn't answer — either because the knowledge source didn't cover it, or no topic matched. Use this list to:
- Add new knowledge sources
- Create new topics for common unhandled intents
- Update instructions to handle edge cases

**Integrating analytics externally:**
- **Power BI** — Export conversation transcript data and build custom dashboards
- **Azure Application Insights** — Advanced telemetry and custom event tracking
- **Dataverse** — All transcript data is stored in the ConversationTranscript table
- **Copilot Studio Kit (Power CAT)** — Extended KPIs and conversation quality analysis

**Best practices:**
- Review analytics weekly — set a recurring calendar reminder
- Use the 7-day view for new agents; 28-day view for mature agents
- Combine metrics — low engagement + low CSAT = structural problem; high engagement + low CSAT = content problem
- Export unanswered questions monthly and use them to build new evaluation test sets
- Share the Analytics Viewer role with business stakeholders so they can self-serve

---

## 🏗️ POC: IT Service Desk Bot

See the [`/poc`](./poc) folder for the complete Proof of Concept.

**Scenario:** A single IT Service Desk Bot that:
- Answers IT questions from a SharePoint knowledge base
- Guides users through password resets step by step (topic)
- Raises IT tickets via a Power Automate flow (tool)
- Escalates unresolved issues to a human agent
- Measures resolution rate and CSAT via analytics

### Agent architecture

```
User
  │
  ▼
┌─────────────────────────────────────────────┐
│           IT Service Desk Bot               │
│                                             │
│  Instructions: IT-only, step-by-step tone   │
│  Knowledge:    IT Wiki (SharePoint)          │
│  Tools:        Raise Ticket (Power Automate) │
│  Topics:       Password Reset, VPN Setup,    │
│                Raise Ticket, Escalate        │
└──────────────────────────┬──────────────────┘
                           │ (if unresolved)
                           ▼
                    Human Agent (Escalate)
```

---

## 📁 Folder Structure

```
copilot-studio-complete-guide/
│
├── README.md                          ← This file (all 9 concepts explained)
├── CONTRIBUTING.md
├── LICENSE
│
├── docs/
│   ├── 01-instructions.md             ← Deep dive: instructions
│   ├── 02-knowledge.md                ← Deep dive: knowledge sources
│   ├── 03-tools.md                    ← Deep dive: tools
│   ├── 04-agents.md                   ← Deep dive: multi-agent
│   ├── 05-topics.md                   ← Deep dive: topics & nodes
│   ├── 06-activity.md                 ← Deep dive: activity tab
│   ├── 07-evaluation.md               ← Deep dive: evaluation & test sets
│   ├── 08-channels.md                 ← Deep dive: channels & deployment
│   └── 09-analytics.md                ← Deep dive: analytics & KPIs
│
└── poc/
    ├── README.md                      ← POC overview & setup steps
    ├── agents/
    │   └── it-service-desk/
    │       ├── instructions.md        ← Agent system instructions
    │       └── description.md         ← Agent description
    ├── topics/
    │   ├── password-reset.md          ← Topic: password reset
    │   ├── vpn-setup.md               ← Topic: VPN setup
    │   ├── raise-ticket.md            ← Topic: raise IT ticket
    │   └── escalate.md                ← Topic: escalate to human
    ├── knowledge/
    │   └── knowledge-sources.md       ← Knowledge source config
    ├── tools/
    │   └── raise-ticket-flow.md       ← Power Automate flow guide
    └── docs/
        ├── evaluation-test-set.csv    ← Ready-to-import test cases
        ├── testing-guide.md           ← Testing scenarios
        └── deployment-checklist.md    ← Pre-launch checklist
```

---

## 🔗 Official Resources

- [Copilot Studio Documentation](https://learn.microsoft.com/en-us/microsoft-copilot-studio/)
- [Analytics Overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-overview)
- [Multi-Agent Patterns](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/multi-agent-patterns)
- [Copilot Studio Labs (Hands-on)](https://microsoft.github.io/mcs-labs/)
- [Copilot Studio Kit (Power CAT)](https://github.com/microsoft/CopilotStudioKit)

---

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) — PRs welcome for new examples, corrections, and translations.

---

## 📄 License

MIT — see [LICENSE](LICENSE)
