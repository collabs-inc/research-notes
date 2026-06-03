# The Generative Web

The genre of experiments where an LLM produces web pages **on the fly** — the "infinite" or "hallucinated" web. Collectively, the strongest demonstration that the web page is a natural unit of LLM output.

## The Projects

- **[[websim]]** (Apr 2024) — type any URL, get a generated interactive page; the canonical example.
- **EndlessWiki** (Sean Goedecke, Sept 2025) — an infinite AI wiki: request any slug; if the page doesn't exist, an LLM (Kimi K2 via Groq) writes it, caches it to a database, and serves it; links generate further pages forever.
- **Wiki of Babel** (Simon Marache-Francisco, Oct 2024) — an infinite Wikipedia where each title generates an article, seeded with neighbor-page context to stay internally consistent.
- **Halupedia / "infinite Wikipedia" clones** — a now-commodity genre. Halupedia (covered by Fast Company) is "the only wiki where AI hallucinations are the entire point."

## Two Mechanics

- **Generate-on-first-visit + persist:** EndlessWiki and Wiki of Babel lazily generate and cache an HTML graph — the LLM as a browsable knowledge surface.
- **Coherence via context:** Wiki of Babel's trick (feed neighbor pages into the prompt) shows how a generated HTML graph stays internally consistent.

## The Cautionary Tale

Unbounded generative-web without curation degrades into slop — the Halupedia "cesspool" story (Fast Company) is a useful warning. It argues for the *curated, persistent, human-in-the-loop artifact* model ([[Television (Telepath)]], Archetype) over pure infinite generation. See [[Implications for Archetype]].

## See Also
- [[websim]] · [[Television (Telepath)]] · [[The Disposable Artifact]]
- [[The Artifact Landscape]] · [[Implications for Archetype]]
