# Market Structure

The agent memory market is not a clean vertical stack. Players from every category reach into adjacent ones: cloud providers partner with middleware, database vendors ship memory SDKs, consumer platforms bypass the entire supply side, and users build their own memory from markdown files. The landscape is better understood as **overlapping competitive zones** than as layers.

## Axes

Three structural axes organize the landscape.

### Axis 1: Standalone vs. Embedded

Is memory the product, or a feature inside something else?

* **Standalone**: memory middleware (Mem0, Zep), grassroots systems (Obsidian vaults, CLAUDE.md)

* **Embedded**: memory as a feature of a platform (ChatGPT), cloud service (AWS AgentCore), framework (LangMem), or database (Neo4j agent-memory)

### Axis 2: Specialized vs. General

Deep memory capabilities, or "good enough" bundled memory?

* **Specialized**: temporal reasoning (Zep), token-efficient retrieval (Mem0), agent-controlled context (Letta), knowledge graph native (Cognee), reasoning-first ([[Honcho]] — logical inference at write time rather than novel storage/retrieval)

* **General**: cloud-managed memory priced to bundle, consumer AI memory, markdown files that handle 80% of use cases

### Axis 3: Integration Decision Maker

At runtime, the agent always decides *when* to read/write memory. But **who decided which memory system the agent uses?**

* **Platform-integrated**: The AI platform chose it. ChatGPT memory, Gemini memory, Copilot memory — you get it because you use the product. No decision required.

* **Developer-integrated**: A developer building an agent chose Mem0 or Zep and wired it into their stack. The end user doesn't know what's underneath.

* **User-integrated**: A power user set up an Obsidian vault, configured CLAUDE.md files, installed a Cline memory bank. They chose the system and structured it themselves.

* **Agent-integrated**: The agent itself decides how to organize its own memory (Letta/MemGPT, A-MEM). Not yet majorly prevalent, but architecturally distinct — the agent is both runtime user and, in a sense, the integrator of its own memory.

* **Org-integrated**: An IT or platform team decides that the organization's agents will use a shared memory system — an [[Enterprise World Model]]. Not a developer wiring middleware into one product, but an organizational capability decision. Microsoft Copilot's Work IQ layer, LinkedIn's internal HLTM, xpander.ai's enterprise world model. Emerging category, not yet widespread.

This axis matters because it determines what you compete on: platform-integrated memory competes on seamlessness, developer-integrated on API quality and benchmarks, user-integrated on transparency and control, org-integrated on coverage of organizational context and governance.

### Combining the Axes

```text
                    Specialized / Deep
                         |
     Memory middleware    |    Database extensions
     (Mem0, Zep, Letta,  |    (Neo4j agent-memory,
      Cognee, Hindsight)  |     Oracle SDK, Redis
                          |     Context Engine)
                          |
  Standalone  ────────────┼──────────── Embedded
                          |
     Grassroots / DIY     |    Platforms & cloud
     (Obsidian vaults,    |    (ChatGPT, Claude, Gemini,
      Cline memory banks, |     AWS AgentCore, Google
      CLAUDE.md pattern)  |     Memory Bank, LangMem)
                          |
                    General / Bundled

Integration decision maker:
  Middleware, DB extensions → developer-integrated
  Platforms & cloud → platform-integrated (consumer) or developer-integrated (cloud APIs)
  Grassroots → user-integrated
  Enterprise world models → org-integrated (emerging)
```

### Memory Middleware (standalone, specialized)

Dedicated memory-as-a-service. See [[Memory Middleware Players]] for detailed profiles.

Companies: [[Mem0]], [[Zep]], [[Letta]], [[Cognee]], [[Honcho]], [[Hindsight]], Supermemory, EverMind, Memvid, [[MemPalace]], Wato.

**Customer**: Developers and companies building agent-powered products. Mem0 has 80K developers on its cloud. Cognee is deployed in 70+ companies (Bayer, University of Wyoming). Zep targets regulated enterprise (SOC 2/HIPAA). The end user of the agent never sees the middleware — it's plumbing. The integration decision is usually made by the developer — though [[Honcho]] also appears as a user-selected plugin in [[OpenClaw and Clawlikes|Hermes Agent]], blurring the developer/user-integrated boundary.

