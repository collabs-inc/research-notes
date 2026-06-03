---
tags: [concept, implications]
created: 2026-06-03
---

# Implications for Archetype

What HTML-as-artifact means for Archetype, whose output is meant to be "a living product vision — structured enough for coding agents to consume, but rich enough to encode the *why*." The thesis is directly relevant, but it resolves into design tensions, not a single answer.

## Where HTML Helps

- **It's the rare format that is model-fluent, universally runnable, and human-legible at once** (see [[Why LLMs Are Fluent in HTML]], [[The Browser as Universal Runtime]]). For a product-thinking tool, a rendered, interactive vision artifact "gets read" far more than a Markdown wall of text ([[HTML Is the New Markdown]]).
- **A self-contained HTML file is the strongest candidate for a *durable, portable* vision artifact** — emailable, archivable, dependency-free ([[Single-File HTML Apps]]).
- **If the artifact also runs, the browser hands you a hardened sandbox for free** — an interactive prototype, not a static doc, with no containers ([[Sandboxing LLM-Generated HTML]]).
- **The cultural moment is aligned** — small, personal, artifact-shaped software made by people who decide what to build ([[Personal Software]]).

## The Tensions to Resolve

1. **Frozen vs. live.** A static single-file artifact is durable; one that phones home to a model API is intelligent but rots when the API changes ([[The Disposable Artifact]]). Decide per artifact.
2. **Human-rich vs. agent-clean.** "Rich enough to encode the why" (HTML, for humans) and "structured enough for coding agents to consume" may want *different representations*. The McGill critique and WebMCP argue HTML is a weak agent-ingestion surface ([[Websites as the Agent Interface]]). The likely answer: keep a structured spec (the durable source) and *render* HTML from it — [[product-engineering/Specs Are the New Code|specs are the new code]].
3. **The standards split is unsettled.** Ship HTML-in-iframe ([[MCP Apps]]) or declarative JSON ([[A2UI]])? A format-agnostic artifact layer hedges ([[The Artifact Format Standards Split]]).
4. **Security is non-negotiable.** A vision artifact ingests private context, so it's a textbook [[The Lethal Trifecta|lethal-trifecta]] case — ship with a deny-by-default CSP.

## The Closest Precedent

[[Television (Telepath)]] is the nearest external bet: an agent environment where persistent, organizable artifacts — not chat — are the unit of work. Archetype's distinction is the *product-thinking* domain on top of that artifact model. The strongest framing borrowed from this research: the artifact is a *view of the durable idea* ([[The Disposable Artifact]]), and "chat is an essentially limited interaction mode" ([[Personal Software]]) — both argue for a manipulable artifact over a transcript.

## See Also
- [[HTML as the Universal LLM Artifact]] · [[The Disposable Artifact]] · [[The Artifact Format Standards Split]]
- [[Television (Telepath)]] · [[The Lethal Trifecta]] · [[product-engineering/Specs Are the New Code]]
