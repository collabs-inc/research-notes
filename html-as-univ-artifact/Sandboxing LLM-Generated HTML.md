# Sandboxing LLM-Generated HTML

The safety precondition for the whole thesis: if rendering generated markup means *running generated code*, the artifact must be contained. The good news — the browser is a battle-tested sandbox.

## "The Browser Is the Sandbox"

Paul Kinlan (Jan 2026): *"Over the last 30 years, we have built a sandbox specifically designed to run incredibly hostile, untrusted code from anywhere on the web."* The same isolation that protects you from malicious websites can contain LLM-generated code — via the `<iframe sandbox>` attribute, Content Security Policy, WebAssembly in workers, and scoped File System Access. This is the security face of [[The Browser as Universal Runtime]].

## The Production Pattern (Claude Artifacts)

[[Claude Artifacts]] run in an iframe sandbox with full-site process isolation and a strict CSP that restricts `localStorage` and `fetch()`. [[Simon Willison]]'s key finding (Apr 2026): a `<meta http-equiv="Content-Security-Policy">` tag injected at the top of iframe content **is enforced at parse time and cannot be removed or disabled by later untrusted JS** inside a `sandbox="allow-scripts"` iframe. So you can render untrusted LLM HTML safely *with only a meta tag*.

Sharp edges: the `sandbox` attribute **alone does not block network requests** — the CSP is what prevents resource fetching and exfiltration; and Firefox ignores the `csp` iframe *attribute*, so the meta-tag CSP is mandatory for cross-browser safety.

## Why It Matters

Sandboxing is what makes HTML defensible as an artifact format — but only inside a *no-network* sandbox. Outside one, a generated artifact that can make requests is an exfiltration vector. See [[The Lethal Trifecta]].

## See Also
- [[The Lethal Trifecta]] · [[Claude Artifacts]] · [[The Browser as Universal Runtime]]
- [[MCP Apps]] · [[Implications for Archetype]]
