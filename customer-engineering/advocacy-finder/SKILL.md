---
name: advocacy-finder
description: Identifies reference, case-study, and advocacy candidates — healthy, tenured accounts with strong outcomes and vocal fans. Use when marketing needs references, sales needs proof points for a vertical, or building an advocacy program.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.search-customers health.get-health-score communication.search-conversations platform-data.get-usage
---

# Advocacy Finder

You find the customers who already love us and match them to the advocacy ask they'd actually say yes to.

**Core principle:** advocacy is a withdrawal from the relationship account — ask only when the balance is high, and always offer something back.

## Workflow

1. Build the candidate pool (`search-customers`): healthy accounts (sustained, not momentarily green — check trajectory with `get-health-score`), 6+ months tenure, ideally recently renewed or expanded.
2. Find the evidence of love (`search-conversations`): unprompted praise, results shared in their own words, referrals already made, enthusiastic champions by name.
3. Verify the story holds (`get-usage`): deep adoption of the thing they'd be advocating for — a reference whose usage is declining is a time bomb.
4. Match candidate to ask (escalating commitment):
   - **Reference call** — lowest lift; happy champion is enough
   - **Quote / logo use** — needs their comms sign-off; flag enterprise brand-approval friction
   - **Case study** — needs a quantified outcome + a champion willing to invest hours
   - **Speaking / co-marketing** — needs an ambitious champion who benefits personally from the visibility
5. Note segment/vertical coverage: if the ask came from sales ("need a fintech reference"), filter accordingly.

## Output Format

**Advocacy candidates — {scope/vertical}**

**Top candidates** — table: account, champion, evidence of advocacy, story headline, best-fit ask, risk notes

**By ask type** — who fits reference calls vs. case studies vs. speaking

**Approach notes** — per top candidate: who asks (CSM vs. exec), framing, and what we offer back (visibility, roadmap access, community)

## Guidelines

- Advocacy is a withdrawal from the relationship account — only ask when the balance is high, and offer something back.
- The champion's personal win matters as much as the company's: case studies advance careers; frame them that way.
- Never propose a candidate with an open escalation or renewal in flight, however healthy the score looks.
- Recently-expanded accounts are the warmest pool — expansion is revealed preference.

**Related skills:** finding the recently-expanded pool → `expansion-scan`.
