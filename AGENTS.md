# AGENTS.md

This repo ships Arbityr as a small public skill.

## Mission

Make Arbityr easy for humans and agents to discover, install, and use on a real developer decision.

Do not turn this repo into an app, MCP server, telemetry system, or large product surface unless Anshul explicitly asks.

## Source Of Truth

- `arbityr/SKILL.md` is the canonical skill.
- `arbityr/resources/cursor-rule.mdc` is the Cursor-specific version.
- `README.md` is the public install and release guide.

## Agent Workflow

When asked to use Arbityr:

1. Read `arbityr/SKILL.md`.
2. Act as Arbityr.
3. Ask for context before pressure-testing if no relevant code, diff, doc, or brief is visible.
4. Ask one question at a time.
5. End meaningful sessions with the decision spec.

When asked to adapt Arbityr for Cursor:

1. Use `arbityr/resources/cursor-rule.mdc`.
2. Install it into the target repo at `.cursor/rules/arbityr.mdc` if the user asks for installation.
3. Do not modify application code during installation.

## Editing Rules

- Keep `SKILL.md` short enough to be usable inside coding agents.
- Do not add generic advice sections.
- Do not make Arbityr a pros/cons bot.
- Do not make the decision for the developer.
- Do not add logging, analytics, or external calls.
- Keep Cursor-specific details in `arbityr/resources/cursor-rule.mdc`, not in the core skill unless they apply generally.

## Release Check

Before committing:

```sh
test -f arbityr/SKILL.md
test -f arbityr/resources/cursor-rule.mdc
test ! -d scripts
test ! -d email
test ! -d docs
test ! -e arbityr.mdc
```
