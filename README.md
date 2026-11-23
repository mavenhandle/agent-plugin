# MavenHandle for coding agents

Check your mobile app for App Store and Google Play rejection risks from Claude Code or
OpenAI Codex. You need a free MavenHandle account; you can create one when you first connect.

What the agent can do: list your apps, add one, start a scan (it uses your account's
monthly scans) and read the results with the next step. It cannot pay, download builds or
fixed code, or send anything to the stores. Paid work is done on mavenhandle.com.
Disconnect any time under Account → Connected coding agents.

## Claude Code

```
/plugin marketplace add mavenhandle/agent-plugin
/plugin install mavenhandle@mavenhandle
```

Or add only the server: `claude mcp add --transport http mavenhandle https://mavenhandle.com/api/agent/v1/mcp`,
then run `/mcp` to sign in.

## Codex

```
codex plugin marketplace add mavenhandle/agent-plugin
```

then open `/plugins` in Codex and install MavenHandle. Or add only the server to
`~/.codex/config.toml`:

```toml
[mcp_servers.mavenhandle]
url = "https://mavenhandle.com/api/agent/v1/mcp"
```

and run `codex mcp login mavenhandle`.

## What is in this plugin

Text only: one skill (`skills/mavenhandle-launch/SKILL.md`) and the address of the
MavenHandle MCP server (`.mcp.json`). There is no code to run on your machine. The checks
themselves run on MavenHandle's servers.
