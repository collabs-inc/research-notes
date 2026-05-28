---
tags: [ecosystem, open-source, agents, memory, openclaw, hermes, clawlikes]
created: 2026-05-27
---

# OpenClaw and Clawlikes

The largest open-source AI agent ecosystem by stars (375K+ for OpenClaw, 170K+ for Hermes Agent). Started as a messaging relay, evolved into a platform with a sprawling satellite ecosystem of memory plugins, skill registries, and derivative projects collectively called "clawlikes."

Memory is the defining extension point: OpenClaw itself has minimal built-in memory, while the ecosystem has generated a dozen competing memory systems that plug into it.

## OpenClaw

**What it is**: An open-source personal AI assistant that runs locally and connects to 20+ messaging platforms (WhatsApp, Telegram, Slack, Discord, Signal, iMessage, Teams, etc.).

- **Creator**: Peter Steinberger (`steipete`), dominant contributor (30K+ commits)
- **Stars**: 375,107 stars, 78,219 forks. Created Nov 24, 2025.
- **Stack**: TypeScript, Node 24, pnpm. MIT-adjacent license.
- **Naming history**: WhatsApp Relay (Nov 2025) → Clawd (Anthropic requested rename) → Moltbot (Dec 2025) → OpenClaw (Jan 2026). Lobster mascot "Molty" persists.

**Architecture**:
- Local-first control plane managing sessions, channels, tools, events
- Multi-agent routing: inbound channels/accounts route to isolated agents with separate workspaces
- Skills system: `~/.openclaw/workspace/skills/<skill>/SKILL.md` format, compatible with the agentskills.io open standard
- Companion apps: macOS menu bar, iOS/Android pairing via WebSocket
- Voice: wake words on macOS/iOS, ElevenLabs or system TTS

**Built-in memory**: Minimal. Three injected prompt files:
- `AGENTS.md` -- agent configuration
- `SOUL.md` -- personality/behavior (the core identity file)
- `TOOLS.md` -- available tools

Persistent workspace at `~/.openclaw/workspace`. No built-in retrieval, consolidation, or reasoning -- memory depth comes entirely from plugins.

**Controversy**:
- Anthropic briefly restricted Claude Code usage for OpenClaw users (Apr 2026, 1,099-point HN thread)
- Privilege escalation CVE (CVE-2026-33579) prompted security-focused alternatives
- Creator Peter Steinberger announced joining OpenAI (Feb 2026); OpenClaw moved to a foundation

## Hermes Agent

**What it is**: An autonomous, self-improving AI agent by NousResearch. The more opinionated, Python-based sibling to OpenClaw.

- **Stars**: 170,350 stars, 28,485 forks. Created Jul 22, 2025. MIT License.
- **Built by**: NousResearch (makers of the Hermes LLM series)
- **Stack**: Python, 300+ model providers, 40+ built-in tools, six terminal backends (local, Docker, SSH, Singularity, Modal, Daytona)
- **Interop**: `hermes claw migrate` imports SOUL.md, memories, skills, configs from OpenClaw
- **Skills**: agentskills.io compatible. Autonomous skill creation during use.

