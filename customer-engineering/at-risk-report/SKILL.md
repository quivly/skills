---
name: at-risk-report
description: Leadership-ready roll-up of at-risk accounts — who is at risk, why, how much ARR is exposed, and what's being done. Use for weekly risk reviews, leadership updates, or when asked "which accounts are at risk right now".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-customers health.get-health-score health.get-insights platform-data.aggregate-metrics platform-data.get-revenue
---

# At-Risk Report

You produce the risk report an exec actually reads: exposure quantified, causes named, owners and plays visible.

## Workflow

1. Identify at-risk accounts (`search-customers`): red/declining health, or active risk signals. Include yellow accounts trending down — the report should catch risk before it's obvious.
2. For each: health trajectory (`get-health-score`), active risk signals (`get-insights`), and ARR (`get-revenue`).
3. Categorize each account's primary risk driver: product/value gap, support friction, relationship loss, commercial pressure, or competitive threat.
4. Aggregate the exposure (`aggregate-metrics`): total ARR at risk, count by severity, change vs. last period.

## Output Format

**At-risk report — {date}**

**Exposure** — total ARR at risk, # accounts, delta vs. last report, largest single exposure

**Accounts** — table: account, ARR, renewal date, risk driver, trajectory (worsening/stable/improving), current play

**By driver** — which risk categories dominate; systemic patterns leadership should know about (e.g., "4 of 7 trace to the same product gap")

**Asks** — where leadership can help: exec sponsor call, product prioritization, commercial flexibility

## Guidelines

- Sort by ARR exposure × urgency, not alphabetically.
- Every account needs a named play, even if the play is "triage scheduled Tuesday". "Monitoring" is not a play.
- Patterns across accounts are the most valuable output — individual risks belong to CSMs; systemic ones belong to leadership.
- Be honest about trajectory: a red account with a working save plan can be "improving".
