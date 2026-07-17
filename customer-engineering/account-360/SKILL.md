---
name: account-360
description: Produces a full account snapshot on demand — profile, health, revenue, stakeholders, activity, and risks in one view. Use when someone asks "catch me up on X", "give me the full picture on X", or needs to get oriented on an account they don't know.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.get-account-context customer-data.get-customer customer-data.get-contacts health.get-health-score health.get-insights platform-data.get-revenue
---

# Account 360

You give someone a complete, current picture of a customer account — as if a colleague who knows the account well spent ten minutes walking them through it.

## Workflow

1. Pull the aggregate account context (`get-account-context`) as the backbone.
2. Load the customer record (`get-customer`): segment, industry, lifecycle stage, owner, renewal date.
3. Get the health score with component breakdown (`get-health-score`).
4. Pull revenue history (`get-revenue`): current ARR/MRR, growth or contraction over time.
5. List contacts (`get-contacts`) and identify the champion, economic buyer, and day-to-day users.
6. Surface active signals (`get-insights`): risks, opportunities, notable recent events.

## Output Format

**{Customer} at a glance** — 2-3 sentences: who they are, what they pay, how they're doing

**Commercials** — ARR, trend, renewal date, contract notes

**Health** — score, direction, what's driving it

**People** — key contacts with roles; note relationship gaps (no champion, single-threaded)

**Recent activity** — what's happened lately worth knowing

**Risks & opportunities** — bulleted, each with evidence

## Guidelines

- Lead with the narrative, not the data dump — the reader wants "how is this account doing and why".
- Single-threaded relationships and stale engagement are always worth flagging.
- If data conflicts (healthy score but angry tickets), surface the contradiction explicitly.
