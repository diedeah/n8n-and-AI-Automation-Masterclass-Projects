# AI Meme Generator with Imgflip

An n8n workflow that uses an AI model to select an appropriate Imgflip meme template, generate short meme captions, and create the final meme through the Imgflip API.

## Workflow

```text
Chat Trigger
      ↓
Get Imgflip Templates
      ↓
Filter 2-Box Templates
      ↓
AI Selects Template & Captions
      ↓
Lookup Exact Template ID
      ↓
Add Imgflip Credentials
      ↓
Imgflip Caption API
      ↓
Generated Meme
```

## What it does

1. Receives a meme idea through the n8n chat interface.
2. Retrieves the available meme templates from Imgflip.
3. Filters the templates to those with exactly two text boxes.
4. Provides the available template names to an AI agent.
5. The AI selects the template that best matches the user's idea.
6. The AI generates short text for the top and bottom sections.
7. JavaScript resolves the AI-selected template name to the correct Imgflip template ID.
8. Uses the Imgflip `caption_image` API to generate the meme.
9. Returns the generated meme as a Markdown image.

## Features

* AI-assisted meme generation
* Dynamic Imgflip template retrieval
* Template filtering based on box count
* Structured AI output
* Exact template-name matching
* Template ID lookup with fallback handling
* Imgflip REST API integration
* Automated meme generation

## AI Output

The AI returns a structured object containing:

```json
{
  "template_name": "Exact template name from the list",
  "text0": "First box text",
  "text1": "Second box text"
}
```

The workflow then matches the selected template against the actual Imgflip template list instead of relying directly on the AI to provide a template ID.

## Technologies

* **n8n**
* **OpenRouter**
* **LLM / AI Agent**
* **JavaScript**
* **Imgflip API**
* **REST API**
* **Structured Output Parser**

## Setup

Before using the workflow:

1. Import the workflow into n8n.
2. Connect your OpenRouter credential.
3. Configure your Imgflip account credentials.
4. Replace the sanitized credential references with your local n8n credentials.
5. Start the chat trigger.
6. Enter a meme idea.

Example input:

```text
When you realize you forgot to save your code before the power went out
```

The AI will select an available two-box template and generate the corresponding top and bottom captions.

## Project Structure

```text
ai-imgflip-meme-generator/
├── workflow.json
└── README.md
```
