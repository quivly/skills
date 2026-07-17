---
name: qbr-prep
description: Prepares a QBR or EBR — value delivered with evidence, usage narrative, health posture, roadmap of asks, and renewal positioning. Use before any quarterly or executive business review, or when asked to "build the QBR for X".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.get-usage platform-data.trend-analysis platform-data.get-revenue health.get-health-score communication.search-calls platform-data.get-contracts
---

# QBR Prep

You build the content for a business review that earns its meeting slot: value proven with their numbers, honest gaps, and a forward plan worth an executive's time.

**Core principle:** usage is evidence; outcomes are the story — a QBR that reads as a usage report wastes an executive hour.

## Workflow

1. Establish the baseline: what success criteria were set at kickoff or the last QBR (`search-calls`, review prior QBR notes). The QBR's spine is "you said X mattered — here's where X stands".
2. Build the value story (`get-usage`, `trend-analysis`): quarter-over-quarter usage narrative, adoption milestones hit, workflows now running through the product. Convert usage into outcome language wherever possible (time saved, revenue influenced, risk reduced).
3. Be honest about gaps: under-adopted capabilities they're paying for, stalled initiatives, unresolved asks from last quarter. Bring each with a proposed fix.
4. Check commercial posture (`get-contracts`, `get-revenue`, `get-health-score`): renewal distance, growth precedent, health — this calibrates how forward the renewal/expansion conversation should be.
5. Draft the forward plan: next quarter's priorities *in their language*, our asks of them (stakeholder time, data access, rollout support), and any expansion motion that genuinely serves their goals.

## Output Format

**QBR: {Customer} — {quarter}**

**Executive summary slide** — 3 bullets: value headline, health headline, next-quarter headline

**Value delivered** — success criteria vs. actuals, with numbers and trend charts to pull

**Honest gaps** — each with a proposed fix and owner

**Next quarter plan** — priorities, milestones, mutual commitments

**Renewal/expansion positioning** — how forward to be, and the specific motion if any

**Meeting design notes** — who must attend, 2-3 discovery questions to ask live, topics to pre-wire before the room

## Guidelines

- A QBR that reads as a usage report wastes an exec meeting; usage is evidence, outcomes are the story.
- Bring last QBR's commitments and score ourselves publicly — credibility compounds.
- If value evidence is thin, the QBR's honest job is realignment, not celebration — say so in the prep.
- Pre-wire anything surprising; the QBR room is for alignment, not ambushes.

## Self-check

- The draft is mostly activity charts → you're building a usage report; restructure around the customer's stated success criteria.
- You can't name last QBR's commitments → find them before drafting; scoring ourselves publicly is the credibility play.

**Related skills:** renewal posture detail → `renewal-risk`; the expansion motion → `expansion-scan`.
