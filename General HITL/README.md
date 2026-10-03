# Human-in-the-Loop Refund Approval

An n8n workflow that automates refund requests while introducing a **Human-in-the-Loop (HITL) approval process** for higher-value refunds.

Refund requests below the configured threshold are automatically approved, while larger requests are sent to Discord for manual approval or rejection.

## Workflow

```text
Refund Form
     │
     ▼
  Check Amount
     │
     ├── Amount < 100
     │       │
     │       ▼
     │      Merge
     │
     └── Amount >= 100
             │
             ▼
        Discord Approval
             │
             ▼
        Wait for Decision
             │
             ▼
        Check Decision
          │       │
       Approve   Deny
          │       │
          ▼       ▼
        Merge   Refund Denied
          │
          ▼
      Refund Email
```

## Features

* Refund request form
* Automatic approval for refunds below the configured threshold
* Human approval for higher-value refunds
* Discord approval interface
* Approval and rejection links
* 24-hour approval window
* Automatic refund confirmation email
* Automatic refund denial email
* Conditional workflow branching
* Human-in-the-Loop automation

## Technologies

* n8n
* Gmail
* Discord
* Webhooks
* n8n Form Trigger
* Conditional logic
* Wait/Resume functionality

## Workflow Nodes

### On form submission

Collects the refund request information:

* Name
* Email
* Amount

The form starts the workflow when a refund request is submitted.

### If

Checks whether the requested refund amount is less than `100`.

Requests below the threshold continue directly toward the refund email.

Requests of `100` or more require manual approval.

### Send a message1

Sends the refund request to a configured Discord server and channel.

The message includes:

* Customer name
* Customer email
* Refund amount
* Approval link
* Disapproval link

### Wait

Pauses the workflow while waiting for a human decision.

The workflow uses a webhook-based resume mechanism and allows up to **24 hours** for the decision.

### If1

Checks the decision submitted through the approval URL.

An approved request continues toward the refund email.

A rejected request continues to the refund-denied email.

### Merge

Combines the automatically approved requests and manually approved requests before sending the final refund confirmation.

### Send a message

Sends an email notifying the customer that their refund has been granted.

### Send a message2

Sends an email notifying the customer that their refund request has been denied.

## Approval Logic

The workflow uses the following rule:

```text
Amount < 100
    → Automatically approved

Amount >= 100
    → Requires human approval
```

For manually reviewed requests:

```text
Approve
    → Refund granted

Disapprove
    → Refund denied
```

The approval process has a maximum waiting period of 24 hours.

## Setup

After importing the workflow into n8n:

1. Configure a Gmail credential.
2. Configure a Discord credential.
3. Select the Discord server where approval requests should be sent.
4. Select the Discord channel where approval requests should be sent.
5. Configure the Form Trigger if necessary.
6. Verify the refund threshold.
7. Test an amount below `100`.
8. Test an amount of `100` or greater.
9. Test both the approval and rejection paths.

## What This Project Demonstrates

This project demonstrates how automation can be combined with human decision-making when a workflow should not operate completely autonomously.

It covers:

* Human-in-the-Loop automation
* Conditional branching
* Form processing
* Automated email notifications
* Discord integration
* Webhook-based approval
* Workflow waiting and resuming
* Merge nodes
* Automated versus manual decision paths
* Multi-step workflow orchestration

## Project Structure

```text
08-human-in-the-loop-refund/
├── workflow.json
└── README.md
```

## Note

This is a demonstration workflow for automation and approval logic. The refund action represented by the workflow is an email notification rather than an actual payment processor refund.
