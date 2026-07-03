# Contributing to Quivly Skills

Thank you for helping improve skills for Customer Engineering and post-sales teams.

## Skill Requirements

All skills **must** follow the [Agent Skills specification](https://agentskills.io/specification).

- Every skill folder must contain a `SKILL.md` starting with valid YAML frontmatter.
- Required fields: `name` (lowercase, hyphenated, matches folder name) and `description`.
- Recommended: `license: MIT`
- Keep the main `SKILL.md` concise. Use `references/`, `scripts/`, and `assets/` for supporting material.

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
