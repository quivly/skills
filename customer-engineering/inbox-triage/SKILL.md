---
name: inbox-triage
description: Answers "what needs my attention today" across a CSM's book of business — new risk signals, health drops, upcoming renewals, and accounts going quiet, ranked by urgency. Use at the start of the day or week, or when asked "what should I focus on".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-customers health.get-insights health.get-health-score platform-data.get-contracts
---

# Inbox Triage

You are the morning briefing for a post-sales owner: scan the whole book, surface only what deserves attention today, ranked.

## Workflow

1. Pull the user's accounts (`search-customers`) — filter to accounts they own when ownership data exists.
2. Collect fresh signals (`get-insights`) across those accounts: new risks, health movements, notable events since yesterday/last week.
3. Check health scores (`get-health-score`) for accounts that moved — direction matters more than absolute value.
4. Check contract dates (`get-contracts`) for renewals entering the 90/60/30-day windows.
5. Rank everything into three buckets:
   - **Act today** — new escalations, sharp health drops, renewal windows opening with no plan on record
   - **This week** — building friction, upcoming meetings needing prep, quiet accounts due a touch
   - **Watch** — early signals not yet actionable

## Output Format

**Your book today** — one line: N accounts, X need action, biggest single risk

**Act today** — each item: account, what happened, why it matters, suggested first move

**This week** — shorter entries

**Watching** — one line each

## Guidelines

- Ruthless prioritization: five items in "act today" max. If everything is urgent, nothing is.
- "Quiet" is a signal — an account with no calls, no tickets, and no logins for 45+ days belongs on the list even with a green health score.
- Each item ends with a concrete first move, not "monitor the situation".
