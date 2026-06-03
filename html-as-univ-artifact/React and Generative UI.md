# React and Generative UI

Component output: the LLM emits framework components rendered as live UI. The richest interactivity, but it needs a build step, a runtime, and a trusted component contract.

## The Approaches

- **Vercel AI SDK generative UI:** `streamUI` streams React Server Components alongside model generations; the model picks which component (chart, weather card, flight widget) to render from a provided kit. (Note: AI SDK RSC development is paused.)
- **LangChain/LangGraph generative UI:** `LoadExternalComponent` fetches a component's JS/CSS and renders it in a shadow DOM for style isolation.

## Weaknesses vs HTML

- **Build/runtime required** — not "open in a browser and it just works."
- **Security:** rendering untrusted LLM content in React often routes through `dangerouslySetInnerHTML`, which must be sanitized (DOMPurify). A critical **unauthenticated RCE in React Server Components** was disclosed Dec 2025 (unsafe deserialization of Flight payloads) — a reminder that the richer runtime is also more attack surface.

## React Compiles *to* HTML Anyway

The decisive point: [[OpenAI Apps SDK]] widgets *are* "self-contained React components bundled as standalone HTML files," and [[Claude Artifacts]] runs React inside the HTML iframe. React is the *source*; HTML is the *artifact*. This is the "framework project" pole of [[The Artifact Landscape]] — see [[v0]] for the LLM tool that lives there.

## See Also
- [[v0]] · [[Generative UI]] · [[Format Alternatives]]
- [[OpenAI Apps SDK]] · [[The Artifact Landscape]]
