# JSON and Structured Outputs

Schema-constrained structured data — the *data* artifact. Perfectly parseable by machines, but not a human-renderable artifact on its own.

## What It Is

Structured Outputs force a model's response to conform to a JSON Schema via constrained/grammar-based decoding. Its value is **parseability** — downstream validation, tool calling, and evaluation — not human rendering. (Distinct from function/tool calling, where the model emits structured params to invoke an external tool.)

## Vs HTML

JSON is the *input/transport* layer, not the artifact a person looks at. Notably, HTML's interactive-UI competitors increasingly use JSON *under* the UI rather than shipping markup: [[A2UI]] sends declarative JSON describing a UI; [[AG-UI]] streams a JSON event sequence. So JSON isn't really competing with HTML for the human terminus — it's the substrate beneath both HTML-in-iframe and declarative-UI approaches. JSON is for when a *program* consumes the output; HTML is for when a *person* does.

## See Also
- [[Format Alternatives]] · [[A2UI]] · [[AG-UI]] · [[Generative UI]]
- [[The Artifact Format Standards Split]]
