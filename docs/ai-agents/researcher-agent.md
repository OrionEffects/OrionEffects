# Researcher Agent

**Platform:** Zapier Agents  
**Current version shown:** v5 Published  
**Trigger:** Slack message posted to the `#research` channel  
**Role:** Business prospect research and qualification  
**Status:** Published / actively configured

> This document describes the agent configuration supplied by Orion Effects. It is documentation of the workflow, not a claim that every external search result or integration outcome has been independently audited.

## Purpose

The Researcher Agent is designed to turn a research request posted in Slack into a structured shortlist of potential Orion Effects prospects.

The workflow is intended for businesses that may benefit from Meta Ads and that fit Orion Effects' prospecting criteria.

## Trigger

A new message posted to the Slack `#research` channel starts the workflow.

The agent is configured to understand two request formats.

### Natural language

Examples:

```text
Find dental clinics in Toronto, Canada
Find dental clinics in London, UK
Find marketing agencies in Berlin, Germany
```

### Structured

Examples:

```text
country:Canada, industry:Dental, region:Ontario
country:India, industry:IT Services, region:Bangalore
```

The agent extracts the industry, country, region or state, city and other filtering criteria from the request.

## Workflow

### 1. Parse the research request

Extract the target industry, location and additional qualification criteria.

### 2. Create a dedicated Google Sheets worksheet

The configured workflow creates a new worksheet based on the research criteria, for example:

```text
Dental - Toronto, Canada
Marketing Agencies - Berlin, Germany
IT Services - Bangalore, India
```

A timestamp based name can be used to reduce duplicate worksheet names.

### 3. Research businesses

The agent is instructed to use web search and verification to identify 2 to 5 businesses matching the requested industry and location.

The configuration asks the agent to check for:

• A business website
• Active Facebook presence
• Active Instagram presence
• Potential suitability for Meta Ads
• Priority industry fit
• Estimated employee size where available, with a target range of 2 to 200 employees

### 4. Verify public information

For each candidate, the agent is instructed to review publicly available sources, including:

• Official website
• Facebook
• Instagram
• LinkedIn company page, when available

The agent also evaluates the apparent quality of the business's online marketing and whether Meta Ads could realistically be useful.

### 5. Score prospects

Each lead receives a qualification score from 1 to 100 based on the configured criteria:

| Criterion | Considered |
| --- | --- |
| Website quality | Yes |
| Active social media presence | Yes |
| Business growth potential | Yes |
| Suitability for Meta Ads | Yes |
| Industry competitiveness | Yes |
| Overall online presence | Yes |
| Contact information accessibility | Yes |

### 6. Opportunity analysis

Leads scoring **70 or higher** receive an opportunity analysis covering:

• Why the business may be a good prospect
• Observed marketing weaknesses, where supported by public evidence
• Potential areas where Orion Effects could help

### 7. Populate qualified leads in Google Sheets

The configured output fields are:

```text
Business Name
Industry
Qualification Score
Website
City
Country
Contact Person
Job Title
Email
Phone
Facebook
Instagram
LinkedIn
Estimated Employees
Opportunity Summary
```

Only leads meeting the configured qualification threshold of **70+** are intended to be appended as qualified prospects.

### 8. Report back to Slack

The agent is configured to reply in the Slack thread with a summary of the research, including the number of leads found, scores and relevant notes.

## Intended operating model

```text
Slack Research Request
        ↓
Parse Criteria
        ↓
Business Discovery
        ↓
Website + Social Verification
        ↓
Prospect Qualification
        ↓
1–100 Score
        ↓
70+ Qualification Gate
        ↓
Opportunity Analysis
        ↓
Google Sheets
        ↓
Slack Summary
        ↓
Human Review
```

## Human oversight

The final purpose of the workflow is to provide a research shortlist for Orion Effects to review before prospects are added to the sales pipeline or contacted.

The agent should therefore be treated as **research and decision support**, not as an autonomous sales decision maker.

## Data and privacy principles

The workflow is designed around publicly available business information. Personal or sensitive information should not be collected unless there is a legitimate business purpose and appropriate legal basis.

Prospect data should be handled in accordance with applicable privacy and data protection requirements.

## GitHub documentation boundary

This repository documents the agent's architecture and intended behaviour. It does **not** contain:

• Zapier credentials
• API keys
• OAuth tokens
• Private Slack data
• Private Google Sheets data
• Prospect databases
• Hidden agent configuration or secrets

## Improvement roadmap

Potential future improvements should be implemented only after testing and verification:

1. Add reproducible scoring criteria and weighting documentation.
2. Record evidence supporting each qualification score.
3. Separate verified facts from estimates and AI generated assessments.
4. Add duplicate detection across research runs.
5. Add an explicit human approval checkpoint before CRM entry.
6. Track research quality and false positive rates.
7. Version the agent's prompt and workflow changes alongside this documentation.

## Source of this documentation

The current description is based on the Orion Effects Zapier Agent configuration shown to the project owner in August 2026. It should be updated whenever the live agent configuration materially changes.
