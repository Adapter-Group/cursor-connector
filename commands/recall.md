---
name: recall
description: Pull context relevant to the current task from the Adapter workspace.
---

Query the Adapter workspace for context relevant to the current task, following the adapter-mind skill:

1. Determine the repository name and topic from the open files and the conversation.
2. Call `ask` with a focused question, scoped with `metadata: {"repo": "<name>"}`.
3. If the answer is thin, call `search_knowledge` with the same scope, then `recall_remembered`.
4. Summarize what the workspace holds: prior decisions, outcomes, open follow-ups, and stated preferences. Say plainly if it holds nothing yet.
