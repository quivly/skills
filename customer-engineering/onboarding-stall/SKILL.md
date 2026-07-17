---
name: onboarding-stall
description: Checks whether a new customer is adopting on schedule and diagnoses where onboarding is stuck — setup incomplete, usage shallow, engagement fading. Use for accounts in their first 90 days, time-to-value reviews, or when an onboarding feels quiet.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: platform-data.get-usage communication.search-conversations communication.get-notes customer-data.get-customer
---

# Onboarding Stall Check

You detect onboarding drift early — the quiet weeks where a new account slides from "excited" to "we never really rolled it out".

**Core principle:** silence is the loudest stall signal — a quiet onboarding is further gone than a complaining one.

## Workflow

1. Load the customer (`get-customer`) — start date, expected go-live, seats purchased.
2. Read usage against the onboarding clock (`get-usage`):
   - **Activation** — is the technical setup actually done (integrations connected, data flowing)?
   - **Breadth** — active users vs. seats purchased
   - **Depth** — core workflow adoption vs. login-and-look-around
3. Check engagement temperature (`search-conversations`): response latency trend, meeting attendance, tone shift from proactive to polite.
4. Check notes (`get-notes`) for known blockers already logged.
5. Locate the stall stage (each has a different fix):
   - **Setup stall** — technical blocker or IT dependency → escalate/unblock, don't nudge
   - **Rollout stall** — setup done, team never onboarded → champion enablement, internal launch help
   - **Value stall** — people log in but the core workflow isn't landing → use-case coaching, success re-alignment
   - **Sponsor stall** — the project lost its internal priority → exec-to-exec re-engagement

## Output Format

**Onboarding check: {Customer}** — day N of onboarding, verdict: On track / Drifting / Stalled

**The clock** — key milestones vs. actual, days since last meaningful engagement

**Where it's stuck** — stage + evidence

**Recommended intervention** — matched to stage, with a concrete first step and owner

## Guidelines

- Silence is the loudest stall signal — a customer who stops responding is further gone than one complaining.
- Never send a generic "how's it going" to a stalled onboarding; name the specific blocked step and offer the specific fix.
- If onboarding is on track, say so plainly and set the next checkpoint — no invented problems.

**Related skills:** the kickoff itself → `kickoff-prep`; stall has hardened into churn risk → `churn-save-plan`.
