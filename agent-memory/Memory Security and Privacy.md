---
tags: [index, security, privacy, forgetting]
created: 2026-05-27
---

# Memory Security and Privacy

Long-term memory introduces a new attack surface for AI agents. Unlike prompt injection (targeting the current session), memory attacks persist across sessions.

## Attacks

See [[Memory Poisoning]] for detailed coverage of:
- **MINJA** -- injection through regular queries (95% success rate)
- **MemoryGraft** -- implanting fake [[Episodic Memory|episodic memories]]
- The **Mnemonic Sovereignty** threat taxonomy (injection, extraction, manipulation, denial)

## OWASP Guidance

The AI Agent Security Cheat Sheet recommends:
- Sanitize before storage
- Isolate memory between users (strict tenant boundaries)
- Set expiration limits (TTLs)
- Audit for sensitive data (PII, credentials)
- Cryptographic integrity checks
- Principle of least privilege for memory read/write

## Privacy-Aware Forgetting

The "Forgetful but Faithful" paper (December 2025) proposes privacy-aware [[Memory Operations#Forgetting|forgetting]] with differential privacy guarantees. The MaRS framework defines six forgetting policies.

Core tension: agents need to remember enough to be useful but forget enough to respect privacy. GDPR "right to be forgotten" applies to agent memories.

## Multi-Agent Security

Additional risks in [[Multi-Agent Shared Memory]] environments:
- Cross-agent memory leakage
- Shared memory poisoning affecting all agents in a team
- Privilege escalation via unauthorized memory access

## Practical Checklist

1. Treat memory as untrusted input at retrieval time (defense in depth)
2. Implement per-user memory isolation from day one
3. Log memory operations for audit trails
4. Plan for memory deletion/expiration at the data model level
5. Test against [[Memory Poisoning|memory poisoning]] as part of security review

## See Also

- [[Memory Poisoning]] -- attack vectors in detail
- [[Memory Operations#Forgetting]] -- the forgetting lifecycle
- [[Platform Memory Features]] -- how platforms handle user memory privacy
