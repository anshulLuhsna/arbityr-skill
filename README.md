# Arbityr Skill

Arbityr is a decision checkpoint for developers building with AI.

Use it before you ask an AI agent to build something non-trivial, so you can defend the decision before the code exists.

## Repo Structure

```text
arbityr-skill/
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
arbityr/SKILL.md
```

The Cursor rule version is:

```text
arbityr/resources/cursor-rule.mdc
```

## GitHub Skill Install

After the first GitHub skill release is published, install with:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent claude-code
```

Use project scope when you want Arbityr only in the current repo, or user scope if you want it globally:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent claude-code --scope user
```

## Cursor Install

For Cursor, copy:

```text
arbityr/resources/cursor-rule.mdc
```

Into your project as:

```text
.cursor/rules/arbityr.mdc
```

Then open Cursor chat and say:

```text
Use Arbityr on this decision: [your real decision]
```

Or:

```text
Before I build this, run Arbityr on the current diff.
```

## Claude Or Other Agents

Ask the agent to read:

```text
arbityr/SKILL.md
```

Then say:

```text
Act as Arbityr for this decision: [your real decision]
```

## Publishing

The intended GitHub-native release path is:

```sh
gh extension install <publisher>/gh-skill
gh skill publish --dry-run
gh skill publish --tag v0.1.0
```

After publishing, developers can install the skill with `gh skill install`.

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
**Standing on:** ...
**Challenge:** ...
**Held / Changed:** ...
**This decision was wrong if:** ...
```

## Discoverability Checklist

- Add GitHub topics: `claude-skills`, `agent-skills`, `ai-skill`, `cursor`.
- Publish a GitHub skill release after `gh skill publish --dry-run` passes.
- Submit the repo to relevant public skill catalogs when the package is ready for broader discovery.

## Privacy

This repo has no server and no telemetry.

Arbityr runs inside your existing AI coding session. Nothing is sent anywhere by this skill repo.
