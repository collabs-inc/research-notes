---
tags: [company, middleware, memory-service, virtual-memory, memgpt]
created: 2026-05-27
---

# Letta

The agent-controlled memory pioneer. Originally [[Generative Agents|MemGPT]] (the paper), now a company building on the OS-inspired virtual memory architecture.

## Company

- **Origin**: Berkeley AI Research Lab (BAIR) spinout
- **Funding**: $10M seed (Sep 2024, Felicis). Angels: Jeff Dean (Google DeepMind), Clem Delangue (HuggingFace), Cristobal Valenzuela (Runway).
- **GitHub**: 22,999 stars, 2,452 forks (verified May 27 2026)
- **PyPI**: 709K total downloads, ~125K/month (~4.2K/day)
- **Revenue**: ~$1.4M ARR (reported 2025, via GetLatka) -- only publicly reported revenue figure among [[Memory Middleware Players]]
- **Pricing**: $0.00015/sec API / $5-10/mo self-hosted / Enterprise

## Architecture: Virtual Memory for LLMs

Treats the LLM context window as virtual memory, inspired by operating systems. Two-tier model:

- **Main context** -- actively managed in-window memory ("RAM")
- **External context** -- recall storage (recent history) + archival storage (long-term facts) ("disk")

The agent manages its own memory via function calls:
- `core_memory_replace` -- update working memory
- `archival_memory_insert` -- store to long-term
- `archival_memory_search` -- retrieve from long-term

**Key differentiator**: The *agent itself* decides what to remember and forget, rather than an external system making those decisions. This is architecturally distinct from [[Mem0]], [[Zep]], and other middleware where memory operations are system-controlled.

## Key Milestones

- **Oct 2025**: New agent architecture optimized for frontier reasoning models
- **Oct 2025**: Letta Evals -- open-source evaluation for stateful agents
- **Jan 2026**: Conversations API for shared memory across parallel experiences
- **Apr 2026**: Letta Code -- memory-first coding agent
- **Benchmark**: #1 model-agnostic open-source agent on Terminal-Bench

## Strategic Position

More "agent framework with deep memory" than pure middleware. Less directly competitive with [[Mem0]]/[[Zep]] because the architecture is fundamentally different. Pluggable backends mean it can use any storage layer underneath.

## See Also

- [[Hybrid Memory Architectures#The Virtual Memory Alternative]]
- [[Short-Term Memory]] -- the constraint Letta's architecture directly addresses
- [[Agentic Memory]] -- the broader trend Letta pioneered
