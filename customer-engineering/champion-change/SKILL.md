---
name: champion-change
description: Responds to a champion or sponsor departure — maps the remaining relationship surface, assesses exposure, and builds a re-entry plan for the new stakeholder. Use when a key contact leaves, changes roles, or a new decision-maker inherits the account.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-contacts communication.search-conversations communication.search-calls customer-data.get-customer
---

# Champion Change Response

Executive and champion turnover is one of the top churn causes in B2B. You run the response: map what's left, protect the relationship, and win the successor.

**Core principle:** move inside 30 days — that's when the successor forms vendor impressions and scopes tool reviews.

## Workflow

1. Confirm the change and its shape (`get-contacts`, `search-conversations`): who left/moved, what they owned (budget? daily usage? political air cover?), and who inherits.
2. Map the remaining relationship surface (`get-contacts`, `search-calls`): who else knows us, likes us, and has influence. Rate the exposure:
   - **Cushioned** — multi-threaded; other engaged stakeholders can carry the story
   - **Exposed** — the departed champion was the main thread
   - **Critical** — single-threaded AND renewal inside 6 months
3. Reconstruct the value story the champion carried (`search-calls`, `search-conversations`) — the successor inherits a line item, not the context. Collect the wins, metrics, and history that justify us.
4. Build the two-track plan:
   - **Successor track** — early intro meeting framed as "here's what your team achieves with us" (business outcomes, not product tour); learn *their* priorities; expect and prepare for a tool review
   - **Departed-champion track** — stay warm; where they land, they're a future deal

## Output Format

**Champion change: {Customer}** — who changed, exposure rating, renewal distance

**Remaining relationship map** — who we still have, strength of each thread

**Value story to transfer** — the 3-5 proof points the successor must hear early

**Two-track plan** — successor plays with dates; departed-champion follow-up

**Risk note** — if exposure is Critical, the explicit escalation ask (exec sponsor intro, priority handling)

## Guidelines

- Move fast: the first 30 days of a new stakeholder are when vendor impressions form and reviews get scoped.
- Never open with "let me show you the product" — open with what their team accomplishes with it.
- A new exec often brings their preferred stack; assume a competitive review is coming and pre-empt it with outcomes evidence.
- Log the departed champion's destination — champion tracking is a pipeline source.

**Related skills:** renewal inside 6 months → `renewal-risk`; briefing for the successor intro → `account-360`.
