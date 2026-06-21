# Knowledge — Deep Dive

Knowledge sources let your agent answer questions from your organization's content
without manually creating a topic for every possible question.

## Where: Agent → Knowledge

## Supported sources
| Source | Best for |
|---|---|
| SharePoint | Internal wikis, policy docs, how-to guides |
| Files / File collection | PDFs, Word docs, Excel, PowerPoint |
| Public website | Product docs, help centers |
| Dataverse | Structured enterprise data |
| Azure AI Search | Custom search indexes |
| Bing Custom Search | Scoped web search |
| OneNote | Notes and team knowledge |
| Outlook / Teams | Email and chat history (M365) |

## How it works
User asks a question → agent searches all knowledge sources → retrieves most relevant content → generates grounded answer.

## Best practices
- Connect authoritative, up-to-date sources
- Review unanswered questions in Analytics weekly
- Use file collections to group related documents
- Remove duplicate content — it confuses retrieval
