# Websites as the Agent Interface

The inverse direction of the thesis: not LLMs *producing* HTML for humans, but agents *consuming* HTML to act on the web — and the open question of whether human-designed HTML is the right substrate for them.

## The Critique

"Build the web for agents, not agents for the web" (Lù, Kamath, Mosbach, Reddy; McGill/Mila, June 2025) argues that human-designed HTML interfaces are a poor fit for agents — they struggle with "massive DOM trees" and screenshots — and proposes an agent-optimized interaction paradigm. This is the direct challenge to "HTML is the universal substrate": great for humans-and-rendering, weaker as a clean *agent-ingestion* surface.

## The Standards Response

- **WebMCP** (Google + Microsoft, W3C Web ML Community Group; Chrome early preview Feb 2026) lets websites expose **structured tools** to agents — moving away from agents scraping HTML toward sites publishing agent-facing APIs. It offers a declarative (HTML-attribute) and an imperative (JS) surface, running client-side in the tab.
- **Agentic browsers** (Perplexity Comet, ChatGPT Atlas, Gemini-in-Chrome) are agents acting over live human HTML at scale; agentic web traffic reportedly grew sharply through 2025.

## Why It Matters

It tempers the thesis: HTML is the clear winner for the *human terminus* of LLM output, but for the *agent terminus* the field is actively building structured alternatives (WebMCP, [[A2UI]]). For Archetype, this is the reminder that an artifact "rich enough for humans" is not automatically "structured enough for coding agents to consume" — the two may want different representations of the same thing. See [[Implications for Archetype]].

## See Also
- [[Implications for Archetype]] · [[A2UI]] · [[The Artifact Format Standards Split]]
- [[agentic-dev-envs/Model Context Protocol (MCP)]]