This is the most active startup zone, but also the most exposed to squeeze from above (cloud bundling) and below (DIY approaches that are "good enough").

**Business model**: Predominantly open-core (OSS framework + managed cloud + enterprise tier). Monetization is early -- Letta's ~$1.4M ARR (at $0.00015/sec API pricing) is the only publicly reported revenue figure.

### Database Extensions (embedded, specialized)

Infrastructure vendors reaching up into memory by building SDKs and managed features on top of their core storage products.

**Customer**: The same developers and infrastructure teams already using these databases. Memory features are an upsell on existing relationships — "you already run Neo4j, now use our agent-memory package too." The integration decision is made by the developer, but often path-dependent on prior infrastructure choices.

[[Vector Databases for Memory|Vector databases]]**:**

| Company       | Funding                                | Position                                                     |
| ------------- | -------------------------------------- | ------------------------------------------------------------ |
| Pinecone      | $138M+                                 | Managed leader, but ARR fell from $26.6M to $14M (2024-2025) |
| Qdrant        | $87.8M (incl. $50M Series B, Mar 2026) | Fastest-growing; Rust-based, speed leader                    |
| Weaviate      | $100M+                                 | Strongest hybrid search (vector + BM25)                      |
| Zilliz/Milvus | $100M+                                 | Growing enterprise traction                                  |
| Chroma        | $18M                                   | Developer experience leader, embedded-first                  |
| pgvector      | Open source                            | Postgres-native default; "good enough" for most              |

**Trend**: Vectors becoming a data type inside multi-model databases (pgvector, MongoDB Atlas Vector Search) rather than requiring standalone DBs. The standalone vector DB market is compressing.

[[Knowledge Graphs for Memory|Graph databases]]**:**

* **Neo4j** -- $100M investment (Oct 2025) to become the "knowledge layer for agentic systems." Ships `agent-memory` package, MCP server, Aura Agent (early access).

* **FalkorDB** -- RedisGraph successor. Sub-10ms queries. Graphiti integration for multi-agent environments.

**Cloud-native storage**: Amazon S3 Vectors, Neptune Analytics, Azure AI Search -- hyperscalers building native vector/graph into their storage stacks.

### Platforms and Cloud-Managed Memory (embedded, general)

Memory as a feature inside something bigger: agent platforms, cloud services, and consumer AI products. This zone spans two different customers and two different integration decisions:

* **Cloud services and frameworks**: customer is the developer building on the platform. The developer chooses AWS AgentCore or LangMem the same way they choose any cloud service. Developer-integrated.

* **Consumer AI products**: customer is the end user of ChatGPT, Claude, Gemini, or Copilot. Memory is a product feature — the user didn't choose it, it came with the product. Platform-integrated. Nobody pays for memory specifically; they pay for the AI product.

Three sub-categories:

**Cloud provider managed services** ([[Cloud Provider Memory Services]]):

| Provider  | Product                      | Status        | Pricing             |
| --------- | ---------------------------- | ------------- | ------------------- |
| Google    | Vertex AI Memory Bank        | GA (Jan 2026) | $0.25 / 1K events   |
| AWS       | Bedrock AgentCore Memory     | GA (2026)     | Bundled             |
| Microsoft | Foundry Agent Service Memory | Preview       | Free (preview)      |
| Oracle    | AI Agent Memory SDK          | Expected 2026 | Leverages Oracle DB |

**Agent frameworks with built-in memory**:

* **LangChain/LangGraph** -- LangMem SDK for long-term memory, namespace-based tenant isolation. Caveat: p95 search latency of 59.82 seconds on benchmarks.

* **CrewAI** -- Four memory types (short/long/entity/user), LanceDB default storage.

* **Microsoft Agent Framework (MAF)** -- Merges Semantic Kernel + AutoGen. RC status Feb 2026. Mem0 integration via official provider.

