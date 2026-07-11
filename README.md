# n8n AI Research & Meeting Intelligence Agent

This repository contains n8n workflow configurations for an AI-powered Research Agent and a Meeting Intelligence Agent. These workflows utilize Google Gemini and the Tavily Search API to automate research synthesis and meeting transcript analysis.

## Workflows Included

### 1. Research Agent — Web Search & Synthesis (`workflow/research-agent.json`)
An automated research assistant triggered via a form submission.
- **Trigger**: n8n Form Trigger (collects research queries/questions).
- **Search Integration**: Fetches relevant results using the Tavily Search API.
- **Synthesis**: Utilizes Google Gemini to summarize search results, compile a comprehensive research briefing, and cite references.
- **Output**: Generates formatted research summaries containing key points and source URLs.

### 2. Meeting Intelligence Agent (`workflow/meeting-intelligence-agent.json`)
A workflow that analyzes meeting transcripts to extract structured key insights.
- **Input**: Accepts meeting transcript data.
- **AI Processing**: Instructs Google Gemini to parse transcripts and identify:
  - **Decisions**: Key agreements and conclusions reached.
  - **Action Items**: Tasks with assigned owners and deadlines.
  - **Open Questions**: Pending questions or unresolved issues.
- **Output**: Returns a clean, structured JSON format for downstream integrations (e.g., Slack notifications, Notion database entries, Jira tasks).

---

## How to Import These Workflows into n8n

1. Download or clone this repository.
2. In your n8n workspace, click **Add Workflow** -> **Import from File**.
3. Choose either `research-agent.json` or `meeting-intelligence-agent.json` from the `workflow` folder.
4. Configure the required credentials:
   - **Google Gemini (PaLM) API**: For LLM-based summary and extraction.
   - **Tavily Search API**: Header Authentication for search integration.
5. Save and activate the workflows.
