---
name: template-skill
description: A minimal starting template for a new Quivly skill. Replace this description with a clear explanation of what the skill does and when an agent should activate it.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or in Claude Code / claude.ai / any MCP-enabled agent via the Quivly MCP connector. Without tools, the skill degrades to a guided manual workflow.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer communication.search-calls
---

# Template Skill

Replace this with the actual skill name.

## When to Use This Skill

Describe the situations, keywords, or customer scenarios that should trigger this skill. Be specific — this text is used by agents for discovery.

Good descriptions mention:
- The core task (e.g., "run a customer health review")
- Trigger signals ("when the user mentions churn risk, health score, or QBR")
- The outcome the agent should deliver

## Instructions

Provide clear, step-by-step guidance the agent should follow. Reference tools by their short capability name so any runtime can map them:

1. Load the customer record (`get-customer`) and capture ARR, tier, and owner.
2. Search recent calls (`search-calls`) for commitments and open questions.
3. ...

## Tool Bindings

Two layers keep skills portable:

- **The body** (above) references tools by capability — "load the customer record (`get-customer`)". Any runtime with equivalent tools can execute it; agents without tools fall back to asking the user for the data.
- **`metadata.quivly-tools`** is a space-separated list of exact Quivly tool-catalog IDs. Quivly's GitHub import reads this to attach tools automatically. Other platforms ignore it per the Agent Skills spec.

In Claude Code / claude.ai, connect the [Quivly MCP connector](https://quivly.ai) — its tool names map 1:1 to the short names used in skill bodies.

## Examples

### Example 1
**Input:** ...
**Expected behavior:** ...

## Guidelines & Best Practices

- Key constraint or rule
- Common pitfalls to avoid
- Flag gaps where data is missing rather than guessing.

## References

Prefer a single self-contained SKILL.md — Quivly's importer only ingests the SKILL.md file. Use `references/` only for material that is genuinely optional.
