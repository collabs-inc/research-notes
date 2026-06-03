# Single-File HTML Apps

The load-bearing pattern of the whole thesis: one `.html` file with inline CSS and JS, no build step, no bundler, no framework — small enough that any model can read, understand, and rewrite it. The most articulated philosophy comes from [[Simon Willison]], who has vibe-coded **150+ single-file HTML tools** (`tools.simonwillison.net`).

## The Rules (per Willison)

- **A single file** — "inline JavaScript and CSS in a single HTML file means the least hassle in hosting or distributing them."
- **No build step** — "Avoid React, or anything with a build step… JSX requires a build step, which makes everything massively less convenient." Load any dependencies from a CDN.
- **Keep them small** — "A few hundred lines means the maintainability of the code doesn't matter too much: any good LLM can read them and understand what they're doing." Small enough to regenerate from scratch in minutes.
- **State without a backend** — "you can store a lot of state directly in the URL," or in `localStorage`.
- **Host anywhere** — GitHub Pages, a gist preview, or inline as a `data:` URL.

## Why It's the Ideal LLM Unit

A single-file HTML doc extracts cleanly from a chat response, copy-pastes into a repo, hosts trivially, renders instantly, and **round-trips back into any model for editing**. It is the format with the least friction at every step from generation to use. Independent practitioners reached the same conclusion (e.g. Taivo Pungas, "Creating single-file apps with LLMs," reporting "20× faster" than traditional coding, crediting Willison).

This is the *single-file pole* of [[The Artifact Landscape]] — the opposite end from framework projects ([[v0]]) and deployed apps ([[agentic-dev-envs/Bolt.new|Bolt]], [[agentic-dev-envs/Lovable|Lovable]]).

## See Also
- [[Simon Willison]] · [[Claude Artifacts]] · [[tldraw Make Real]]
- [[HTML as the Universal LLM Artifact]] · [[The Disposable Artifact]] · [[The Artifact Landscape]]
