# Reporting Agent

**Platform:** Zapier Agents  
**Trigger:** Schedule by Zapier, daily at 09:00 and 20:00  
**Primary outputs:** Google Sheets and Slack  
**Status:** Experimental / in development

> This document describes the current agent instructions supplied by Orion Effects. It documents the configured workflow and does not claim that placeholder integrations are already live.

## Purpose

The Reporting Agent is designed to consolidate recurring business signals into a twice-daily management report and turn those signals into action points.

## Current workflow

```text
Scheduled trigger
        ↓
Daily report sheet
        ↓
Gmail inbox summary
        ↓
HubSpot ticket summary
        ↓
Marketing / website metric inputs
        ↓
Code-based formatting
        ↓
Action-point identification
        ↓
Report object
        ↓
Slack summary
        ↓
Google Sheets record
```

## Configured workflow

### 1. Schedule

The agent is instructed to run at **09:00 and 20:00 every day**.

### 2. Google Sheets

The agent is instructed to create a sheet using the title format:

`Daily Report - YYYY-MM-DD`

Configured headers:

```text
Timestamp
Meta Ads Metrics
Facebook Page Visits
Website Visits
Inbox Messages
HubSpot Tickets
Action Points
```

The agent then creates a row containing the current report data.

### 3. Gmail summary

The agent is instructed to:

• Count unread messages
• Identify the top three key senders
• Extract subject lines from emails received that day

### 4. HubSpot ticket summary

The agent is instructed to:

• Find open tickets
• Identify high-priority tickets
• Count tickets by status distribution

### 5. Marketing and website metrics

The current instructions contain placeholders for:

• Meta Ads metrics
• Facebook Page metrics
• Website analytics

These are documented as **placeholders** because the supplied configuration does not demonstrate verified live data retrieval from those sources.

### 6. Code processing

The agent is instructed to use Code by Zapier to format the available data and identify action points, including:

• Meta Ads performance formatting
• Facebook Page metric formatting
• Website analytics formatting
• Gmail summary formatting
• HubSpot ticket formatting
• Follow-up opportunities
• Marketing optimisation opportunities

### 7. Report object

The intended report object contains:

• Timestamp
• Formatted metrics
• Key highlights
• Anomalies
• Action-point summary

### 8. Slack delivery

The report is formatted as a readable Slack message with sections and emojis and sent to the designated Orion Effects Slack channel.

## Architecture assessment

The concept is strong: combine operational information from different business systems, summarise it consistently and turn the information into decisions or follow-up actions.

The current configuration should **not** yet be described as a fully integrated business intelligence platform because three major data areas are explicitly placeholders.

## Important implementation consideration

The agent runs twice on the same calendar day while using a date-only sheet title. The implementation should explicitly prevent duplicate daily sheets or define a morning/evening sheet strategy.

The cleaner design is:

```text
One sheet per day
        ↓
09:00 report row
        ↓
20:00 report row
```

This preserves the twice-daily reporting cadence without creating duplicate daily workbooks or sheets.

## Recommended evolution

### Phase 1 — Stabilise

• Verify the Gmail workflow
• Verify HubSpot ticket retrieval
• Confirm Google Sheets creation and row updates
• Confirm Slack delivery
• Add failure handling when an individual source is unavailable

### Phase 2 — Connect real marketing data

Replace the current placeholders with verified, authenticated sources for:

• Meta Ads
• Facebook Page insights
• Website analytics

Document exactly which metrics are retrieved and their reporting periods.

### Phase 3 — Improve intelligence

Separate the report into:

```text
What happened
      ↓
What changed
      ↓
Why it may have changed
      ↓
What needs attention
      ↓
Recommended action
```

The distinction matters because AI-generated explanations should not be presented as verified facts.

### Phase 4 — Measure the agent itself

Track:

• Source success rate
• Report delivery success rate
• Missing-data frequency
• False or unsupported action points
• Time saved versus manual reporting

## Human accountability

The agent is designed to support business monitoring and decision-making. Recommendations should be treated as decision support and reviewed by a human before material business actions are taken.

## GitHub documentation boundary

GitHub documents the architecture and evolution of the agent. Zapier remains the execution environment.

This repository should never contain:

• API keys
• OAuth tokens
• Passwords
• Private client information
• Private inbox content
• Private CRM records
• Slack credentials

## Source

This documentation is based directly on the Orion Effects Zapier Agent configuration supplied in August 2026. It should be updated whenever the live agent materially changes.

---

**Build principle:** Automate the reporting process without automating accountability.
