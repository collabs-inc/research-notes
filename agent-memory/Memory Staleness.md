---
tags: [concept, challenge, temporal, retrieval]
created: 2026-05-27
---

# Memory Staleness

Memories become outdated but remain in the store with high similarity scores. The agent retrieves superseded facts because [[Vector Databases for Memory|vector search]] is time-blind -- cosine similarity cannot distinguish current from outdated information.

## The Problem

If a user switched from Python to Rust three months ago, a vector search for "preferred language" may still surface the Python preference. The old memory has high semantic similarity and nothing in the retrieval system knows it's been superseded.

This is identified as one of the hardest open problems in [[Challenges and Open Problems|agent memory]].

## Why It's Hard

- Cosine distance has no temporal dimension -- a fact from yesterday and one from last year look identical
- The system often isn't explicitly told when facts change; it must infer staleness from context
- Stale memories can be reinforced: if the agent acts on an outdated preference and the user doesn't correct it, the old memory appears confirmed

## Solutions

### Temporal Knowledge Graphs ([[Zep]])

[[Temporal Knowledge Graphs|Graphiti]]'s bitemporal approach: every fact carries "valid from" and "superseded at" timestamps. When new information contradicts an existing edge, the old edge is invalidated (not deleted). Retrieval filters by temporal validity.

This is the most developed solution but requires structured extraction and explicit invalidation logic.

### Temporal Recency Weighting ([[Mem0]])

Exponential decay applied to retrieval scores -- recent memories get a boost. Simpler than full temporal graphs but doesn't handle the case where an *old* fact is still current while a *recent* fact has been superseded.

### Contradiction Detection

Some systems detect when new information contradicts existing memories and trigger [[Memory Operations#Consolidation|consolidation]]. This requires the system to recognize semantic contradiction -- non-trivial for implicit changes.

## Open Questions

- How to detect staleness *automatically* when the agent isn't explicitly told a fact changed?
- How to handle partial staleness (the fact is mostly true but one detail changed)?
- How to propagate staleness through a [[Knowledge Graphs for Memory|graph]] (if entity A's role changed, do memories *about* A need updating too)?

## See Also

- [[Temporal Knowledge Graphs]] -- the primary architectural response
- [[Zep]] -- the company most focused on solving this
- [[Challenges and Open Problems]] -- broader context
- [[Memory Operations#Forgetting]] -- related lifecycle operation
