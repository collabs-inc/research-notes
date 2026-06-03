# tldraw Make Real

The seminal "sketch → single HTML file" demo: draw a low-fidelity UI on tldraw's canvas, click a button, and a vision model returns working HTML/CSS/JS rendered back on the canvas.

- **Launched** November 2023 (by Steve Ruiz / tldraw; the viral "Make It Real" / `draw-a-ui` demos). The repo hit 10k+ GitHub stars within ~2 weeks.

## How It Works

It generates a base64 PNG of the drawn components, passes it to a vision model (originally GPT-4 Vision) with instructions to produce "a single HTML file using Tailwind," and renders the resulting **working HTML/CSS/JavaScript** as an embedded result on the canvas. You can then draw annotations on top and regenerate.

## Why It Matters

Make Real established the pattern that a *spatial, visual* prompt (a sketch) compiles to a self-contained HTML artifact — a non-chat interface for generating UI. It's directly adjacent to a product-thinking environment (and to the spatial-canvas bets of [[websim]] and [[Television (Telepath)]]). The artifact is a [[Single-File HTML Apps|single HTML file]].

## See Also
- [[Single-File HTML Apps]] · [[websim]] · [[v0]] · [[The Generative Web]]
- [[The Artifact Landscape]]
