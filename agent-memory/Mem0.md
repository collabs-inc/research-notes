---
tags: [company, middleware, memory-service]
created: 2026-05-27
---

# Mem0

The market leader in [[Memory Middleware Players|agent memory middleware]] by community size and distribution.

## Company

- **Founded**: 2024 (YC-backed)
- **Funding**: $24M Series A (Oct 2025). Lead: Basis Set Ventures. Participants: Peak XV Partners, Y Combinator, GitHub Fund. Angels: Scott Belsky, Dharmesh Shah, CEOs of Datadog, Supabase, PostHog.
- **GitHub**: 56,909 stars, 6,476 forks (verified May 27 2026)
- **Pricing**: Free (10K memories) / $19/mo / $249/mo Pro / Enterprise. Startup program: 3 months free Pro for companies under $5M funding.

## Architecture

Hybrid multi-store: [[Vector Databases for Memory|vector]] ([[Qdrant]]) + [[Knowledge Graphs for Memory|graph]] (Neo4j) + key-value store.

- Graph traversal for entity-linked memories
- Temporal recency weighting
- Metadata filters for user/session scoping
- 21+ framework integrations, 20 vector store backends

**Token-efficient algorithm** (Apr 2026): single-pass hierarchical extraction cuts write-time LLM calls by 60-70%. Multi-signal retrieval at ~7K tokens per query vs. 25-100K for full-context approaches. +29.6 points on temporal queries, +23.1 on multi-hop reasoning.

## Traction

- API calls: 35M (Q1 2025) → 186M (Q3 2025) -- ~30% MoM growth (from Series A announcement, verified by TechCrunch)
- 80,000+ developers on cloud service (same source)
- **PyPI**: 30M total downloads, ~3M/month (~101K/day) as of May 2026
- Published at ECAI 2025 (first broad benchmark of 10 memory approaches on LoCoMo)
- Show HN: 201 points, 61 comments (Sep 2024)

## Strategic Position

- **Exclusive memory provider for AWS Strands Agents SDK** -- the biggest distribution win in the middleware market. See [[Cloud Provider Memory Services#AWS]].
- Microsoft Agent Framework integration via official `Mem0Provider`
- Wins on ecosystem breadth and developer adoption, not retrieval quality

## Weakness

49.0% on [[Memory Benchmarks|LongMemEval]] -- lowest of the benchmarked middleware players. [[Zep]] scores 63.8%, [[Hindsight]] scores 91.4%. Mem0's moat is ecosystem, not accuracy.

## See Also

- [[Memory Middleware Players]] -- competitive landscape
- [[Competitive Dynamics#Mem0 vs. Zep]] -- head-to-head
- [[Hybrid Memory Architectures]] -- the architectural pattern Mem0 implements
