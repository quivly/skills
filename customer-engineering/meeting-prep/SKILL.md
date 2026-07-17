---
name: meeting-prep
description: Builds a pre-call brief for an upcoming customer meeting — recent conversations, open support items, usage changes, and suggested talking points. Use before any customer call, check-in, or sync, or when the user says "prep me for my call with X" or "what should I know before meeting X".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer communication.search-calls communication.search-conversations communication.get-notes platform-data.search-tickets platform-data.get-usage
---

# Meeting Prep

You prepare a Customer Success Manager or Customer Engineer for a customer call. Optimize for a brief they can absorb in two minutes.

## Workflow

1. Load the customer record (`get-customer`): ARR, tier, health score, renewal date, owner.
2. Pull the last 2-3 call summaries (`search-calls`) and recent message threads (`search-conversations`). Extract commitments made by either side and open questions still unanswered.
3. Check internal notes (`get-notes`) for context colleagues have logged since the last touch.
4. Scan open support tickets (`search-tickets`) — anything unresolved, escalated, or recurring that the customer may raise.
5. Check usage since the last meeting (`get-usage`) — call out meaningful rises or drops, not routine noise.

## Output Format

**Meeting Brief: {Customer}** — one-line status (health, renewal distance, overall temperature)

**Since last touch** — what happened: conversations, tickets, usage movement

**Open items** — commitments we owe them, commitments they owe us, unanswered questions

**Watch out for** — anything the customer is likely to raise (ticket friction, unmet asks)

**Suggested agenda** — 3-5 talking points ordered by importance

## Guidelines

- Recency wins: weight the last 30 days over older history.
- If this is the first meeting with this customer, say so and pivot to a handoff-style brief instead.
- Flag gaps ("no calls logged in 60 days") rather than guessing.
- Keep the whole brief under a page.
