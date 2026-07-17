---
name: health-drop-diagnosis
description: Explains a health score drop — decomposes which score components moved, finds the triggering events, and recommends a proportionate response. Use when a health score fell, a risk alert fired, or someone asks "why did X's health drop".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: health.get-health-score health.get-insights platform-data.get-usage platform-data.search-tickets communication.search-conversations
---

# Health Drop Diagnosis

You explain a health score movement in plain language: which inputs moved, what real-world events drove them, and how worried to be.

**Core principle:** a health score is a smoke detector, not a diagnosis — never recommend action from the score alone; trace it to real events first.

## Workflow

1. Get the current health score with its component breakdown (`get-health-score`). Identify which components dropped and by how much — the composite hides the story.
2. For each falling component, find the underlying event:
   - Usage component → pull usage detail (`get-usage`)
   - Support component → recent tickets (`search-tickets`)
   - Engagement component → conversation recency and tone (`search-conversations`)
3. Check signals on record (`get-insights`) for events the score may lag: champion departure, funding news, org changes.
4. Judge severity honestly:
   - **Mechanical** — one input crossed a threshold, no real-world change (e.g., a holiday week tanked logins)
   - **Early warning** — real deterioration, early stage, recoverable
   - **Confirmed risk** — multiple components falling together with corroborating events

## Output Format

**Health drop: {Customer}** — score before → after, severity verdict

**What moved** — component-by-component, each mapped to its real-world cause

**The story** — 2-3 sentences of narrative: what is actually happening at this account

**Response** — proportionate to severity: nothing (mechanical), targeted play (early warning), or escalate to save-plan mode (confirmed)

## Guidelines

- A score is a smoke detector, not a diagnosis — always trace to real events before recommending action.
- Call out mechanical drops confidently; false alarms erode trust in the whole scoring system.
- If severity is "confirmed risk", recommend running a churn save plan rather than duplicating one here.

**Related skills:** usage component is the driver → `usage-drop-investigation`; confirmed risk → `churn-save-plan`; full structured review → `customer-health-review`.
