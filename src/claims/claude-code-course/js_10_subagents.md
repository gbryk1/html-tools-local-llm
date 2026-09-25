# Claims ledger — claude-code-course.html — js_10_subagents

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0379 · js:10. subagents · L- · script
> Same question, two strategies. Watch where the reading lands.
- pass 1:
- pass 2: n/a narration

### C0380 · js:10. subagents · L- · script
> 114K of raw file contents now sit in your main context. The answer is in there somewhere — along with everything Claude read to find it. The rest of the session is slower, pricier and noisier.
- pass 1:
- pass 2: ✅ best-practices "Delegate verbose operations to subagents" — verbose reading "can consume significant context" (114K illustrative n/a)

### C0381 · js:10. subagents · L- · script
> Three Explore subagents start in parallel, each with its own fresh context…
- pass 1:
- pass 2: ✅ sub-agents.md — Explore "read-only ... searching"; "Each subagent starts with a fresh, isolated context window"; "Run parallel research"

### C0382 · js:10. subagents · L- · script
> +4.5K in main: three short summaries (“payments retries 3× with exponential backoff in retry.ts:42…”). The 114K of reading stayed in the subagents, and they ran at the same time.
- pass 1:
- pass 2: ✅ best-practices — "the verbose output stays in the subagent's context while only a summary returns to your main conversation" (numbers illustrative n/a)
