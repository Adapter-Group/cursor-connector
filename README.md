# Adapter for Cursor

A mind for Cursor, backed by your [Adapter](https://adapter.com) workspace. Cursor recalls context
from it before working and saves results back as it goes, so decisions, task outcomes, and
conventions persist across sessions and machines.

Requires an Adapter account. Sign-in happens in the browser; there is no API key to manage.

## Install

Install **Adapter** from the Cursor plugin marketplace, or add the server to `~/.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "adapter": {
      "url": "https://api.adapter.com/v1/mcp/mind/http",
      "auth": { "CLIENT_ID": "cursor", "scopes": ["mcp:read", "mcp:write", "offline_access"] }
    }
  }
}
```

On first connect, Cursor opens a browser to sign in to Adapter. Use the server from an Agent chat.
The same sign-in works from Cursor's cloud agents.

## Commands

- `/recall` pulls context relevant to the current task from your workspace.
- `/remember` saves the durable result of the current work.

The commands are optional. In an Agent chat, Cursor calls `ask`, `search_knowledge`, `remember`, and
the other tools directly.

## What it stores

Only what Cursor explicitly saves with `remember`: decisions, task outcomes, facts, summaries, and
documents, tagged by repository. It does not upload your source code, and it is instructed not to save
secrets or transient chat. Data lives in your Adapter workspace.

## Layout

```
.cursor-plugin/plugin.json   manifest
logo.svg                     marketplace logo
mcp.json                     the adapter MCP server
rules/adapter-mind.mdc       always-on guidance
skills/adapter-mind/         recall and remember procedures
commands/                    /recall, /remember
```
