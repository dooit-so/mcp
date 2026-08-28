# Dooit MCP server

**This repo is metadata and docs, not source.** Dooit's MCP server is hosted —
it runs as part of the Dooit app, and its code lives in the product repo. This
repo exists because the ecosystem assumes one: [`server.json`](server.json)
wants a `repository`, aggregators key their claim flow off it, and directory
entries are `owner/repo` shaped.

Dooit is a lightweight, keyboard-first personal task manager. The MCP server
lets an agent read your board, agenda, projects and weekly/monthly/yearly
goals, then create, reschedule, complete, archive and delete tasks on your
behalf — in your own timezone, with your own permissions.

## Connect

```
claude mcp add --transport http dooit https://app.dooit.so/mcp
```

Claude Desktop, claude.ai, ChatGPT, Cursor and other clients take the same URL
as a custom connector. Auth is OAuth 2.1 with dynamic client registration —
there is no API key.

You need a [Dooit account](https://app.dooit.so). Reads work on any account;
writes require an active subscription and are rate limited.

## Docs

- [MCP server page](https://dooit.so/mcp) — connection guide per client, tools, limits
- [Agent guide](https://dooit.so/llm-info) — the same reference, written for LLMs
- [Server card](https://app.dooit.so/.well-known/mcp/server-card.json)
- [Skill](https://github.com/dooit-so/skill) — `npx skills add dooit-so/skill`

## Tools

Context: `get_board`, `get_agenda`
Tasks: `list_tasks`, `get_task`, `create_task`, `update_task`, `set_task_done`, `archive_task`, `delete_task`
Projects: `create_project`, `update_project`
Goals: `list_goals`, `create_goal`, `update_goal`

Call `get_board` first — it returns today's date in the user's timezone plus
the status and project ids every write needs.

## License

MIT
