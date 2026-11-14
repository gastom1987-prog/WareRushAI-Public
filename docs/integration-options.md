# Ways to connect to WareRushAI

This page describes which integration options exist **today**, so developers and AI assistants do not have to guess.

| Option | Status | Details |
| --- | --- | --- |
| **MCP connector** (read-only) for AI assistants such as Claude and ChatGPT | Available | [MCP connector guide](mcp-connector.md) · https://warerushai.com/guide/developers-mcp-connector |
| **Built-in channel integrations** (marketplaces, webshops, invoicing, price comparison, carriers) | Available, with per-service status | [Integrations overview](integrations.md) · https://warerushai.com/integrations |
| **Public REST API for third parties** | **Not available yet** | There is no public, documented REST API today. If you need one for a concrete integration, tell us about the use case through the contact details on https://warerushai.com so it can be considered. |
| **Write actions through AI assistants** | Planned | Only as a preview plus an explicit, one-time approval. Not available in the current version. |

## If you are building with MCP

- Use the server address `https://app.warerushai.com/mcp` and the standard OAuth 2.1 discovery documents of the same host; clients register dynamically and use PKCE.
- Request only the scopes you need: `catalog.read`, `inventory.read`, `orders.read`, `account.read`.
- Expect results to be limited by the signed-in user's role and company.
- Tool list and behaviour: [MCP connector guide](mcp-connector.md).

## Product documentation

- User guide (every screen, step by step): https://warerushai.com/guide
- Troubleshooting by channel (known errors and fixes): https://warerushai.com/guide/troubleshooting-allegro and the other `troubleshooting-` chapters in the guide index
- Pricing: https://warerushai.com/pricing
