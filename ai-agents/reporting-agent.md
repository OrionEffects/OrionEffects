# Reporting Agent

## Overview

The Reporting Agent is a Zapier Agent designed to produce scheduled Orion Effects business reports twice per day.

**Trigger:** Daily at 09:00 and 20:00 via Zapier Schedule.

**Primary outputs:** Google Sheets logging and a formatted Slack report.

**Current status:** Experimental / In development.

## Current workflow

```text
Schedule
   ↓
Daily report sheet
   ↓
Gmail summary
   ↓
HubSpot ticket summary
   ↓
Marketing and website metric inputs
   ↓
Code-based data formatting
   ↓
Action-point identification
   ↓
Report object
   ↓
Slack message
   ↓
Google Sheets record
```

## Inputs and processing

### 1. Schedule

Runs at 09:00 and 20:00.

### 2. Google Sheets

The agent is instructed to create a daily report sheet using the title format:

`Daily Report - YYYY-MM-DD`

The documented headers are:

`Timestamp | Meta Ads Metrics | Facebook Page Visits | Website Visits | Inbox Messages | HubSpot Tickets | Action Points`

### 3. Gmail

The agent is instructed to:

• Count unread messages
• Identify the top three key senders
• Extract subject lines from the day's emails

### 4. HubSpot

The agent is instructed to:

• Find open tickets
• Identify high-priority tickets
• Count tickets by status

### 5. Marketing and website metrics

The current instructions contain placeholders for:

• Meta Ads metrics
• Facebook Page metrics
• Website analytics

These should be treated as **placeholders**, not verified live integrations, until the relevant data sources are connected and tested.

### 6. Code processing

The agent is instructed to use Code by Zapier to:

• Format Meta Ads performance
• Format Facebook Page metrics
• Format website analytics
• Format the inbox summary
• Format HubSpot ticket data
• Identify action points such as ticket follow-ups and optimisation opportunities

### 7. Report object

The intended report contains:

• Timestamp
• Formatted metrics
• Key highlights
• Anomalies
• Action-point summary

### 8. Slack

The report is formatted as a readable Slack message with sections and emojis and sent to the designated Orion Effects Slack channel.

## Current architecture assessment

The agent has a useful operational concept: consolidate business signals into one recurring management report and turn raw information into action points.

However, the current instructions should not be described as a fully integrated business intelligence system yet. The Meta Ads, Facebook Page and website sections are explicitly placeholders.

## Recommended next improvements

### 1. Prevent duplicate daily sheets

Because the agent runs twice on the same date, the workflow should explicitly decide whether to:

• Create one sheet per day and append both reports to it, or
• Create separate morning and evening sheets.

The cleaner design is one daily sheet with separate 09:00 and 20:00 rows.

### 2. Connect verified marketing data

Replace the current placeholders with authenticated data sources and document exactly which metrics are retrieved.

### 3. Add source timestamps

Each metric should retain its source period so the report does not accidentally compare incompatible time windows.

### 4. Separate observations from recommendations

The report should distinguish:

`What happened` → `Why it may have happened` → `What should be done`

This reduces the risk of presenting an AI interpretation as a verified fact.

### 5. Add failure handling

If one source fails, the report should clearly mark that source as unavailable rather than silently generating a complete-looking report.

## Portfolio note

This documentation describes the agent configuration supplied by Orion Effects. GitHub is used as the technical documentation and version-history layer; Zapier remains the execution environment.

No credentials, private client data or access tokens should be committed to this repository.

---

**Build principle:** Automate the reporting process without automating accountability.
