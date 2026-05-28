---
tags: [market, cloud, google, aws, microsoft, oracle, managed-services]
created: 2026-05-27
---

# Cloud Provider Memory Services

All three hyperscalers now offer managed agent memory -- the classic "AWS/GCP/Azure builds it" dynamic that threatens [[Memory Middleware Players|middleware startups]].

## Google Cloud: Vertex AI Memory Bank

- **Status**: GA (January 2026)
- **Pricing**: $0.25 per 1,000 events/memories
- **Architecture**: Managed service within Vertex AI Agent Platform
- **Integration**: Google ADK, Redis-backed agent memory
- **Also**: Open-sourced an "Always On Memory Agent" (2026) built with ADK + Gemini 3.1 Flash-Lite that ditches vector databases for a continuous-ingestion, background-consolidation approach

Google moved first to GA and has the most transparent pricing.

## AWS: Bedrock AgentCore Memory

- **Status**: GA (2026)
- **Architecture**: Managed episodic memory within the AgentCore platform
- **Notable**: AWS partnered with [[Memory Middleware Players|Mem0]] as the exclusive memory provider for its Strands Agents SDK rather than building everything in-house

The AWS-Mem0 partnership is the most significant competitive signal -- it suggests that even hyperscalers see dedicated memory middleware as non-trivial to build well.

## Microsoft: Azure Foundry Agent Service Memory

- **Status**: Preview (free during preview, pay for model calls only)
- **Architecture**: Managed long-term memory store within Azure AI Foundry
- **Also**: Microsoft Agent Framework (MAF) integrates with Mem0 via `Microsoft.SemanticKernel.Memory.Mem0Provider`
- **GitHub Copilot Memory** (Mar 2026): repository-level memory of coding conventions, architecture, cross-file dependencies. 28-day expiry. On by default for Pro/Pro+.
- **VS Code Local Memory Tool**: built-in agent tool for saving/recalling notes across workspaces

Microsoft's approach is the most distributed -- memory features across Azure Foundry, GitHub Copilot, VS Code, and the Agent Framework.

## Oracle: AI Agent Memory SDK

- **Status**: Expected CY2026
- **Architecture**: Leverages converged Oracle Database
- **Benchmark**: 93.8% on LongMemEval
- **Signal**: Database incumbents see agent memory as a natural extension of their core business

## Implications for Middleware

The cloud provider entry creates a two-speed market:
1. **"Good enough" memory** bundled into cloud platforms -- sufficient for simple agents, priced to bundle
2. **Differentiated memory** from middleware -- temporal reasoning ([[Memory Middleware Players|Zep]]), token efficiency ([[Memory Middleware Players|Mem0]]), agent-controlled context ([[Memory Middleware Players|Letta]])

The [[Competitive Dynamics|AWS-Mem0 partnership]] model may become the template: hyperscalers partnering with best-of-breed middleware rather than building from scratch.
