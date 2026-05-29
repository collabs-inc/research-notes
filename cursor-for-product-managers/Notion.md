# Notion

General-purpose workspace with powerful AI agent capabilities, but no opinionated product discovery workflow.

## AI Capabilities

- **Notion AI** bundled with all paid plans since May 2025. Model choice: GPT-5, Claude Opus 4.1, o3 — switchable in one click.
- **Custom Agents** (Feb 2026, Notion 3.3) — persistent bots that run on schedules or event triggers, write results back into databases. Each agent gets its own permissions. Can access Notion, Slack, Mail, Calendar, and MCP integrations. 1M+ custom agents created.
- **Developer Platform** (May 2026, Notion 3.5) — Workers (cloud sandbox for custom code), orchestration layer for multi-tool coordination. Full Agent Hub launched May 2026.
- **Enterprise Search** across Notion + 14+ connected third-party tools.

## Pricing

Business plan required for Custom Agents. Agent credits: $10/1,000 credits (add-on). Credit consumption is unpredictable — teams should model costs before deploying many scheduled agents.

## Relevance to "Cursor for PMs"

A PM *could* build a discovery workflow in Notion using Custom Agents, tables, and integrations. But there's nothing out of the box — no feedback ingestion, no theme detection, no customer signal processing, no prioritization framework. The "build-it-yourself" nature means high setup cost and maintenance burden. Not a turnkey discovery solution.

Agents can search Slack but can't reply; can surface a Jira ticket but can't assign it. Performance degrades above 5,000 database rows (3-5 second loads).

See also: [[Incumbent AI Features]]
