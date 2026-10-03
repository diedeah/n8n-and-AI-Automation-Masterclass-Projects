# AI Crypto News Sentiment Analyzer

An AI-powered workflow built with **n8n** that collects cryptocurrency news from multiple RSS feeds, filters the articles based on a user-provided keyword, and uses an LLM to summarize the news and analyze overall market sentiment.

The workflow combines **AI agents, RSS feeds, JavaScript data processing, multiple news sources, and LLM analysis** into a single automated pipeline.

## Workflow

```text
Chat Trigger
     │
     ▼
  AI Agent
  (Extract Keyword)
     │
     ├──────────────► CoinTelegraph
     ├──────────────► Decrypt
     ├──────────────► CoinDesk
     ├──────────────► Bitcoinist
     ├──────────────► NewsBTC
     ├──────────────► CryptoSlate
     ├──────────────► CryptoPotato
     ├──────────────► 99Bitcoins
     ├──────────────► CryptoBriefing
     └──────────────► Crypto.News
                    │
                    ▼
                  Merge
                    │
                    ▼
            JavaScript Filter
                    │
                    ▼
          Prompt Preparation
                    │
                    ▼
             GPT-4o-mini
                    │
                    ▼
              Chat Response
```

## Features

* Chat-based cryptocurrency news search
* AI-powered keyword extraction
* Aggregation of 10 cryptocurrency RSS feeds
* Keyword-based article filtering
* JavaScript data processing
* AI-generated news summaries
* Market sentiment analysis
* Links to reference news articles
* Multi-source news aggregation
* OpenRouter and OpenAI LLM integrations

## News Sources

The workflow retrieves news from:

* CoinTelegraph
* Decrypt
* CoinDesk
* Bitcoinist
* NewsBTC
* CryptoSlate
* CryptoPotato
* 99Bitcoins
* CryptoBriefing
* Crypto.News

## Technologies

* n8n
* AI Agents
* OpenRouter
* OpenAI GPT-4o-mini
* RSS
* JavaScript
* REST/API integrations

## Workflow Nodes

### When chat message received

Starts the workflow when the user submits a cryptocurrency-related topic or keyword.

### AI Agent

Analyzes the user's question and extracts a single keyword that is used to filter the collected news articles.

### OpenRouter Chat Model

Provides the language model used by the keyword-extraction AI Agent.

The workflow uses:

```text
openrouter/free
```

### RSS Feed Nodes

The workflow retrieves articles from multiple cryptocurrency news publications simultaneously.

Using multiple sources provides a broader set of articles for the selected topic.

### Merge

Combines the results from the 10 RSS feeds into a single workflow stream.

### Code in JavaScript

Filters the collected articles by checking the extracted keyword against:

* Article title
* Content snippet
* Description
* Full article content

Only articles containing the selected keyword continue through the workflow.

### Code in JavaScript1

Builds the prompt used for the final AI analysis.

The prompt asks the model to provide:

1. Summary of News
2. Market Sentiment
3. Links to reference news articles

### Message a model

Uses **GPT-4o-mini** to analyze the filtered cryptocurrency news and generate the final response.

### Chat

Returns the generated analysis to the user through the n8n chat interface.

## Example Workflow

A user could enter:

```text
What is the latest news about Bitcoin?
```

The AI Agent extracts the keyword:

```text
Bitcoin
```

The workflow then:

1. Retrieves articles from the configured RSS sources.
2. Searches the collected articles for the keyword.
3. Filters out unrelated articles.
4. Creates an analysis prompt from the matching articles.
5. Sends the prompt to GPT-4o-mini.
6. Returns a summary, sentiment analysis, and article links.

## Setup

After importing the workflow into n8n:

1. Configure an OpenRouter credential.
2. Configure an OpenAI credential.
3. Assign the credentials to their respective nodes.
4. Configure the Chat Trigger if necessary.
5. Verify that the RSS feeds are accessible.
6. Run the workflow.
7. Enter a cryptocurrency topic through the n8n chat interface.

## What This Project Demonstrates

This project demonstrates how n8n can combine multiple external data sources with AI processing.

It covers:

* AI Agent usage
* LLM integration
* RSS feed aggregation
* Multi-source data collection
* JavaScript data filtering
* Prompt generation
* Sentiment analysis
* API integrations
* Automated news analysis
* n8n workflow orchestration

## Project Structure

```text
07-crypto-sentiment-analyzer/
├── workflow.json
└── README.md
```

## Note

This workflow analyzes the sentiment expressed in collected cryptocurrency news. It is intended as a **news analysis and automation project**, not as financial advice, trading advice, or a price-prediction system.
