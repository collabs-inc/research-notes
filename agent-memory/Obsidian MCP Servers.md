---
tags: [tool, mcp, obsidian, integration]
created: 2026-05-27
---

# Obsidian MCP Servers

[[Model Context Protocol|MCP]] servers that connect Obsidian vaults to AI coding agents, enabling agents to read, search, and write vault notes.

## Key Implementations

| Server | Stars | Approach | Notes |
|--------|-------|----------|-------|
| **mcp-obsidian** | 3,791 | Requires Obsidian's Local REST API plugin running | Most established. Works with Claude Desktop, Claude Code, Cursor, Windsurf. |
| **MCPVault** | 1,312 | Reads raw .md files directly, BM25 search | Zero-dependency. No Obsidian app required. Recommended for new installs. |
| **obsidian-claude-code-mcp** | -- | Purpose-built for Claude Code | Focused integration for Claude Code workflows. |

## Claude Code Hooks Integration

Beyond MCP, Claude Code hooks enable automatic memory management with Obsidian:

- **Pre-session hook**: Fires before the agent sees user input, injecting relevant vault files into context
- **Post-session hook**: Extracts lessons, patterns, and decisions from the session and writes them back to the vault
- **Post-compaction hook**: Re-inserts core identity when context compresses during long sessions

This creates a "compounding knowledge loop" -- each session makes future sessions better. Documented at MindStudio's blog on self-evolving Claude Code memory with Obsidian hooks.

## Obsidian Plugins

| Plugin | Stars / Downloads | Function |
|--------|-------------------|----------|
| **Smart Connections** | 4,700 stars, 853K downloads | RAG with local embeddings. Chat with entire vault. Works offline. |
| **Copilot for Obsidian** | 6,400 stars | AI assistant within the vault. |
| **Claudian** | 11,941 stars | Embeds Claude Code CLI directly in Obsidian sidebar. |
| **Agent Client** | -- | Built on Agent Client Protocol (ACP). Brings coding agents into vault workspace. |

## Vault-as-Memory Projects

| Project | Approach |
|---------|----------|
| **obsidian-mind** | 15 slash commands, 9 subagents, 5 lifecycle hooks. Auto-loads context on startup, updates indexes on shutdown. `npm install -g shardmind`. |
| **obsidian-memory-for-ai** (v3.1) | "Agentic Atomic Markdown Memory." No database, no daemon, no vector store. Just Markdown + YAML. |
| **claude-code-memory-setup** | Claims 71.5x fewer tokens using Obsidian + Graphify (tree-sitter AST). Generates 456 notes from a codebase. |
| **claude-obsidian** | Based on [[Karpathy LLM Wiki]] pattern. `/wiki`, `/save`, `/autoresearch` commands. 5,500+ stars. |
| **obsidian-second-brain** | 32 commands, vault-first research, scheduled agents. Works across Claude Code, Codex CLI, Gemini CLI, OpenCode. |

## See Also

- [[Obsidian Vaults as Agent Memory]] -- the broader phenomenon
- [[Model Context Protocol]] -- the standard these servers implement
- [[Why Obsidian for Agent Memory]] -- why Obsidian specifically
