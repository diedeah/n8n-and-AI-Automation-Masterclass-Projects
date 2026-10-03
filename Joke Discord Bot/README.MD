# AI Discord Joke Bot

An n8n workflow that receives a Discord interaction, sends the user's input to an AI agent, generates a joke, and returns the response to Discord through the Discord API.

## Workflow

```text
Discord Interaction
        ↓
n8n Webhook
        ↓
AI Agent
        ↓
OpenRouter Chat Model
        ↓
JavaScript JSON Escaping
        ↓
Discord API
        ↓
Generated Joke
```

## What it does

1. Receives a POST request from a Discord interaction.
2. Extracts the user's input from the Discord payload.
3. Sends the input to an AI agent.
4. Generates a joke based on the user's request.
5. Escapes characters that could cause problems in the JSON response.
6. Sends the generated joke back to Discord using the interaction's application ID and token.

## Features

* Discord interaction webhook
* AI-generated responses
* OpenRouter LLM integration
* Dynamic Discord application ID and interaction token handling
* JavaScript response sanitization
* Discord REST API integration

## Technologies

* **n8n**
* **OpenRouter**
* **AI Agent**
* **JavaScript**
* **Discord API**
* **Webhooks**
* **REST API**

## How it works

The Discord interaction sends the user's input through the webhook payload.

The workflow extracts the value using:

```text
$json.body.data.options[0].value
```

The AI agent then generates a joke based on that input.

Before sending the response back to Discord, the JavaScript node escapes backslashes and quotation marks to help ensure the generated content can be safely included in the JSON request.

The final HTTP Request sends the response to Discord using the `application_id` and `token` supplied by the original interaction.

## Setup

1. Import the workflow into n8n.
2. Connect an OpenRouter credential.
3. Configure the Discord application and interaction endpoint to send requests to the n8n webhook.
4. Replace the sanitized OpenRouter credential references.
5. Replace the webhook and n8n instance identifiers where necessary.
6. Test the Discord interaction.

## Project Structure

```text
ai-discord-joke-bot/
├── workflow.json
└── README.md
```
