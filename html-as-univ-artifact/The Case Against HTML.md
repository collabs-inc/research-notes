# The Case Against HTML

The skeptic's rebuttal to [[HTML Is the New Markdown]]. The sharpest single piece is "The Unreasonable Ineffectiveness of HTML" (Kurtis Redux, 10 May 2026), arguing the switch "chases visual gloss at the expense of source readability, security, ecosystem compatibility, and reviewability."

## The Arguments

- **Readability:** *"HTML is only readable after rendering; its raw source is inherently hostile to human eyes."*
- **Security:** *"Running unvetted, AI-generated JS risks XSS or local data leaks. Reading text has now become running code."* See [[The Lethal Trifecta]].
- **Ecosystem:** [[Markdown]] is "the lingua franca of modern collaboration. Paste it into GitHub, GitLab, Notion, or Slack and it renders natively."
- **Reviewability / diffing:** "HTML diffs are noisy and harder to review than Markdown" — a wall of attribute and closing-tag changes that hide the substance. This is the killer for versioned, enterprise, compliance workflows.
- **Token cost:** clean HTML is ~2–3× Markdown's tokens; real-world HTML with CSS/JS can balloon to 8–10×. Million-token windows neutralize this for *output* but not for *ingestion*.
- **Attention dilution:** "spewing tons of redundant HTML tokens dilutes the model's attention" in long outputs.
- **Agent-to-agent:** for machine processing and chained-agent handoffs, Markdown "is cheaper, more accurately parsed, and easier to version."

## Accessibility

A structural weakness: LLM-generated HTML routinely omits ARIA, semantic landmarks, and labeled controls. One study found only **34% of AI-generated sortable tables properly announced sort states** to screen readers. Declarative protocols like [[A2UI]] sidestep this by rendering through the client's vetted native components.

## The Reconciliation

The emerging consensus: **match the format to the artifact's lifecycle.** [[Markdown]] for edited/versioned/agent-chained content; HTML for human-facing finished deliverables — and even then, a proposed compromise separates an HTML *template* (one file) from a JSON *data* file to keep diffs clean. See [[Format Alternatives]] and [[Implications for Archetype]].

## See Also
- [[HTML Is the New Markdown]] · [[Markdown]] · [[The Lethal Trifecta]]
- [[A2UI]] · [[Format Alternatives]]
