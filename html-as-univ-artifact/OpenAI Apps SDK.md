# OpenAI Apps SDK

OpenAI's framework for third-party apps that run *inside ChatGPT* as iframe-embedded HTML/JS components — built on [[agentic-dev-envs/Model Context Protocol (MCP)|MCP]], announced at DevDay (6 Oct 2025) in preview. Early partners: Spotify, Zillow, Canva, Booking.com.

## How HTML Is the Artifact

- Widgets are **"self-contained React components bundled as standalone HTML files,"** rendered in an **iframe** (desktop and mobile), communicating with ChatGPT via a `window.openai` bridge and receiving `toolInput`/`toolOutput`.
- Display modes: inline cards (default), fullscreen, picture-in-picture. State splits into UI-only (`setWidgetState`) and model-visible (`ui/update-model-context`).
- OpenAI now steers developers to the [[MCP Apps]] bridge by default, treating `window.openai` as a ChatGPT-specific extension layer.

## Why It Matters

The Apps SDK is the consumer-scale proof of HTML-in-iframe artifacts, and its convergence with Anthropic on the [[MCP Apps]] standard ("build your UI once and run it in ChatGPT and other MCP Apps hosts") is the strongest sign the artifact format is settling on HTML. It also illustrates [[React and Generative UI|React-as-source, HTML-as-artifact]].

## See Also
- [[MCP Apps]] · [[MCP-UI]] · [[ChatGPT Canvas]] · [[React and Generative UI]]
- [[The Artifact Format Standards Split]]
