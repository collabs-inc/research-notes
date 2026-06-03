# websim

The "hallucinated internet": type any (real or fictitious) URL or prompt and an LLM generates a full interactive webpage on the fly; clicking the generated links recursively hallucinates more pages — an endless fake web. The purest demonstration that **an LLM can emit a complete, navigable web page as its native output.**

- **Creators:** Rob Haisfield and Sean Lee. (Secondary summaries that name a "Sarah Chen" are wrong.)
- **Launched** ~1 April 2024 (built for the Mistral AI hackathon). Funding figures circulating online are **unverified.**

## How It Works

A prompt or typed URL → **Claude generates HTML/CSS/JS dynamically**, rendered in real time inside a simulated browser window. Originally Claude 3 Opus, later Claude 3.5 Sonnet. Links inside a generated page are themselves clickable and generate further pages on demand. The main social feature is **remixing (forking)**, and you can **download a creation as a single static `.html` file**.

## Why It Matters

websim reframes LLM output as *browsing* rather than *reading* — the artifact *is* a web page. It's the art-project ancestor of the product-shaped persistent-artifact bets ([[Television (Telepath)]]), and a vivid argument for HTML as the natural unit because it's instantly renderable and navigable. See [[The Generative Web]] for the broader genre.

## See Also
- [[The Generative Web]] · [[tldraw Make Real]] · [[Single-File HTML Apps]]
- [[Television (Telepath)]] · [[The Artifact Landscape]]
