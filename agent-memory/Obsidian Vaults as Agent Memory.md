---
tags: [phenomenon, grassroots, obsidian, markdown, power-users]
created: 2026-05-27
---

# Obsidian Vaults as Agent Memory

A grassroots phenomenon: coding agent power users building persistent memory systems out of Obsidian vaults and structured markdown files. Since every major coding agent (Claude Code, Cursor, Cline, Roo Code, Windsurf, Aider) loses all context between sessions, users externalize the agent's "memory" into files the agent reads at startup and updates at shutdown.

## Three Workflow Variants

### 1. Project-Local Memory Banks

A `memory-bank/` directory at the project root containing files like `projectbrief.md`, `activeContext.md`, `progress.md`, `systemPatterns.md`, `techContext.md`, `decisionLog.md`. The agent reads all of these at session start and updates them as work progresses. This is the [[Cline Memory Bank]] pattern, widely adopted by Roo Code (now Kilo Code) and ported to Cursor and Copilot.

### 2. Centralized Obsidian Vault

A single Obsidian vault stores decisions, context, progress, and knowledge for *all* projects. Connected to agents via [[Obsidian MCP Servers]], Claude Code hooks, or direct filesystem access. Notes follow Zettelkasten principles (atomic, interlinked, standardized frontmatter). Championed by projects like obsidian-mind and claude-code-memory-setup.

### 3. CLAUDE.md / .cursorrules as Memory Index

The agent's instruction file references structured documentation, becoming a pointer into a knowledge base. CLAUDE.md instructs the agent to read specific vault files in priority order: hot context first, then indexes, then domain sub-indexes, then specific pages.

## Why Obsidian Specifically

See [[Why Obsidian for Agent Memory]] for the full analysis. In short: local-first plain markdown (zero translation for LLMs), existing knowledge graph structure (wikilinks, backlinks), 1,400+ plugins, CLI support (since Feb 2026), git-friendly, data sovereign, and free.

## The Karpathy Catalyst

In April 2026, Andrej Karpathy posted about using LLMs to build personal knowledge bases rather than primarily for code generation. The post went viral (16M+ views). His [[Karpathy LLM Wiki]] pattern -- `raw/` (immutable sources), `wiki/` (LLM-generated pages), `CLAUDE.md` (schema) -- became the most viral single contribution to this ecosystem and spawned dozens of implementation repos (5,000+ stars on the GitHub Gist).

## Who Does This

- **Senior engineers** managing complex projects across many sessions
- **AI automation engineers** building agent workflows
- **"Vibe coders"** -- non-traditional developers using AI agents who need memory *more* because they lack the mental model to re-explain context
- **Knowledge management enthusiasts** who were already Obsidian power users
- **Design/product leaders** incorporating AI into workflows (e.g., Jason Cyr, VP Design at Cisco)

## Relationship to Formal Memory Systems

This practice is a bottom-up, human-curated version of what [[Memory Middleware Players|memory middleware]] attempts to automate. The tradeoffs:

| | Obsidian Vault | [[Mem0]] / [[Zep]] / [[Letta]] |
|---|---|---|
| Encoding | Human-curated | Automated extraction |
| Storage | Plain markdown files | Vector DB + graph + KV |
| Retrieval | Brute-force file read | Semantic search + ranking |
| Maintenance | Manual | Automated |
| Scalability | Breaks at ~hundreds of notes | Handles millions of memories |
| Transparency | Full (you can read every note) | Opaque (embeddings, scores) |
| Cost | Free | API calls, infrastructure |

The [[A-MEM]] paper's Zettelkasten inspiration connects directly to this practice -- the same self-organizing principles human note-takers use are being formalized into agent memory architecture.

## Limitations

See [[Limitations of Vault-Based Memory]] for the full breakdown. Key issues: token bloat, [[Memory Staleness|context rot]], no enforced schema, concurrency problems, and the "brute force" problem (dumping files into context is not querying).

## See Also

- [[Cline Memory Bank]] -- the most widely adopted template
- [[Obsidian MCP Servers]] -- tools connecting vaults to agents
- [[Karpathy LLM Wiki]] -- the viral pattern that catalyzed adoption
- [[Limitations of Vault-Based Memory]] -- what breaks
- [[Why Obsidian for Agent Memory]] -- platform properties
- [[Agentic Memory]] -- the formal research parallel
