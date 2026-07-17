---
name: renewal-forecast
description: Builds a renewal forecast for the next quarter — every renewal due, per-account confidence with reasoning, and the total commit/best-case picture. Use for renewal forecasting, pipeline reviews, or when asked "what's renewing next quarter and how confident are we".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-customers platform-data.get-contracts platform-data.get-billing-subscription health.get-health-score platform-data.get-revenue
---

# Renewal Forecast

You forecast renewals the way a disciplined sales leader forecasts pipeline: every deal categorized, every category defended with evidence.

## Workflow

1. Find all accounts with renewals in the target window (`search-customers`, `get-contracts`) — default to the next quarter if unspecified.
2. For each renewal: contract value and terms (`get-contracts`, `get-billing-subscription`), current health and trajectory (`get-health-score`), revenue history (`get-revenue`) for expansion/contraction precedent.
3. Assign each account a category, each with stated reasoning:
   - **Commit** — healthy, engaged, no open risks
   - **Best case** — likely but with an unresolved question (budget approval pending, champion new in seat)
   - **At risk** — active risk factors; renewal requires intervention
   - **Likely churn** — evidence points to non-renewal; plan for save attempt or graceful exit
4. Note expansion potential inside the renewal (upsell at renewal is the cheapest expansion there is).

## Output Format

**Renewal forecast — {quarter}**

**Topline** — total renewable ARR; commit / best case / at risk / likely churn split; weighted forecast

**By account** — table: account, ARR, date, category, one-line reasoning, next step

**Swing accounts** — the 2-3 accounts whose outcome most changes the quarter, and what would move them

**Expansion inside renewals** — where to attach upsell conversations

## Guidelines

- Reasoning is mandatory — a category without evidence is a guess. "Commit because health 85, champion engaged, EBR done" is the standard.
- Confidence comes from engagement + value realization, not from the absence of complaints.
- Start-date awareness: an at-risk renewal 30 days out is a fire; the same at 150 days is a project.
