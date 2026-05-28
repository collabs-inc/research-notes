# A-MEM

**Paper**: "A-MEM: Agentic Memory for LLM Agents" (NeurIPS 2025). The landmark paper establishing [[Agentic Memory]] -- memories that actively self-organize rather than being passively stored.

## Key Innovation

Inspired by the Zettelkasten method, A-MEM lets memories:

* **Generate their own descriptions** -- each memory writes its own metadata

* **Form connections** to other memories autonomously

* **Evolve relationships** over time as new information arrives

* **Self-organize** without predetermined memory operations

This is a qualitative shift from [[Memory Operations]] as a fixed pipeline (encode → store → retrieve → forget) to memory as an emergent, agent-directed process.

## Why It Matters

Previous systems like [[Generative Agents]] and [[Mem0]] use *system-controlled* memory operations -- external code decides what to remember, how to index it, and when to consolidate. A-MEM pushes these decisions to the agent itself.

This connects to [[Letta]]'s agent-controlled memory philosophy but goes further: in Letta the agent decides *when* to read/write; in A-MEM the memories themselves have agency.

## Relationship to Other Work

* Extends [[Generative Agents]]' reflection mechanism into full self-organization

* Philosophically aligned with [[Letta]]'s agent-controlled approach

* Inspired [[MemEvolve]]'s work on evolving not just memories but memory *architecture*

* The Zettelkasten inspiration connects to the broader [[Agentic Memory]] trend and to grassroots practices like using Obsidian vaults as agent memory

## See Also

* [[Agentic Memory]] -- the broader trend this paper defines

* [[MemEvolve]] -- extends the idea to architecture evolution

* [[Memory Operations]] -- the fixed pipeline A-MEM transcends

## Demand Signal

- Accepted as **main conference track paper at NeurIPS 2025** -- legitimizes agent memory as a top-tier research direction
- GitHub (WujiangXu/A-mem): 896 stars, 92 forks
- Agent-Memory-Paper-List (survey repo tracking this subfield): 2,061 stars

⠀