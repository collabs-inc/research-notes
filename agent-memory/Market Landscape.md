# Market Landscape

The AI agent memory market in mid-2026: a fast-growing segment within the broader agentic AI infrastructure stack, transitioning from early fragmentation toward consolidation.

## Demand Signals

No credible independent sizing exists for "agent memory" as a market. But the demand signals are loud:

### Developer Adoption (GitHub Stars, May 2026)

**Memory middleware and systems** (verified via `gh api`, May 27 2026):

| Repo                                   | Stars  | Forks |
| -------------------------------------- | ------ | ----- |
| **mem0ai/mem0**                        | 56,909 | 6,476 |
| **MemPalace/mempalace**                | 52,945 | 6,983 |
| **getzep/graphiti**                    | 26,672 | 2,656 |
| **letta-ai/letta**                     | 22,999 | 2,452 |
| **rohitg00/agentmemory**               | 18,693 | 1,538 |
| **topoteretes/cognee**                 | 17,545 | 1,851 |
| **memvid/memvid**                      | 15,579 | 1,343 |
| **vectorize-io/hindsight**             | 14,867 | 843   |
| **getzep/zep** (examples/integrations) | 4,615  | 631   |
| **Agent-Memory-Paper-List** (survey)   | 2,061  | 94    |
| **WujiangXu/A-mem** (NeurIPS 2025)     | 896    | 92    |

**Grassroots memory banks and Obsidian ecosystem** (verified via `gh api`, May 27 2026):

| Repo / Tool                              | Stars  | Forks  | Category                        |
| ---------------------------------------- | ------ | ------ | ------------------------------- |
| **thedotmack/claude-mem**                | 79,200 | 6,800  | User-integrated memory system   |
| **cline/cline**                          | 62,417 | 6,549  | Agent (5M+ installs)            |
| **YishenTu/claudian**                    | 11,941 | 719    | Obsidian plugin                 |
| **AgriciDaniel/claude-obsidian**         | 5,636  | 644    | Vault-as-memory (Karpathy wiki) |
| **Karpathy LLM Wiki gist**               | 5,000+ | 4,000+ | Pattern                         |
| **MarkusPfundstein/mcp-obsidian**        | 3,791  | 448    | MCP server                      |
| **vanzan01/cursor-memory-bank**          | 3,035  | 440    | Memory bank template            |
| **breferrari/obsidian-mind**             | 2,710  | 337    | Vault-as-memory                 |
| **GreatScottyMac/roo-code-memory-bank**  | 1,674  | 189    | Memory bank template            |
| **eugeniughelbur/obsidian-second-brain** | 1,403  | 153    | Vault-as-memory                 |
| **bitbonsai/mcpvault**                   | 1,312  | 105    | MCP server                      |
| **lucasrosati/claude-code-memory-setup** | 714    | 60     | Vault-as-memory                 |
| **nickbaumann98/cline_docs**             | 582    | 70     | Original template               |

### Package Downloads (PyPI, May 2026)

| Package           | Total Downloads | Last 30 Days     |
| ----------------- | --------------- | ---------------- |
| **mem0ai**        | 30.0M           | 3.0M (~101K/day) |
| **graphiti-core** | 5.69M           | 542K (~18K/day)  |
| **langmem**       | 4.49M           | ~450K (~15K/day) |
| **letta**         | 709K            | 125K (~4.2K/day) |

### First-Party Traction ([[Mem0]])

From Mem0's Series A announcement (Oct 2025, verified by TechCrunch):

* API calls: 35M (Q1 2025) → 186M (Q3 2025), ~30% MoM growth

* 80,000+ developers on cloud service

* 14M PyPI downloads at announcement (now 30M, 6 months later)

### Viral Moments

* **Karpathy LLM Wiki tweet** (Apr 2026): 16M+ views, 59K likes, 106K bookmarks, 9.2K quotes. Spawned dozens of implementation repos within two weeks.

* **Karpathy's gist**: 5,000+ stars, 4,000+ forks

* **Mem0 Show HN**: 201 points, 61 comments (Sep 2024)

## Market Structure

See [[Market Structure and Value Chain]] for the full breakdown.

The market is better understood as four overlapping competitive zones than as a linear stack:

* **Memory middleware** (standalone, specialized) -- [[Memory Middleware Players|Mem0, Zep, Letta, Cognee, Hindsight]]

* **Database extensions** (embedded, specialized) -- [[Vector Databases for Memory|vector DBs]], [[Knowledge Graphs for Memory|graph DBs]] reaching up into memory

* **Platforms and cloud** (embedded, general) -- [[Cloud Provider Memory Services|Google Memory Bank, AWS AgentCore]], [[Platform Memory Features|ChatGPT, Claude, Gemini]], agent frameworks

* **Grassroots / DIY** (standalone, general) -- [[Obsidian Vaults as Agent Memory|Obsidian vaults]], [[Cline Memory Bank|memory banks]], file-based patterns

## Investment

Memory-specific funding is early-stage but accelerating:

| Company     | Round    | Amount | Date     | Lead               |
| ----------- | -------- | ------ | -------- | ------------------ |
| [[Mem0]]    | Series A | $24M   | Oct 2025 | Basis Set Ventures |
| [[Letta]]   | Seed     | $10M   | Sep 2024 | Felicis            |
| [[Cognee]]  | Seed     | $7.5M  | Feb 2026 | Pebblebed          |
| Supermemory | Seed     | $3M    | Oct 2025 | --                 |
| [[Zep]]     | Pre-seed | $500K  | Mar 2024 | Y Combinator       |

Active VCs: Y Combinator (Mem0 + Zep), Basis Set Ventures (Mem0 lead), Felicis (Letta lead), Pebblebed (Cognee lead), Peak XV / GitHub Fund (Mem0).

Notable angels: Jeff Dean and Clem Delangue (Letta), Scott Belsky and Dharmesh Shah (Mem0), OpenAI and FAIR founders (Cognee).

See [[Competitive Dynamics]] for how these players interact and where the market is heading.

⠀