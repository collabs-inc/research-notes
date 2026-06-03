# Gemini Canvas and Generative UI

Google's two bets on HTML-as-artifact — a collaborative canvas, and a per-prompt generative interface.

## Gemini Canvas

Launched 18 Mar 2025: a side-panel workspace where Gemini generates and previews **React or HTML** in a code editor, with per-turn change review. Reached "AI Mode" for all US users in early 2026. (Whether the preview runs in a live sandbox vs. a static preview isn't stated in the launch materials.) The analog to [[Claude Artifacts]] and [[ChatGPT Canvas]].

## Generative UI / Dynamic View

The more radical bet (Nov 2025, powered by Gemini 3): Gemini "designs and codes a fully customized interactive response for each prompt" and **"outputs HTML/CSS/JS to the user's browser,"** streamed in chunks and re-rendered live. The stated rationale: give users "dynamic interfaces tailored to their needs, rather than having to select from an existing catalog of applications." Here the HTML artifact is *ephemeral* — regenerated each interaction, not saved (the same bet as [[Imagine with Claude]]).

This is backed by Google's own research showing LLM-generated HTML beats Markdown in human preference (see [[Generative UI]]) — which sits in tension with Google's *product* protocol, [[A2UI]], which argues *against* shipping HTML.

## See Also
- [[Generative UI]] · [[A2UI]] · [[Imagine with Claude]]
- [[Claude Artifacts]] · [[ChatGPT Canvas]] · [[The Artifact Format Standards Split]]
