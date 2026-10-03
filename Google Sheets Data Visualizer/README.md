# Google Sheets Data Visualizer

An n8n workflow that reads e-commerce KPI data from Google Sheets, processes the data with JavaScript, and generates a revenue chart using QuickChart.

## Workflow

```text
Manual Trigger
      ↓
Edit Fields
      ↓
Get Data from Google Sheets
      ↓
JavaScript Data Processing
      ↓
QuickChart API
      ↓
PNG Chart
```

## What it does

1. Manually triggers the workflow.
2. Sets the chart type to a line chart.
3. Reads data from a Google Sheets dataset.
4. Extracts the `Month` and `Revenue ($)` columns.
5. Converts revenue values into numbers.
6. Builds a Chart.js-compatible configuration.
7. Sends the chart configuration to QuickChart.
8. Returns the generated chart as a PNG file.

## Features

* Google Sheets data retrieval
* JavaScript data transformation
* Dynamic Chart.js configuration
* External API integration with QuickChart
* PNG chart generation
* Automated data visualization

## Technologies

* **n8n**
* **Google Sheets**
* **JavaScript**
* **QuickChart**
* **Chart.js**

## Setup

Before importing or publishing this workflow:

1. Connect your Google Sheets account in n8n.
2. Replace the Google Sheets document ID with your own spreadsheet.
3. Select the appropriate worksheet.
4. Update the Google Sheets credential reference.
5. Execute the workflow manually.

The source spreadsheet should contain at least:

* `Month`
* `Revenue ($)`

## Example Use Case

This workflow can be used to turn business KPI data into a visual report without manually creating charts. The same approach can be adapted for sales, expenses, website traffic, customer metrics, or other spreadsheet-based datasets.

## Project Structure

```text
google-sheets-data-visualizer/
├── workflow.json
└── README.md
```
