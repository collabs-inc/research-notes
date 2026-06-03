# HTML Is the New Markdown

The specific 2026 articulation that crystallized the thesis, from **[[Thariq Shihipar]]** (an Anthropic engineer on Claude Code): finished LLM deliverables should be **HTML, not [[Markdown]]**.

## Thariq's Thesis ("The Unreasonable Effectiveness of HTML")

Posted to X on **8 May 2026** (companion site `thariqs.github.io/html-effectiveness` with ~20 self-contained example files); reach reported in the millions of views (figures vary by source — treat as approximate). His argument, in five parts:

1. **Information density** — HTML embeds tables, SVG, CSS, JS, and images in one self-contained file.
2. **Document length** — "nobody really reads a Markdown file longer than a hundred lines"; HTML survives length via tabs and collapsible sections.
3. **Sharing** — HTML uploads to a CDN as a direct link and renders natively in any browser; Markdown doesn't.
4. **Two-way interaction** — sliders and buttons turn a document into an exploratory tool that feeds results back to Claude.
5. **The token objection has evaporated** — HTML costs ~2–4× more tokens, but with million-token context windows that overhead is now negligible.

> "Markdown has become the dominant file format used by agents to communicate with us… but as agents have become more and more powerful, I have felt that markdown has become a restricting format." — Thariq Shihipar

He concedes Markdown still wins for READMEs, Slack/Discord snippets, RAG-ingested docs, and anything needing heavy git history.

## Willison's (Qualified) Conversion

[[Simon Willison]] responded the same day, reconsidering a three-year Markdown habit *for output*: he'd defaulted to Markdown "since the GPT-4 days, when the 8,192 token limit meant that Markdown's token-efficiency over HTML was extremely worthwhile" — a constraint that million-token windows removed. His prompt recipe: *"Output HTML, neatly styled and using capabilities of HTML and CSS and JavaScript to make the explanation rich and interactive and as clear as possible."*

## The Rebuttal

Two days later, "The Unreasonable Ineffectiveness of HTML" (Kurtis Redux) argued the shift "chases visual gloss at the expense of source readability, security, and reviewability." See [[The Case Against HTML]].

## See Also
- [[Thariq Shihipar]] · [[Simon Willison]] · [[Markdown]]
- [[HTML as the Universal LLM Artifact]] · [[The Case Against HTML]]
