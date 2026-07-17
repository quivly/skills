# Contributing to Quivly Skills

Thank you for helping improve skills for Customer Engineering and post-sales teams.

## Skill Requirements

All skills **must** follow the [Agent Skills specification](https://agentskills.io/specification).

- Every skill folder must contain a `SKILL.md` starting with valid YAML frontmatter.
- Required fields: `name` (lowercase, hyphenated, matches folder name) and `description`.
- Recommended: `license: MIT`
- **Prefer a single self-contained `SKILL.md`.** Quivly's GitHub import ingests only the `SKILL.md` file, so skills that depend on `references/` or `scripts/` lose content on import. Use supporting files only for genuinely optional material.

## Tool Bindings

Skills in this repo separate two layers so the same file works on every platform:

- **In the body**, reference tools by capability name with the short tool name in parentheses — "load the customer record (`get-customer`)". Agents with equivalent tools (Quivly native, or the Quivly MCP connector elsewhere) resolve them; agents without tools fall back to asking the user for the data.
- **In frontmatter**, declare exact Quivly tool-catalog IDs as a space-separated string under `metadata.quivly-tools`. Quivly reads this on import; other platforms ignore it per the Agent Skills spec (metadata values must be strings — don't use nested lists).

```yaml
metadata:
  author: your-handle
  version: "1.0"
  category: customer-engineering
  quivly-tools: customer-data.get-customer communication.search-calls
```

## House Conventions

Match the structure of existing skills:

- **Core principle** — one bold, memorable hard rule right after the intro line. The single sentence you'd want the agent to remember if it forgets everything else.
- **Workflow → Output Format → Guidelines** — ordered steps, then the exact output contract, then judgment rules.
- **Stop conditions / Self-check** — optional sections; add them only where the skill has a genuine halt condition or a characteristic mid-task mistake. Don't force them.
- **Related skills** — a one-line footer routing to sibling skills (`escalates to`, `follows`, `feeds into`). This is what makes the catalog compose into workflows.

## Writing Great Skills

The `description` field is critical. Agents use it to decide whether to load the skill.

**Good:**
> Runs a structured customer health review using usage data, support tickets, and renewal signals. Use when the user asks about customer health, churn risk, or health scoring.

**Bad:**
> Helps with customers.

## Process

1. Fork or branch from main.
2. Create your skill in an appropriate category (or propose a new one).
3. Test it in at least one Agent Skills-compatible client.
4. Submit a PR with:
   - Clear description of the use case
   - Example prompts that activate the skill
   - Any limitations

## Style

- Use professional but practical language.
- Include concrete examples from real customer engineering work.
- Prefer progressive disclosure: put detailed reference material in separate files.

## Questions?

Open an issue or reach out via Quivly channels.
