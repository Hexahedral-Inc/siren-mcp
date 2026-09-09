<p align="center"><img src="mark.png" width="96" alt="Siren"></p>

# Siren MCP

Your agent makes the images, captions, and videos for your brand, then posts them to your socials. You show Siren the brand once. After that you type `post this` in Cursor, Claude, ChatGPT, Codex, or Grok and it goes out.

Remote MCP server, Streamable HTTP, OAuth 2.1. No API keys to copy.

| | |
|---|---|
| Server | `https://mcp.mysiren.ai/mcp` |
| Registry | `ai.mysiren/siren` |
| Docs | https://mysiren.ai/docs/mcp |
| Plans | Plans start at $19 per month. MCP is Pro and up. |

## Connect

**Claude Code**

```
claude mcp add --transport http siren https://mcp.mysiren.ai/mcp
```

**Claude (claude.ai)**: Settings → Connectors → Custom → `https://mcp.mysiren.ai/mcp`

**Cursor**: Settings → Tools & MCP → add a remote server, or in `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "siren": { "url": "https://mcp.mysiren.ai/mcp" } } }
```

**ChatGPT**: Developer Mode on → Settings → Apps & Connectors → Create → `https://mcp.mysiren.ai/mcp`

**Grok**: [grok.com/connectors](https://grok.com/connectors) → Custom, or `grok mcp add --transport http siren https://mcp.mysiren.ai/mcp`

The agent opens a consent page on app.mysiren.ai. Approve once. Posting stays off until you turn on **Allow posting** on that screen. Revoke any time under Developers.

## Tools

| Tool | What it does |
|---|---|
| `get_account` | Workspace, plan, credits, connected channels |
| `clarify_brief` | Turns a one-line ask into a brief Siren can render |
| `create_campaign` | Generates the asset. Optional `scheduled_at`, `timezone`, `platforms` |
| `render_asset` | Renders a specific output type |
| `list_runs`, `get_run` | Status and result URLs |
| `post_run` | Publishes a finished run to your connected channels now |
| `schedule_post` | Queues a finished run for a time in your timezone |
| `get_brand_dna`, `update_brand_dna` | Read and patch the brand profile |
| `list_product_screens`, `upload_product_screen`, `update_product_screen`, `delete_product_screen` | Product screenshots Siren can paint into assets |

Posts go through the channels already connected in the Siren dashboard: X, LinkedIn, Instagram, TikTok, YouTube. The agent never sees your platform tokens.

## Example

```
> Post an update about the new export feature. Use the dashboard screenshot.
```

The agent calls `clarify_brief`, then `create_campaign`, waits on `get_run`, and calls `post_run`. One image or film, a caption, and the post, on brand every time.

## This repo

Listing and connect docs. The server is hosted at mcp.mysiren.ai. Questions: open an issue or write to hello@mysiren.ai.

Siren · a thousand voices, one signature.
