# n8n AI Research & Meeting Intelligence Agent

An automation system built in n8n that combines two AI-powered agents to streamline research and meeting follow-ups — reducing manual work in synthesizing information and tracking action items.

## Overview

This project consists of two independent but complementary workflows:

### 1. Research Agent
Takes a user-submitted research question via a web form, performs real-time web search, and uses an LLM to synthesize the results into a structured, cited research briefing — automatically saved to a Notion database.

**Flow:** Form Input → Tavily Web Search → Gemini Synthesis → Notion Storage

### 2. Meeting Intelligence Agent
Parses meeting transcripts using LLM-based structured extraction to automatically identify decisions, actionable tasks (with owners and deadlines), and open questions — then routes them into trackable Notion databases.

**Flow:** Transcript Input → Gemini Extraction → JSON Parsing → Split into two branches:
- Action items → Notion (Meeting Actions database, one row per task)
- Decisions & Open Questions → Notion (Meeting Notes database)

## Tech Stack
- **Automation/Orchestration:** n8n (self-hosted via Docker)
- **AI/LLM:** Google Gemini API
- **Search API:** Tavily
- **Data Storage:** Notion API
- **Infrastructure:** Docker

## Key Technical Challenges Solved
- **Notion API text limits:** Notion's rich_text fields cap at 2,000 characters. Built a chunking mechanism to split longer AI-generated summaries across multiple text blocks without losing content.
- **Dynamic array handling:** Used n8n's Split Out node to convert a single LLM response containing multiple action items into individual trackable Notion database rows.
- **Structured LLM output:** Prompted Gemini to return strict JSON for reliable downstream parsing, then validated/parsed it via a custom Code node.

## Setup
1. Clone this repo
2. Import the workflow JSON files (`/workflows`) into your n8n instance
3. Set up credentials for:
   - Google Gemini API
   - Tavily API (Header Auth)
   - Notion API
4. Create the required Notion databases (see `/docs/notion-schema.md`)
5. Update node references to point to your own Notion database IDs

## Demo
[Add your Loom/YouTube link here]

## Screenshots
[Add 2-3 screenshots of the workflow canvas + Notion output here]