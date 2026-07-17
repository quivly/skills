---
name: post-call-followup
description: Turns the most recent customer call into structured follow-up — action items with owners, commitments made, risks heard, and a draft recap message. Use after a customer call ends, or when the user says "summarize my call with X" or "draft the follow-up for X".
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: communication.get-call-summary communication.get-call-transcript communication.get-notes customer-data.get-contacts
---

# Post-Call Follow-up

You convert a customer call into follow-through: clear actions, honest risk notes, and a recap the CSM can send with light editing.

**Core principle:** a follow-up item that isn't verb-first, owned, and dated isn't a follow-up — it's a wish.

## Workflow

1. Get the call summary (`get-call-summary`) for the most recent call with the customer. When nuance matters — exact wording of a commitment, tone on a sensitive topic — go to the transcript (`get-call-transcript`).
2. Cross-check attendees against known contacts (`get-contacts`) — note any new stakeholders who appeared.
3. Check recent notes (`get-notes`) so follow-ups don't duplicate work already in motion.
4. Extract, in order of importance:
   - Action items — ours and theirs, each with an owner and a suggested due date
   - Commitments made (exact language if the stakes are high)
   - Risks or friction heard, even if implicit (hesitation about renewal, mention of a competitor, budget language)
   - New information about goals, org changes, or timeline

## Output Format

**Call recap: {Customer} — {date}**

**Action items** — table: item, owner, due

**Commitments** — what we promised, what they promised

**Signals worth logging** — risks, expansion hints, stakeholder changes

**Draft follow-up message** — short, warm, specific; confirms actions and next step. Write it in the first person for the CSM to send.

## Guidelines

- Action items must be verb-first and assignable — "Send SSO setup guide (us, Friday)", not "discuss SSO".
- Don't soften risks in the recap-for-internal-use section; do keep the customer-facing draft positive and concrete.
- If the call was a negative one (escalation, complaint), lead the draft message with acknowledgment, not agenda.

**Related skills:** a new stakeholder appeared on the call → `champion-change`; prepping the next touch → `meeting-prep`.
