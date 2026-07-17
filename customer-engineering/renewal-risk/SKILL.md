---
name: renewal-risk
description: Assesses renewal risk for a specific account 60-90 days out — health trend, usage trajectory, billing history, champion strength, and contract posture in one read. Use when a renewal window opens or whenever an upcoming renewal feels uncertain.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer customer-data.get-contacts health.get-health-score platform-data.get-usage platform-data.get-billing-subscription platform-data.get-contracts platform-data.trend-analysis
---

# Renewal Risk Read

You give a clear-eyed renewal read on one account: will they renew, what could change the answer, and what to do in the time remaining.

## Workflow

1. Load the customer (`get-customer`) and contract terms (`get-contracts`, `get-billing-subscription`): renewal date, value, auto-renew clause, notice period — the notice period is the real deadline.
2. Health trajectory (`get-health-score`, `trend-analysis`): direction over the last two quarters matters more than today's number.
3. Usage trajectory (`get-usage`): growing, flat, or declining; seat utilization vs. what they pay for (under-utilization = downgrade pressure even when they renew).
4. Relationship strength (`get-contacts`): is the champion still there, engaged, and senior enough? Single-threaded = elevated risk regardless of other signals.
5. Weigh the four dimensions — value realization, usage trajectory, relationship strength, commercial posture — into a verdict.

## Output Format

**Renewal read: {Customer}** — renewal date, notice deadline, ARR, verdict: Safe / Needs work / At risk / Likely churn

**The four dimensions** — one line each with evidence: value, usage, relationship, commercial

**What could change the outcome** — the 1-2 factors that most swing this renewal

**Runway plan** — what to do with the remaining weeks, in order: e.g., value recap deck → exec touch → commercial conversation. Include dates working back from the notice period.

## Guidelines

- Anchor every deadline to the notice period, not the renewal date.
- Under-utilization deserves proactive right-sizing conversation over hoping they don't notice — the trust trade is worth it.
- If verdict is "likely churn", shift the plan to save-attempt-or-graceful-exit; pretending otherwise wastes the runway.
