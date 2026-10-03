# AI Chatbot with Memory, Tools & Web Search

An AI chatbot built with **n8n** using an AI Agent, conversation memory, calculation tools, date/time information, and Google search through SerpApi.

The workflow uses **OpenRouter** as the language model and allows the AI Agent to use different tools depending on the user's request.

## Workflow

```text
Chat Trigger
     │
     ▼
  AI Agent
   │  │  │  │
   │  │  │  └── Google Search (SerpApi)
   │  │  ├───── Date & Time
   │  ├──────── Calculator
   │  └──────── Simple Memory
   │
   ▼
OpenRouter Chat Model
```

## Features

* Chat-based interaction
* AI Agent orchestration
* Short-term conversation memory
* Calculator tool
* Date & Time tool
* Google search through SerpApi
* OpenRouter LLM integration
* 20-message conversation memory window

## Technologies

* n8n
* n8n AI Agent
* OpenRouter
* SerpApi
* JSON
* REST/API integrations

## Workflow Nodes

### When chat message received

Starts the workflow when a user sends a message through the n8n chat interface.

### AI Agent

Acts as the main decision-making component of the workflow. It processes the user's request and can use the connected tools when needed.

### Simple Memory

Maintains short-term conversation context with a window of 20 messages.

### Calculator

Allows the AI Agent to perform mathematical calculations.

### Date & Time

Provides date and time information to the AI Agent.

### Google search in SerpApi

Provides web search capabilities through SerpApi.

### OpenRouter Chat Model

Provides the language model used by the AI Agent.

The workflow is configured with:

```text
openrouter/free
```

and a maximum token setting of 2,000.

## Setup

After importing the workflow into n8n:

1. Configure an OpenRouter credential.
2. Configure a SerpApi credential.
3. Assign the credentials to their respective nodes.
4. Configure the Chat Trigger if necessary.
5. Run or activate the workflow.
6. Test the chatbot through the n8n chat interface.

## What This Project Demonstrates

This project demonstrates how an AI Agent can work with multiple tools inside an n8n workflow.

It covers:

* LLM integration
* AI Agent orchestration
* Conversation memory
* Tool calling
* Web search
* API integrations
* n8n workflow automation
* Credential management

