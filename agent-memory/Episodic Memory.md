---
tags: [memory-type, episodic, experience]
created: 2026-05-27
---

# Episodic Memory

Records of specific past experiences and interactions, stored with temporal context. "In session #47, the user asked about deployment and we resolved a Docker networking issue." Preserves *what* happened, *when*, and *in what sequence*.

## Why It Matters

Episodic memory allows agents to learn from past successes and failures without gradient updates. An agent that remembers resolving a similar error last week can apply the same strategy -- or avoid a strategy that failed.

## The Generative Agents Approach

The Stanford [[Generative Agents]] paper (Park et al., 2023) established the canonical approach to episodic memory in agents. Each observation is stored as a memory object and retrieved using a weighted score across three dimensions:

- **Recency** -- exponential decay; recent memories score higher
- **Relevance** -- cosine similarity between the query and the memory embedding
- **Importance** -- an LLM-assigned score (1-10) reflecting how significant the event is

This triple-weighted retrieval outperforms any single signal alone. Removing the reflection mechanism (which synthesizes episodic memories into higher-level insights) caused agent behavior to degenerate within 48 simulated hours.

## Episodic vs Semantic Memory

| Dimension | Episodic | [[Semantic Memory]] |
|-----------|----------|---------------------|
| Content | Specific events with context | General facts and concepts |
| Temporal | "Last Tuesday at 3pm" | Timeless (until updated) |
| Example | "User got a 403 error when deploying to staging" | "Staging requires VPN access" |

In practice, episodic memories are often *consolidated* into semantic memories over time. A pattern across many episodes ("user always deploys on Fridays") becomes a semantic fact. See [[Memory Operations#Consolidation]].

## In Production

CrewAI implements episodic memory as short-term storage for recent task execution traces. [[Mem0]] stores interaction-level memories with temporal metadata. [[Hindsight]] (2026) is purpose-built for extracting lessons from episodic traces, scoring 91.4% on [[Memory Benchmarks|LongMemEval]].
