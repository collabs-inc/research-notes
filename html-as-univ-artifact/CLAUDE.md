# Research Vault: HTML as the Universal LLM Artifact

This is an Obsidian-style wiki of ~37 interlinked markdown notes on the idea that **a single self-contained HTML file is the ideal output format for LLM-generated artifacts** — the lowest-friction interface between a model and a human. It covers the thesis and its proponents, the format alternatives, the interactive-UI standards racing to define agent UI, the tools that embody the idea, the security model, and the implications for Archetype. Current as of June 2026.

## Where to Start

- **[[HTML as LLM Artifact MOC]]** is the map of content. Start here for any question.
- **[[HTML as the Universal LLM Artifact]]** for the central thesis.
- **[[HTML Is the New Markdown]]** for the 2026 articulation that crystallized it.
- **[[The Artifact Format Standards Split]]** for the central architectural fault line (HTML-in-iframe vs declarative JSON).
- Notes use `[[wiki-links]]`. Cross-vault links use the folder path (e.g. `[[product-engineering/Specs Are the New Code]]`).

## Structure

- **Concept notes** (e.g., `HTML as the Universal LLM Artifact.md`, `The Disposable Artifact.md`) explain one idea each.
- **Format notes** (e.g., `Markdown.md`, `React and Generative UI.md`) cover one alternative format.
- **Standard/protocol notes** (e.g., `MCP Apps.md`, `A2UI.md`) cover one interactive-UI standard.
- **Tool notes** (e.g., `Claude Artifacts.md`, `websim.md`) profile one product.
- **Person notes** (`Simon Willison.md`, `Thariq Shihipar.md`) profile one proponent.

## A Note on Sourcing

This is a fast-moving 2024–2026 topic. Well-verified facts are stated plainly; secondary, contested, or company-reported figures are hedged inline. Two specific cautions baked into the notes: **television.run is Telepath's persistent-artifact agent GUI, not a generative-TV project** (a common misconception), and circulating "$20M / USV / Lightspeed" Telepath funding figures are a confabulation — only the verified investor list is used. websim's founders are Rob Haisfield and Sean Lee (not "Sarah Chen").

## If You're Looking For…

| Question | Start at |
|----------|----------|
| What is the thesis? | `HTML as the Universal LLM Artifact.md` |
| The "HTML is the new Markdown" argument? | `HTML Is the New Markdown.md` |
| What HTML competes with | `Format Alternatives.md` |
| The standards fight | `The Artifact Format Standards Split.md` |
| What is television.run? | `Television (Telepath).md` |
| Security / sandboxing | `Sandboxing LLM-Generated HTML.md`, `The Lethal Trifecta.md` |
| What it means for Archetype | `Implications for Archetype.md` |
