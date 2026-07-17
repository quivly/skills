---
name: expansion-scan
description: Scans an account or a whole book for expansion signals — usage nearing plan limits, new teams appearing, whitespace against products owned, and buying signals in conversations. Use for expansion planning, pipeline generation from the install base, or "where's the upsell in my book".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.get-usage platform-data.get-billing-subscription platform-data.search-opportunities communication.search-calls platform-data.trend-analysis
---

# Expansion Scan

You find expansion that is already happening and merely needs recognizing — usage pressure, new teams, unowned products solving problems they've mentioned.

**Core principle:** expansion is only credible from a healthy base — fix first, grow second.

## Workflow

1. Scope: one account if named, otherwise the user's book.
2. Usage pressure (`get-usage`, `trend-analysis`): seats near capacity, volume limits approaching, usage growth outpacing plan. This is the highest-conversion signal that exists.
3. Whitespace (`get-billing-subscription`): products/tiers not owned, mapped against problems they've voiced.
4. Conversational signals (`search-calls`): new team names appearing on calls, "can it also do X" questions, mentions of adjacent workflows handled by spreadsheets or competitors.
5. Check for existing open expansion opportunities (`search-opportunities`) — don't duplicate what sales is already working.
6. Qualify each signal: expansion advice is only credible from a healthy base — note current health and any open friction next to every signal.

## Output Format

**Expansion scan: {scope}**

**Ready now** — signals with evidence + suggested motion + rough sizing; each marked with account health

**Developing** — real but early; what would ripen them

**Whitespace map** — product/tier not owned → the stated problem it solves → source quote or event

**Cautions** — accounts where expansion talk would land badly right now (open escalation, renewal at risk)

## Guidelines

- Expansion signals from an unhealthy account go in Cautions, not Ready — fix first, grow second.
- The best expansion pitch quotes the customer to themselves: "you mentioned X on the March call — this is that."
- Usage-pressure expansions are a service ("you're about to hit a limit"), not a sale — frame them that way.
- Always hand off cleanly if an opportunity already exists in the pipeline.

**Related skills:** attach to a renewal → `renewal-forecast`; deliver through the business review → `qbr-prep`.
