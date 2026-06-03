# AG-UI

The Agent-User Interaction protocol (by CopilotKit) — an open, event-based *transport* that streams a JSON event sequence between an agent backend and a frontend. Not a UI format; the runtime channel beneath them.

## What It Is

AG-UI streams "a single JSON event sequence over standard HTTP" (or an optional binary channel) — events for messages, tool calls, state patches, and lifecycle signals, with bi-directional shared state. It was born from CopilotKit's partnership with LangGraph and CrewAI; Microsoft's Agent Framework integrates it. Reported ~9,000+ GitHub stars by Oct 2025.

## The Layer Model

> **MCP** = Agent ↔ Tools/Data · **A2A** = Agent ↔ Agent · **AG-UI** = Agent ↔ User

AG-UI is *transport*, not *format* — it "natively supports all of the generative-UI specs," including both [[MCP Apps|HTML-in-iframe]] and [[A2UI|declarative JSON]]. It carries whichever artifact format a host chooses. Useful context for the [[The Artifact Format Standards Split|standards split]]: AG-UI is the pipe; the split is about what flows through it.

## See Also
- [[The Artifact Format Standards Split]] · [[A2UI]] · [[MCP Apps]]
- [[JSON and Structured Outputs]] · [[Generative UI]]
