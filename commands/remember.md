---
name: remember
description: Save the durable result of the current work to the Adapter workspace.
---

Save what should outlive this conversation with the `remember` tool, following the adapter-mind skill:

1. Choose a `kind` for each item: `decision`, `task_outcome`, `summary`, `fact`, `document`, or `note`. Usually one or two items, not one per message.
2. Call `recall_remembered` first and reuse an `external_id` if the topic already exists.
3. Set `metadata: {"repo": "<name>"}` and `tags: ["repo:<name>"]`, and `agent: "cursor"`.
4. Write `content` as Markdown: what was decided or done, why, and how it was verified.
5. Confirm in one or two lines what you saved.

Do not save secrets, transient discussion, or content already in the repository.
