# MCP-UI

The community-built UI layer over the [[agentic-dev-envs/Model Context Protocol (MCP)|Model Context Protocol]] that let MCP tools return *interactive UI* — proving the "HTML in a sandboxed iframe" pattern before it became an official standard.

- **Creators:** Ido Salomon and Liad Yosef. Shopify published its implementation ("Breaking the text wall") on **5 Aug 2025**; adopters include Shopify, Postman, Hugging Face, ElevenLabs.
- **Built on** MCP's "embedded resources" spec.

## How It Works

Three delivery modes: (1) inline HTML in a sandboxed iframe (`srcDoc`), (2) a remote URL in a sandboxed iframe, (3) **Remote DOM** for direct client-side rendering. A `UIResource` uses a `ui://component/id` URI scheme with MIME types `text/html`, `text/uri-list`, or `application/vnd.mcp-ui.remote-dom`.

**Intent-based messaging** is the key safety idea: components don't mutate state directly — they "bubble up intents that the agent interprets" (`view_details`, `checkout`, `notify`), preserving agent control.

## Why It Matters

MCP-UI is the origin of the HTML-in-iframe artifact pattern for agent tools, and its creators co-authored the official successor, [[MCP Apps]]. It sits on the HTML side of [[The Artifact Format Standards Split]].

## See Also
- [[MCP Apps]] · [[OpenAI Apps SDK]] · [[The Artifact Format Standards Split]]
- [[agentic-dev-envs/Model Context Protocol (MCP)]]
