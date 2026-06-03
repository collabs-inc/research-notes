---
tags: [concept]
created: 2026-06-03
---

# The Disposable Artifact

The reframing that resolves HTML's persistence and versioning weaknesses: the generated artifact is **cheap and regenerable**, so the durable asset is the *idea/spec*, not the file.

## The "Idea File"

[[product-engineering/Andrej Karpathy|Andrej Karpathy]]'s framing (2026): "in this era of LLM agents, there is less of a point/need of sharing the specific code/app — you just share the idea, then the LLM regenerates it." The artifact becomes a *view* of the idea that any model can re-emit on demand. This connects directly to [[product-engineering/Specs Are the New Code|"specs are the new code"]] — the spec is the source, the HTML is the compile.

## Micro-Software

[[Thariq Shihipar]] frames the smallest version: HTML artifacts as "disposable user interfaces" — "micro-software on top of micro-software." He notes only ~1% of generated tokens become production code; the other ~99% is scaffolding (plans, interfaces, design systems) — which justifies spending tokens on rich, sometimes-throwaway HTML.

## The Tension

Disposability dodges the versioning and persistence objections — but only while the artifact stays small and personal. It does not answer enterprise reviewability or compliance ([[The Case Against HTML]]). And there's a deeper tension: a *frozen* single-file artifact is durable and portable; an artifact that phones home to a model API (e.g. Claude's `window.claude.complete()`) is intelligent but no longer self-contained, and rots when the API changes. Archetype must choose, per artifact: **frozen and portable, or live and dependent.** See [[Implications for Archetype]].

## See Also
- [[Single-File HTML Apps]] · [[Personal Software]] · [[The Case Against HTML]]
- [[product-engineering/Andrej Karpathy]] · [[product-engineering/Specs Are the New Code]]
