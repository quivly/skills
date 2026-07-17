---
name: sales-handoff
description: Compiles a sales-to-CS handoff brief when a deal closes — deal context, contacts and roles, commitments made during the sales cycle, and a recommended first-touch agenda. Use when a deal closes, a new customer lands, or a CSM is preparing for their first touch on an account.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer customer-data.get-contacts communication.get-call-summary communication.search-calls health.get-insights
---

# Sales Handoff Brief

You compile everything a CSM needs before their first touch on a newly closed account — so the customer never has to repeat what they already told sales.

## Workflow

1. Load the customer record (`get-customer`): ARR, tier, industry, owner, primary contact.
2. List all known contacts (`get-contacts`). Identify the economic buyer, the champion, and everyone who engaged during the sales cycle.
3. Pull the last 2-3 sales call summaries (`search-calls`, `get-call-summary`). Extract:
   - Success criteria the customer stated — in their words where possible
   - Pain points that drove the purchase
   - Commitments made by the AE (features, timelines, pricing, services)
   - Objections raised and how they were resolved
4. Check signals on record (`get-insights`) for anything notable already flagged.

## Output Format

**Handoff brief: {Customer}**

**Snapshot** — ARR, segment, industry, close date, contract term

**Why they bought** — pain, success criteria, decision drivers

**People** — table: name, role, sales-cycle involvement, notes

**Commitments & landmines** — what was promised, what was contentious, what to never re-litigate

**First-touch agenda** — recommended kickoff structure that shows continuity ("you told our team X — here's how we start delivering it")

## Guidelines

- The cardinal sin of handoff is making the customer repeat themselves — quote the sales cycle back to them.
- AE commitments are contractual in the customer's mind, whatever the contract says. List every one.
- Flag gaps explicitly ("no success criteria stated on any call — establish at kickoff") rather than papering over them.
