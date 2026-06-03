# MCP Apps

The official [[agentic-dev-envs/Model Context Protocol (MCP)|MCP]] extension (SEP-1865) standardizing interactive agent UI — and a strong cross-vendor vote for **HTML as the universal artifact.**

- **Timeline:** Proposed 21 Nov 2025; became the **first official MCP extension on 26 Jan 2026.** Optional, backward-compatible.
- **Authored jointly by Anthropic, OpenAI, and the [[MCP-UI]] creators** — consolidating MCP-UI and the [[OpenAI Apps SDK]] patterns into one standard. This is the first real cross-vendor artifact interop between the two largest labs.

## The Format Choice

> "Initially supports only **HTML rendered in sandboxed iframes**" — chosen explicitly for "universal browser support" and a "well-understood security model."

UI templates are pre-declared with `ui://` URIs (prefetchable and reviewable *before* the tool executes); components communicate with the host via MCP JSON-RPC over `postMessage`. Security layers: iframe sandboxing, HTML template pre-review, auditable JSON-RPC logging, and user-consent requirements.

Launch support spanned Claude (web/desktop), Goose, VS Code Insiders, and ChatGPT, with interest from JetBrains, AWS Kiro, Google Antigravity, and Microsoft.

## Why It Matters

When the two biggest model labs agreed on a UI standard, they chose **HTML-in-iframe** — the clearest external endorsement of the universality argument. The lone holdout is Google's [[A2UI]] (declarative JSON). See [[The Artifact Format Standards Split]].

## See Also
- [[MCP-UI]] · [[OpenAI Apps SDK]] · [[A2UI]] · [[The Artifact Format Standards Split]]
- [[Sandboxing LLM-Generated HTML]] · [[agentic-dev-envs/Model Context Protocol (MCP)]]