**Memory system** (more sophisticated than OpenClaw's):

Two bounded markdown files injected at session start:
- `MEMORY.md` (~2,200 chars / ~800 tokens) in `~/.hermes/memories/`
- `USER.md` (~1,375 chars / ~500 tokens) in `~/.hermes/memories/`

Injected as a frozen snapshot (preserves LLM prefix caching). The `memory` tool uses add/replace/remove actions with `§` delimiters. At 80%+ capacity, auto-consolidation triggers.

**Session search**: FTS5 full-text search over all sessions in SQLite (`~/.hermes/state.db`, ~20ms latency). Queries past conversations without LLM summarization.

**Security**: Memory entries scanned for prompt injection and credential exfiltration patterns.

**Eight pluggable memory providers** (one active at a time, alongside built-in):

| Provider | Approach | Hosting | Notes |
|----------|----------|---------|-------|
| [[Honcho]] | Dialectic user modeling | Cloud | 5 tools, Theory of Mind |
| **OpenViking** | Filesystem hierarchy | Self-hosted | AGPL |
| [[Mem0]] | Automatic extraction | Cloud | |
| [[Hindsight]] | Knowledge graph + entity resolution | Local or cloud | |
| **Holographic** | HRR (Holographic Reduced Representations) | Local SQLite | Algebraic queries |
| **RetainDB** | Delta compression + hybrid search | Cloud ($20/mo) | |
| **ByteRover** | Pre-compression extraction | Local-first | |
| **Supermemory** | Semantic recall + user profiling | Cloud | |

## The Clawlike Ecosystem

Satellite projects inspired by or built around the OpenClaw/Hermes architecture:

### Major Projects

| Project | Stars | What it does |
|---------|-------|--------------|
| **[[Claude-Mem]]** (`thedotmack/claude-mem`) | 79,200 | Persistent memory compression for Claude Code and other agents. 5 lifecycle hooks, SQLite + Chroma, 3-layer progressive disclosure (10x token savings). |
| **VoltAgent/awesome-openclaw-skills** | 49,400 | 5,400+ skills from the OpenClaw Skills Registry |
| **NanoClaw** (`nanocoai/nanoclaw`) | 29,473 | Lightweight OpenClaw using Docker isolation. Security-focused response to CVE-2026-33579. Claude Agent SDK, SQLite per session. |
| **GBrain** (`garrytan/gbrain`) | 19,437 | Memory/knowledge layer by Garry Tan (YC CEO). PGLite/Postgres dual engine, self-wiring knowledge graph, 43 skills, 30+ MCP tools. Powers 146K+ pages. |
| **AgentMemory** (`rohitg00/agentmemory`) | 18,700 | Framework-agnostic memory. 4-tier hierarchy, 12 lifecycle hooks, BM25 + vectors + graph, 53 MCP tools. |
| **memU** (`NevaMind-AI/memU`) | 13,700 | Memory-as-filesystem for 24/7 agents. Resources/Items/Categories hierarchy. Self-described "enterprise-ready OpenClaw." |
| **MemOS** (`MemTensor/MemOS`) | 9,400 | Memory OS claiming +43.7% over OpenAI Memory. Multi-modal, async MemScheduler. Academic paper published. |
| **OpenClaw-RL** (`Gen-Verse/OpenClaw-RL`) | 5,400 | RL training from conversation feedback. arXiv:2603.10165. |
| **OpenClaw Mission Control** | 4,000 | Governance dashboard for team deployments. Approval workflows, audit trails. |
| **Clawith** (`dataelement/Clawith`) | 3,900 | Multi-agent collaboration ("OpenClaw for Teams"). Per-agent `soul.md` + `memory.md` + private filesystem. |
| **awesome-openclaw-agents** | 3,500 | 205 production-ready SOUL.md templates across 24 categories |

### Smaller Projects

- **n8n-claw** (447 stars): OpenClaw-inspired agent in n8n with adaptive RAG memory
- **NovelClaw** (303 stars): Dynamic-memory-first framework for long-form story generation
- **ChatClaw** (286 stars): Go-based "OpenClaw-like knowledge base agent in 5 mins"
- **ClawMem** (176 stars): On-device memory for Claude Code, Hermes, OpenClaw
- **ShibaClaw** (88 stars): Self-hosted agent with 3-level memory architecture
- **OpenAtta** (Rust): "Claw-like AI agent with enterprise features"
- **OpenCrane** (TypeScript): Wraps OpenClaw with organizational awareness

## Memory as the Extension Point

The ecosystem's memory landscape mirrors the broader [[Market Structure and Value Chain|market structure]]:

| Layer | Examples |
|-------|----------|
| **Built-in** (minimal, file-based) | OpenClaw's SOUL.md, Hermes's MEMORY.md + USER.md |
| **User-integrated** (community plugins) | Claude-Mem, AgentMemory, GBrain, ClawMem |
| **Middleware** (external services) | [[Honcho]], [[Mem0]], [[Hindsight]], Supermemory |
| **Experimental** (novel architectures) | Holographic (HRR), MemOS (graph OS), OpenClaw-RL (RL from memory) |

This makes the clawlike ecosystem a microcosm of the broader agent memory market -- every approach (file-based, vector, graph, reasoning, hybrid) is represented, competing for adoption within the same user base.

## Shared Infrastructure

**agentskills.io**: Open standard for portable agent skills (`SKILL.md` format). Originally developed by Anthropic, now adopted by 35+ products including Claude Code, Cursor, GitHub Copilot, Gemini CLI, OpenAI Codex. The shared skill format is the primary interop mechanism between OpenClaw and Hermes.

**MCP**: GBrain (30+ tools), AgentMemory (53 tools), MemOS, NanoClaw, OpenClaw, and Hermes all support [[Model Context Protocol|MCP]] servers.

## Relationship to OpenAI

"Claw" is NOT an OpenAI codename -- it derives from the lobster/crustacean mascot. However, creator Peter Steinberger announced joining OpenAI in Feb 2026 to "bring agents to everyone." OpenClaw was moved to a foundation to remain independent. The project supports multiple LLM providers, not just Claude.

## See Also

- [[Honcho]] -- the most architecturally distinctive memory provider in the ecosystem
- [[Obsidian Vaults as Agent Memory]] -- parallel grassroots phenomenon, different community
- [[Cline Memory Bank]] -- the "clawlike" equivalent for coding agents
- [[Memory Middleware Players]] -- how middleware serves this ecosystem
- [[Model Context Protocol]] -- integration standard used across the ecosystem
