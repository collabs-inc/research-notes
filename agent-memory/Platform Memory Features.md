---
tags: [market, platforms, chatgpt, claude, gemini, copilot, consumer]
created: 2026-05-27
---

# Platform Memory Features

How the major consumer AI platforms handle memory as of mid-2026. All four now offer native memory; cross-platform portability is emerging.

## ChatGPT (OpenAI)

- **April 2025**: Memory became comprehensive -- references all past conversations plus saved memories
- **June 2025**: Rolled out to free users (lightweight short-term); Plus/Pro get longer-term understanding
- **May 2026**: Enhanced memory for Plus/Pro -- pulls from past chats, saved memories, files, and connected Gmail
- **Two modes**: "Saved memories" (explicit) and "Chat history" (implicit insights from past chats)
- **Memory Sources UI**: Users can see which memories helped personalize a response and edit/delete

The most mature consumer implementation -- iterating since early 2024.

## Claude (Anthropic)

- **September 2025**: Claude Memory launched
- **March 2026**: Available on all tiers including Free
- **Architecture**: File-based approach using Markdown (CLAUDE.md) in hierarchical structure -- architecturally distinct from the vector-database approach used by others
- **"Dreaming" feature** (May 2026): For managed agents -- asynchronous memory consolidation modeled on hippocampal sleep replay
- **[[Claude Managed Agents Memory Store]]**: File-based memory API for developers -- workspace-scoped text documents mounted into agent sessions, no vector DB
- **Limitation**: Memory lives on Anthropic's servers only; not yet portable

## Gemini (Google)

- Automatic memory on Gemini 2.5 Pro -- recalls past conversations without explicit prompting
- Extracts "key details and preferences" rather than storing entire histories
- **Limitations**: Select countries only; not available for under-18, work/school accounts, or EEA/Switzerland/UK (GDPR)
- **Enterprise**: Gemini Enterprise Agent Platform Memory Bank

## Microsoft Copilot

- **July 2025**: Copilot Memory GA for all M365 Copilot-licensed users worldwide
- **2026 Work IQ layer**: Persistent understanding of roles, org structure, project history across M365
- **GitHub Copilot Memory** (Mar 2026): Repository-level understanding, 28-day expiry, on by default for Pro/Pro+
- **VS Code Local Memory Tool**: Save/recall notes across workspaces; first 200 lines auto-loaded at session start

Broadest surface area -- memory across M365, GitHub, and VS Code.

## Cross-Platform Portability

An emerging battleground:
- **Anthropic**: Launched "Import Memory" tool (March 2026)
- **Google**: Shipped cross-platform memory import around the same time
- The memory portability question maps to [[Memory Security and Privacy|privacy and sovereignty concerns]] -- who owns the agent's memories of you?

## Relationship to Middleware

Platform memory competes with [[Memory Middleware Players]] at the consumer layer but complements them at the developer layer. Platform memory is simple and opinionated; middleware offers control, customization, and multi-platform portability.
