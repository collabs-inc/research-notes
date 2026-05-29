# The Full Loop Gap

The central concept behind the [[YC RFS Spring 2026|"Cursor for Product Managers"]] category: no tool today supports the full loop from customer signal to executable specification.

## The Loop

1. **Ingest** — customer interviews, support tickets, usage analytics, sales calls, app reviews
2. **Synthesize** — detect themes, find recurring pain points, quantify signal strength
3. **Recommend** — "what should we build next?" with evidence-based justifications
4. **Specify** — propose concrete UI, data model, and workflow changes
5. **Hand off** — break down into development tasks that coding agents can execute

## Where Everyone Stops

No single tool covers this pipeline end to end as of May 2026.

**[[Productboard]]** gets closest on steps 1-3: ingests multi-channel feedback, auto-detects themes, links insights to features, does AI gap analysis, and generates specs (requires 3+ linked insights). But it stops at "what to build and why" — no bridge to executable specs for coding agents.

**[[Atlassian Jira]]** is building toward the full loop via Product Collection (JPD + Cycle acquisition + Rovo AI + Pendo integration), but the critical discovery pieces are in early access, not GA.

**[[BuildBetter]]** generates evidence-linked PRDs from customer conversations with quotes and timestamps — closest among non-YC startups — but stops at the PRD level.

**[[ChatPRD]]** helps write better PRDs and offers PM coaching but focuses on document generation, not the full discovery loop.

The three YC companies that came closest — [[Inari]], [[Kraftful]], [[Monterey AI]] — were all acquired in 2025-2026. See [[Competitive Dynamics]] for the acquisition wave thesis.

## Why It's Hard

From [[Practitioner Sentiment]]:

- **Strategy generation vs. critique** — AI can critique strategy using frameworks but cannot generate original strategy. (Sachin Rekhi)
- **Product sense is experiential** — "AI won't tell you what to build. Product sense comes from direct exposure to customers and markets."
- **Stated vs. revealed preferences** — "AI can tell you what users said but cannot tell you what users meant."
- **False precision** — AI-generated specs create "confusion and misalignment" because they look authoritative even when wrong. (Alan Wright)
- **Context depth** — connecting a customer complaint to the right product change requires understanding the existing product's architecture, business model, and strategic priorities. Generic AI lacks this context.

## The Opportunity

The gap is structural: incumbents are adding AI to their existing paradigms (better triage, faster ticket writing, automated status updates) rather than rethinking the loop. Execution tools (Linear, Notion, Coda) explicitly don't want to be discovery tools. Discovery tools (Productboard, Dovetail) don't bridge to execution. The tool Miklas described — customer signal in, coding-agent-ready tasks out — remains unbuilt.
