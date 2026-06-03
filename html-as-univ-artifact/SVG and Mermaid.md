# SVG and Mermaid

Two text-based graphics formats LLMs can emit directly — with very different reliability.

## SVG: models can't reliably "draw"

SVG is a text-described vector format, so an LLM can output it without an image generator. But models are weak at it as a *drawing* medium. [[Simon Willison]]'s recurring informal benchmark — *"generate an SVG of a pelican riding a bicycle"* — and Tom Gally's "LLM SVG Generation Benchmark" (Nov 2025) show frontier models producing crude or mangled results; the academic SVGenius study finds "all models degrade with increasing complexity." SVG works well for code-described geometry (charts, simple diagrams), poorly for representational drawing.

Crucially, SVG is a *primitive inside* HTML: Willison cites HTML's ability to "drop in SVG diagrams" as a reason it wins. Standalone SVG is a weak general artifact; embedded in HTML it's a strength.

## Mermaid: diagrams-as-code that works

Mermaid is a small text DSL for flowcharts, sequence, and UML diagrams. It's "one of the few diagram formats AI assistants generate well because the syntax is text-based, the spec is small, and the training data is full of GitHub README examples" — the model writes plain text and a deterministic renderer turns it into the diagram, so there are "no SVG paths to hallucinate." It usually "renders on the first try," and it's diff-friendly (it's text). It needs a Mermaid renderer — which a self-contained HTML file can bundle via CDN.

## The Lesson

Mermaid offloads the "draw" problem to a renderer — the inverse of LLM-drawn SVG. For Archetype: prefer Mermaid (or code-generated SVG) over asking a model to free-hand SVG. See [[Format Alternatives]].

## See Also
- [[Format Alternatives]] · [[Simon Willison]] · [[React and Generative UI]]
- [[HTML as the Universal LLM Artifact]]
