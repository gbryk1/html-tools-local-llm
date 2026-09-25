# Claims ledger — claude-code-course.html — js_9_skills

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0370 · js:9. skills · L- · script
> REST conventions, error format, pagination. Use when adding or changing API endpoints.
- pass 1:
- pass 2: n/a illustrative skill description

### C0371 · js:9. skills · L- · script
> Build PDF reports with our template. Use for exports.
- pass 1:
- pass 2: n/a illustrative skill description

### C0372 · js:9. skills · L- · script
> Draft release notes from merged PRs.
- pass 1:
- pass 2: n/a illustrative skill description

### C0373 · js:9. skills · L- · script
> At start only descriptions load — except for the dashed skill, which Claude can't even see.
- pass 1:
- pass 2: ✅ skills.md — default "Description always in context"; `disable-model-invocation: true` "Description not in context"

### C0374 · js:9. skills · L- · script
> Your prompt: “add a /invoices endpoint”. Claude matches it against skill descriptions…
- pass 1:
- pass 2: ✅ skills.md `description` — "Claude uses this to decide when to apply the skill" (prompt n/a)

### C0375 · js:9. skills · L- · script
> api-style matched (“Use when adding or changing API endpoints”) and its full body loaded. pdf-report stayed a one-line description. That's why descriptions must say when.
- pass 1:
- pass 2: ✅ skills.md — "full skill content only loads when invoked"; description = "what the skill does and when to use it" (scenario n/a)

### C0376 · js:9. skills · L- · script
> /deploy was invisible to Claude (zero context) until you typed it. Anything with side effects should work this way — Claude should never decide to deploy on its own.
- pass 1:
- pass 2: ✅ skills.md — `disable-model-invocation: true` "prevent Claude from automatically loading ... Description not in context"; advice consistent with docs

### C0377 · js:9. skills · L- · script
> /release-notes has context: fork: it runs in a forked subagent…
- pass 1:
- pass 2: ✅ skills.md `context` — "Set to `fork` to run in a forked subagent context"

### C0378 · js:9. skills · L- · script
> The 30K of git log and PR reading stayed in the fork. Your main session got only the finished notes.
- pass 1:
- pass 2: ✅ skills.md "Run skills in a subagent" — "its result arrives in your conversation when it completes" (30K illustrative n/a)
