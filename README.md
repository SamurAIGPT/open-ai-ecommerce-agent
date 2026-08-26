# AI E-Commerce Agent

An AI agent for e-commerce and CRO — Amazon review mining, marketplace intelligence, local business leads, and cross-border expansion research — backed by real marketplace and maps APIs.

Part of [Agency Agents OS](https://github.com/Anil-matcha/agency-agents-os), an open ecosystem of specialized AI agents for real business work.

## Related Projects

- [Agency Agents OS](https://github.com/Anil-matcha/agency-agents-os) — the central catalog this repo is part of.
- [ai-seo-agent](https://github.com/SamurAIGPT/ai-seo-agent) — its live local-SEO endpoints (`seo.business_listings`, `seo.business_profile`, `seo.local_serp`) overlap with this repo's local-business-leads sub-agent.
- [ai-competitor-intelligence-agent](https://github.com/SamurAIGPT/ai-competitor-intelligence-agent) — cross-cuts this repo's marketplace intelligence with ads and social data.
- [ai-reputation-agent](https://github.com/SamurAIGPT/ai-reputation-agent) — shares this repo's Amazon/Google review-data needs.
- [MuAPI MCP docs](https://muapi.ai/docs/mcp) — connect this repo's `SKILL.md` files via MCP.
- [MuAPI access keys](https://muapi.ai/access-keys) — create the API key this agent needs.

## What this covers

This repo is the umbrella for anything an agency or in-house team would call "the AI e-commerce agent": mining customer reviews for product and CRO decisions, sizing up marketplace competitors, qualifying local business leads, and scoping what a store needs before entering a new country.

## Sub-agents

| Agent | Does | Status |
|---|---|---|
| [Amazon Review Mining](agents/amazon-review-mining/SKILL.md) | Extract themes, complaints, and feature requests from a product's reviews to inform CRO/product decisions | Coming Soon |
| [Amazon Market Intelligence](agents/amazon-market-intelligence/SKILL.md) | Competitor listing, pricing, and ranking analysis for a product category | Coming Soon |
| [Local Business Leads](agents/local-business-leads/SKILL.md) | Find and qualify local business leads via maps/location data | Coming Soon |
| [Cross-Border E-Commerce](agents/cross-border-ecommerce/SKILL.md) | Research market-entry requirements and localization needs for expanding a store to a new country | Coming Soon |

## Required Muapi APIs

- `ecommerce.product_reviews` — pull and structure a product's review history for theme/complaint/feature-request mining.
- `ecommerce.marketplace_search` — competitor listing, pricing, and ranking data for a product category.
- `local.business_search` — maps/location-based business discovery and qualification data.

See each sub-agent's `SKILL.md` for the specific capabilities it uses.

## Setup

1. Create a Muapi account and API key at [muapi.ai](https://muapi.ai).
2. Review the [Muapi API quickstart](https://muapi.ai) and [OpenAPI schema](https://api.muapi.ai/openapi.json) for the e-commerce and local-data endpoints.
3. Load the `SKILL.md` for the sub-agent you need into your agent runtime (hosted agent, MCP client, or custom LLM app), or follow it manually.


## Using with an AI agent

Every sub-agent's `SKILL.md` is model- and runtime-agnostic — it's plain Markdown, so it works with any LLM agent, not just Claude. Two integration paths:

**As an MCP connection (the agent gets live Muapi tools):**

Muapi runs an MCP server at `https://api.muapi.ai/mcp` that any MCP-compatible client can connect to — Cursor, Windsurf, Claude, or your own custom agent.

- **Cursor / Windsurf / other clients with a header field:** connect to `https://api.muapi.ai/mcp` with an `Authorization: Bearer YOUR_MUAPI_KEY` header.
- **claude.ai / Claude Cowork / other connector UIs with no header field:** use the URL-embedded key form instead, `https://api.muapi.ai/mcp/YOUR_MUAPI_KEY`, via Settings → Connectors → Add custom connector.
- **Claude Code / Claude Desktop:** `claude mcp add muapi -e MUAPI_API_KEY=YOUR_MUAPI_KEY -- muapi mcp serve` (uses the muapi CLI's stdio transport — Claude Code's HTTP MCP client doesn't reliably inject tools).

Full setup details for every client: [muapi.ai/docs/mcp](https://muapi.ai/docs/mcp).

**As agent instructions (any LLM follows the workflow directly):**

Drop a sub-agent's `SKILL.md` into a Claude Code project's `.claude/skills/` directory, paste it into a custom-GPT/Project's system instructions, hand it to an autonomous agent framework as a tool spec, or attach it directly in a chat conversation — then ask the agent to follow it.

## Read-only vs. write actions

Every action in this repo is `read-only` — reviews, listings, and business records are pulled and analyzed, never modified or posted. Nothing here writes back to a marketplace, a maps listing, or a storefront.

## Status and limitations

Every sub-agent in this repo is Coming Soon. All four depend on marketplace and maps data capabilities (`ecommerce.*`, `local.*`) that are not yet live on Muapi. Nothing here should be treated as producing real data until those capabilities ship.

## Contributing

See [Agency Agents OS CONTRIBUTING.md](https://github.com/Anil-matcha/agency-agents-os/blob/main/CONTRIBUTING.md).

## License

[MIT](LICENSE)
