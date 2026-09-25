# Claims ledger — claude-code-course.html — js_1_agentic_loop

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0290 · js:1. agentic loop · L- · script
> Press ▶ to watch Claude gather, act and verify.
- pass 1:
- pass 2: n/a figure instruction

### C0291 · js:1. agentic loop · L- · script
> Gather: beyond CLAUDE.md and auto memory, Claude knows nothing about this code yet, so it searches and reads first.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "Each new session starts with a fresh context window"; CLAUDE.md and auto memory load at start; Claude then gathers context by reading/searching (nuance: git status snapshot also loads)

### C0292 · js:1. agentic loop · L- · script
> expects session valid until expiry
- pass 1:
- pass 2: n/a illustrative demo code/comment

### C0293 · js:1. agentic loop · L- · script
> Act: a hypothesis becomes an edit.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "take action" phase (scenario illustrative)

### C0294 · js:1. agentic loop · L- · script
> No tests exist, so Claude has nothing to run. It reports success based on reading alone.
- pass 1:
- pass 2: ✅ best-practices.md — "Without a check it can run, 'looks done' is the only signal available" (scenario illustrative)

### C0295 · js:1. agentic loop · L- · script
> ✓ Done: fixed the comparison in isValid().
- pass 1:
- pass 2: n/a simulated Claude output

### C0296 · js:1. agentic loop · L- · script
> …in production: users still logged out early (refresh bug untouched)
- pass 1:
- pass 2: n/a simulated scenario

### C0297 · js:1. agentic loop · L- · script
> Plausible, wrong, shipped. The second bug (token refresh) was never exercised. Without a way to verify, you are the test suite.
- pass 1:
- pass 2: ✅ best-practices.md — "you become the verification loop: every mistake waits for you to notice it" (scenario n/a)

### C0298 · js:1. agentic loop · L- · script
> Verify: run the tests. The loop closes itself.
- pass 1:
- pass 2: ✅ best-practices.md — "Give Claude something that produces a pass or fail, and the loop closes on its own"

### C0299 · js:1. agentic loop · L- · script
> A failing test is information. Back to gathering, with a sharper question.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "A bug fix cycles through all three phases repeatedly"

### C0300 · js:1. agentic loop · L- · script
> refresh scheduled exactly at expiry
- pass 1:
- pass 2: n/a illustrative demo text

### C0301 · js:1. agentic loop · L- · script
> schedule refresh at expiresAt − 60s
- pass 1:
- pass 2: n/a illustrative demo text

### C0302 · js:1. agentic loop · L- · script
> ✓ Fixed two bugs; all auth tests pass.
- pass 1:
- pass 2: n/a simulated Claude output

### C0303 · js:1. agentic loop · L- · script
> Done — and proven. Two bugs, found because the loop could check itself. Same model, same prompt; the difference is the test suite.
- pass 1:
- pass 2: n/a pedagogy summary of the simulation (consistent with best-practices 'loop closes on its own')

### C0304 · js:1. agentic loop · L- · script
> Claude starts writing its own date comparison helper…
- pass 1:
- pass 2: n/a simulated scenario

### C0305 · js:1. agentic loop · L- · script
> stop — we already have isExpired() in utils/time.ts, use that
- pass 1:
- pass 2: n/a simulated user message

### C0306 · js:1. agentic loop · L- · script
> Esc stopped the step before a duplicate helper landed. Your message steers the next step.
- pass 1:
- pass 2: ✅ interactive-mode.md — Esc "Stop the current response or tool call mid-turn so you can redirect. Claude keeps the work done so far"

### C0307 · js:1. agentic loop · L- · script
> Steered early, cheap fix. Correcting after 2 steps costs little; after 20 it costs a rewind.
- pass 1:
- pass 2: n/a advice/opinion (rewind exists per checkpointing.md)
