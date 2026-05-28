---
tags: [index, market, companies, middleware]
created: 2026-05-27
---

# Memory Middleware Players

The dedicated memory-as-a-service companies -- the most active startup zone in the [[Market Structure and Value Chain|market structure]]. Each major player has its own note.

## Established Players

- [[Mem0]] -- market leader by community (56.9K stars) and distribution (AWS Strands partnership). Hybrid vector + graph + KV. $24M Series A.
- [[Zep]] -- temporal reasoning specialist. [[Temporal Knowledge Graphs|Graphiti]] engine. SOC 2/HIPAA. ~$2.3M total funding.
- [[Letta]] -- agent-controlled memory pioneer. OS-inspired virtual memory. $10M seed. ~$1.4M ARR.
- [[Cognee]] -- knowledge-graph-native, enterprise-first. 70+ companies. $7.5M seed.

## Emerging Players

- [[Honcho]] -- reasoning-first middleware by Plastic Labs. Custom Neuromancer XR model, Theory of Mind via directional peer modeling. AGPL. 4.4K stars. 90.4% LongMemEval S.
- [[Hindsight]] -- open source, highest verified [[Memory Benchmarks|LongMemEval]] score (91.4%). Biomimetic four-network model.
- **Supermemory** -- all-in-one memory API. $3M seed. 81.6% LongMemEval. Closed source.
- **EverMind / EverOS** -- "memory OS for self-evolving agents." Public beta Apr 2026.
- **Memvid** -- database-free .mv2 files. Zero infrastructure. 0.025ms P50 retrieval.
- **MemPalace** -- 52.9K stars, 7K forks (nearly tied with [[Mem0]]). Claims 96.6% LongMemEval but [[Memory Benchmarks|benchmarks disputed]].
- **Memvid** -- 15.6K stars. Database-free .mv2 files. Zero infrastructure. 0.025ms P50 retrieval.
- **Wato** -- YC-backed. Shared memory + reusable workflows for agent teams.

## Framework-Embedded Memory

Not standalone middleware, but memory features built into agent frameworks:
- **LangMem** -- LangChain sub-package. LangGraph integration. p95 search latency of 59.82s on benchmarks.
- **CrewAI Memory** -- four types (short/long/entity/user). LanceDB default. Uses [[Mem0]] for user memory.
- **Microsoft Agent Framework** -- merges Semantic Kernel + AutoGen. Official [[Mem0]] integration.

## Comparison

| | [[Mem0]] | [[Zep]] | [[Letta]] | [[Cognee]] | [[Honcho]] |
|---|---|---|---|---|---|
| Graph layer | Neo4j | Graphiti | No | Native | No (reasoning) |
| Temporal reasoning | Partial | Best-in-class | Agent-managed | No | Via consolidation |
| Self-managed memory | No | No | Yes | No | No (system-reasoned) |
| Token efficiency | Best | Good | Good | Baseline | Good |
| Multi-agent | Yes | Limited | Yes (2026) | Yes | Yes (peer model) |
| Compliance | In progress | SOC 2/HIPAA/GDPR | -- | -- | -- |
| Differentiator | Distribution | Temporal graphs | Agent-controlled | Enterprise KG | Logical reasoning + ToM |

## See Also

- [[Memory Benchmarks]] -- LongMemEval leaderboard and benchmark limitations
- [[Competitive Dynamics]] -- how these players interact
- [[Market Structure and Value Chain]] -- competitive zones and where middleware sits
