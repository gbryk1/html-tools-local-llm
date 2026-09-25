# Claims ledger — claude-code-course.html — js_13_parallel_chooser

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0406 · js:13. parallel chooser · L- · script
> Find how retries work in 3 services without flooding my session
- pass 1:
- pass 2: n/a scenario prompt text

### C0407 · js:13. parallel chooser · L- · script
> Short, independent research questions → subagents. Each reads in its own window and returns a summary. Ask: “use subagents to…”.
- pass 1:
- pass 2: ✅ best-practices.md — "Subagents run in separate context windows and report back summaries"; "Delegate research with \"use subagents to investigate X\""

### C0408 · js:13. parallel chooser · L- · script
> Build 3 unrelated features at once without file collisions
- pass 1:
- pass 2: n/a scenario prompt text

### C0409 · js:13. parallel chooser · L- · script
> Worktrees: claude -w search, claude -w billing… Each session gets its own checkout and branch under .claude/worktrees/, sharing git history.
- pass 1:
- pass 2: ✅ worktrees.md — "its own files and branch, sharing the same repository history"; "created under .claude/worktrees/<name>/"

### C0410 · js:13. parallel chooser · L- · script
> Start a long refactor, close the terminal, check back later
- pass 1:
- pass 2: n/a scenario prompt text

### C0411 · js:13. parallel chooser · L- · script
> Background sessions: /background detaches the session; claude agents (agent view) dispatches and monitors them. Step back in by attaching from agent view (or claude attach &lt;id&gt;); claude -r reopens it once it has finished.
- pass 1:
- pass 2: ✅ agent-view.md "From inside a session" + shell commands table — "`/background` sends the current conversation there and frees your terminal"; "`claude attach <id>` Attach to a session"; transcript "available through `claude --resume`" (cli-reference: `--resume`, `-r`)

### C0412 · js:13. parallel chooser · L- · script
> A bug with 3 competing theories — agents should argue and converge
- pass 1:
- pass 2: n/a scenario prompt text

### C0413 · js:13. parallel chooser · L- · script
> Agent team (experimental): a lead spawns teammates who investigate different hypotheses and message each other to challenge findings.
- pass 1:
- pass 2: ✅ agent-teams.md — "Debugging with competing hypotheses: teammates test different theories in parallel and converge"; "Teammates message each other directly"; "experimental"

### C0414 · js:13. parallel chooser · L- · script
> Migrate 500 files and have a second agent verify each change
- pass 1:
- pass 2: n/a scenario prompt text

### C0415 · js:13. parallel chooser · L- · script
> Dynamic workflow: Claude writes a script that fans out subagents and cross-checks results; you can re-run it. For a big mechanical change, the bundled /batch skill splits it across subagents in their own worktrees.
- pass 1:
- pass 2: ✅ workflows.md intro — "A dynamic workflow is a JavaScript script that orchestrates many subagents… you can rerun"; commands.md `/batch` — "Skill… decomposes the work into 5 to 30 independent units"; best-practices.md — "Each subagent works in its own worktree"

### C0416 · js:13. parallel chooser · L- · script
> Keep working until every test in the module passes
- pass 1:
- pass 2: n/a scenario prompt text

### C0417 · js:13. parallel chooser · L- · script
> /goal “all tests in src/billing pass”: after each turn a small model checks the condition; if not met, Claude takes another turn.
- pass 1:
- pass 2: ✅ goal.md — "After each turn, a small fast model checks whether the condition holds. If … not yet met, Claude starts another turn"

### C0418 · js:13. parallel chooser · L- · script
> Check the deploy status every 5 minutes while I work
- pass 1:
- pass 2: n/a scenario prompt text

### C0419 · js:13. parallel chooser · L- · script
> /loop 5m check the deploy and tell me if it fails. Session-scoped: stops when the session ends.
- pass 1:
- pass 2: ✅ scheduled-tasks.md — "Tasks are session-scoped"; "Closing the terminal or letting the session exit stops them firing" (backgrounding carries /loop over)

### C0420 · js:13. parallel chooser · L- · script
> Triage new issues every night, even with my laptop closed
- pass 1:
- pass 2: n/a scenario prompt text

### C0421 · js:13. parallel chooser · L- · script
> Routine via /schedule: runs in the cloud on a cron, an API call or GitHub events. No open terminal needed.
- pass 1:
- pass 2: ✅ routines.md — "run on a schedule, trigger on API calls, or react to GitHub events from cloud infrastructure"; "/schedule update … specific cron expression"

### C0422 · js:13. parallel chooser · L- · script
> Each scenario lights up the approach that fits best.
- pass 1:
- pass 2: n/a UI instruction
