---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS (`$TMPDIR`, else `/tmp`; `%TEMP%` on Windows) - not the current workspace.

Include a "suggested skills" section in the document, naming which skills the next agent should call the Skill tool for.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.

## Next-session prompt

End the document with a "Next-session prompt" section: a ready-to-paste opening message for the next session, in a fenced code block. It must:

- Tell the agent to read the handoff document first, by its absolute path.
- State the goal of the next session in one or two sentences (from the user's arguments when given, otherwise the most likely next step).
- Name the first concrete action to take, and what "done" looks like.
- Name the skills to load from the "suggested skills" section.
- Stand on its own: no "as discussed" or references to this conversation.

After saving, reply with the document's path, then print the same prompt in a fenced code block so the user can copy it straight into a new session.
