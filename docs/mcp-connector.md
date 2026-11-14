# Connect WareRushAI to Claude, ChatGPT and other MCP assistants

WareRushAI runs a remote **Model Context Protocol (MCP)** server. After you approve access, an MCP-capable AI assistant can read data of **your own WareRushAI company**: products, stock, marketplace listing problems and open orders. In this version the connector is **read-only**: it cannot change, create or delete anything.

- Server address (Streamable HTTP): `https://app.warerushai.com/mcp`
- Authorization: OAuth 2.1 with PKCE (S256) and dynamic client registration; discovery documents at the standard `/.well-known/` addresses of the same host.
- Full, always-current guide on the website: https://warerushai.com/guide/developers-mcp-connector

## Requirements

- A WareRushAI account that belongs to a company.
- An assistant plan that supports adding a custom remote MCP connector (menu names differ by product and plan; some call it an app or a connector).
- You sign in with your normal WareRushAI login. The connector never sees your password.

## How to connect

1. In your assistant, add a custom connector / remote MCP server and enter `https://app.warerushai.com/mcp`.
2. The assistant registers itself and opens a WareRushAI approval page. There you see which app asks for which access for which company.
3. Choose **Allow** to grant read access or **Deny** to refuse. You can revoke access at any time.

To connect another company, switch company in WareRushAI first and start the connection again.

## Tools

All tools are read-only. A tool is offered to an assistant only if the granted scope **and** your role allow it; financial data is visible to owners and administrators only.

| Tool | Scope | What it returns |
| --- | --- | --- |
| `get_account_info` | `account.read` | The company of the signed-in user, their role, subscription plan and enabled modules. |
| `list_warehouses` | `inventory.read` | Warehouses/locations of the company and which one is linked to a Shopify location. |
| `search_products` | `catalog.read` | Products by name, SKU, barcode, brand or model: a short row per product (price, category, stock), paginated. |
| `get_product` | `catalog.read` | One product's data, stock per location and marketplace listing status. |
| `get_inventory_summary` | `inventory.read` | Total stock quantity per location. |
| `find_missing_product_data` | `catalog.read` | Products that lack data required for selling, with what is missing; paginated. |
| `find_listing_problems` | `catalog.read` | Products that did not get listed on a marketplace/channel, with the error and a plain-language fix. |
| `find_unfulfilled_orders` | `orders.read` | Open webshop, marketplace and B2B orders that have not been shipped yet. |

Details: https://warerushai.com/guide/developers-mcp-tools

## Example questions

- "Which of my products are missing data needed for selling?"
- "Which products did not go live on Allegro, and why?"
- "How much stock do I have in each warehouse?"
- "Which orders are waiting to be fulfilled?"

## Security and privacy in short

- Every call runs as the signed-in user inside exactly one company, with the same permission and isolation code as the web application.
- Every tool call is logged (tool name, outcome, duration). Tokens can be revoked at any time.
- Tools return short summaries and only the fields an assistant needs.
- Where data is processed by the assistant provider, that provider's terms and privacy policy apply.

More: https://warerushai.com/guide/developers-security-privacy

## Status

The connector works today with the address above. Listing in the public Claude and ChatGPT connector directories and in the MCP registry is being prepared; until then, add it as a custom connector. Write actions (always preview plus an explicit one-time approval) are planned, not available.

This repository does not apply beyond what the website states; the website is the source of truth for current availability.
