---
tags: [system, anthropic, managed-agents, memory-store, api, dreaming]
created: 2026-05-27
---

# Claude Managed Agents Memory Store

Anthropic's approach to agent memory in their [[Platform Memory Features|Managed Agents]] platform (beta, April 2026). Architecturally distinctive: memory is a **workspace-scoped filesystem of plain text documents**, not a vector database. The agent reads and writes memory using the same file tools it uses for everything else -- no separate "memory tool" exists.

Requires `managed-agents-2026-04-01` beta header. Available to all API accounts.

## Data Model

Three entities:

- **Memory Store** (`memstore_...`): Named container, workspace-scoped. Has `name`, `description` (up to 1024 chars, injected into the agent's system prompt), and `metadata` (up to 16 key-value pairs, hidden from agent).
- **Memory** (`mem_...`): Individual text document within a store. Addressed by a hierarchical **path** (e.g., `/preferences/coding-style.md`). Content is UTF-8, max **100 kB (~25K tokens)**. Carries `content_sha256` hash for diffing and optimistic concurrency.
- **Memory Version** (`memver_...`): Immutable snapshot created on every mutation. Retained for **30 days** (most recent always kept). Survives even after the parent memory is deleted. Enables audit trail and point-in-time recovery.

## How It Works

1. **Create** a memory store via the API
2. Optionally **pre-populate** it with memories (text documents at hierarchical paths)
3. **Attach** the store as a `resource` when creating a session (up to **8 stores per session**)
4. The store is **mounted as a directory** inside the session's container at `/mnt/memory/<slug>`
5. The agent uses standard file tools (`read`, `write`, `edit`, `glob`, `grep`) to interact with it
6. Writes are **persisted back** and stay in sync across all sessions sharing the store

Store descriptions and per-attachment `instructions` (max 4096 chars) are automatically injected into the system prompt, guiding the agent on what the store contains and how to use it.

## API Surface

All endpoints require the `managed-agents-2026-04-01` beta header.

### Memory Stores

| Operation | Method | Endpoint |
|-----------|--------|----------|
| Create | POST | `/v1/memory_stores` |
| Retrieve | GET | `/v1/memory_stores/{id}` |
| Update | POST | `/v1/memory_stores/{id}` |
| List | GET | `/v1/memory_stores` |
| Archive | POST | `/v1/memory_stores/{id}/archive` |
| Delete | DELETE | `/v1/memory_stores/{id}` |

### Memories (within a store)

| Operation | Method | Endpoint |
|-----------|--------|----------|
| Create | POST | `/v1/memory_stores/{store_id}/memories` |
| Retrieve | GET | `/v1/memory_stores/{store_id}/memories/{mem_id}` |
| Update | POST | `/v1/memory_stores/{store_id}/memories/{mem_id}` |
| List | GET | `/v1/memory_stores/{store_id}/memories` |
| Delete | DELETE | `/v1/memory_stores/{store_id}/memories/{mem_id}` |

List supports `path_prefix`, `depth`, `order_by` parameters. Update supports `precondition` with `content_sha256` for optimistic concurrency (returns HTTP 409 on conflict).

### Memory Versions (audit trail)

| Operation | Method | Endpoint |
|-----------|--------|----------|
| List | GET | `/v1/memory_stores/{store_id}/memory_versions` |
| Retrieve | GET | `/v1/memory_stores/{store_id}/memory_versions/{ver_id}` |
| Redact | POST | `/v1/memory_stores/{store_id}/memory_versions/{ver_id}/redact` |

### Attaching to Sessions

Memory stores connect to sessions via the `resources` array at session creation:

```json
{
  "resources": [{
    "type": "memory_store",
    "memory_store_id": "memstore_01Hx...",
    "access": "read_write",
    "instructions": "Store user preferences and project context here."
  }]
}
```

Access modes: `read_write` (default) or `read_only`. Stores cannot be added or removed from a running session.

### SDK Support

Available in Python (`client.beta.memory_stores`), TypeScript (`client.beta.memoryStores`), Go, Java, C#, Ruby, PHP, and the `ant` CLI tool.

### Rate Limits

| Type | Limit |
|------|-------|
| Create endpoints | 300 req/min |
| Read endpoints | 600 req/min |

## Dreams (Async Memory Consolidation)

**Research Preview** -- requires additional `dreaming-2026-04-21` header and separate [access request](https://claude.com/form/claude-managed-agents).

Dreams let Claude **reflect on past sessions to curate and consolidate** a memory store. The system reads an existing store plus session transcripts, then produces a **new, reorganized store** -- duplicates merged, stale entries replaced, new insights surfaced. The input store is never modified.

Modeled on hippocampal sleep replay: background consolidation of episodic experience into structured long-term memory. See [[Memory Operations#Consolidation]] for the general concept.

### Dream API

| Operation | Method | Endpoint |
|-----------|--------|----------|
| Create | POST | `/v1/dreams` |
| Retrieve | GET | `/v1/dreams/{id}` |
| List | GET | `/v1/dreams` |
| Cancel | POST | `/v1/dreams/{id}/cancel` |
| Archive | POST | `/v1/dreams/{id}/archive` |

```json
{
  "inputs": [
    {"type": "memory_store", "memory_store_id": "memstore_01Hx..."},
    {"type": "sessions", "session_ids": ["sesn_01...", "sesn_02..."]}
  ],
  "model": "claude-opus-4-7",
  "instructions": "Focus on coding-style preferences; ignore one-off debugging notes."
}
```

### Dream Constraints

- Up to **100 sessions** per dream
- `instructions` max **4,096 characters**
- Models: `claude-opus-4-7`, `claude-sonnet-4-6`
- Runtime: minutes to tens of minutes depending on input size
- Lifecycle: `pending` -> `running` -> `completed` | `failed` | `canceled`
- Once running, exposes a `session_id` for real-time observability (stream the dream's own events)
- Billed at standard API token rates for the selected model

## Architecture: Why Files, Not Vectors

The design is philosophically aligned with Anthropic's CLAUDE.md approach to consumer memory: plain text, hierarchical, human-readable.

Key properties:
- **No embedding or semantic search.** The agent uses its own reasoning to decide what to read and what to write.
- **No retrieval-augmented generation** in the traditional sense. The agent navigates memory like a filesystem.
- **Optimistic concurrency** via SHA-256 preconditions, not locks.
- **Immutable versioning** for audit trail, not real-time deduplication.
- **Dreams** handle consolidation asynchronously rather than at write time.

This is a bet that frontier models are good enough at reasoning over file structures that they don't need embedding-based retrieval as a crutch. It also means memory is **inspectable and editable** by humans -- you can read, write, and debug memories directly through the API without understanding vector spaces.

Contrast with [[Mem0]] (hybrid vector + graph, system-controlled extraction), [[Zep]] ([[Temporal Knowledge Graphs|bitemporal knowledge graph]], system-controlled), and [[Letta]] (agent-controlled but using structured archival/recall functions).

## Security Considerations

The docs explicitly warn about [[Memory Poisoning|prompt injection risks]] with `read_write` stores: if the agent processes untrusted input, a successful injection could write malicious content that later sessions read as trusted memory. Recommendation: use `read_only` for reference material and any store the agent doesn't need to modify.

Not eligible for Zero Data Retention (ZDR) or HIPAA BAA coverage due to stateful nature.

## Competitive Position

The first model provider to ship file-based agent memory as a managed service. The approach is opinionated -- it trades the flexibility of [[Vector Databases for Memory|vector search]] and [[Knowledge Graphs for Memory|graph traversal]] for simplicity and inspectability.

The Dreams feature is the most direct implementation of [[Memory Operations#Consolidation|memory consolidation]] in a commercial product. Most middleware handles consolidation at write time (extract-then-store); Dreams handle it as a distinct async phase, which may prove more robust for long-running agents that accumulate noisy episodic data.

Open question: how well does filesystem-style navigation scale as memory stores grow to thousands of documents? The 100 kB per-document limit and hierarchical path structure suggest Anthropic expects relatively structured, curated stores rather than unbounded accumulation.

## See Also

- [[Platform Memory Features#Claude (Anthropic)]] -- consumer-facing Claude Memory
- [[Memory Operations]] -- encoding, storage, retrieval, consolidation, forgetting
- [[Agentic Memory]] -- the broader trend of agent-directed memory
- [[Cloud Provider Memory Services]] -- how hyperscalers compare
- [[Memory Security and Privacy]] -- attack vectors for persistent memory
- [[Memory Poisoning]] -- the specific risk Anthropic warns about
