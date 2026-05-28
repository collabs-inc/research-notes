---
tags: [architecture, rag, retrieval]
created: 2026-05-27
---

# Retrieval-Augmented Generation

RAG is the dominant pattern for grounding LLM agents in external knowledge. The core loop: given a query, retrieve relevant context from a datastore, inject it into the prompt, and generate a response conditioned on that context.

## Traditional RAG Pipeline

1. **Chunk** documents into passages
2. **Embed** each chunk using an embedding model
3. **Index** embeddings in a [[Vector Databases for Memory|vector database]]
4. At query time, **embed the query** and find nearest neighbors
5. **Inject** top-k results into the prompt
6. **Generate** response grounded in retrieved context

This "chunk-and-embed" approach remains the baseline for most memory retrieval systems, but by 2026 its limitations are well-understood.

## Limitations of Pure Vector RAG

- **No multi-hop reasoning** -- "Who manages the team that owns the payments service?" requires traversing relationships, not similarity search
- **No temporal reasoning** -- cosine distance treats a fact from yesterday and one from last year identically
- **Chunk boundary problems** -- relevant information split across chunks may never be co-retrieved
- **Scalability ceiling** -- as the corpus grows, retrieval precision degrades

Microsoft's GraphRAG benchmark showed **86% accuracy** for hierarchical graph approaches vs. **32% for baseline vector RAG** on enterprise data -- a dramatic gap for complex queries.

## The Evolution: Hybrid RAG

By mid-2026, the production standard is [[Hybrid Memory Architectures|hybrid RAG]]:

- **Vector layer** for semantic breadth (find related concepts)
- **Graph layer** for relational depth (traverse entity connections)
- **Keyword/BM25 layer** for exact term matching

This addresses the multi-hop and temporal reasoning gaps while retaining the semantic flexibility of embeddings.

## RAG as Memory

In agent memory systems, RAG is the retrieval mechanism rather than the memory itself. The agent's [[Semantic Memory]], [[Episodic Memory]], and [[Procedural Memory]] are the *what*; RAG is the *how* for getting relevant memories back into [[Short-Term Memory|context]].

The shift from "RAG over documents" to "RAG over agent memories" is a key theme. Documents are static; agent memories are dynamic, temporal, and interconnected. This is why pure vector RAG is insufficient -- agent memory needs temporal awareness and relationship tracking that document RAG doesn't require.
