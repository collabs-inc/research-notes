---
tags: [concept]
created: 2026-06-03
---

# Generative UI

The broader idea behind the artifact thesis: an LLM generates a custom *interface* per prompt, rather than returning text or selecting from a fixed catalog of apps. HTML is the most common output target for it.

## The Research Backing

Google Research, "Generative UI: LLMs are Effective UI Generators" (Yaniv Leviathan et al., Nov 2025): an LLM "designs and codes a fully customized interactive response for each prompt," **outputting self-contained HTML/CSS/JS to the browser.** The human-preference result is striking — human-expert sites ranked highest, "followed closely by the results from our generative UI implementation, with a substantial gap from all other output methods" (raw text / standard Markdown). LLM-generated HTML beats a wall of text.

## The Product Forms

- **Per-prompt / ephemeral:** Google's Gemini "Dynamic View" (see [[Gemini Canvas and Generative UI]]) and Anthropic's [[Imagine with Claude]] generate UI on the fly with no prewritten code — HTML regenerated each interaction.
- **Persistent artifact:** [[Claude Artifacts]], [[v0]] — the generated UI is kept and reused.
- **In-chat embedded:** [[OpenAI Apps SDK]], [[MCP-UI]] — UI rendered inline in the conversation.

## The Format Question

Generative UI is where the [[The Artifact Format Standards Split|standards split]] lives: does the model ship **HTML to sandbox** ([[MCP Apps]], OpenAI) or **declarative JSON to render with trusted components** ([[A2UI]])? Same goal — a custom interface per intent — opposite bets on the artifact format.

## See Also
- [[The Artifact Format Standards Split]] · [[A2UI]] · [[Gemini Canvas and Generative UI]]
- [[Imagine with Claude]] · [[The Artifact Landscape]]
