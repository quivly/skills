<p align="center">
  <img src="assets/banner.png" alt="Quivly Skills" width="100%">
</p>

# Quivly Skills

**Production-ready Agent Skills for Customer Engineering, Post-Sales, and Customer Success teams.**

Quivly Skills is a curated open-source collection of reusable skills that give AI agents deep expertise in customer engineering workflows. Every skill follows the official [Agent Skills specification](https://agentskills.io/specification).

**Topics:** `agent-skills` `ai-agents` `customer-success` `post-sales` `customer-engineering` `anthropic` `claude` `skills` `ai-workflows`

## About

This repository provides production-ready skills focused on real customer engineering and post-sales use cases, including health reviews, expansion playbooks, churn risk detection, QBR preparation, and technical workflows.

## Why Quivly Skills?

Customer engineering and post-sales work involves repeatable but high-context processes: health reviews, expansion planning, churn mitigation, technical onboarding, QBR preparation, and more. 

Quivly Skills turn that expertise into portable, version-controlled skills that any Agent Skills-compatible agent can discover and use.

- **Follows the open standard** — Compatible with the [Agent Skills specification](https://agentskills.io/specification) (originally from Anthropic, now widely adopted).
- **Designed for real teams** — Built from patterns that work at scale in B2B post-sales and customer engineering organizations.
- **Progressive disclosure** — Agents load just the metadata first, then full instructions only when needed.
- **Composable** — Use individual skills or combine them for complex workflows.

## Quick Start

### Using in Claude Code

```bash
/plugin marketplace add quivly/skills
```

Then install skill sets or individual skills.

### Manual use (any compatible agent)

1. Clone or copy the skill directory you need.
2. Place it in your agent's skills folder (exact location depends on the client).
3. The agent will discover the skill via its `name` and `description`.

See the [Agent Skills documentation](https://agentskills.io) for client-specific instructions.

## Repository Structure

```
├── customer-engineering/  # 21 skills: account intelligence, meeting prep,
│                          # health & risk, renewals, escalations, growth
└── template/              # Starter template for new skills
```

Each skill is a self-contained folder with a `SKILL.md` file.

## Skill Catalog

21 production-ready Agent Skills for customer success, customer engineering, and post-sales AI workflows — meeting prep, QBR preparation, churn risk, renewal forecasting, onboarding, escalations, and expansion. Organized by how often teams reach for them.

| Skill | What it does | Tier |
|-------|--------------|------|
| [meeting-prep](customer-engineering/meeting-prep/SKILL.md) | Pre-call brief for any customer meeting: recent conversations, open tickets, usage changes, suggested talking points | Daily |
| [account-360](customer-engineering/account-360/SKILL.md) | Full account snapshot on demand: profile, health, revenue, stakeholders, risks | Daily |
| [post-call-followup](customer-engineering/post-call-followup/SKILL.md) | Turn the latest call into owned action items, commitments, and a draft recap message | Daily |
| [ticket-pulse](customer-engineering/ticket-pulse/SKILL.md) | Support health read: aging tickets, recurring themes, escalation candidates | Daily |
| [inbox-triage](customer-engineering/inbox-triage/SKILL.md) | "What needs my attention today" across a book of business, ranked by urgency | Daily |
| [portfolio-digest](customer-engineering/portfolio-digest/SKILL.md) | Weekly book-of-business review: health movers, usage droppers, renewals inside 90 days | Weekly |
| [usage-drop-investigation](customer-engineering/usage-drop-investigation/SKILL.md) | Diagnose why product usage fell — pattern-matched root cause before any outreach | Weekly |
| [health-drop-diagnosis](customer-engineering/health-drop-diagnosis/SKILL.md) | Decompose a health score drop into moving components and the real-world events behind them | Weekly |
| [at-risk-report](customer-engineering/at-risk-report/SKILL.md) | Leadership roll-up of at-risk accounts: ARR exposure, risk drivers, named plays | Weekly |
| [renewal-forecast](customer-engineering/renewal-forecast/SKILL.md) | Next quarter's renewals with per-account confidence categories and reasoning | Weekly |
| [sales-handoff](customer-engineering/sales-handoff/SKILL.md) | Deal-close handoff brief: deal context, contacts, AE commitments, first-touch agenda | Lifecycle |
| [kickoff-prep](customer-engineering/kickoff-prep/SKILL.md) | Onboarding kickoff design: agenda, stakeholder map, milestone plan, success criteria | Lifecycle |
| [onboarding-stall](customer-engineering/onboarding-stall/SKILL.md) | Time-to-value check for new accounts — locate exactly where onboarding is stuck | Lifecycle |
| [renewal-risk](customer-engineering/renewal-risk/SKILL.md) | 60–90 day renewal read across value, usage, relationship, and commercial posture | Lifecycle |
| [churn-save-plan](customer-engineering/churn-save-plan/SKILL.md) | Root-caused save plan for a red account, with stop conditions and a tripwire | Lifecycle |
| [champion-change](customer-engineering/champion-change/SKILL.md) | Respond to a champion or sponsor departure: exposure map, value-story transfer, successor plan | Lifecycle |
| [escalation-brief](customer-engineering/escalation-brief/SKILL.md) | Executive escalation one-pager: timeline, stakes, temperature, talking points | Lifecycle |
| [customer-health-review](customer-engineering/customer-health-review/SKILL.md) | Full structured customer health review with scoring dimensions and action plan | Lifecycle |
| [qbr-prep](customer-engineering/qbr-prep/SKILL.md) | QBR / EBR preparation: value story with evidence, honest gaps, forward plan, renewal positioning | Quarterly |
| [expansion-scan](customer-engineering/expansion-scan/SKILL.md) | Upsell and cross-sell signals: usage pressure, whitespace, buying language in calls | Quarterly |
| [advocacy-finder](customer-engineering/advocacy-finder/SKILL.md) | Reference and case-study candidates matched to the advocacy ask they'd say yes to | Quarterly |

Skills cross-reference each other via a **Related skills** footer (e.g. a health drop routes to `health-drop-diagnosis`, which escalates to `churn-save-plan`), so they compose into full workflows.

## How tool compatibility works

Every skill separates two layers so the same file runs everywhere:

- **The body** references tools by capability name — "load the customer record (`get-customer`)". Any agent with equivalent tools executes it; agents without tools fall back to asking the user for the data.
- **`metadata.quivly-tools`** carries exact Quivly tool-catalog IDs (space-separated). Importing the repo into Quivly attaches the right tools automatically. Other platforms ignore this key, per the Agent Skills spec.

To run these skills in **Claude Code, claude.ai, or any MCP-enabled agent**, connect the [Quivly MCP connector](https://quivly.ai) — its tool names map 1:1 to the capability names used in skill bodies.

## Creating a New Skill

Use the template:

```bash
cp -r template/my-new-skill ./category/my-new-skill
```

Edit `SKILL.md`:

```markdown
---
name: my-new-skill
description: Clear description of what this skill does and when an agent should use it. Include trigger keywords.
license: MIT
compatibility: Tool calls resolve natively in Quivly, or via the Quivly MCP connector in any MCP-enabled agent.
metadata:
  author: quivly
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer communication.search-calls
---

# My New Skill

## When to Use
...

## Steps
1. ...
```

See the full [specification](https://agentskills.io/specification) for all supported frontmatter fields.

## Contributing

We welcome contributions from Customer Engineering and post-sales practitioners.

1. Follow the Agent Skills format strictly.
2. Write excellent `description` fields — this is how agents decide when to activate the skill.
3. Keep `SKILL.md` focused. Move detailed references to `references/`.
4. Test the skill with at least one compatible agent.
5. Open a PR with a clear description of the use case.

Please read the skills in this repo for style and structure examples.

## License

This repository is licensed under the [MIT License](LICENSE).

Individual skills declare their license in the `license` field of `SKILL.md` (per the Agent Skills spec).

---

Built with ❤️ by the team at [Quivly](https://quivly.ai) — the AI workforce for post-sales.
