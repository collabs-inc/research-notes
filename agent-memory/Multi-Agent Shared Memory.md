---
tags: [concept, trend, multi-agent, shared-memory, architecture]
created: 2026-05-27
---

# Multi-Agent Shared Memory

How multiple AI agents share, synchronize, and access common memory stores. Framed as a computer architecture problem in a March 2026 paper: I/O layer, cache layer, memory layer.

## The Architecture Problem

When multiple agents need to share context:

| Layer | Function | Challenge |
|-------|----------|-----------|
| **I/O** | Agent reads/writes to memory | Standardized via [[Model Context Protocol\|MCP]] |
| **Cache** | Working context shared between agents | No standard sharing protocol |
| **Memory** | Persistent shared store | Access control, consistency |

## Unsolved Problems

- **Cache sharing protocols** -- how do agents share working context without flooding each other?
- **Access control** -- who can read/write which memories? How is authorization scoped?
- **Consistency guarantees** -- what happens when two agents update the same memory simultaneously?
- **Memory drift** -- shared memories diverge from ground truth as agents independently update them
- **Hallucinated recall** -- one agent's confabulation enters shared memory and contaminates others
- **Bias propagation** -- systematic errors spread through the agent team via shared memory

## Systems and Approaches

**G-Memory** (June 2025) -- hierarchical memory tracing for multi-agent systems. Introduced structured approaches to tracking which agent contributed which memory.

**[[Letta]] Conversations API** (January 2026) -- enables agents to maintain shared memory across parallel experiences. The first production-ready shared memory API from a [[Memory Middleware Players|middleware provider]].

**[[Cognee]]** -- knowledge graph architecture naturally supports multi-agent access to shared knowledge structures.

**CrewAI** -- native multi-agent memory with four types (short/long/entity/user), but simpler consistency guarantees than dedicated solutions.

**FalkorDB** -- multi-graph, multi-tenant deployments with isolated schemas. Sub-10ms queries enable real-time shared memory for [[Zep|Graphiti]]-based multi-agent systems.

## Security Implications

Shared memory creates additional attack surface for [[Memory Poisoning]]:
- Cross-agent memory leakage (Agent A's memories contaminating Agent B)
- Shared memory poisoning (corrupting the common store affects all agents)
- Privilege escalation (agent gaining access to memories above its authorization)

## See Also

- [[Emerging Trends in Agent Memory]] -- broader trend context
- [[Memory Poisoning]] -- security risks specific to shared memory
- [[Model Context Protocol]] -- the integration standard enabling shared access
