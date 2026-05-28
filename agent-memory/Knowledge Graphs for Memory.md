---
tags: [architecture, knowledge-graph, temporal, neo4j]
created: 2026-05-27
---

# Knowledge Graphs for Memory

Knowledge graphs store memories as entity-relationship-entity triples (e.g., `Alice --manages--> Payments Team`), enabling structured traversal and multi-hop reasoning that [[Vector Databases for Memory|vector search]] cannot provide.

## Why Graphs for Agent Memory

The major architectural shift of 2025-2026. Graph layers address failures that vector search misses:

- **Multi-hop queries**: "Who manages the team that owns the service that caused the outage?" requires traversing 3 relationships -- vector similarity can't express this.
- **Entity disambiguation**: Graph nodes represent distinct entities; vectors collapse "Python (language)" and "Python (snake)" into nearby embeddings.
- **Provenance tracking**: Graph edges carry metadata about when, how, and from whom a fact was learned.

Microsoft's GraphRAG benchmark: **86% accuracy** for graph-based approaches vs. **32% for baseline vector** [[Retrieval-Augmented Generation|RAG]] on enterprise data.

## Zep's Graphiti: Temporal Knowledge Graphs

Graphiti (Zep, January 2025) is the leading temporal knowledge graph for agent memory. Key innovation: **dual timelines**.

- **Event time** -- when the event actually occurred
- **Fact validity time** -- when a fact became true and when it was superseded

This directly solves the [[Challenges and Open Problems#Staleness|staleness problem]]. When the user switches from Python to Rust, the old preference edge gets a "superseded_at" timestamp. Retrieval queries can filter by temporal validity.

Benchmark results: 63.8% on LongMemEval, 94.8-98.2% on the DMR Benchmark.

## Graph Databases

| Database | Notes |
|----------|-------|
| **Neo4j** | Market leader, Cypher query language, used by [[Zep|Graphiti]] and [[Mem0]] |
| **FalkorDB** | Redis-based, low-latency graph queries |
| **Amazon Neptune** | Managed, multi-model (property graph + RDF) |

## Limitations

- **Setup complexity** -- schema design, entity resolution, and relationship extraction require more engineering than "embed and store"
- **Query overhead** -- graph traversals can be expensive for large, densely connected graphs
- **Extraction quality** -- converting unstructured text to accurate triples is non-trivial; errors in entity extraction propagate through the graph

These tradeoffs are why [[Hybrid Memory Architectures]] pair graphs with vectors rather than replacing them entirely.
