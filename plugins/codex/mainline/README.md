# Mainline for Codex

Work from your team's Mainline stories: tests from the acceptance scenarios first, small steps, then a walkthrough.

## Install

```sh
codex plugin marketplace add mainline-dev/plugins
codex plugin add mainline@mainline-dev
```

In a session: run `/plugins` and install Mainline from the Mainline marketplace. Start a new session before using it.

## Connect to Mainline

This plugin brings the skills. Codex's plugin format cannot read a token from an environment variable, so add the Mainline server yourself.

1. Set the three variables:
   - `MAINLINE_TEAM_ID`: your team ID. Required.
   - `MAINLINE_TOKEN`: your team's MCP server token. Required.
   - `MAINLINE_URL`: only if your team self-hosts. Defaults to `https://mainline.dev`.
2. Run:

   ```sh
   codex mcp add mainline --url "${MAINLINE_URL:-https://mainline.dev}/mcp/${MAINLINE_TEAM_ID}" --bearer-token-env-var MAINLINE_TOKEN
   ```

Set the variables before you run the command: your shell fills in the URL only once, when you run it. Run it again if your team ID or Mainline address changes. Codex reads `MAINLINE_TOKEN` each time it connects, so keep it set wherever you run Codex.

Both the team ID and the token are on the **MCP server** page in your team menu in Mainline.

## What it connects to and runs

The plugin contains three skills. It has no scripts, programs or server settings of its own.

- **Connects to** one service: the Mainline MCP server you add with the command above, sending your team's token in the `Authorization` header. It sends nothing to any other service.
- **Reads** your team's maps, stories, acceptance scenarios and story import format, through the server's read-only tools. Mainline notes in each story's history that a coding agent read it.
- **Runs in your project**, through Codex: your test suite, and `git` to read the history and commit each step with the story ID. It doesn't push or deploy unless you ask.
- **Writes** only in your project: the tests and code for a story, and the import file that propose-stories produces.

## Try

- work-a-story: "Work on ABC12345"
- prepare-walkthrough: "Prepare the walkthrough for ABC12345"
- propose-stories: "Propose stories from spec.md"

Story IDs are the 8-character short IDs on each story card.

The plugin never marks a scenario done or a story released, and never pushes or deploys unless you say so. Docs: https://mainline.dev/docs. MIT licence.
