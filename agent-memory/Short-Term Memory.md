---
tags: [memory-type, context-window, working-memory]
created: 2026-05-27
---

# Short-Term Memory

The agent's context window functions as its working memory -- the scratchpad where active reasoning happens. Everything the agent can "see" at inference time lives here: the current conversation, system instructions, retrieved context, and intermediate reasoning steps.

## Constraints

The fundamental limitation is token budget. Even with context windows of 1M+ tokens (Gemini, Claude), fitting everything into context is impractical for long-running agents. This constraint is the primary driver behind all other [[Memory Operations|memory types and operations]].

Key tradeoffs:
- **More context = better grounding** but higher latency, cost, and "lost in the middle" effects
- **Less context = faster, cheaper** but the agent forgets recent interactions

## Relationship to Long-Term Memory

Short-term memory is volatile -- it evaporates when the session ends. The transition from short-term to long-term storage is one of the core [[Memory Operations]], analogous to memory consolidation in neuroscience.

[[Letta|MemGPT/Letta]] treats this explicitly as a virtual memory problem: main context is "RAM" and external storage is "disk," with the agent managing page-in/page-out operations via function calls.

## In Practice

Most production agents use a layered approach:
1. System prompt + instructions (always in context)
2. Retrieved memories from [[Semantic Memory]] or [[Episodic Memory]] stores
3. Recent conversation turns (sliding window)
4. Tool outputs and intermediate results

The art is in deciding what gets promoted from short-term to long-term storage, and what gets retrieved back into context when needed. See [[Hybrid Memory Architectures]] for how modern systems handle this.
