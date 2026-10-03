# AI LinkedIn News Content Bot

An n8n workflow that collects recent AI news, uses an AI agent to select an impactful article and generate LinkedIn-ready content, publishes the post, then removes it after a short delay.

## Workflow

```text
Manual Trigger
      ↓
Google News RSS
      ↓
Limit to 10 Articles
      ↓
Format Articles
      ↓
AI Selects Article & Writes Post
      ↓
Structured Output
      ↓
Build LinkedIn Post
      ↓
Publish to LinkedIn
      ↓
Wait 30 Seconds
      ↓
Delete LinkedIn Post
```

## What it does

1. Manually starts the workflow.
2. Retrieves recent AI-related news through Google News RSS.
3. Limits the results to 10 articles.
4. Formats the article titles and links into a prompt.
5. Sends the articles to an AI agent.
6. The AI selects an impactful or insightful article.
7. Generates a LinkedIn-style post containing:

   * Title
   * Opening paragraph
   * Relevant bullet points
   * Closing paragraph
   * Article link
   * Hashtags
8. Publishes the generated content to LinkedIn.
9. Waits for 30 seconds.
10. Deletes the published post.

## Features

* Google News RSS integration
* AI-powered article selection
* AI-generated LinkedIn content
* Structured AI output
* LinkedIn API integration
* Automated post publishing
* Automated post deletion
* JavaScript-based article formatting

## Technologies

* **n8n**
* **OpenRouter**
* **AI Agent**
* **JavaScript**
* **Google News RSS**
* **LinkedIn API**
* **REST API**

## AI Output

The workflow uses a structured output parser with the following fields:

```json
{
  "title": "Title",
  "opening": "The first paragraph",
  "bullet_points": "Bullet points",
  "closing": "The closing paragraph",
  "link": "https link",
  "hashtags": "Hashtags"
}
```

These fields are combined into the final LinkedIn post before being sent to LinkedIn.

## Post Lifecycle

The workflow currently publishes the generated post only temporarily.

After publishing, it waits **30 seconds** and then sends a DELETE request to LinkedIn using the post's URN.

This makes the workflow useful for testing the generated content and LinkedIn API interaction without leaving the test post permanently published.

## Setup

1. Import the workflow into n8n.
2. Connect an OpenRouter credential.
3. Connect a LinkedIn credential.
4. Configure the LinkedIn person/account identifier.
5. Replace the sanitized credential references.
6. Test the workflow manually.

## Project Structure

```text
ai-linkedin-news-content-bot/
├── workflow.json
└── README.md
```
