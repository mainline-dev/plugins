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

Then sign in: type `/mcp` in a session, choose the Mainline server and authenticate. Your browser opens Mainline. Tick the teams your agent may read and approve.

## Install in Codex

From a shell:

```sh
codex plugin marketplace add mainline-dev/plugins
codex plugin add mainline@mainline-dev
```

Or in a Codex session, run `/plugins` and install Mainline from the Mainline marketplace. Start a new session before using it.

Then sign in:

```sh
codex mcp login mainline
```

Your browser opens Mainline. Tick the teams your agent may read and approve, then start a new Codex session.

## Signing in

The plugin brings the address of one server, `https://mainline.dev/mcp`, and no token. You sign in to Mainline in your browser and choose which of your teams the agent may read. The agent can read those teams' maps and stories and can change nothing in Mainline. End a sign-in at any time in Mainline, under Profile, then Coding agents.

Two cases need a server you add yourself:

- **An agent that can't open a browser,** such as one on a build runner. Make a personal token in Mainline under Profile, then Coding agents. The page gives the command for Claude Code and for Codex.
- **A team that hosts Mainline itself.** Add your own address as a server, for example `claude mcp add --transport http mainline https://your-mainline-address/mcp`, and sign in to that.

## Learn more

The Mainline docs, including how coding agents fit in: https://mainline.dev/docs

## This repository

`skills/` holds the three skills and `assets/` holds the icon. `scripts/sync` copies both into `plugins/claude/mainline` and `plugins/codex/mainline`, and CI fails if a copy differs. Edit `skills/` and `assets/`, never the copies.

Each plugin folder also holds its own server settings, which are not shared: `.mcp.json` for Claude Code and `mcp.json` for Codex.

## Licence

This repository is under the MIT licence; see [LICENSE](LICENSE). The Mainline app itself is under the AGPL.
