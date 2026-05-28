---
tags: [paper, system, self-evolving, meta-learning, 2025]
created: 2026-05-27
---

# MemEvolve

**Paper**: "MemEvolve: Meta-Evolution of Agent Memory Systems" (December 2025). Goes beyond [[Agentic Memory]] to evolve the memory *system itself*, not just its contents.

## Key Innovation: EvolveLab

Introduces a modular design space where memory system components can be reconfigured through meta-learning:

- **Encode** module -- how raw interactions become memories
- **Store** module -- where and how memories persist
- **Retrieve** module -- how memories are found and ranked
- **Manage** module -- consolidation, pruning, conflict resolution

The system jointly evolves experiential knowledge AND architecture. The memory system adapts to its task domain rather than being designed upfront.

## Results

- Up to **17.06% performance improvements** over fixed architectures
- Cross-task generalization -- architecture learned for one task transfers to others

## Why It Matters

Most [[Memory Middleware Players|memory middleware]] uses a fixed architecture (e.g., [[Mem0]]'s vector + graph + KV). MemEvolve suggests that the optimal architecture varies by task, and that agents could discover it themselves.

This signals a future where:
- Memory systems self-configure during deployment
- Architecture becomes a learned parameter, not a design choice
- The "best memory system" is task-dependent and discoverable

## Related Work

- **EvolveMem** (May 2026) -- applies AutoResearch principles to memory architecture evolution, extending MemEvolve's ideas
- **[[A-MEM]]** -- self-organizing content (memories organize themselves)
- **MemEvolve** -- self-organizing structure (the system organizes itself)

## See Also

- [[Agentic Memory]] -- the broader self-organizing trend
- [[Memory Operations]] -- the fixed pipeline MemEvolve makes adaptive
- [[Emerging Trends in Agent Memory]] -- market context
