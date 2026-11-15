# Mainline plugins

The Mainline plugin teaches a coding agent to work the Mainline way, in Claude Code and in Codex. It reads your team's stories and their acceptance scenarios from Mainline, turns each scenario into a failing test before writing any code, and works in small steps, one story at a time. When every scenario passes, it stops and prepares a short summary so a person can be walked through the change.

## Install in Claude Code

From a shell:

```sh
claude plugin marketplace add mainline-dev/plugins
claude plugin install mainline@mainline-dev
```

Or in a Claude Code session:

```
/plugin marketplace add mainline-dev/plugins
/plugin install mainline@mainline-dev
```

The plugin connects to Mainline using the environment variables below.

## Install in Codex

From a shell:

```sh
codex plugin marketplace add mainline-dev/plugins
codex plugin add mainline@mainline-dev
```

Or in a Codex session, run `/plugins` and install Mainline from the Mainline marketplace. Start a new session before using it.

Codex's plugin format cannot read a token from an environment variable, so in Codex the plugin brings the skills only. Set the environment variables below, then add the Mainline server once:

```sh
codex mcp add mainline --url "${MAINLINE_URL:-https://mainline.dev}/mcp/${MAINLINE_TEAM_ID}" --bearer-token-env-var MAINLINE_TOKEN
```

Your shell fills in the URL only once, when you run this command, so set the variables first, and run it again if your team ID or Mainline address changes. Codex reads `MAINLINE_TOKEN` each time it connects.

## Environment variables

| Variable | | |
|---|---|---|
| `MAINLINE_URL` | Optional | Your Mainline address, if your team self-hosts. Defaults to `https://mainline.dev`. Leave it unset rather than empty. |
| `MAINLINE_TEAM_ID` | Required | Your team ID. |
| `MAINLINE_TOKEN` | Required | Your team's MCP server token. This is not the deploy webhook token. |

Set them in the environment you start Claude Code or Codex from, such as your shell profile. Keep the token out of your repositories.

## Find your team ID and token

In Mainline, open the team menu (your team's name in the top bar) and choose **MCP server**.

- **Token:** the team's account holder generates it there with **Generate Token**. It is shown only once, so store it somewhere safe. Regenerating it stops the old token working.
- **Team ID:** once a token exists, the page shows the endpoint, which ends in `/mcp/` followed by your team ID.

## Learn more

The Mainline docs, including how coding agents fit in: https://mainline.dev/docs

## This repository

`skills/` holds the three skills and `assets/` holds the icon. `scripts/sync` copies both into `plugins/claude/mainline` and `plugins/codex/mainline`, and CI fails if a copy differs. Edit `skills/` and `assets/`, never the copies.

## Licence

This repository is under the MIT licence; see [LICENSE](LICENSE). The Mainline app itself is under the AGPL.
