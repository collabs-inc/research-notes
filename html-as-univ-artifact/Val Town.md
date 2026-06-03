# Val Town

A platform where you chat with an LLM (Townie) to generate deployed full-stack "vals" — including HTTP endpoints that serve HTML — hosted instantly at a URL. Represents the *instant-deploy* pole of [[The Artifact Landscape]].

- **Townie** (the AI codegen bot) emerged in 2024, powered by Claude 3.5 Sonnet.

## How It Relates to HTML-as-Artifact

Townie "creates deployed apps with a backend and database in seconds" as vals; an HTTP val's endpoint is reachable immediately at a URL. The deployed template is built around a client-side React template demarcating frontend vs. backend, with persistence via blob or SQLite. The artifact here is a **hosted HTTP endpoint**, not a static single file — the difference from [[Single-File HTML Apps]] is *where state and serving live*. Notably, Townie can inspect and edit its own system prompt.

## See Also
- [[The Artifact Landscape]] · [[Single-File HTML Apps]] · [[Simon Willison]]
- [[agentic-dev-envs/Bolt.new]]
