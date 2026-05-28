---
tags: [paper, system, skill-library, procedural-memory, foundational]
created: 2026-05-27
---

# Voyager

**Paper**: "Voyager: An Open-Ended Embodied Agent with Large Language Models" (2023). The canonical example of [[Procedural Memory]] as a skill library in AI agents.

## How It Works

Voyager operates in Minecraft and builds a library of verified JavaScript skill functions:

1. Agent encounters a new challenge
2. Writes a JavaScript function to solve it
3. **Verifies** the function by execution
4. Stores verified skill in the library, indexed by natural language description
5. Future challenges retrieve and **compose** existing skills

Skills are compositional -- new skills build on existing ones, enabling increasingly complex behavior without rewriting from scratch.

## Results

- **15.3x speedup** from the skill library alone
- Without procedural memory, the agent essentially starts from zero every time

## Why It Matters

Voyager established that **executable skill storage** is a powerful complement to factual memory. The pattern -- *runnable code indexed by natural language* -- generalizes beyond games to any agent that uses tools.

Modern parallels:
- Coding agents that learn tool-use patterns across sessions
- [[Letta]] Code's memory-first approach to coding
- Workflow automation agents that store verified action sequences

## Design Pattern

The Voyager skill library pattern has three key properties:
1. **Verified before storage** -- only working code enters the library
2. **Indexed by intent** -- natural language descriptions enable semantic retrieval
3. **Compositional** -- skills chain together, compounding capability over time

This is [[Procedural Memory]] at its most concrete: the agent literally stores *how to do things* as executable code.

## See Also

- [[Procedural Memory]] -- the memory type Voyager exemplifies
- [[Reflexion]] -- complementary approach (stores failure knowledge vs. working skills)
- [[Generative Agents]] -- established the memory architecture foundations Voyager builds on
