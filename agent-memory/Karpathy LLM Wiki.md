---
tags: [pattern, karpathy, wiki, knowledge-base, viral]
created: 2026-05-27
---

# Karpathy LLM Wiki

A three-layer knowledge base architecture proposed by Andrej Karpathy in April 2026. The most viral single contribution to the [[Obsidian Vaults as Agent Memory|vault-as-memory]] ecosystem.

## The Pattern

```
raw/      # Immutable source documents (PDFs, transcripts, data)
wiki/     # LLM-generated synthesized pages
CLAUDE.md # Schema and instructions for the agent
```

The key insight: a **compiled knowledge base** (synthesized understanding) is more useful than raw document retrieval ([[Retrieval-Augmented Generation|RAG]]). The LLM reads raw sources once, synthesizes them into wiki pages, and then works from the wiki going forward. Karpathy claims 70x more efficiency than traditional RAG.

## Engagement

- Original X post (Apr 3, 2026): **16M+ views, 59K likes, 106K bookmarks, 9.2K quotes, 2.8K retweets**
- GitHub Gist: **5,000+ stars, 4,000+ forks** within two weeks
- Spawned dozens of implementation repos, including claude-obsidian (5,500+ stars)
- Follow-up "Farzapedia" tweet praised explicit memory artifacts over opaque "AI that learns"
- Rohit Ghumare's LLM Wiki v2 extension: 111 gist stars in one week

The pattern resonated because it formalized something power users were already doing: building curated knowledge bases that agents read, rather than relying on retrieval over raw documents.

## Connection to Formal Memory Research

The Karpathy wiki pattern is essentially human-curated [[Semantic Memory]] with a manual [[Memory Operations#Consolidation|consolidation]] step. The `raw → wiki` transformation mirrors what [[Generative Agents]]' reflection mechanism does automatically: synthesize low-level observations into higher-level understanding.

The difference: Karpathy's approach keeps the human in the loop for quality control, trading automation for accuracy.

## See Also

- [[Obsidian Vaults as Agent Memory]] -- the broader practice
- [[Cline Memory Bank]] -- the project-local alternative
- [[Semantic Memory]] -- the formal memory type this implements
- [[Memory Operations#Consolidation]] -- the automated version of raw → wiki synthesis
