---
tags: [concept, evaluation, benchmarks, longmemeval]
created: 2026-05-27
---

# Memory Benchmarks

Evaluating agent memory systems is an unsolved problem. Classical IR metrics (precision, recall) miss agent-specific concerns like [[Memory Staleness|staleness]], contradiction handling, and multi-session coherence.

## Key Benchmarks

| Benchmark | Focus | Scale |
|-----------|-------|-------|
| **LongMemEval** | Long-term conversational memory | Multi-session, temporal reasoning |
| **MemoryArena** (Stanford, Feb 2026) | Multi-session agentic tasks (web nav, planning, reasoning) | Exposes gap between memory recall and memory-guided action |
| **LoCoMo** | Single-session memory | 1,540 questions across 35 sessions, 300+ turns |
| **DMR Benchmark** | Dialogue memory retrieval | Focused on retrieval accuracy |
| **MemoryBench** | General memory evaluation | Broad coverage |
| **MemoryAgentBench** | Agent-specific memory tasks | Agentic workflows |
| **EvoMem** | Memory evolution and updating | Dynamic knowledge |
| **BEAM** ([[Mem0]]) | Scale testing (1M-10M tokens) | Shows ~25% accuracy degradation at 10M tokens |

## LongMemEval Leaderboard (Mid-2026)

| System | Score | Notes |
|--------|-------|-------|
| [[MemPalace]] | 96.6% (R@5) | **Disputed** -- independent audit found `top_k=50` on 19-32 item sessions (retrieves everything), hand-tuned fixes, API calls despite "no API" claims. Honest numbers: 60.3% R@10 without reranking, 88.9% with hybrid. |
| Oracle SDK | 93.8% | Database incumbent |
| [[Hindsight]] | 91.4% | Strongest independently verified; multi-session 79.7% |
| EverOS | 83.0% | Also 93.05% on LoCoMo |
| Supermemory | 81.6% | Self-reported |
| [[Zep]]/Graphiti | 63.8% | [[Temporal Knowledge Graphs|Temporal graph]] advantage |
| [[Mem0]] | 49.0% | Wins on ecosystem, not retrieval accuracy |

**Caveat**: Benchmark methodologies vary significantly. Self-reported scores are common. Independent replication is limited.

## What Benchmarks Miss

| What's Measured | What's Missed |
|-----------------|---------------|
| Retrieval accuracy | [[Memory Staleness\|Staleness]] of retrieved memories |
| Recall completeness | Contradiction handling quality |
| Response quality | [[Memory Operations#Forgetting\|Forgetting]] quality |
| Single-session tasks | Multi-session coherence |
| Passive recall | Memory-guided action (MemoryArena gap) |

The December 2025 survey proposes evaluating across the full [[Memory Operations|memory lifecycle]] (formation, evolution, retrieval) rather than just retrieval accuracy.

## The MemoryArena Gap

Stanford's MemoryArena (February 2026) revealed that agents saturating existing benchmarks (like LoCoMo) fail dramatically in multi-session agentic tasks. The gap between *recalling a fact* and *using that fact correctly in an ongoing workflow* is large and unaddressed.

## See Also

- [[Challenges and Open Problems]] -- evaluation as an open problem
- [[Competitive Dynamics]] -- benchmark wars between vendors
