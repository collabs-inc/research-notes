---
tags: [index, challenges, open-problems]
created: 2026-05-27
---

# Challenges and Open Problems

The hard problems that remain unsolved or partially solved. Major challenges link to dedicated notes.

## Core Challenges

- [[Memory Staleness]] -- outdated memories persist with high similarity scores. [[Temporal Knowledge Graphs]] are the best current response but add complexity.
- [[Memory Poisoning]] -- attacks that corrupt agent behavior by targeting how the system remembers, not just the current session.
- [[Memory Benchmarks]] -- evaluation gaps. Classical IR metrics miss staleness, contradiction handling, multi-session coherence. The MemoryArena gap: agents that recall well fail to *act* on memories correctly.

## Hallucination from Memory

The HaluMem paper (November 2025) identifies a distinct failure mode: agents "remember" things that didn't happen, or confabulate details when combining memories.

Memory-augmented agents hallucinate *more confidently* because they have (false) evidence to cite. "Based on our conversation on March 3rd..." reads as trustworthy -- even when fabricated.

## Cross-Session Identity

Maintaining coherent agent identity across many sessions. [[Memory Benchmarks|MemoryArena]] (Stanford, February 2026) showed agents scoring well on single-session benchmarks fail dramatically in multi-session agentic tasks.

The gap: recalling a fact in isolation is easier than using it correctly in an ongoing workflow.

## Scalability

As memory stores grow:
- Retrieval quality degrades (more noise, less signal)
- Latency increases (larger indices, more graph traversals)
- Token budgets for context injection become a constraint
- Cost scales with every [[Memory Operations|memory operation]]

[[Mem0]]'s token-efficient algorithm (~7K tokens/retrieval vs. 25-100K) is the leading response.

## Temporal Reasoning

Beyond [[Memory Staleness]], agents struggle with temporal queries:
- "What did we discuss *before* the deployment?" (ordering)
- "Has this been resolved *since* last week?" (state change)
- "What was the endpoint *at the time* of the incident?" (point-in-time)

[[Temporal Knowledge Graphs|Graphiti]]'s dual-timeline approach is most developed, but temporal reasoning remains an active research area.

## See Also

- [[Memory Staleness]], [[Memory Poisoning]], [[Memory Benchmarks]] -- detailed coverage
- [[Competitive Dynamics]] -- how challenges shape market competition
