---
tags: [company, middleware, memory-service, reasoning, theory-of-mind, cognitive-science]
created: 2026-05-27
---

# Honcho

The reasoning-first entrant in [[Memory Middleware Players|agent memory middleware]], built by Plastic Labs. Where [[Mem0]] retrieves what was explicitly said, Honcho performs multi-step logical reasoning to extract *latent* insights. Where [[Zep]] tracks temporal validity, Honcho models directional peer relationships with computational Theory of Mind.

## Company: Plastic Labs

- **Founded**: Late 2023 (GitHub repo created Sep 2023)
- **Funding**: Pre-seed (Variant Fund, betaworks, Mozilla Ventures, Greycroft, Seed Club Ventures, White Star Capital, Differential). Amount undisclosed.
- **Team**: 8 people. Vince Trost (CEO, ML), Vineeth Voruganti (CTO, Systems), Courtland Leer (President, Cognitive Science).
- **Mission**: "Continual learning system for modeling personal identity"
- **GitHub**: 4,402 stars, 508 forks
- **License**: AGPL-3.0 (server), Apache-2.0 (SDK)
- **Other products**: YouSim (identity simulation, 135 stars), Tutor-GPT/Bloom (AI tutor, 905 stars), Neuromancer (custom reasoning models)

## Architecture: Four Primitives

| Primitive | Purpose |
|-----------|---------|
| **Workspace** | Top-level isolation (one per app) |
| **Peer** | Any participant -- human OR agent -- treated as first-class entity |
| **Session** | Temporal interaction boundary (conversation, task, channel) |
| **Message** | Atomic data unit attributed to a peer, ordered chronologically |

The key design choice: **peers are directional**. Each peer has a separate representation of every other peer via `(observer, observed)` pairs. This enables information asymmetry -- what one agent "knows" about a user can differ from what another agent knows, modeling Theory of Mind computationally.

## The Honcho Loop

1. **Store** -- Messages written to PostgreSQL; non-blocking writes
2. **Reason** -- Background async workers ("deriver") trigger when pending tokens cross ~1,000, generating structured logical conclusions via Neuromancer XR (custom-trained reasoning model, not publicly available)
3. **Query** -- Developers retrieve context via `session.context()` or `peer.chat()` with five dialectic reasoning levels (minimal → max, $0.001 → $0.50/query)
4. **Inject** -- Results formatted via `.to_openai()` / `.to_anthropic()` helpers

The reasoning pipeline:
1. Explicit extraction (stated premises)
2. Deductive reasoning (certain conclusions from premises)
3. Pattern identification (cross-conclusion patterns)
4. Abductive inference (simplest explanations for behavior)
5. Induction (patterns across 2+ source conclusions)
6. Consolidation (resolve redundant/contradictory information)
7. Peer card generation (stable biographical facts, max 40 per card)

## Storage and Retrieval

**Backend**: PostgreSQL + pgvector (default). Swappable vector backends: pgvector, LanceDB, Turbopuffer. Optional Redis cache.

**Embeddings**: Configurable. Default OpenAI `text-embedding-3-small` (1536 dims). Supports `nomic-embed-text` or any OpenAI-compatible endpoint.

Three types of stored representations:
- **Conclusions** -- Vector-embedded insights from logical reasoning, stored per `(observer, observed)` pair
- **Summaries** -- Short (every 20 messages, 1K tokens) and long (every 60 messages, 4K tokens), recursively compressed
- **Peer cards** -- Stable biographical facts extracted from conclusions

Retrieval modes:
- `session.context(tokens=N)` -- Assembles summary (40%) + recent messages (60%) within token budget
- `peer.chat(query, reasoning_level=...)` -- Natural language query searching conclusions + synthesis
- `peer.search()` / `session.search()` -- Direct search with filtering

## Dreaming (Consolidation)

Triggers at 50+ new conclusions, 8+ hours since last dream, 60-min idle timeout. Two-agent process: Deduction Agent (resolves contradictions) then Induction Agent (finds behavioral patterns). Operates at `(workspace, observer, observed)` level.

Conceptually similar to [[Claude Managed Agents Memory Store#Dreams (Async Memory Consolidation)|Anthropic's Dreams]] -- both are async consolidation modeled on hippocampal sleep replay. See [[Memory Operations#Consolidation]].

## API and SDKs

**Managed service**: `api.honcho.dev` ($100 free credits on signup)

SDKs: Python (`honcho-ai` on PyPI, v2.1.2), TypeScript (`@honcho-ai/sdk`), CLI (`honcho-cli`). Self-hostable via Docker Compose.

**MCP**: First-class support at `mcp.honcho.dev`. Works with Claude Desktop, Claude Code, Cursor, Windsurf, Copilot, Cline, Zed, Codex.

**Integrations**: LangGraph, CrewAI (`honcho-crewai`), Vercel AI SDK, n8n, [[OpenClaw and Clawlikes|OpenClaw]], [[OpenClaw and Clawlikes|Hermes Agent]], SillyTavern, Discord, Telegram, Gmail.

## Pricing

| Component | Price |
|-----------|-------|
| Memory ingestion (storage + reasoning) | $2.00 / M tokens |
| `context()` calls | Unlimited (~200ms) |
| Dreaming | Included |
| Dialectic minimal | $0.001 / query |
| Dialectic low | $0.01 / query |
| Dialectic medium | $0.05 / query |
| Dialectic high | $0.10 / query |
| Dialectic max | $0.50 / query |

Startup program: $1,000 credits for 12 months (<$5M raised). Enterprise: custom.

Notable pricing model: charges for ingestion, not retrieval. Opposite of most middleware.

## Benchmarks

- **LongMemEval S**: 90.4%
- **LoCoMo**: 89.9%
- **BEAM 100K**: 0.630

Results stored in `plastic-labs/honcho-benchmarks` repo (commit-hash reproducibility). Detailed methodology and competitor comparisons not publicly broken down.

## Strategic Position

Not a pure middleware play -- more "cognitive science applied to agent memory." The reasoning pipeline and Theory of Mind modeling are genuinely novel in the space. The AGPL license creates friction for enterprises who want to self-host and modify. The custom Neuromancer XR model is a moat but also a black box (not on HuggingFace, no papers).

Competes with [[Mem0]] on developer-facing memory middleware but with a fundamentally different philosophy: reason at write time, not just retrieve at query time. The five-tier dialectic pricing lets developers trade cost for reasoning depth per query.

## See Also

- [[Memory Middleware Players]] -- competitive context
- [[Agentic Memory]] -- Honcho's reasoning pipeline is an example of agent-directed memory
- [[Memory Operations#Consolidation]] -- Honcho's Dreaming feature
- [[Memory Benchmarks]] -- evaluation context
- [[OpenClaw and Clawlikes]] -- major integration partner
