---
tags: [index, trends, frontiers, 2025-2026]
created: 2026-05-27
---

# Emerging Trends in Agent Memory

The frontier of agent memory research and practice (2025-2026). Major trends link to dedicated notes.

## Major Trends

- [[Agentic Memory]] -- the shift from passive storage to agent-directed memory management. Defined by [[A-MEM]] (NeurIPS 2025).
- [[Multi-Agent Shared Memory]] -- how agent teams share, synchronize, and access common memory. Framed as a computer architecture problem.
- [[Temporal Knowledge Graphs]] -- bitemporal fact tracking, pioneered by [[Zep|Graphiti]]. Addresses [[Memory Staleness]].
- **Self-evolving architectures** -- [[MemEvolve]] and EvolveMem: not just evolving what's remembered, but the memory system itself.

## Additional Trends

### Memory-Augmented Planning

Agents using past execution memories to plan better:
- **Reflection-Augmented Planning (ReAP)** -- leverages both successes and failures via self-reflections
- **DIVERGE** -- reflection + memory-based refinement for open-ended information seeking
- **JADE** -- joint optimization of planning and execution through multi-agent cooperation

Connects [[Procedural Memory]] (learned strategies) with [[Episodic Memory]] (past outcomes).

### Hybrid RAG as Table Stakes

[[Hybrid Memory Architectures|Vector + graph + episodic]] is the expected production baseline. The debate has moved from "do we need graphs?" to "how do we integrate graphs efficiently?"

### Token-Efficient Memory

Reducing cost of memory-augmented agents. [[Mem0]]'s single-pass extraction cut write-time LLM calls by 60-70%. ~7K tokens per retrieval vs. 25-100K baseline. Critical for production economics.

### Memory Security as a Discipline

[[Memory Poisoning]] attacks and the "Mnemonic Sovereignty" framework are establishing agent memory security as a distinct field. See [[Memory Security and Privacy]].

### Standards

[[Model Context Protocol]] (MCP) commoditizes the integration layer and shifts competition to memory quality. 970x growth in SDK downloads (2025-2026).
