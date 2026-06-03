# A2UI

Google's declarative-JSON generative-UI spec — the explicit *counter-bet* to HTML-as-artifact. Agents emit UI *intent*, not code, and the client renders it with trusted native components.

- **Announced** 15 Dec 2025 by the Google A2UI team (public preview v0.8, then a framework-agnostic v0.9). Built with input from CopilotKit/[[AG-UI]], Gemini Enterprise, and the Flutter GenUI SDK.

## The Core Claim

> "A2UI is a *declarative* data format, not executable code." Security comes from **component-catalog whitelisting**: the client keeps "a catalog of trusted, pre-approved UI components (e.g. `Card`, `Button`, `TextField`), and the agent can only request to render components from that catalog."

And the direct framing against HTML: rendering UI from an untrusted source historically "meant sending HTML or JavaScript and sandboxing it inside iframes, which is heavy, visually disjointed, and introduces complexity around security boundaries. A2UI addresses this by passing UI layouts as messages, not as executable code." It's pitched as "safe like data, but expressive like code," and the same JSON renders across web, mobile, and desktop.

## Why It Matters

A2UI is the one serious dissent from the HTML-in-iframe consensus ([[MCP Apps]], [[OpenAI Apps SDK]], [[MCP-UI]]). It eliminates the [[The Lethal Trifecta|execution risk class]] and the [[The Case Against HTML|accessibility problem]] by never shipping executable markup — at the cost of HTML's universality (it needs a host with the catalog). Notably, Google's own *research* arm ships LLM-generated HTML that beats Markdown ([[Generative UI]]), while its *product* protocol argues against HTML — two camps inside one company. This is the central architectural fault line: see [[The Artifact Format Standards Split]].

## See Also
- [[The Artifact Format Standards Split]] · [[MCP Apps]] · [[Generative UI]]
- [[The Case Against HTML]] · [[AG-UI]]