**Consumer AI platforms** ([[Platform Memory Features]]):\
ChatGPT, Claude, Gemini, and Copilot all have native memory. These bypass the entire middleware/infrastructure supply side -- they're vertically integrated.

**Notable: [[Claude Managed Agents Memory Store]]** -- Anthropic's managed agents memory is the architectural outlier in this zone. Where every other cloud/platform solution uses vectors, embeddings, or graph retrieval, Anthropic ships plain text documents at hierarchical paths — the agent navigates memory with the same file tools (`read`, `write`, `glob`, `grep`) it uses for code. No embedding model, no semantic search. This is the grassroots file-based approach (CLAUDE.md, Obsidian vaults) productized as developer infrastructure. The async **Dreams** consolidation feature (modeled on hippocampal sleep replay) addresses the grassroots ceiling of context rot without abandoning the file paradigm.

### Grassroots / DIY (standalone, general)

Users building their own agent memory from files, templates, and Obsidian vaults. See [[Obsidian Vaults as Agent Memory]].

**Customer**: The user *is* the builder. Power users and individual developers who set up their own memory systems — choosing the structure, writing the templates, curating the content. User-integrated. Nobody pays anyone; the "product" is a pattern or template that gets forked and adapted.

Not a product category in the traditional sense, but a competitive force: if developers can get "good enough" memory from a folder of markdown files, the bar for paid middleware rises. Cline (62K stars) has higher adoption than any middleware product.

Key examples: [[Cline Memory Bank]], [[Karpathy LLM Wiki]], [[Obsidian MCP Servers]], Claude's own CLAUDE.md hierarchical file approach.

## Usage Patterns

How memory systems actually get used at runtime — independent of who built them or who integrated them. Three questions: how does memory enter the agent's context, how does memory get created, and who decides what's relevant.

### Read: How Memory Enters Context

**Context injection** -- memory is loaded into the system prompt or context window before the agent acts. The agent doesn't choose to access it; it's already there.
- CLAUDE.md files (loaded by the harness at session start)
- Cline memory bank ("you MUST read ALL memory bank files at start of EVERY task")
- ChatGPT memory (platform selects and injects relevant memories)
- Copilot Work IQ (persistent understanding injected into M365 context)
- [[Claude Managed Agents Memory Store]] store descriptions (injected into system prompt automatically)

**Memory tool calls** -- the agent explicitly invokes a memory-specific tool to search or retrieve.
- [[Mem0]] (`search_memory`, `add_memory`)
- [[Letta]] (`archival_memory_search`, `core_memory_replace`)
- [[Claude-Mem]] MCP tools (`search`, `timeline`, `get_observations`)
- [[Obsidian MCP Servers]] (search, read note)

**File operations** -- the agent uses general-purpose file tools (`read`, `write`, `glob`, `grep`) to navigate memory. No memory-specific API exists; memory is just files.
- [[Claude Managed Agents Memory Store]] (standard file tools on a mounted directory)
- Direct vault access (agent reads .md files from disk)

These aren't mutually exclusive. Claude Managed Agents Memory Store injects store descriptions (context injection) but the agent navigates the actual contents via file operations. [[Claude-Mem]] captures via hooks (automatic) but the agent retrieves via MCP tool calls.

### Write: How Memory Gets Created

**Automatic capture** -- the system records memories without the agent explicitly deciding to store.
- [[Claude-Mem]] lifecycle hooks (PostToolUse, SessionEnd capture observations automatically)
- ChatGPT (extracts memories from conversation in the background)
- Gemini (extracts "key details and preferences" without prompting)

**Agent-initiated** -- the agent decides to write a memory via tool call or file write.
- [[Letta]] (`archival_memory_insert`, `core_memory_replace`) -- the agent is the author
- [[Mem0]] (`add_memory`) -- though Mem0's extraction is system-controlled, the agent triggers it
- [[Claude Managed Agents Memory Store]] -- the agent writes files when it judges something worth persisting
- [[Cline Memory Bank]] -- the agent updates memory files during the session per its instructions

**User-curated** -- the user manually creates or edits memories.
- Obsidian vaults (user writes and organizes notes)
- CLAUDE.md (user edits directly in their editor)
- ChatGPT memory settings (user adds/deletes explicit "saved memories")

