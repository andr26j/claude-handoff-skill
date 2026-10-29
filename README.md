# handoff

A Claude Code skill that compacts the current conversation into a handoff document, so a fresh session can pick up the work, and writes the opening prompt for that next session.

## What it does

Run `/handoff [what the next session is for]` and it:

- Writes a handoff doc to your OS temp directory (not your workspace).
- Lists the skills the next agent should load.
- Points to existing specs, plans, issues, commits and diffs instead of repeating them.
- Redacts API keys, passwords and personal information.
- Ends with a **next-session prompt**: a ready-to-paste opening message that points at the doc, states the goal, names the first step and what "done" looks like. It also prints that prompt in the reply so you can copy it straight into a new session.

It only runs when you call it (`disable-model-invocation: true`).

## Install

```bash
git clone https://github.com/andr26j/claude-handoff-skill ~/.claude/skills/handoff
```

Then start a new Claude Code session and run `/handoff`.

## Files

- `SKILL.md`: the skill.
- `agents/openai.yaml`: display metadata for other agent hosts.
