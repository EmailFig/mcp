# EmailFig for Hermes Agent

[EmailFig](https://emailfig.com) is email marketing without the bloat: fast, focused campaigns, easy list management, and pricing that scales fairly. It's free for up to 4,000 contacts.

This plugin connects Hermes Agent to EmailFig's hosted MCP server at `https://emailfig.com/mcp`. The agent can check how a campaign or automation did, look up a contact and what has happened to them, add someone to a list, tag or unsubscribe them, add images to your library, and draft campaigns. Drafts open in EmailFig, where you check them and send them yourself: the agent never sends, schedules or deletes a campaign. The only email it can send is a test of a draft to your own address.

## What the plugin contains

- `mcp.json`: the EmailFig server, reached through the pinned `mcp-remote@0.15.2` sign-in bridge.
- `plugin.json`: marks the server `untrusted`, so Hermes asks before every tool the server doesn't mark read-only.

No hooks, scripts or skills. It asks for no key or password and reads no files, environment variables or saved logins.

## Install

You need Hermes Agent 0.21.6 or newer and Node.js 20.18.1 or newer with `npx` on your `PATH`.

```bash
hermes plugins install emailfig
hermes plugins enable emailfig
```

Start a new session. The first time the server starts, your browser opens EmailFig. Sign in, choose the account, and click **Approve**. EmailFig marks Hermes as an unverified app on that page, since it registers itself. The token is kept under `~/.mcp-auth` for later sessions. If the tools don't show up after you sign in, run `/reload-mcp`.

## What to know before installing

- Every tool call goes to EmailFig's server (emailfig.com) and acts on the account you approved. The tool set comes from that server at runtime.
- Adding someone to a double opt-in list emails them to confirm, and adding or tagging someone can start your EmailFig automations. Only add people who agreed to hear from you.
- In cron and other unattended runs, Hermes refuses every tool that changes data.
- The package sends no telemetry.
- You can disconnect it any time in EmailFig under **Settings > Integrations**.

Help: [Connect Claude or ChatGPT](https://emailfig.com/help/api/connect-claude-and-chatgpt) covers what the server can do. Questions: [contact@emailfig.com](mailto:contact@emailfig.com).
