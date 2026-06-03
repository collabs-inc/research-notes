# Format Alternatives

A hub comparing the formats HTML competes with as "the LLM artifact." Most are *source or export* formats that compile into or out of HTML rather than rivaling it as the final human-facing artifact.

## The Contenders

| Format | Owns | Weakness vs HTML |
|---|---|---|
| [[Markdown]] | Cheap, diffable, model-native text | Flat, non-interactive |
| [[JSON and Structured Outputs\|JSON]] | Machine-parseable data | Not human-renderable on its own |
| [[React and Generative UI\|React / JSX]] | Rich interactivity | Needs a build step and runtime |
| [[SVG and Mermaid\|SVG]] | Vector graphics described as text | Models can't reliably "draw"; lives inside HTML |
| Mermaid | Diagrams-as-code | Needs a renderer (bundles into HTML) |
| MDX | Authoring docs with components | Unsafe at runtime; stripped to Markdown for LLMs |
| PDF | Fixed print fidelity | Models don't emit it; an export *of* HTML |
| Canvas (`<canvas>`) | Dense raster graphics | No DOM, no semantics, no accessibility |

## The Pattern

Almost everything funnels through HTML. PDF and MDX get *converted to* HTML (or Markdown) for consumption; React, SVG, Canvas, and Mermaid all *render inside* an HTML document. The two genuine rivals as a final artifact are [[Markdown]] (for text) and the declarative-JSON UI protocols ([[A2UI]]) — which deliberately avoid shipping HTML at all. See [[The Case Against HTML]] and [[The Artifact Format Standards Split]].

## See Also
- [[The Artifact Landscape]] · [[Markdown]] · [[JSON and Structured Outputs]]
- [[React and Generative UI]] · [[SVG and Mermaid]]