**Async consolidation** -- a separate process reorganizes or compresses memories after the session.
- [[Claude Managed Agents Memory Store#Dreams|Dreams]] (model-powered consolidation of session transcripts into reorganized stores)
- [[Karpathy LLM Wiki]] (raw → wiki synthesis, typically user-initiated)
- [[Claude-Mem]] (AI compression of captured observations)

### Retrieval Decision: Who Decides What's Relevant

**System-automatic** -- the platform decides what memories are relevant and surfaces them without being asked.
- ChatGPT memory (platform selects relevant memories per conversation)
- Copilot Work IQ (surfaces org context based on task)

**Agent-chosen** -- the agent decides when to search and what to search for.
- [[Letta]] (agent searches its own archival memory as needed)
- [[Claude Managed Agents Memory Store]] (agent navigates files using its own judgment)
- [[Claude-Mem]] MCP tools (agent issues search queries)
- [[Mem0]] (agent calls search when it judges context is needed)

**Instruction-driven** -- the agent follows rules about what to read, typically set by the developer or user.
- [[Cline Memory Bank]] ("read ALL files at start" -- no selection, no judgment)
- CLAUDE.md (always loaded by the harness, agent doesn't choose)
- Developer-authored system prompts that tell the agent when to call memory tools

### Patterns by System

| System | Read | Write | Retrieval decision |
|--------|------|-------|-------------------|
| [[Mem0]] | Tool calls | Agent-initiated (system extracts) | Agent-chosen |
| [[Zep]] | Tool calls | Automatic (Graphiti extraction) | Agent-chosen |
| [[Letta]] | Tool calls | Agent-initiated | Agent-chosen |
| [[Claude Managed Agents Memory Store]] | File ops + context injection | Agent-initiated + async consolidation (Dreams) | Agent-chosen |
| [[Claude-Mem]] | MCP tool calls | Automatic capture + async compression | Agent-chosen |
| [[Honcho]] | Tool calls (dialectic query, five cost/depth tiers) + context injection | Automatic (background deriver at ~1K token threshold) + async consolidation (Dreaming) | System-reasoned (write) + agent-chosen (read) |
| [[Cline Memory Bank]] | Context injection (read all) | Agent-initiated (update during session) | Instruction-driven (read everything) |
| CLAUDE.md | Context injection | User-curated | Instruction-driven (always loaded) |
| Obsidian vault + MCP | MCP tool calls | User-curated | Agent-chosen |
| ChatGPT memory | Context injection | Automatic + user-curated | System-automatic |
| Copilot Work IQ | Context injection | Automatic | System-automatic |

## Cross-Cutting Competitive Axes

These tensions cut across all four zones. See [[Competitive Dynamics]] for deeper analysis.

1. **Quality vs. distribution** -- [[Hindsight]]'s 91.4% LongMemEval vs. [[Mem0]]'s 49% but massive ecosystem and AWS partnership. The best retrieval doesn't always win.

2. **Open vs. closed** -- [[Zep]] killed Community Edition; [[Mem0]] thrives on OSS (56.9K stars). Open source drives adoption but is hard to monetize.

3. **Specialized vs. bundled** -- Middleware depth vs. cloud "good enough." The [[Cloud Provider Memory Services|AWS-Mem0 partnership]] suggests even hyperscalers see memory as non-trivial to build well.

4. **Standards (**[[Model Context Protocol|MCP]]**) as leveler** -- Commoditizes integration, shifts competition to retrieval quality. If any MCP-compatible memory plugs into any agent, the best retrieval wins.

## Where Value Accrues

The infrastructure zone is commoditizing (vectors are becoming a commodity data type). Middleware captures the most differentiated value today -- retrieval quality, temporal reasoning, token efficiency. But cloud bundling is the existential threat: when AWS/GCP/Azure offer "good enough" memory inside their agent platforms, middleware must differentiate on quality or get squeezed. Meanwhile, the grassroots zone exerts pressure from below -- free, transparent, user-controlled, and surprisingly effective for many use cases.

⠀