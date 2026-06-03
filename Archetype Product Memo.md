# Archetype Product Memo

## What is Archetype?

Archetype is an Agentic Development Environment for product thinking. It's geared toward product-shaped work — developing vision, synthesizing user signal, exploring creative directions, making build decisions — rather than engineering-shaped work. Think Cursor or Warp, but for the person deciding *what* to build, not *how* to build it.

## The Opportunity

Y Combinator named "Cursor for Product Managers" as an explicit RFS category in Spring 2026 (authored by Andrew Miklas). The thesis: AI coding tools have solved how to build software, but figuring out *what* to build remains unsolved. No tool supports the full loop from customer signal to executable specification. See [[cursor-for-product-managers/YC RFS Spring 2026]] for the full text.

The market research confirms the gap is real:
- No incumbent or startup delivers the full loop today ([[cursor-for-product-managers/The Full Loop Gap]])
- Three YC companies that tried (Inari, Kraftful, Monterey AI) were all acquired before scaling ([[cursor-for-product-managers/Competitive Dynamics]])
- Incumbents are adding AI superficially — better triage, faster ticket writing — not rethinking the paradigm ([[cursor-for-product-managers/Incumbent AI Features]])
- Practitioners want help but are skeptical of current tools — 38 of 47 AI PM tools failed Aakash Gupta's $28K test ([[cursor-for-product-managers/Practitioner Sentiment]])

## How Archetype Is Different

### 1. An ADE, not a SaaS dashboard

Every competitor in this space is building a web app you log into — a dashboard for organizing feedback, writing PRDs, or managing tickets. Archetype is an environment that lives where the work happens, open all day, the way Cursor is open all day for engineers.

Product people are already adopting ADEs: a head of product at a seed-stage startup uses Warp with Claude Code because someone on her engineering team introduced her to it. The behavior exists — product work inside an ADE — but no ADE is designed for it. People are tolerating the mismatch because the form factor is right.

### 2. Vision and point of view, not feature aggregation

The YC RFS framing is analytical: data in, recommendations out. That's a better-instrumented suggestion box. But great products don't come from aggregating feature requests — they come from someone with a point of view about how the world should work, who uses customer signal to sharpen and validate that vision, not to generate it.

Every tool in this space optimizes for the analytical side. None support the creative, generative side of product work — developing an opinion, finding non-obvious connections, building conviction around a direction customers can't articulate yet.

Archetype supports the development and refinement of product visions, while staying grounded in user feedback and other important signals. It doesn't try to tell you what to build. It helps you think about what to build.

### 3. The product thinker's companion

Engineers have an entire ecosystem: IDEs, terminals, ADEs, Stack Overflow, GitHub, a culture of tool-sharing. Product people are comparatively isolated — often the only PM in a small org, or one of a handful. Their tools are either enterprise bloatware designed for big PM orgs (Jira, Productboard, Aha!) or generic docs apps they've jury-rigged.

Archetype's message: you don't have to think alone. Not a dashboard for reporting status. Not a ticket tracker. A thinking partner that understands product work — that can pull in customer signal, help you explore creative directions, stress-test your intuitions, and turn your vision into something a coding agent can build.

## Day-One Users

**Founders** at early-stage companies who are simultaneously the product manager, the engineer, and the visionary. Already in Cursor or Claude Code building the thing. Don't want a separate SaaS dashboard for "product management" — that's a big-company artifact. Need a place to develop product thinking that stays connected to what they're building and grounded in what they're hearing from users.

**PM/engineers** at seed-to-Series-A companies who straddle product thinking and technical implementation. Already comfortable in code-adjacent tools. Increasingly doing both with AI.

Go-to-market is likely bottom-up through engineering-adjacent product people, not top-down through PM orgs. Founders and technical PMs who are already in terminals, already using Claude Code, already vibe coding prototypes. Traditional PMs in Confluence and Jira are a later expansion.

## Native Capabilities

The environment would natively understand product concepts (user needs, market context, competitive positioning, design intent) the way Cursor understands code concepts (files, functions, types, dependencies).

Example integrations that signal the product orientation:
- **Granola** — synthesize signal from customer conversations and meetings
- **Are.na** — grab inspiration for creative, combinatorial ideation
- **Customer feedback channels** — Intercom, Zendesk, app reviews, support tickets
- **Usage analytics** — product usage data for grounding decisions in behavior
- **Coding agents** — bridge to Cursor, Claude Code, etc. when ready to build

The output isn't a PRD or a Jira ticket. It's a living product vision — structured enough for coding agents to consume, but rich enough to encode the *why* and the point of view, not just the *what*.

## Strategic Positioning

Archetype avoids the acquisition trap that killed Inari, Kraftful, and Monterey AI. Those companies built "better feedback analytics" and ended up as features inside Amplitude and Reforge. Archetype is a *working environment*, not a feature. You can't bolt an environment onto Productboard the way you can bolt a feedback widget onto Amplitude.

The Warp analogy holds: Warp went after engineers with a better terminal. Archetype goes after product-minded builders with a better environment for product thinking. Same form factor bet, different user, different primitives. Engineers outnumber product people, but product people decide what gets built — disproportionately high-leverage per user.

## Open Questions

- What's the smallest version that delivers value before the full vision is built?
- Is the primary artifact a "product vision document" that evolves, a workspace with multiple artifacts, or something more fluid?
- How does Archetype handle the transition from thinking to building — is it a clean handoff to Cursor/Claude Code, or does Archetype support implementation too?
- How do you build for solo users (founders, lone PMs) while also enabling team collaboration as companies grow?
- What's the pricing model? Credit-based AI pricing is universally disliked in this space.

## Reference

- [[cursor-for-product-managers/Cursor for Product Managers MOC]] — full research vault
- [[cursor-for-product-managers/YC RFS Spring 2026]] — the original RFS text
- [[cursor-for-product-managers/The Full Loop Gap]] — why nobody has built this yet
- [[cursor-for-product-managers/Competitive Dynamics]] — market structure and acquisition patterns
- [[cursor-for-product-managers/Practitioner Sentiment]] — how PMs feel about AI tools today
