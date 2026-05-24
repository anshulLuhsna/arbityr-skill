# AGENTS.md

This repo ships Arbityr as a small public Agent Skill.

## Mission

Make Arbityr easy for humans and agents to discover, install, and use on a real developer decision.

Do not turn this repo into an app, MCP server, telemetry system, or large product surface unless Anshul explicitly asks.

## Source Of Truth

- `skills/arbityr/SKILL.md` is the canonical skill.
- `skills/arbityr/resources/cursor-rule.mdc` is the Cursor-specific rule version.
- `README.md` is the public install and release guide.

## Agent Workflow

When asked to use Arbityr:

1. Read `skills/arbityr/SKILL.md`.
2. Act as Arbityr.
3. Ask for context before pressure-testing if no relevant code, diff, doc, or brief is visible.
4. Ask one question at a time.
5. End meaningful sessions with the decision spec.

When asked to install Arbityr into another repo:

1. Prefer `gh skill install anshulLuhsna/arbityr-skill arbityr --agent universal --scope project`.
2. Add `--agent codex`, `--agent cursor`, `--agent opencode`, or `--agent claude-code` when the current host is known.
3. If `gh skill` is unavailable, copy `skills/arbityr` into the target repo's `.agents/skills/arbityr`.
4. For native Cursor rules only, copy `skills/arbityr/resources/cursor-rule.mdc` to `.cursor/rules/arbityr.mdc`.
5. Do not modify application code during installation.
6. After installation, ask: "Arbityr is installed. Do you want to start a decision session now?"
7. If the user says yes, act as Arbityr and ask where to look for context.

## Editing Rules

- Keep `SKILL.md` short enough to be usable inside coding agents.
- Do not add generic advice sections.
- Do not make Arbityr a pros/cons bot.
- Do not make the decision for the developer.
- Do not add logging, analytics, or external calls.
- Keep Cursor-specific details in `skills/arbityr/resources/cursor-rule.mdc`, not in the core skill unless they apply generally.

## Release Check

Before committing:

```sh
test -f skills/arbityr/SKILL.md
test -f skills/arbityr/resources/cursor-rule.mdc
gh skill publish --dry-run
```
