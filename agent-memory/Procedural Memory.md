---
tags: [memory-type, procedural, skills]
created: 2026-05-27
---

# Procedural Memory

Knowledge of *how to do things* -- stored routines, workflows, tool-use patterns, and executable skills. While [[Semantic Memory]] stores facts and [[Episodic Memory]] stores experiences, procedural memory stores capabilities.

## The Voyager Skill Library

Voyager (2023) is the canonical example of procedural memory in AI agents. It operates in Minecraft and builds a library of verified JavaScript routines (skills), each indexed by a natural language description:

- Skills are composed on the fly to solve complex tasks
- New skills build on existing ones (compositional)
- Each skill is verified by execution before being stored
- Without the skill library, Voyager was **15.3x slower** at reaching milestones

This pattern -- executable code indexed by natural language -- generalizes beyond games to any agent that uses tools.

## In Production Systems

| System | Procedural Memory Form |
|--------|----------------------|
| Voyager | JavaScript skill functions |
| [[Foundational Systems\|Reflexion]] | Natural language post-mortems prepended to future attempts |
| CrewAI | Task execution patterns and tool-use traces |
| Code agents (Devin, Claude Code) | Learned tool sequences, CLAUDE.md-style instructions |

## Relationship to Other Memory Types

Procedural memory is the bridge between knowing and doing:
- [[Episodic Memory]] provides the raw material (past execution traces)
- [[Semantic Memory]] provides the facts needed during execution
- Procedural memory encodes the *strategy* -- which tools to use, in what order, with what parameters

The [[Emerging Trends in Agent Memory|Reflexion]] approach is interesting because it stores procedural knowledge as natural language self-critique rather than executable code. After failing a task, the agent writes a post-mortem ("I should have checked the return type before calling `.json()`") and prepends it to the next attempt. This achieved 91% pass@1 on HumanEval vs. 80% for GPT-4 without reflection.
