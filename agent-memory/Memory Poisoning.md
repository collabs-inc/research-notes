---
tags: [concept, security, attack, poisoning]
created: 2026-05-27
---

# Memory Poisoning

A class of attacks targeting how AI agents *remember*, not just how they respond in the current session. Poisoned memories persist across sessions and can influence thousands of future interactions.

## Attack Vectors

### MINJA (Memory INJection Attack)

Poisons long-term memory through regular-looking queries. The attacker crafts inputs that, once stored as memories, will influence future retrieval and responses. **95% injection success rate** in tested systems.

The attack exploits the [[Memory Operations#Encoding|encoding]] pipeline -- if the system stores user inputs as memories without sufficient validation, adversarial content enters the memory store through normal conversation.

### MemoryGraft

Implants fake "successful experiences" into [[Episodic Memory|episodic memory]]. The agent "remembers" executing a strategy that worked, biasing it toward that strategy in future tasks -- even though the experience never happened.

Targets [[Procedural Memory]]: by injecting false success memories, the attacker steers the agent's future behavior.

## Why It's Dangerous

Traditional prompt injection targets a single session. Memory poisoning targets the *substrate* of future behavior:
- A poisoned memory can influence thousands of future interactions
- The user (or even the operator) may never see the poisoned content directly
- The agent acts on contaminated memories with high confidence ("Based on our previous conversation...")

## Defenses (OWASP Guidance)

From the AI Agent Security Cheat Sheet:
- **Sanitize before storage** -- validate and clean all data entering memory
- **Isolate memory between users** -- strict tenant boundaries prevent cross-contamination
- **Set expiration limits** -- memories should have TTLs to limit attack persistence
- **Audit for sensitive data** -- scan memories for injected instructions
- **Cryptographic integrity checks** -- detect tampering with stored memories
- **Treat memory as untrusted input at retrieval time** -- defense in depth

## The Mnemonic Sovereignty Framework

The April 2026 survey "Mnemonic Sovereignty" establishes memory security as a distinct domain with its own threat taxonomy:
- **Injection** -- inserting false memories
- **Extraction** -- stealing stored personal data from memory
- **Manipulation** -- modifying existing memories to change behavior
- **Denial** -- preventing the agent from accessing its memories

## See Also

- [[Memory Security and Privacy]] -- broader security and privacy context
- [[Memory Operations#Encoding]] -- the pipeline stage where poisoning enters
- [[Multi-Agent Shared Memory]] -- additional attack surface when agents share memory
