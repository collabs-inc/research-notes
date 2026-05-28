---
tags: [company, middleware, memory-service, temporal, knowledge-graph]
created: 2026-05-27
---

# Zep

The temporal reasoning specialist in [[Memory Middleware Players|agent memory middleware]]. Creators of [[Temporal Knowledge Graphs|Graphiti]], the leading temporal knowledge graph for agent memory.

## Company

- **Founded**: 2023
- **Funding**: ~$2.3M total. $500K pre-seed (Mar 2024, YC + Bessemer Venture Partners).
- **GitHub**: Graphiti 26,672 stars, 2,656 forks (verified May 27 2026; grew from 20K in Nov 2025)
- **PyPI**: graphiti-core at 5.69M total downloads, ~542K/month (~18K/day)
- **Pricing**: Free / $25/mo Flex (per-episode billing) / Enterprise (BYOK/BYOM/BYOC)
- **Compliance**: SOC 2 Type II, HIPAA, GDPR -- strongest compliance posture among middleware players

## Architecture: Graphiti

Graphiti is Zep's temporal knowledge graph engine (paper: arXiv:2501.13956, Jan 2025).

Core innovation: **bitemporal edge annotation**. Every fact carries two timestamps:
- **Event time** -- when the event actually occurred
- **Fact validity time** -- when the fact became true and when it was superseded

This directly solves the [[Memory Staleness]] problem. When the user switches from Python to Rust, the old preference edge gets a "superseded_at" timestamp. Retrieval queries filter by temporal validity.

Retrieval combines vector embeddings + BM25 keyword search + graph traversal.

## Key Milestones

- **Apr 2025**: Community Edition deprecated; Graphiti became sole OSS component
- **Nov 2025**: Graphiti MCP Server v1.0 (compatible with Claude Desktop, Cursor, any [[Model Context Protocol|MCP]] client)
- **Late 2025**: Scaled 30x in two weeks; P95 graph search from 600ms to 150ms
- **2026**: FalkorDB backend integration for [[Multi-Agent Shared Memory|multi-agent]] environments with sub-10ms queries

## Benchmarks

- [[Memory Benchmarks|LongMemEval]]: 63.8% (15 points above [[Mem0]]'s 49.0%)
- DMR Benchmark: 94.8% (GPT-4 Turbo) / 98.2% (GPT-4o Mini)

## Strategic Position

Wins on temporal reasoning and enterprise compliance. Smallest funding of the middleware group but strongest technical differentiation. CE deprecation risks community goodwill but focuses resources.

## See Also

- [[Temporal Knowledge Graphs]] -- the architectural pattern Zep pioneered
- [[Memory Staleness]] -- the core problem Graphiti solves
- [[Knowledge Graphs for Memory]] -- broader context
