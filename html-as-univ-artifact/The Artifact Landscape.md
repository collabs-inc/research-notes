---
tags: [market]
created: 2026-06-03
---

# The Artifact Landscape

A map of how LLM-output formats are settling. The underlying medium is largely decided — HTML/JS won as the human-facing target — but the *packaging* and *hosting* still split into distinct poles.

## The Two-Axis Grid

- **Text ↔ Interactive:** [[Markdown]] owns cheap, diffable, model-native *text*; HTML owns *interactive* output.
- **Code ↔ Data:** [[JSON and Structured Outputs|JSON]] owns machine-parseable *data*; HTML owns the human terminus. [[React and Generative UI|React]], MDX, PDF, and [[SVG and Mermaid|SVG]] are mostly *source or export* formats that compile *into* or *out of* HTML.

## The Packaging Poles

| Pole | What the artifact is | Examples |
|---|---|---|
| **Single self-contained file** | One `.html` with inline CSS/JS | [[Claude Artifacts]] (web), [[tldraw Make Real]], [[websim]], [[Simon Willison]]'s tools |
| **Framework project** | React + build ecosystem | [[v0]] |
| **Deployed app** | Hosted, multi-file, has a backend | [[agentic-dev-envs/Bolt.new|Bolt]], [[agentic-dev-envs/Lovable|Lovable]], [[agentic-dev-envs/Replit Agent|Replit]], [[Val Town]] |
| **Ephemeral stream** | Regenerated per prompt, not saved | [[Imagine with Claude]], [[Gemini Canvas and Generative UI|Gemini Generative UI]], [[The Generative Web]] |
| **Persistent agent artifact** | Pinned, organized, reused | [[Television (Telepath)]] |

## Vendor Convergence

The sandboxed iframe is the near-universal runtime — [[Claude Artifacts]], [[ChatGPT Canvas]], [[OpenAI Apps SDK]], [[websim]], and [[tldraw Make Real]] all render generated HTML/JS in an iframe governed by CSP. The biggest convergence is the cross-vendor [[MCP Apps]] standard (Anthropic + OpenAI, Jan 2026), which chose HTML-in-iframe explicitly for "universal browser support." The lone dissent is Google's [[A2UI]], betting on declarative JSON instead. See [[The Artifact Format Standards Split]].

## See Also
- [[HTML as the Universal LLM Artifact]] · [[Format Alternatives]] · [[The Artifact Format Standards Split]]
- [[Generative UI]] · [[Television (Telepath)]]
