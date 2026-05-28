---
tags: [company, open-source, memory-system, controversial]
created: 2026-05-27
---

# MemPalace

Open-source AI memory system. Second-highest GitHub stars in the agent memory space (nearly tied with [[Mem0]]), but with heavily disputed benchmark claims.

## Basics

- **GitHub**: 52,945 stars, 6,983 forks (verified May 27 2026). Created April 5, 2026.
- **License**: MIT
- **Language**: Python (93.9%)
- **Co-founders**: Milla Jovovich (actress) + Ben Sigman (crypto CEO). Hit 7K+ stars in 48 hours at launch.

## Origin Story

### The Founders

**Milla Jovovich** -- the actress (Resident Evil, The Fifth Element) -- was working on a gaming project and became frustrated with how AI systems store and retrieve information. She spent months designing a solution. Her GitHub account (`milla-jovovich`) was created September 14, 2025 -- six months before MemPalace launched. Her GitHub bio: *"Creator/Architect of MemPalace -- an open-source platform using structure to save your thoughts, verbatim. Lumi is my CLI agent aka Lu_Code."*

**Ben Sigman** (`bensig`, GitHub since 2012) -- founder of XAVIOR (an "AI operating system"), Libre Labs (decentralized Bitcoin lending), and 2718 Capital (Bitcoin hedge fund). UCLA alumnus, Santa Monica-based. Co-authored two Bitcoin books with Fred Krueger. Sigman introduced Jovovich to Anthropic's Claude.

How they connected is undocumented, but the division of labor is clear: Jovovich designed the concept and architecture; Sigman engineered the software. Jovovich's own framing: *"Claude could turn my words and ideas into reality."*

### How It Was Built

AI tools were central. Jovovich works with Claude and a personal CLI agent she calls "Lumi" (Lu_Code). The commit history shows `gemini-code-assist` providing code review and `Copilot` as a contributor. This is vibe coding at scale -- or more precisely, AI-assisted architecture by a non-traditional developer.

The commit timeline tells the story:
- **Apr 5, 2026 01:12 UTC** -- repository created
- **Apr 5, 01:16** -- Jovovich's foundational commit: full palace architecture, AAAK compression dialect, knowledge graph, 19 MCP tools
- **Apr 5, 01:33** -- Sigman adds benchmark runners, results docs, test suite
- **Apr 5, 01:37** -- Sigman fixes ruff lint/format errors across codebase
- **Apr 6** -- v3.0.0 released publicly (already at v3, suggesting significant pre-public development)

Jovovich is not a figurehead. She has 63 commits on main, authors substantive feature code (entity detection, performance optimizations, dependency management), manages releases, and was still actively committing as of v3.3.6 (May 24, 2026). Also: *"AI only knows what's already been done. It's the humans running it that actually create something unique and different."*

**Igor Lins e Silva** (`igorls`, CTO at RioBlocks/EOS Rio) emerged as the #1 contributor by commit count -- primary code reviewer, release coordinator, and merge gatekeeper from day one.

### The Launch

April 7, 2026. It went nuclear: **10,000 stars and 50 pull requests within 24 hours**. ~130 PRs in the first 48 hours. Decrypt published "Fifth Element Star Milla Jovovich Reveals AI Memory Tool MemPalace." Multiple Hacker News submissions, the top reaching 67 points.

A Penfield Labs analysis estimated a comparable project without celebrity attribution would have received ~50 stars in its first week. The celebrity name transformed engagement by orders of magnitude.

### The Controversy (and the Response)

The benchmark claims unraveled within hours of launch (see below). But the founders' response was notably fast and honest: **one day after launch** (April 7, 18:08 UTC), Jovovich committed "README: honest update from Milla & Ben -- own the mistakes, fix the claims." They relabeled headline scores as "raw mode only," removed "lossless" claims, added transparency notes, and marked unfinished features as experimental.

The repo's own 5,000-word `BENCHMARKS.md` had always disclosed many of the issues. The launch marketing simply stripped all caveats -- creating a gap between internal honesty and public claims that the auditors exposed.

### What This Says About the Agentic Era

The community mostly debated benchmark methodology. The meta-narrative -- an actress shipping a 53K-star open-source project using AI coding tools -- was surprisingly under-discussed. The closest commentary:

- *"Ideas are worth more than the code itself nowadays"* -- denysvitali (HN), framing Jovovich's architectural vision as the primary contribution
- *"It's cool that milla jovovich is vibe coding"* -- darkhanakh (HN), casual
- *"Famous B-rated movie star, crypto dudes and automatic programming hype"* -- diimdeep (HN), dismissive

The evidence sits between these takes. Jovovich has real architectural vision, uses AI tools to implement it, is learning engineering along the way, and actively maintains the project 8 weeks post-launch with 1,600+ PRs and dozens of contributors. Whether this constitutes "real" software engineering depends on definitions that are rapidly losing their meaning.

The question MemPalace poses isn't "is it any good?" (it's decent, overhyped, and improving). It's: **what happens when the barrier to shipping software drops to "have a clear idea and access to Claude"?** The answer is apparently 53K GitHub stars in seven weeks.

## Architecture

Hierarchical memory palace metaphor on top of ChromaDB:
- **Wings** -- top-level scopes (people, projects)
- **Rooms** -- topics within a wing
- **Drawers** -- individual content items

Stores conversation history as verbatim text, retrieves via semantic search. Includes a temporal entity-relationship graph with validity windows (SQLite-backed), 29 MCP tools, and auto-save hooks for Claude Code sessions.

## Benchmark Claims vs. Reality

**Claimed**: 96.6% R@5 on [[Memory Benchmarks|LongMemEval]] (no API calls), 98.4% hybrid, ~99% with LLM reranking.

**Independent audit findings**:
- The 100% LongMemEval score used `top_k=50` on sessions containing only 19-32 items -- effectively retrieving the *entire* conversation pool. The memory system contributed nothing to the score.
- The 100% scores required Claude API calls, contradicting "no cloud, no API" positioning.
- Hand-tuned: specific failing questions were identified and fixes engineered, then re-tested on those same questions. The benchmark's own `BENCHMARKS.md` integrity section asks testers not to do this.
- Metrics measure whether correct memories are *retrieved*, not whether the system *answers correctly* -- fundamentally different measurements conflated in marketing.

**Honest numbers** (per independent audit): 60.3% recall@10 without reranking; 88.9% recall@10 with hybrid retrieval. Competitive with local alternatives, but far below marketing claims.

**The underlying architecture is sound** -- the criticism is about how results were presented, not the engineering.

## Why It Matters

MemPalace at 53K stars in under two months is a demand signal regardless of benchmark validity. It shows:
1. Massive latent demand for local-first, zero-infrastructure agent memory
2. Celebrity co-founders + viral launch can manufacture GitHub stars at scale
3. The [[Memory Benchmarks|benchmark ecosystem]] is broken -- self-reported scores with no independent replication are the norm, and MemPalace is the most visible example of why that's a problem

## See Also

- [[Memory Benchmarks]] -- the broader evaluation problem
- [[Memory Middleware Players]] -- competitive context
- [[Obsidian Vaults as Agent Memory]] -- the grassroots zero-infrastructure trend MemPalace targets
