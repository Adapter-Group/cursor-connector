---
name: adapter-mind
description: Read from and write to the user's Adapter workspace via the "adapter" MCP server. Use when a task may have prior context, when the user asks what was decided or done before, or when finishing work worth keeping.
---

# Adapter mind

The `adapter` MCP server is the user's Adapter workspace, used as long-term memory.

## Recall
1. Determine the repository name from the workspace folder or `git remote`.
2. Call `ask` with a direct question. Scope it with `metadata: {"repo": "<name>"}` for project-specific questions; omit `metadata` for cross-project ones.
3. If `ask` returns little, call `search_knowledge` with the same scope, or `recall_remembered` for recent items.
4. Cite what you find and act on it. If the workspace is empty, say so briefly and continue; it fills up as you save work.

## Remember
1. Call `recall_remembered` first to avoid duplicating an existing item.
2. Call `remember` with:
   - `kind`: one of `decision`, `task_outcome`, `summary`, `fact`, `document`, `note`.
   - `title`: short and specific.
   - `content`: Markdown. For a decision, give context, the decision, the reasoning, and rejected alternatives. For a task outcome, give what changed, why, and how it was verified.
   - `external_id`: stable, such as `<repo>/<topic>`, so a later save updates it.
   - `tags`: include `repo:<name>`.
   - `metadata`: `{"repo": "<name>"}`.
   - `agent`: `cursor`.
3. Confirm in one line what you saved.
