# Orion Effects AI Agents

This directory documents AI agents that Orion Effects is actually building or testing with Zapier Agents and related automation tools.

The purpose of this section is documentation and portfolio transparency. The agents remain hosted and executed in their respective platforms; GitHub is used to document their architecture, logic, inputs, outputs, limitations and evolution.

## Current agent

### Reporting Agent

An automated business reporting agent designed to run twice daily and consolidate operational signals into Google Sheets and Slack.

**Current documented workflow:**

```text
Scheduled trigger
      ↓
Create / prepare daily report sheet
      ↓
Gmail inbox summary
      ↓
HubSpot ticket summary
      ↓
Marketing / website metric inputs
      ↓
Code-based formatting and action-point analysis
      ↓
Comprehensive report object
      ↓
Slack summary
      ↓
Google Sheets record
```

The current agent instructions explicitly use placeholders for Meta Ads, Facebook Page and website analytics data. Those sources should therefore not be represented as live integrations until they are actually connected and verified.

## Documentation standard

Each agent documented here should include:

• Purpose
• Trigger
• Inputs
• Connected tools
• Processing logic
• Outputs
• Human review points
• Known limitations
• Future improvements
• Current implementation status

## Principle

GitHub documents what exists. It does not turn planned integrations into completed ones.

That distinction is intentional and keeps the Orion Effects portfolio credible.

---

**Status:** Experimental / In development
