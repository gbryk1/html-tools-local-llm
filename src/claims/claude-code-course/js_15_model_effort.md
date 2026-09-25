# Claims ledger — claude-code-course.html — js_15_model_effort

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0433 · js:15. model & effort · L- · script
> Mechanical change with a clear finish line. Low effort is fast and cheap; even haiku works for many such tasks.
- pass 1:
- pass 2: ✅ model-config.md low "short, scoped, latency-sensitive tasks"; "Lower effort is faster and cheaper"; haiku "for simple tasks"

### C0434 · js:15. model & effort · L- · script
> The plan already holds the hard thinking. A solid mid-size model at default effort executes it well — this is where opusplan shines.
- pass 1:
- pass 2: ✅ model-config.md "opusplan … uses opus during plan mode, then switches to sonnet for execution" (rest is advice)

### C0435 · js:15. model & effort · L- · script
> Subtle bugs reward deeper reasoning: more hypotheses considered, fewer wrong fixes. Raise effort for this session, lower it afterwards.
- pass 1:
- pass 2: ✅ model-config.md "higher effort provides deeper reasoning for complex problems"; "s in the /effort slider … apply the level to this session only"

### C0436 · js:15. model & effort · L- · script
> opus or fable · /effort xhigh · plan mode
- pass 1:
- pass 2: ✅ model-config.md — xhigh supported on Opus 5.5/5 and Fable 5.1/5; plan mode exists (suggestion itself is advice)

### C0437 · js:15. model & effort · L- · script
> Design and hard refactors are where top models and high effort earn their price. Use plan mode so the thinking produces a reviewable plan. max can overthink — test before adopting it.
- pass 1:
- pass 2: ✅ model-config.md — max "may show diminishing returns and is prone to overthinking. Test before adopting broadly"

### C0438 · js:15. model & effort · L- · script
> Fast mode: same Opus model, up to ~2.5× faster output, higher cost per token — for when you're waiting on it interactively.
- pass 1:
- pass 2: ✅ fast-mode.md — "high-speed configuration for Claude Opus, making the model up to 2.5x faster at a higher cost per token … for interactive work"; "not a different model"

### C0439 · js:15. model & effort · L- · script
> Fast mode only runs on Opus — turning it on switches you from Sonnet to Opus — so it isn't part of this Sonnet pick.
- pass 1:
- pass 2: ✅ fast-mode.md — "Fast mode is supported on Opus 5.5, Opus 5, and Opus 4.8. It is not available on Sonnet, Haiku…"; "If your current model doesn't support fast mode, Claude Code switches to Opus"
