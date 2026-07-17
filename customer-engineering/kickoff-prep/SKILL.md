---
name: kickoff-prep
description: Prepares the onboarding kickoff — agenda, stakeholder map, success criteria to confirm, and a proposed milestone plan. Use before a kickoff call with a new customer or when asked to "prep the kickoff for X".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer customer-data.get-contacts communication.search-calls communication.get-notes platform-data.search-opportunities
---

# Kickoff Prep

You design a kickoff that converts sales momentum into an onboarding plan with dates, owners, and a definition of "live".

## Workflow

1. Load the customer (`get-customer`) and contacts (`get-contacts`); identify who will attend vs. who *should* attend (exec sponsor present?).
2. Mine the sales cycle (`search-calls`) for stated goals, timeline pressure, and technical constraints mentioned pre-sale.
3. Check notes (`get-notes`) and the closed opportunity (`search-opportunities`) for scope: which products/tiers were bought, any services attached.
4. Draft the kickoff structure:
   - Confirm success criteria (bring the sales-cycle version; ask them to sharpen it into measurable outcomes)
   - Map roles: their implementation owner, our owner, escalation paths both ways
   - Propose milestones backward from their target date: technical setup → first value moment → team rollout → success review
   - Identify the fastest path to a first "aha" — the single workflow that proves value earliest

## Output Format

**Kickoff prep: {Customer}**

**Attendee map** — who's coming, who's missing, roles to confirm

**Draft agenda** — timed, 45-60 min, confirmation-oriented (they talk more than we present)

**Success criteria to validate** — from the sales cycle, phrased as questions

**Proposed milestone plan** — table: milestone, target date, owner, definition of done

**Risks going in** — missing stakeholders, unrealistic timelines, scope ambiguity

## Guidelines

- A kickoff that's a product demo is a failure — the product was sold already; the meeting sells the *plan*.
- Every milestone needs a customer-side owner. No customer owner = flag as top risk.
- Time-to-first-value is the metric that predicts everything downstream; design the plan around shortening it.
