---
tags: [tool, user-integrated, memory-system, portable, grassroots]
created: 2026-05-27
---

# Claude-Mem

A persistent memory system that captures agent sessions, compresses them with AI, and injects relevant context into future sessions. Despite the Claude branding, explicitly supports Claude Code, OpenClaw, Codex, Gemini, Hermes, Copilot, OpenCode, and more. Apache 2.0 licensed.

- **GitHub**: thedotmack/claude-mem -- 79.2K stars, 6.8K forks (verified May 27 2026)
- **License**: Apache 2.0, explicitly chosen to enable embedding in "developer tools, local agents, MCP servers, enterprise systems, robotics stacks, and production agent harnesses"

## Architecture

More sophisticated than typical [[Obsidian Vaults as Agent Memory|grassroots memory]] — has actual retrieval infrastructure, not just brute-force file loading.

**Lifecycle hooks** (6): SessionStart, UserPromptSubmit, PostToolUse, Stop, SessionEnd, plus a Smart Install pre-hook for dependency checking. Hooks capture what happens during sessions automatically.

**Storage**: SQLite database storing sessions, observations, and summaries. FTS5 full-text search.

**Retrieval**: Hybrid system combining Chroma vector database with keyword search. Uses a "3-layer workflow pattern" for token efficiency — search returns index IDs first, user/agent fetches full details selectively. Claims ~10x token savings over brute-force context loading.

**MCP tools** (4): `search` (index queries), `timeline` (chronological context), `get_observations` (batch fetching), `mem-search` (natural language queries with progressive disclosure).

**Worker service**: Local HTTP API (port 37777) with web viewer UI, managed by Bun runtime. 10 search endpoints. Runs entirely on the user's machine.

## Where It Sits in the Market

Claude-Mem is the most prominent example of the [[User-Integrated Memory Gap|user-integrated memory product]] category:

- **User-integrated**: the user installs it, it runs locally, the user is the customer and the integration decision maker
- **Portable**: works across agent providers via hooks and MCP, despite the Claude branding
- **Addresses grassroots ceilings**: real retrieval (hybrid vector + keyword), AI-powered compression/consolidation, token efficiency, structured storage (SQLite, not raw markdown)
- **Preserves grassroots strengths**: local-first, user-controlled, runs on the user's machine

On the [[Market Structure and Value Chain|market structure]] axes:
- **Standalone** -- memory is the product, not a feature inside something else
- **Specialized** (more than grassroots, less than middleware) -- has vector search and structured retrieval, but aimed at individual users rather than developer integration
- **User-integrated** -- the user chose and installed it

The name is instructive: branded after a specific agent ("claude-mem") but portable across agents. This mirrors the broader grassroots pattern where tools are agent-branded even though the underlying capability is agent-agnostic.

## See Also

- [[User-Integrated Memory Gap]] -- the market gap this addresses
- [[Obsidian Vaults as Agent Memory]] -- the grassroots approach it builds on
- [[Limitations of Vault-Based Memory]] -- the ceilings it addresses
- [[Claude Managed Agents Memory Store]] -- Anthropic's developer-integrated file-based approach (different product, similar bet on model reasoning)
