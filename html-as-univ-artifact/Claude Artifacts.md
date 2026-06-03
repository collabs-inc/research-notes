# Claude Artifacts

Anthropic's feature that mainstreamed the thesis: Claude renders generated code/docs/apps in a side panel, with HTML/CSS/JS and React running live in a **sandboxed iframe.** The canonical example of "LLM generates a self-contained app, rendered safely."

- **Launched** 20 June 2024 (with Claude 3.5 Sonnet); generally available 27 Aug 2024. Anthropic later reported users have created **over half a billion artifacts** (company-stated; treat as approximate).

## How HTML Is the Artifact

A web artifact is a single-page HTML/CSS/JS document (or a React component) rendered live. The **sandbox model** (per [[Simon Willison]]): artifacts run in "a strictly controlled browser sandbox — access to features like `localStorage` or external APIs via `fetch()` is restricted by CSP headers and the `<iframe sandbox>` mechanism." A CDN allowlist (Chart.js, D3, Tailwind, Google Fonts) is permitted; arbitrary external fetches are blocked. Published artifacts get shareable URLs that Anthropic hosts directly. See [[Sandboxing LLM-Generated HTML]].

## Static → AI-Powered

The June 2025 update let an artifact's JS call **`window.claude.complete()`** — running prompts against Claude from inside the sandboxed page, with the key innovation that **the viewer is billed** (they sign into their own Anthropic account). This turned a frozen HTML artifact into a shareable AI app — at the cost of self-containment (see the tension in [[The Disposable Artifact]]).

## Why It Matters

Artifacts is the proof at scale that a self-contained HTML file is a viable mass-market LLM output, and the reference implementation of the sandbox pattern later standardized by [[MCP Apps]].

## See Also
- [[Single-File HTML Apps]] · [[Sandboxing LLM-Generated HTML]] · [[Imagine with Claude]]
- [[ChatGPT Canvas]] · [[The Artifact Landscape]]
