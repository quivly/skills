---
name: ticket-pulse
description: Reads a customer's support health — open ticket load, recurring themes, aging issues, and escalation candidates. Use when asked "how is support going for X", before meetings with support-sensitive accounts, or when ticket friction might explain churn risk.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-tickets communication.search-conversations customer-data.get-customer health.get-insights
---

# Ticket Pulse

You assess whether support experience is helping or hurting this customer relationship.

**Core principle:** volume is engagement; aging, repetition, and escalating severity are the risk.

## Workflow

1. Load the customer record (`get-customer`) for tier and context — a P1 for an enterprise account 30 days from renewal is different from the same ticket at a small account.
2. Pull tickets for the customer (`search-tickets`), last 90 days. Bucket them:
   - **Open & aging** — unresolved past a reasonable SLA
   - **Recurring themes** — same feature or failure appearing repeatedly
   - **Severity pattern** — are issues getting more serious over time?
3. Check surrounding conversations (`search-conversations`) for frustration that never became a ticket — often the loudest signal.
4. Check signals on record (`get-insights`) for support-related risk already flagged.

## Output Format

**Support pulse: {Customer}** — one-line verdict: Healthy / Friction building / Escalation needed

**The numbers** — open count, oldest unresolved, volume trend vs. prior period

**Themes** — recurring issues grouped, each with occurrence count and current status

**Sentiment check** — what the customer's tone says beyond the tickets

**Recommended actions** — e.g., escalate ticket X to product, proactive check-in on theme Y, close-the-loop message on resolved-but-unacknowledged items

## Guidelines

- Volume alone isn't a red flag — an engaged customer files tickets. Aging, repetition, and severity escalation are the red flags.
- Distinguish "customer is blocked" from "customer is annoyed" — different plays.
- If there are zero tickets and low usage, flag disengagement, not health.

**Related skills:** friction has boiled over → `escalation-brief`; support friction is driving churn risk → `churn-save-plan`.
