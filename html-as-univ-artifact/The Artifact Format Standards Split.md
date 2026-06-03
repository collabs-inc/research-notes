---
tags: [concept, market]
created: 2026-06-03
---

# The Artifact Format Standards Split

The central architectural fault line in how agents return interactive UI — and the clearest test of the HTML-as-universal-artifact thesis.

## The Two Camps

| | **Ship HTML, sandbox it** | **Ship JSON, render natively** |
|---|---|---|
| Standards | [[MCP Apps]], [[MCP-UI]], [[OpenAI Apps SDK]] | [[A2UI]] (Google) |
| Backers | Anthropic + OpenAI (joint) | Google |
| Artifact | HTML/JS in a sandboxed iframe | Declarative JSON → trusted components |
| Security model | Sandbox + CSP contains the code | No executable code ever ships |
| Bet | **Universality** — runs in any browser | **Safety + accessibility** — vetted components |

[[AG-UI]] is the transport beneath both — it carries whichever format the host chooses.

## What's at Stake

The HTML camp's argument is universality and zero-build: when Anthropic and OpenAI co-authored [[MCP Apps]] (Jan 2026), they chose HTML-in-iframe explicitly for "universal browser support" and a "well-understood security model." The JSON camp's argument is that shipping executable markup is "heavy" and unsafe, and that accessibility belongs in vetted native components, not LLM-authored HTML ([[The Case Against HTML]]).

## The Tell

Even the dissenter is split internally: Google's *research* arm shows LLM-generated **HTML** beating Markdown in human preference ([[Generative UI]]), while Google's *product* protocol ([[A2UI]]) argues against shipping HTML. The medium (a generated interface per intent) is settled; the *packaging* is the live fight.

## Implication for Archetype

Whichever standard an agent host adopts dictates whether Archetype's interactive artifacts ship as HTML or as declarative JSON. A format-agnostic artifact layer — author once, render as HTML *or* declarative components — hedges the bet. See [[Implications for Archetype]].

## See Also
- [[MCP Apps]] · [[A2UI]] · [[Generative UI]] · [[The Artifact Landscape]]
- [[Implications for Archetype]]
