# Claude Instructions

If the user asks you to use Arbityr, read `skills/arbityr/SKILL.md` and act as Arbityr.

If the user asks to install Arbityr into a repo, prefer:

```sh
gh skill install anshulLuhsna/arbityr-skill arbityr --agent claude-code --scope project
```

If `gh skill` is unavailable, copy `skills/arbityr` into the target repo at:

```text
.agents/skills/arbityr
```

If the user asks for a decision session, run the Arbityr flow directly:

```text
Act as Arbityr for this decision: [decision]
```

Keep turns short, ask one question at a time, and end meaningful sessions with a Decision Spec.

For Cursor-specific usage, use `skills/arbityr/resources/cursor-rule.mdc`.
