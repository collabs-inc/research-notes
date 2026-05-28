---
tags: [architecture, vector-db, embeddings, storage]
created: 2026-05-27
---

# Vector Databases for Memory

Vector databases are the workhorse for semantic similarity search in agent memory systems. They store high-dimensional embedding vectors and enable fast approximate nearest-neighbor (ANN) retrieval.

## How They Work

1. Text (a memory, fact, or document chunk) is passed through an embedding model
2. The resulting vector (e.g., 1536 dimensions for OpenAI's `text-embedding-3-small`) is stored alongside metadata
3. At query time, the query is embedded and the database returns the k nearest vectors by cosine similarity (or other distance metric)

## Key Players (2026)

| Database | Notes |
|----------|-------|
| **Qdrant** | Rust-based, strong filtering, used by [[Mem0]] |
| **Pinecone** | Managed service, serverless tier |
| **Weaviate** | Hybrid search (vector + keyword), GraphQL API |
| **Chroma** | Lightweight, popular for prototyping |
| **pgvector** | Postgres extension -- vectors as a data type in your existing DB |
| **LanceDB** | Embedded, used as CrewAI's default |

The 2025-2026 trend is vectors becoming a data type within multi-model databases (Postgres + pgvector, MongoDB Atlas Vector Search) rather than requiring standalone vector DBs.

## Strengths

- **Fuzzy semantic matching** -- "deployment issues" retrieves memories about "CI/CD failures" and "release problems"
- **Scale** -- handles millions of vectors with sub-second retrieval
- **Simplicity** -- well-understood, easy to set up

## Limitations

- **No temporal reasoning** -- a memory from 5 minutes ago and one from 5 months ago have identical similarity scores. This is the root of the [[Challenges and Open Problems#Staleness|staleness problem]].
- **No multi-hop reasoning** -- can't traverse relationships between entities
- **"Lost in the middle"** -- top-k retrieval may miss relevant memories ranked just below the threshold
- **Embedding quality ceiling** -- retrieval is only as good as the embedding model

These limitations drive the adoption of [[Knowledge Graphs for Memory]] and [[Hybrid Memory Architectures]].

## Role in Hybrid Architectures

In [[Hybrid Memory Architectures|modern production systems]], vector databases serve as the *breadth* layer -- casting a wide semantic net. [[Knowledge Graphs for Memory|Graph layers]] provide *depth* for relationship traversal, and temporal weighting addresses recency. Vector search alone is being relegated to simple, static-data use cases.
