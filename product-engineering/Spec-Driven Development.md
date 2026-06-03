# Spec-Driven Development

Make the *specification* — not the code — the durable, versioned, "executable" source of truth, and have AI agents implement against it through structured phases. The production-grade counter-movement to [[Vibe Coding]].

## The Canonical 2025 Artifacts

- **GitHub Spec Kit** — open-sourced Sept 2025 (MIT), by Den Delimarsky. A four-phase loop: **Specify → Plan → Tasks → Implement.** GitHub frames specs as *"living, executable artifacts that evolve with the project."* Its pitch against vibe coding: the "looks right but doesn't quite work" approach "is great for quick prototypes, but less reliable when building serious, mission-critical applications." Works with 30+ agents.
- **AWS Kiro** — agentic IDE (public preview July 2025, GA late 2025). Generates user stories + acceptance criteria → a technical design doc → an implementation task list *before* coding. Demand exceeded provisioned infrastructure in week one. Positioned explicitly as "beyond vibe coding."

## The Thesis: "Specs Are the New Code"

See [[Specs Are the New Code]] for Sean Grove (OpenAI)'s argument that "specifications, not prompts or code, are becoming the fundamental unit of programming." The connective idea: as code becomes a *compiled artifact* of a precise English spec, the durable source of truth migrates upward — toward the document that encodes intent. This is the same move as [[Working Backwards|Amazon's PR-FAQ]] and the [[Evals as the New PRD|eval-as-spec]].

## The Critique

Detractors call SDD a "repackaging of established SWE practices" or "a return to waterfall." The fair reading: it re-imposes a stable, testable artifact on top of cheap, non-deterministic generation — which is exactly what production work needs.

## See Also
- [[Specs Are the New Code]] · [[Vibe Coding]] · [[Augmented Coding]]
- [[Working Backwards]] · [[The AI-Native SDLC]]
