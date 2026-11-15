# Mainline for Claude Code

Work from your team's Mainline stories: tests from the acceptance scenarios first, small steps, then a walkthrough.

## Install

```sh
claude plugin marketplace add mainline-dev/plugins
claude plugin install mainline@mainline-dev
```

In a session: `/plugin marketplace add mainline-dev/plugins`, then `/plugin install mainline@mainline-dev`.

## Connect to Mainline

Set these before you start Claude Code:

- `MAINLINE_TEAM_ID`: your team ID. Required.
- `MAINLINE_TOKEN`: your team's MCP server token. Required.
- `MAINLINE_URL`: only if your team self-hosts. Defaults to `https://mainline.dev`.

Both the team ID and the token are on the **MCP server** page in your team menu in Mainline. `claude mcp list` shows the server as `plugin:mainline:mainline`. If a variable is unset, its `${...}` text stays in the URL and the connection fails.

## What it connects to and runs

The plugin contains three skills and the settings for one server. It has no scripts or programs of its own.

- **Connects to** one service: your team's Mainline MCP server, at `$MAINLINE_URL/mcp/$MAINLINE_TEAM_ID`, sending your team's token in the `Authorization` header. It sends nothing to any other service.
- **Reads** your team's maps, stories, acceptance scenarios and story import format, through the server's read-only tools. Mainline notes in each story's history that a coding agent read it.
- **Runs in your project**, through Claude Code: your test suite, and `git` to read the history and commit each step with the story ID. It doesn't push or deploy unless you ask.
- **Writes** only in your project: the tests and code for a story, and the import file that propose-stories produces.

## Try

- work-a-story: "Work on ABC12345"
- prepare-walkthrough: "Prepare the walkthrough for ABC12345"
- propose-stories: "Propose stories from spec.md"

Story IDs are the 8-character short IDs on each story card.

The plugin never marks a scenario done or a story released, and never pushes or deploys unless you say so. Docs: https://mainline.dev/docs. MIT licence.
