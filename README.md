# EmailFig MCP server

[EmailFig](https://emailfig.com) is email marketing without the bloat: fast, focused campaigns, easy list management, and pricing that scales fairly. It's free for up to 4,000 contacts.

The EmailFig MCP server lets an AI assistant work in your EmailFig account: ask how a campaign or automation did, look up a subscriber and what has happened to them, add someone to a list, tag or unsubscribe them, and draft your next campaign. Drafts open in EmailFig's drag and drop editor, where you check them and send them yourself. The assistant never sends, schedules or deletes a campaign; the only email it can send is a test of a draft to your own address.

It is a hosted server. There is nothing to install or run.

| | |
|---|---|
| Server URL | `https://emailfig.com/mcp` |
| Transport | Streamable HTTP |
| Auth | OAuth 2.1 with PKCE. Clients register themselves (dynamic client registration or a client metadata document). |
| Registry name | `com.emailfig/emailfig` |

## Connect

You need an EmailFig account. [Sign up free](https://emailfig.com) if you don't have one.

- **Claude**: open [EmailFig in Claude's connector directory](https://claude.ai/directory/emailfig-mcp) and click **Connect to Claude**.
- **ChatGPT**: open [EmailFig in ChatGPT's plugin directory](https://chatgpt.com/plugins/plugin_asdk_app_6ad7214b7a7c8191af6bfbce37463942) and click **Install plugin**.
- **Claude Code**: `claude mcp add --transport http emailfig https://emailfig.com/mcp`, then `/mcp` to connect.
- **VS Code**: run **MCP: Add Server**, choose **HTTP** and enter `https://emailfig.com/mcp`, or add it to `.vscode/mcp.json`:

  ```json
  {
    "servers": {
      "emailfig": { "type": "http", "url": "https://emailfig.com/mcp" }
    }
  }
  ```

- **Cursor**: add it to `~/.cursor/mcp.json`:

  ```json
  {
    "mcpServers": {
      "emailfig": { "url": "https://emailfig.com/mcp" }
    }
  }
  ```

- **Hermes Agent**: `hermes plugins install emailfig`, then `hermes plugins enable emailfig`. See [hermes/](hermes/).
- **Any other MCP client**: point it at `https://emailfig.com/mcp`.

Your browser opens EmailFig. Sign in, choose the account, and click **Approve**. Apps other than Claude, Claude Code and ChatGPT are marked unverified on that page; only approve a connection you just started. Each connection covers one account, and you can disconnect it any time from **Settings > Integrations**.

Full guide: [Connect Claude or ChatGPT](https://emailfig.com/help/api/connect-claude-and-chatgpt).

## Tools

| Tool | What it does |
|---|---|
| `get_account` | Name, plan, contact count, sending domain, and whether the account can send |
| `search_contacts` | Find contacts by address or name |
| `get_contact` | One contact by id or address |
| `get_contact_activity` | A contact's recent email events, automation runs and any suppression |
| `add_contact_to_list` | Add someone to a list, creating the contact |
| `update_contact` | Change a contact's name and custom fields |
| `tag_contact` / `untag_contact` | Add or remove a tag |
| `unsubscribe_contact` | Unsubscribe an address |
| `list_lists` | Lists with counts and whether signup needs confirmation |
| `list_tags` | Tags with subscribed counts |
| `list_segments` | Saved segments |
| `list_custom_fields` | Custom fields and their choices |
| `list_forms` | Signup forms with their last 30 days of views, signups and confirmations |
| `list_campaigns` | Recent campaigns |
| `get_campaign` | One campaign's email, sender, audience and, for a draft, what it still needs |
| `get_campaign_report` | One campaign's results and top links |
| `list_automations` | Automations with their trigger, people in progress and email steps |
| `get_automation_report` | One automation's results, step by step |
| `list_templates` / `get_template` | Saved templates and their design |
| `get_email_format` | The format and design rules for writing a draft |
| `create_campaign_draft` | Save a new campaign draft |
| `update_campaign_draft` | Revise a draft the assistant made, until someone saves it in EmailFig |
| `list_images` | The image library |
| `upload_image_from_url` | Add an image from a public https link |
| `send_test_email` | Email a test of a draft to your own address |

People added from a chat are treated like any other signup: a double opt-in list emails them to confirm first, someone who unsubscribed can't be added back, and adding or tagging someone can start your automations.

## Support

Email [contact@emailfig.com](mailto:contact@emailfig.com) and a real person will help.
