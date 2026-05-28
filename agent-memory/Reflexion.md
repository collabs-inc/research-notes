---
tags: [paper, system, self-critique, procedural-memory, foundational]
created: 2026-05-27
---

# Reflexion

**Paper**: "Reflexion: Language Agents with Verbal Reinforcement Learning" (Shinn et al., 2023). Demonstrated that natural language self-critique can serve as [[Procedural Memory]] -- no gradient updates required.

## How It Works

After failing a task, the agent:
1. Writes a natural language **post-mortem** analyzing what went wrong
2. **Prepends** the post-mortem to the next attempt as context
3. Retries with the benefit of its own self-critique

Example post-mortem: *"I should have checked the return type before calling `.json()`. The API returns a string when the request fails, not a dict."*

## Results

- **91% pass@1 on HumanEval** vs. 80% for GPT-4 without reflection
- Achieved through purely in-context learning -- no fine-tuning, no gradient updates

## Why It Matters

Reflexion proved that **memory of failure** is as valuable as memory of success. The post-mortem pattern is a form of [[Procedural Memory]] -- the agent learns *how to do things* by explicitly recording what not to do.

This influenced:
- **Memory-augmented planning** systems (ReAP, DIVERGE, JADE) that leverage both successes and failures
- **[[Agentic Memory]]** approaches where agents actively manage their own learning
- Production coding agents that maintain internal "lessons learned" context

## Relationship to Other Systems

- [[Generative Agents]] established that reflection improves behavior; Reflexion showed it improves task performance
- [[Voyager]] stores positive procedural knowledge (working skills); Reflexion stores negative procedural knowledge (failure analyses)
- [[A-MEM]] extends the self-organizing aspect further

## See Also

- [[Procedural Memory]] -- the memory type Reflexion implements
- [[Memory Operations#Consolidation]] -- post-mortems as a consolidation mechanism
