# Mainline for Codex

Work from your team's Mainline stories: tests from the acceptance scenarios first, small steps, then a walkthrough.

## Install

```sh
codex plugin marketplace add mainline-dev/plugins
codex plugin add mainline@mainline-dev
```

In a session: run `/plugins` and install Mainline from the Mainline marketplace. Start a new session before using it.

## Connect to Mainline

The plugin brings the Mainline server with it. Sign in once:

```sh
codex mcp login mainline
```

Your browser opens Mainline. Sign in, tick the teams your agent may read and approve. Then start a new Codex session.

There is no token to copy and nothing to set in your environment. You can end the sign-in at any time in Mainline, under Profile, then Coding agents.

Two cases need a server you add yourself, because the plugin's own server always signs in at mainline.dev:

- **An agent that can't open a browser,** such as one on a build runner. Make a personal token in Mainline under Profile, then Coding agents. The page gives the command to run.
- **A team that hosts Mainline itself.** Run `codex mcp add mainline --url https://your-mainline-address/mcp` and sign in when your browser opens.

## What it connects to and runs

The plugin contains three skills and the address of one server. It has no scripts or programs of its own, and it holds no token or password.

- **Connects to** one service: the Mainline MCP server at `https://mainline.dev/mcp`. You sign in through your browser, and Codex keeps that sign-in. It sends nothing to any other service.
- **Reads** your team's maps, stories and acceptance scenarios, a story's scenarios as a feature file, the story import format and Mainline's own docs, through the server's read-only tools. Reading a story is recorded: Mainline notes in its history that a coding agent read it, for whom and with which tool.
- **Runs in your project**, through Codex: your test suite, and `git` to read the history and commit each step with the story ID. It doesn't push or deploy unless you ask.
- **Writes** only in your project: the tests and code for a story, and the import file that propose-stories produces.

## Try

- work-a-story: "Work on ABC12345"
- prepare-walkthrough: "Prepare the walkthrough for ABC12345"
- propose-stories: "Propose stories from spec.md"

Story IDs are the 8-character short IDs on each story card.

The plugin never marks a scenario done or a story released, and never pushes or deploys unless you say so. Docs: https://mainline.dev/docs. MIT licence.
