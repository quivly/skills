---
name: churn-save-plan
description: Deep-dives a red account and produces a structured save plan — root causes ranked, save plays matched to causes, and a realistic assessment of whether the account is savable. Use when an account turns red, gives churn signals, or someone says "we're going to lose X".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: health.get-health-score health.get-insights platform-data.search-tickets communication.search-calls platform-data.get-usage customer-data.get-contacts
---

# Churn Save Plan

You build the save plan for an account in real danger — honest about root causes, honest about odds, specific about plays.

## Workflow

1. Establish the full risk picture: health components (`get-health-score`), active signals (`get-insights`), ticket history (`search-tickets`), usage trend (`get-usage`), recent call tone (`search-calls`), relationship map (`get-contacts`).
2. Identify root causes — usually 1-2 dominate. Rank them:
   - **Value gap** — never reached the outcome they bought for
   - **Product gap** — a needed capability doesn't exist or underperforms
   - **Trust damage** — support failures, missed commitments, outage scars
   - **Relationship loss** — champion gone, sponsor disengaged, single thread cut
   - **External** — budget cuts, M&A, strategy shift (least addressable by us)
3. Assess savability honestly: is there time before the notice deadline, an engaged human on their side, and a cause we can actually fix?
4. Build the plan: each play matched to a root cause, with owner, deadline, and a "proof point" — the observable event that tells us it's working.

## Output Format

**Save plan: {Customer}** — ARR, renewal/notice date, savability: Good odds / Uphill / Long shot

**Root causes** — ranked, each with evidence

**The plan** — table: play, targets which cause, owner, deadline, proof point

**Ask list** — internal help needed: exec sponsor, product commitment, commercial flexibility

**Tripwire** — the date/event at which we stop investing in the save and shift to graceful-exit + win-back planning

## Guidelines

- One play per root cause beats five generic plays. Discounts don't fix value gaps.
- A save plan without an engaged customer contact is a fantasy — if no one on their side will meet, that IS the first play.
- Set the tripwire on day one. Zombie save plans consume the team's best hours.
- "Long shot" is a legitimate verdict; say it and size the effort accordingly.
