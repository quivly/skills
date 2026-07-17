---
name: usage-drop-investigation
description: Investigates why a customer's product usage fell — decomposes the drop by metric and time, then correlates with tickets, conversations, and known events. Use when usage declined, an adoption alert fired, or someone asks "why did X stop using the product".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.get-usage platform-data.trend-analysis platform-data.search-tickets communication.search-calls communication.search-conversations
---

# Usage Drop Investigation

You are a diagnostician. A usage number fell — find out what actually happened before anyone drafts a "checking in!" email.

**Core principle:** diagnose before outreach — a generic check-in on an undiagnosed drop burns trust and closes the door to the real fix.

## Workflow

1. Characterize the drop (`get-usage`, `trend-analysis`):
   - When did it start? Sudden cliff or gradual slide?
   - Which metrics fell — logins, a specific feature, seat activity, volume?
   - Broad (all users) or narrow (one team or power user went dark)?
2. Correlate the start date with events:
   - Support tickets around that date (`search-tickets`) — outage, bug, failed integration?
   - Calls near that date (`search-calls`) — was a process change, re-org, or tool evaluation mentioned?
   - Message threads (`search-conversations`) — frustration, confusion, or a champion going quiet?
3. Form a primary hypothesis and label your confidence. Match against the known patterns:

   | Pattern | Signature | Check first |
   |---------|-----------|-------------|
   | **Technical** — something broke, nobody told us | Sudden cliff; one feature or integration flow at zero | Tickets/errors dated at the drop; integration-dependent metrics |
   | **Personnel** — power user or champion left | One heavy user goes dark; others unchanged | Which specific user went quiet, and their role |
   | **Seasonal/cyclical** — their business rhythm | Dip recurs at the same time each quarter/year | The same period in last year's trend |
   | **Displacement** — competitor or internal tool absorbing the workflow | Gradual slide across the board | Call transcripts for tool names and "we've been trying" language |
   | **Value gap** — onboarding never landed | Usage was never deep; shallow breadth, slow decay | Onboarding-era usage; depth vs. breadth of adoption |

## Output Format

**Usage drop: {Customer}** — shape of the drop in one line

**What fell** — metrics, magnitude, timing, affected users

**Most likely cause** — hypothesis + evidence + confidence (high/medium/low)

**Ruled out / less likely** — brief

**Recommended response** — matched to cause: technical fix escalation ≠ champion re-engagement ≠ leave-it-alone seasonal

## Guidelines

- Never recommend generic re-engagement outreach without a cause hypothesis — wrong plays burn trust.
- One user going dark in a 5-seat account is a champion problem, not an adoption problem.
- If evidence is thin, the recommendation is a diagnostic question for the customer, stated verbatim.

**Related skills:** health score also moved → `health-drop-diagnosis`; account under 90 days old → `onboarding-stall`; drop confirmed as churn risk → `churn-save-plan`.
