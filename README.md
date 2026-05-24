# Arbityr Skill

Arbityr is a decision checkpoint for developers building with AI.

Use it before you ask an AI agent to build something non-trivial, so you can defend the decision before the code exists.

## Install

Arbityr is published as a GitHub Agent Skill:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent universal --scope project
```

Project scope installs Arbityr into the current repo so your agent can discover it there.

Pin a known release:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent universal --pin v0.1.4 --scope project
```

Install globally:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent universal --scope user
```

## Agent-Specific Installs

Use the same skill package and choose the agent host:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent codex --scope project
gh skill install anshulLuhsna/arbityr-skill arbityr --agent cursor --scope project
gh skill install anshulLuhsna/arbityr-skill arbityr --agent opencode --scope project
gh skill install anshulLuhsna/arbityr-skill arbityr --agent claude-code --scope project
```

GitHub's skill installer also supports other hosts such as GitHub Copilot, Gemini CLI, Windsurf, Warp, Goose, Cline, Amp, and OpenCode-compatible agents.

## Point An Agent At This Repo

Ask your coding agent:

```text
Install Arbityr for this repo.

Use GitHub Agent Skills if available:
gh skill install anshulLuhsna/arbityr-skill arbityr --agent universal --scope project

If the current agent is known, replace universal with the right --agent value: codex, cursor, claude-code, or opencode.

If gh skill is unavailable, install manually by copying skills/arbityr to the agent's project-local skills directory, preferably .agents/skills/arbityr.

After installation, ask the user:
"Arbityr is installed. Do you want to start a decision session now?"

If yes, start by asking where to look for context.
```

## Repo Structure

```text
arbityr-skill/
  skills/
    arbityr/
      SKILL.md
      resources/
        cursor-rule.mdc
  AGENTS.md
  CLAUDE.md
  README.md
  LICENSE
```

The core skill is:

```text
skills/arbityr/SKILL.md
```

The Cursor rule version is:

```text
skills/arbityr/resources/cursor-rule.mdc
```

## Cursor Native Rule

The recommended Cursor install is still `gh skill install ... --agent cursor`.

If you specifically want a Cursor project rule instead, copy:

```text
skills/arbityr/resources/cursor-rule.mdc
```

Into your project as:

```text
.cursor/rules/arbityr.mdc
```

Then open Cursor chat and say:

```text
Use Arbityr on this decision: [your real decision]
```

## Claude, Codex, OpenCode, Or Other Agents

After installation, ask:

```text
Use Arbityr on this decision: [your real decision]
```

Or:

```text
Before I build this, run Arbityr on the current diff.
```

Agents with skills support should discover Arbityr from the installed `SKILL.md`. Agents without skill discovery can still read `skills/arbityr/SKILL.md` directly.

## Publishing

Validate:

```sh
gh skill publish --dry-run
```

Publish a release:

```sh
gh skill publish --tag v0.1.4
```

## What To Test

Use Arbityr only on a real decision you are about to make.

Good decisions:

- Should I add Redis here or keep state in Postgres?
- Should this feature ship as a manual workflow first or as automation?
- Should this schema change happen now or wait until the next version?
- Should I let the AI agent implement this whole flow or split the work?

Bad tests:

- "Try the prompt and tell me if it sounds good."
- "Ask me random questions."
- "Review this code."

## What Arbityr Produces

Arbityr runs a short decision session and ends with a decision spec:

```md
## Decision Spec

**Decision:** ...
**Why:** ...
**Load-bearing assumption:** ...
**Challenge:** ...
**Held / Changed:** ...
**This decision was wrong if:** ...
```

## Discoverability Checklist

- GitHub topics: `agent-skills`, `ai-skill`, `claude-skills`, `cursor`
- GitHub skill release: `v0.1.4`
- Public catalogs: submit after more field usage

## Privacy

This repo has no server and no telemetry.

Arbityr runs inside your existing AI coding session. Nothing is sent anywhere by this skill repo.
