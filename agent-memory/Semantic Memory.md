---
tags: [memory-type, semantic, knowledge-base]
created: 2026-05-27
---

# Semantic Memory

An organized repository of facts, concepts, and relationships -- the agent's knowledge base. Unlike [[Episodic Memory]], semantic memories are context-free: "the API endpoint is `/v3/users`" rather than "yesterday the user told me the endpoint changed."

## What Gets Stored

- User preferences ("prefers Python over JavaScript")
- Domain facts ("staging requires VPN access")
- Entity relationships ("Alice manages the payments team")
- Learned rules ("always run migrations before deploying")

This is the most commonly implemented long-term memory type in production systems because it directly improves response quality.

## Storage Approaches

Semantic memories map naturally onto multiple storage backends:

- **[[Vector Databases for Memory]]** -- embeddings enable fuzzy semantic retrieval ("find memories about deployment" matches "CI/CD pipeline" and "release process")
- **[[Knowledge Graphs for Memory]]** -- entity-relationship triples enable structured queries ("what do we know about Alice?" traverses her relationships)
- **Key-value stores** -- simple factual lookups ("user.preferred_language = Python")

Modern [[Hybrid Memory Architectures]] combine all three.

## The Staleness Problem

Semantic memory's biggest challenge: facts change, but old memories persist with high similarity scores. If the user switched from Python to Rust three months ago, a vector search for "preferred language" may still surface the outdated Python preference.

[[Knowledge Graphs for Memory|Zep's Graphiti]] engine addresses this with temporal validity windows -- every fact carries a "valid from" and "superseded at" timestamp. See [[Challenges and Open Problems#Staleness]] for the broader discussion.

## Relationship to Other Types

- [[Episodic Memory]] often consolidates into semantic memory over time
- [[Procedural Memory]] can be thought of as a specialized form of semantic memory (facts about how to do things)
- [[Short-Term Memory]] content is promoted to semantic memory during [[Memory Operations#Encoding|encoding]]
