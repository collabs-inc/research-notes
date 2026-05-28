---
tags: [concept, architecture, temporal, graph, graphiti]
created: 2026-05-27
---

# Temporal Knowledge Graphs

Knowledge graphs augmented with temporal dimensions -- facts carry timestamps indicating when they became true and when they were superseded. The primary architectural response to the [[Memory Staleness]] problem.

## The Core Idea

Standard [[Knowledge Graphs for Memory|knowledge graphs]] store triples like:
```
(User) --[prefers]--> (Python)
```

Temporal knowledge graphs add validity windows:
```
(User) --[prefers {valid_from: 2024-01, superseded_at: 2026-03}]--> (Python)
(User) --[prefers {valid_from: 2026-03}]--> (Rust)
```

Retrieval queries specify "as of when" and only return currently-valid facts.

## Graphiti ([[Zep]])

The leading implementation. Introduces **bitemporal annotation** (arXiv:2501.13956, January 2025):

- **Event time** -- when the real-world event occurred
- **Ingestion time** -- when the system learned about it

Dual timelines enable queries like:
- "What was true as of March 2026?" (event time)
- "What did the system believe on March 1, before the update?" (ingestion time)

When new facts contradict old ones, Graphiti **invalidates** the old edge (marks it superseded) rather than deleting it. History is preserved.

Benchmarks: 63.8% on [[Memory Benchmarks|LongMemEval]], 94.8-98.2% on DMR.

## FalkorDB Integration

FalkorDB provides sub-10ms graph queries for real-time retrieval. Graphiti + FalkorDB enables temporal knowledge graphs in [[Multi-Agent Shared Memory|multi-agent]] environments where latency matters.

## Why This Matters

Temporal knowledge graphs solve problems that [[Vector Databases for Memory|vector search]] fundamentally cannot:
- Fact validity tracking (what's current vs. superseded)
- Point-in-time queries ("what was true at time X?")
- History preservation without retrieval pollution

The tradeoff is complexity: temporal graphs require structured extraction, entity resolution, and explicit invalidation logic. This is why [[Hybrid Memory Architectures]] pair temporal graphs with simpler vector layers.

## See Also

- [[Memory Staleness]] -- the problem this pattern solves
- [[Zep]] -- the company that pioneered this approach
- [[Knowledge Graphs for Memory]] -- broader graph-based memory
- [[Memory Operations#Consolidation]] -- how temporal updates happen
