# Simon Willison

The most prolific practitioner-advocate of HTML-as-artifact, and the field's leading voice on the *security* of rendering LLM-generated code. Co-creator of Django; author of the widely-read simonwillison.net.

## The Practice

Willison has vibe-coded **150+ single-file HTML tools** (published at `tools.simonwillison.net`, code in `github.com/simonw/tools`), "almost all of them written by LLMs." His December 2025 essay "Useful patterns for building HTML tools" codified the [[Single-File HTML Apps|single-file philosophy]]:

> "A single file: inline JavaScript and CSS in a single HTML file means the least hassle in hosting or distributing them."

> "Keep them small. A few hundred lines means the maintainability of the code doesn't matter too much: any good LLM can read them and understand what they're doing."

His colophon publishes the full prompt/transcript and git commit for each tool — complete provenance.

## The Convert

After [[Thariq Shihipar]]'s May 2026 piece, Willison reconsidered a three-year Markdown-for-output default, noting he'd chosen Markdown "since the GPT-4 days, when the 8,192 token limit meant that Markdown's token-efficiency over HTML was extremely worthwhile" — a constraint million-token windows removed. See [[HTML Is the New Markdown]].

## The Security Voice

Willison coined the **[[The Lethal Trifecta|"lethal trifecta"]]** (June 2025) and tracks [[Markdown|markdown-image exfiltration]] attacks across products. He also proved (Apr 2026) that a CSP `<meta>` tag injected at the top of a sandboxed iframe **cannot be escaped or disabled by untrusted JS inside it** — the technical basis for safely rendering generated HTML. See [[Sandboxing LLM-Generated HTML]].

## See Also
- [[Single-File HTML Apps]] · [[HTML Is the New Markdown]] · [[The Lethal Trifecta]]
- [[Sandboxing LLM-Generated HTML]] · [[Thariq Shihipar]]
