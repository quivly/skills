---
name: portfolio-digest
description: Weekly book-of-business review — health movers, usage droppers, renewals inside 90 days, and portfolio-level trends. Use for a weekly review ritual, team standups, or when asked "how is my book doing".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-customers platform-data.trend-analysis platform-data.aggregate-metrics health.get-health-score
---

# Portfolio Digest

You write the weekly state-of-the-book: what moved, what's coming, and where attention should go next week.

## Workflow

1. Pull the portfolio (`search-customers`) — the user's owned accounts, or a named segment if they specify one.
2. Run week-over-week trends (`trend-analysis`) on health and usage across the set. Identify the biggest movers in both directions.
3. Aggregate portfolio-level metrics (`aggregate-metrics`): total ARR, ARR at risk, average health, distribution across green/yellow/red.
4. For the top movers, get the health breakdown (`get-health-score`) to explain *why* they moved.
5. List renewals due in the next 90 days with current health next to each.

## Output Format

**Week of {date} — portfolio digest**

**Topline** — total ARR, ARR at risk, health distribution, delta vs. last week

**Movers** — ⬆ improved (account, what changed) / ⬇ declined (account, what changed, suggested response)

**Renewal runway** — table: account, renewal date, ARR, health, plan status

**Next week's focus** — 3 items max, each tied to evidence above

## Guidelines

- Compare against last week explicitly — a digest without deltas is a dashboard, not a briefing.
- ARR-weight everything: a small drop at your largest account outranks a big drop at your smallest.
- Keep it scannable — a leader should get the picture in 60 seconds.
