# AI Email Reply with Human Approval

An AI-powered email automation workflow built with **n8n** that monitors incoming Gmail messages, summarizes the email, generates a professional reply, and sends the draft for human approval before it is sent.

If the reply is rejected, the workflow sends the email back through the AI drafting process so a revised response can be reviewed.

## Workflow

```text
Gmail Trigger
     │
     ▼
  Markdown
     │
     ▼
Summarization Chain
     │
     ▼
 Edit Fields
     │
     ▼
  AI Agent
     │
     ▼
Send Draft & Wait
     │
     ▼
 Approval Check
    │      │
Approved  Rejected
    │      │
    ▼      ▼
Send     Edit Fields
Email       │
            ▼
         AI Agent
            │
            ▼
      Review Again
```

## Features

* Automatic Gmail monitoring
* Email content processing
* AI-powered email summarization
* Professional AI-generated replies
* HTML email generation
* Human approval before sending
* Double approval interface
* Automatic revision after rejection
* OpenRouter LLM integration
* Gmail integration

## Technologies

* n8n
* Gmail
* OpenRouter
* AI Agent
* LLMs
* JavaScript expressions
* Human-in-the-Loop automation

## Workflow Nodes

### Gmail Trigger

Checks Gmail for incoming emails every minute and starts the workflow when a new message is detected.

### Markdown

Processes the email snippet before passing it to the summarization stage.

### Summarization Chain

Creates a concise summary of the incoming email.

The workflow instructs the model to keep the summary within **100 words**.

### OpenRouter Chat Model

Provides the language model used by both the summarization chain and AI Agent.

The workflow uses:

```text
openrouter/free
```

### AI Agent

Generates a professional business email reply based on the summarized email.

The workflow instructs the AI Agent to:

* Keep the response concise
* Stay under 100 words
* Write only the email body
* Use HTML formatting where appropriate
* Maintain a professional tone

### Send message and wait for response

Sends the generated email draft for human approval instead of immediately sending it to the original recipient.

The approval configuration uses a **double approval** option.

### If

Checks the approval result.

An approved response proceeds to the final Gmail node.

A rejected response is routed back through the workflow so the AI can generate another draft.

### Send a message

Sends the approved AI-generated response to the original email sender.

### Edit Fields

Acts as the workflow's routing point before the AI Agent, including the path used when a response is rejected and needs to be revised.

## Approval Flow

The workflow follows this process:

```text
Incoming Email
      ↓
Summarize Email
      ↓
Generate AI Reply
      ↓
Human Reviews Reply
      ↓
   ┌───────────────┐
   │               │
Approved        Rejected
   │               │
   ↓               ↓
Send Email     Generate New Reply
                   │
                   ↓
              Review Again
```

This prevents the AI-generated response from being sent automatically without human review.

## Setup

After importing the workflow into n8n:

1. Configure a Gmail credential.
2. Configure an OpenRouter credential.
3. Assign the credentials to the appropriate nodes.
4. Configure the Gmail Trigger.
5. Verify the approval settings.
6. Test the workflow with a test email.
7. Review the generated response.
8. Approve or reject the draft.

## What This Project Demonstrates

This project demonstrates how AI can be integrated into an email workflow while keeping a human involved in the final decision.

It covers:

* Gmail automation
* AI-powered summarization
* LLM integration
* AI Agent orchestration
* Professional email generation
* HTML email formatting
* Human-in-the-Loop approval
* Approval and rejection branching
* AI response revision
* Workflow looping
* Automated email delivery

## Project Structure

```text
10-gmail-hitl/
├── workflow.json
└── README.md
```

## Note

The workflow uses AI to draft email responses, but the final response is subject to human approval before being sent. Rejected drafts are routed back through the AI drafting process for another review cycle.
