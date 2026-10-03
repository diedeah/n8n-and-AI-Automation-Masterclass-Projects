# Google Sheets Request Automation

A simple n8n automation that receives request data through a **Webhook**, stores the information in **Google Sheets**, and returns a JSON confirmation response.

This workflow demonstrates how an incoming HTTP request can be connected to a spreadsheet-based data storage workflow.

## Workflow

```text
HTTP POST Request
       │
       ▼
   Webhook
       │
       ▼
 Google Sheets
  Append Row
       │
       ▼
Respond to Webhook
```

## Features

* HTTP POST webhook
* Request data collection
* Google Sheets integration
* Automatic row insertion
* JSON API response
* REST-style workflow automation
* Simple API-to-spreadsheet pipeline

## Technologies

* n8n
* Google Sheets
* Webhooks
* HTTP/REST
* JSON

## Workflow Nodes

### Webhook

Receives an HTTP `POST` request at the configured webhook path:

```text
request-submission
```

The workflow expects request data containing:

* Name
* Email
* Request

### Append row in sheet

Adds the received information to a Google Sheets spreadsheet.

The workflow maps the incoming fields as follows:

```text
Name    → $json.body.Name
Email   → $json.body.Email
Request → $json.body.Request
```

The data is appended to `Sheet1`.

### Respond to Webhook

Returns a JSON response after the request has been successfully processed.

Example response:

```json
{
  "success": true,
  "message": "Request saved successfully"
}
```

## Example Request

The webhook can receive data similar to:

```json
{
  "Name": "John Doe",
  "Email": "example@email.com",
  "Request": "I would like to request assistance."
}
```

The workflow then adds the values to a new row in Google Sheets.

## Example Flow

```text
Client / Application
        │
        │ POST
        ▼
n8n Webhook
        │
        ▼
Google Sheets
        │
        ▼
JSON Response
```

## Setup

After importing the workflow into n8n:

1. Configure a Google Sheets credential.
2. Select the spreadsheet you want to use.
3. Select the target sheet.
4. Verify the column names:

   * Name
   * Email
   * Request
5. Configure the webhook if necessary.
6. Activate the workflow.
7. Send a POST request to the webhook.
8. Verify that the data appears in Google Sheets.

## What This Project Demonstrates

This project demonstrates a basic but practical API automation pattern using n8n.

It covers:

* Webhook handling
* HTTP POST requests
* Request data mapping
* Google Sheets integration
* Automated data storage
* JSON API responses
* REST-style automation
* External service integration
* n8n workflow orchestration

## Project Structure

```text
02-google-sheets-request-automation/
├── workflow.json
└── README.md
```

## Note

This workflow is designed as a simple example of connecting an external application or form to Google Sheets through n8n.
