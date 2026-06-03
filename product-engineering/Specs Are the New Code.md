# Specs Are the New Code

Sean Grove (OpenAI)'s thesis, from his talk "The New Code" at the AI Engineer World's Fair (June 2025): *"specifications, not prompts or code, are becoming the fundamental unit of programming."*

## The Argument

- Code is only ~10–20% of a programmer's value; the other ~80–90% is "structured communication." Hence: *"The best coder will soon be the best communicator."*
- Today's workflow is backwards: developers prompt, then discard the prompt and version-control the output — *"like you shred the source and then very carefully version control the binary."* The spec is the real source; the code is the compiled artifact.
- His example: OpenAI's own **Model Spec** — a living Markdown document where each clause has a unique ID and example prompts that act as unit tests for model behavior.

## The Through-Line

This connects [[Working Backwards|Amazon's narrative memos]] (2004), [[Spec-Driven Development]] (Spec Kit, Kiro, 2025), and [[Evals as the New PRD|evals]] into one idea: a precise English document that forces clarity and now *compiles* — into code, docs, evals, or model behavior. The durable artifact moved from "the code" to "the spec." a16z's parallel framing: with coding agents, "code becomes the byproduct… more like a compiled artifact than a manually authored source."

## See Also
- [[Spec-Driven Development]] · [[Working Backwards]] · [[The AI-Native SDLC]]
- [[Taste as the Bottleneck]] — the spec encodes the judgment
