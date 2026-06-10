---
tags: [pattern, knowledge-work, obsidian, codex, grassroots]
created: 2026-05-28
source: https://jxnl.co/writing/2026/05/10/codex-maxxing/
---

# Codex-Maxxing

A May 2026 article by Jason Liu (OpenAI Codex team) on pushing an agentic coding
tool past software development into general **knowledge work**, with a markdown
vault as the agent's persistent memory. A concrete, single-user instance of the
[[User-Integrated Memory Gap|user-integrated]] pattern and the broader
[[Obsidian Vaults as Agent Memory|vault-as-memory]] practice.

## Knowledge-Work Workflows

Most of these are not "write code":

- **Chief-of-Staff thread** -- monitors Gmail and Slack every ~30 min, prioritizes
  messages, researches answers, and drafts replies *without sending*.
- **Research & writing** -- raw voice transcripts become starting material for posts.
- **Social monitoring** -- a dedicated pinned thread watching Twitter.
- **Artifact production** -- Slidev decks, PDFs, spreadsheets, HTML.
- **Animation review loop** -- watches Slack feedback every ~15 min, re-renders with
  Remotion, re-uploads the new cut.
- **Customer support** -- autonomously negotiates an Amazon refund, polling chat and
  tightening cadence once a human agent joins.
- **Project coordination** -- tracking people, decisions, and project state.

## Primitives

- **Pinned megathreads + compaction** -- one long-running thread per workstream
  accumulates history, preferences, and old decisions ("not free" in token cost).
- **Voice input** -- captures "the unedited version of my thinking," not for typing
  convenience.
- **Steering** -- add direction *while* the agent works instead of waiting between steps.
- **Heartbeats** -- recurring, self-scheduling automation with dynamic cadence.
- **Remote control** -- drive the agent from anywhere to preserve momentum.

## Memory Architecture

An Obsidian vault kept as a **GitHub repo**, separate from any code repo --
"repositories hold code, the vault holds rolling context":

```
vault/
├── TODO.md
├── people/
├── projects/
├── agent/
└── notes/
```

- An `AGENTS.md` (the Codex analogue of `CLAUDE.md`) carries the standing rule:
  update the relevant page as you learn about people, make progress, make a decision,
  or close an open loop.
- **Git diff is the review interface** -- reading the diff shows "what it thought was
  important enough to remember," rather than letting threads quietly accumulate vibes.
- Files-as-memory give **durability**: if a thread dies, compacts badly, or gets too
  expensive, the knowledge survives on disk.

## Principles

- "The more [the agent] gets places to remember, revisit, inspect, and act, the less my
  work dies between prompts."
- **Operating loops, not one-shots** -- wire tools together into a feedback loop.
- **Strong goals need an oracle** -- "A weak goal is 'implement the plan in this Markdown
  file.' A strong goal has a real success criterion." Execution is only as good as the
  goal and the verification.
- **Artifacts as interface** -- inspect and annotate the rendered thing, don't describe it.

## See Also

- [[Obsidian Vaults as Agent Memory]] -- the broader grassroots practice
- [[User-Integrated Memory Gap]] -- the market category this exemplifies
- [[Why Obsidian for Agent Memory]] -- platform properties it relies on
- [[Karpathy LLM Wiki]] -- the other viral vault-as-memory pattern
- [[Claude Managed Agents Memory Store]] -- the productized file-based precedent
