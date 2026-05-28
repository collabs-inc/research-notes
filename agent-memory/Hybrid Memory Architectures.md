---
tags: [architecture, hybrid, production, vector, graph, episodic]
created: 2026-05-27
---

# Hybrid Memory Architectures

By mid-2026, the production standard for knowledge-intensive agents is a three-layer architecture combining vector, graph, and episodic storage. Pure [[Vector Databases for Memory|vector]] [[Retrieval-Augmented Generation|RAG]] is being relegated to simple static-data use cases.

## The Three Layers

| Layer | Purpose | Backend |
|-------|---------|---------|
| **Vector** | Semantic breadth -- find related concepts via embedding similarity | Qdrant, pgvector, Chroma |
| **Graph** | Relational depth -- traverse entity connections, temporal validity | Neo4j, FalkorDB ([[Knowledge Graphs for Memory\|Graphiti]]) |
| **Episodic** | Experience learning -- past execution traces, session history | Custom stores, file-based |

Each layer compensates for the others' weaknesses:
- Vectors handle fuzzy semantic matching but miss relationships
- Graphs handle structured traversal but miss semantic nuance
- Episodic stores capture temporal context that neither provides alone

## How Retrieval Works

A query fans out across all layers and results are merged:

1. **Vector search** returns semantically similar memories (breadth)
2. **Graph traversal** returns entity-connected facts and relationship chains (depth)
3. **Temporal weighting** adjusts scores based on recency and validity
4. **Re-ranking** merges and prioritizes results before injecting into context

This multi-signal retrieval is detailed in [[Memory Operations#Retrieval]].

## Systems Using This Pattern

- **[[Mem0]]** -- vector (Qdrant) + graph (Neo4j) + key-value store, with graph traversal for entity-linked memories and temporal recency weighting
- **[[Zep]]** -- [[Temporal Knowledge Graphs|Graphiti]] temporal knowledge graph + vector embeddings + BM25 keyword search
- **MAGMA** (January 2026) -- multi-graph approach where each memory is represented across orthogonal semantic, temporal, causal, and entity graphs simultaneously

## The Virtual Memory Alternative

[[Letta]] takes a different approach inspired by operating systems. Rather than multiple retrieval backends, it treats the LLM context as "RAM" and external storage as "disk":

- **Main context** -- actively managed in-window memory
- **Recall storage** -- recent conversation history (paged in on demand)
- **Archival storage** -- long-term facts (searched and retrieved)

The agent manages its own memory through function calls (`core_memory_replace`, `archival_memory_insert`, `archival_memory_search`). This "virtual memory" model is architecturally distinct from hybrid retrieval but solves similar problems.

## Trend

The every-RAG-company-is-building-a-graph-layer trend of 2025-2026 reflects the industry consensus: vectors alone are insufficient for agents that need to reason over relationships, time, and identity.
