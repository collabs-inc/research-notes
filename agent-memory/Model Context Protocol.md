---
tags: [concept, standard, protocol, interoperability, mcp]
created: 2026-05-27
---

# Model Context Protocol

MCP (Model Context Protocol) is the emerging standard for connecting AI agents to external tools and data sources. Donated to the Linux Foundation in December 2025. Relevant to agent memory because it commoditizes the *integration layer* between agents and memory backends.

## Adoption (PyPI + npm, verified)

- **Python `mcp` SDK**: 1.09B total PyPI downloads, 269M/month (May 2026)
- **npm `@modelcontextprotocol/sdk`**: ~24.5M/month
- **Combined**: ~293M monthly SDK downloads
- Growth trajectory: 2M/mo (Nov 2024) → 22M (Apr 2025, OpenAI adopted) → 45M (Jul 2025, Microsoft joined) → 68M (Nov 2025, AWS) → 97M (Mar 2026)
- All major [[Memory Middleware Players|memory vendors]] are moving toward MCP support

## Why It Matters for Memory

MCP standardizes how agents connect to memory services. This means:
- Any MCP-compatible memory service can plug into any MCP-compatible agent
- Switching costs between memory providers decrease
- Competition shifts from *integration breadth* to *memory quality*

Before MCP, each memory provider needed custom integrations with each agent framework (21+ for [[Mem0]]). With MCP, one server implementation covers all MCP clients.

## Implementations

- **[[Zep]] Graphiti MCP Server v1.0** (November 2025) -- temporal knowledge graph accessible from Claude Desktop, Cursor, or any MCP client
- **Neo4j MCP Server** -- natural language querying and memory persistence via graph
- **[[Hindsight]] MCP Server** -- agent memory via Docker
- **Obsidian MCP servers** -- community-built bridges connecting Obsidian vaults to agents (see grassroots memory practices)

## Competitive Implications

MCP is an equalizer. When integration is standardized:
- [[Mem0]]'s "21+ integrations" moat erodes
- [[Zep]]'s retrieval quality advantage becomes more visible
- Smaller players ([[Hindsight]], EverOS) can compete without building integration by integration
- Users can swap memory backends without changing agent code

See [[Competitive Dynamics#Standards: MCP as Equalizer]].

## See Also

- [[Competitive Dynamics]] -- how MCP reshapes the market
- [[Memory Middleware Players]] -- the companies affected
- [[Hybrid Memory Architectures]] -- what sits behind the MCP interface
