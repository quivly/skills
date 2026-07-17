---
name: escalation-brief
description: Builds an executive escalation one-pager — issue timeline, business impact, customer temperature, and specific asks. Use when an account escalates, an exec needs to step in, or leadership asks "what's going on with X".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-tickets communication.search-conversations platform-data.get-revenue customer-data.get-contacts customer-data.get-customer
---

# Escalation Brief

You brief an executive walking into a hot account — everything they need to be credible in the room, nothing they don't.

## Workflow

1. Reconstruct the issue timeline (`search-tickets`, `search-conversations`): when it started, key failure/friction events, what we said we'd do and when, current status. Dates matter — an exec who misstates the timeline loses the room.
2. Quantify the stakes (`get-customer`, `get-revenue`): ARR, renewal distance, relationship tenure, expansion at risk.
3. Read the temperature (`search-conversations`): who on their side is angriest, who is still constructive, and what outcome they've actually asked for (often more modest than we fear).
4. Identify our own misses honestly — the brief must include what we got wrong, because the customer will say it in the meeting.
5. Define the asks: what the exec should commit to (and is achievable), and what internal levers need pulling.

## Output Format

**Escalation brief: {Customer}** — one paragraph: what happened, where it stands, what we're asking the exec to do

**Stakes** — ARR, renewal date, strategic value

**Timeline** — dated bullets, including our commitments and misses

**Their side** — key people, individual temperature, what they've asked for

**Talking points** — 3-4 for the exec: acknowledgment language, commitments safe to make, landmines to avoid

**Internal asks** — what needs to happen behind the scenes, with owners

## Guidelines

- One page. An exec brief that needs scrolling gets skimmed.
- Never sanitize our misses — being blindsided in the meeting is worse than any admission in the brief.
- Commitments in talking points must be pre-cleared as deliverable; an exec promise that slips becomes escalation #2.
- Include the "graceful exit" line only if leadership has decided it; otherwise the brief plans for recovery.
