---
tags: [memory-lifecycle, operations, encoding, retrieval, consolidation, forgetting]
created: 2026-05-27
---

# Memory Operations

The lifecycle of a memory in an AI agent system, from raw interaction to long-term storage to eventual pruning. Based on the taxonomy from the December 2025 survey "Memory in the Age of AI Agents" (Tsinghua/CMU).

## Encoding

Transforming raw interaction traces into storable memory artifacts. Two main approaches:

- **Semantic summarization** -- compresses linear conversation streams into narrative blocks. LLM-generated summaries of key information, decisions, and outcomes.
- **Structured construction** -- parses interactions into knowledge graph triples (entity-relationship-entity). More precise but more brittle.

[[Mem0]]'s single-pass extraction runs one LLM call to extract a structured fact and add it, deferring conflict resolution to consolidation. This cut write-time LLM calls by 60-70% compared to multi-pass approaches.

## Storage

Where encoded memories persist. The choice of storage backend shapes retrieval capabilities:

| Backend | Best For | Limitation |
|---------|----------|------------|
| [[Vector Databases for Memory]] | Fuzzy semantic search | No temporal reasoning |
| [[Knowledge Graphs for Memory]] | Entity relationships, provenance | Complex setup, query overhead |
| Key-value stores | Fast metadata lookup | No semantic search |
| Relational DB (Postgres, SQLite) | Structured records, SQL queries | No native embedding support |
| File-based (Memvid .mv2) | Zero infrastructure, portable | Append-only, limited query |

[[Hybrid Memory Architectures]] combine multiple backends.

## Retrieval

The critical operation. Pure cosine similarity is "a surprisingly blunt instrument" -- a memory from 5 minutes ago and one from 5 weeks ago look identical to it.

Modern multi-signal retrieval combines:
- **Semantic similarity** (embeddings / cosine distance)
- **Keyword search** (BM25 for exact term matching)
- **Graph traversal** (for entity relationships, multi-hop reasoning)
- **Temporal recency** (exponential decay weighting)
- **Importance scoring** (as in [[Episodic Memory|Generative Agents]])
- **Metadata filters** (user ID, session, topic tags)

[[Mem0]]'s retrieval uses ~7K tokens per query vs. 25-100K for full-context approaches.

## Consolidation

Merging, updating, and synthesizing memories over time:

- **Merging fragmented traces** into coherent knowledge
- **Conflict resolution** when new facts contradict old ones ([[Knowledge Graphs for Memory|Graphiti]]'s edge invalidation)
- **Temporal validity updates** (marking superseded facts)
- **Promotion** of frequently-accessed [[Short-Term Memory|short-term]] memories to long-term
- **Reflection** -- [[Generative Agents]]' periodic synthesis of low-level observations into higher-level insights ("I've noticed the user always deploys on Fridays" emerges from many episodic observations)

## Forgetting

Deliberate removal of low-utility information. Essential for scalability and relevance.

Approaches:
- **Exponential decay** (recency-based)
- **Access frequency thresholds** (rarely-retrieved memories are pruned)
- **Contradiction-triggered invalidation** (new fact supersedes old)
- **Privacy-driven forgetting** (the MaRS framework defines six forgetting policies)
- **Capacity-based eviction** (LRU-style, when storage budget is exceeded)

The "Forgetful but Faithful" paper (December 2025) proposes privacy-aware forgetting with differential privacy guarantees. See [[Memory Security and Privacy]] for the broader security implications.
