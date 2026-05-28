---
tags: [tool, pattern, cline, roo-code, memory-bank, grassroots]
created: 2026-05-27
---

# Cline Memory Bank

The most widely adopted template for [[Obsidian Vaults as Agent Memory|project-local agent memory]]. Originally created by Nick Baumann and documented in the Cline docs. The core instruction tells the agent: *"You are an expert software engineer with memory that resets between sessions."*

## How It Works

A `memory-bank/` directory at the project root with structured files:

| File | Purpose |
|------|---------|
| `projectbrief.md` | High-level project description and goals |
| `activeContext.md` | Current focus, recent changes, immediate next steps |
| `progress.md` | What's done, what's remaining |
| `systemPatterns.md` | Architectural decisions, coding conventions |
| `techContext.md` | Tech stack, dependencies, infrastructure |
| `decisionLog.md` | Key decisions and their rationale |

The agent **must read ALL memory bank files at the start of EVERY task**. It updates them as work progresses. The `.clinerules` file serves as a learning journal.

## Adoption

**Cline itself**: 62,417 GitHub stars, 6,549 forks, 5M+ installations (verified May 27 2026). Memory Bank is one of the most-used community features.

Ecosystem repos:
- **cursor-memory-bank**: 3,034 stars, 440 forks
- **roo-code-memory-bank**: 1,674 stars, 189 forks
- **roo-advanced-memory-bank**: 120 stars
- **Cline memory bank MCP server**: 851 stars
- **nickbaumann98/cline_docs** (original template): 582 stars

Adopted nearly verbatim by **Roo Code** (now Kilo Code). Ported to **Cursor**, **Claude Code** (via CLAUDE.md), and **Copilot**. Formalized by **Tweag's Agentic Coding Handbook** as a standard workflow pattern alongside spec-first, exploratory, and debug workflows.

The Tweag handbook lent institutional legitimacy to what had been a grassroots practice, placing memory banks alongside spec-first, exploratory, and debug workflows.

## Design Principles

1. **Session-boundary aware** -- assumes total memory loss between sessions
2. **Read-everything-first** -- agent loads full context before any action
3. **Update-as-you-go** -- memory evolves during the session, not just at the end
4. **Human-readable** -- plain markdown, inspectable and editable by the user
5. **Git-friendly** -- can be committed alongside code

## Limitations

This pattern inherits all the [[Limitations of Vault-Based Memory|limitations of vault-based memory]]: token bloat as files grow, no semantic search, brute-force context loading, and manual curation overhead. The "read ALL files at start" instruction becomes expensive as the memory bank grows.

## See Also

- [[Obsidian Vaults as Agent Memory]] -- the broader phenomenon
- [[Karpathy LLM Wiki]] -- an alternative structural pattern
- [[Short-Term Memory]] -- the context window constraint this works around
