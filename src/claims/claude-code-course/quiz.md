# Claims ledger — claude-code-course.html — quiz

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0276 · quiz · L1 · quiz
> 1. What most improves the quality of Claude's result on a bug fix? → A way for Claude to verify its work, such as a failing test it must make pass — 💡 The loop is gather → act → verify. With a check it can run, Claude finds its own mistakes; without one, you are the test suite.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "gather context, take action, and verify results"; best-practices.md — "you become the verification loop"

### C0277 · quiz · L1 · quiz
> 2. Your session has been going for two hours across three unrelated tasks and answers are getting worse. Best move? → /clear and start the next task fresh, with decisions saved in files — 💡 Noise hurts before the window is full, and summaries keep traces of dead ends. /clear between unrelated tasks; persist decisions in files.
- pass 1:
- pass 2: ✅ best-practices.md — "performance degrades as it fills"; failure patterns "Fix: /clear between unrelated tasks"

### C0278 · quiz · L1 · quiz
> 3. Where does a nested packages/web/CLAUDE.md get loaded? → Only when Claude reads files in packages/web/ — 💡 Files above the working directory load at launch; nested ones load on demand when Claude works in that folder.
- pass 1:
- pass 2: ✅ memory.md — "Files in subdirectories load on demand when Claude reads files in those directories" (above cwd load at launch)

### C0279 · quiz · L1 · quiz
> 4. You have deny: Bash(aws *) and allow: Bash(aws s3 ls). What happens to "aws s3 ls"? → Denied — deny is checked first and first match wins — 💡 Rules are evaluated deny → ask → allow; first match wins, specificity does not matter. An allow can't carve an exception out of a deny.
- pass 1:
- pass 2: ✅ permissions.md — "A broad deny rule like `Bash(aws *)` blocks every matching call, including… `Bash(aws s3 ls)`. An allow rule can't carve an exception out of a deny rule"

### C0280 · quiz · L1 · quiz
> 5. Which permission mode fits a CI job with an exact list of allowed tools and no human present? → dontAsk — 💡 dontAsk denies anything that would prompt, so only reads and pre-approved tools run.
- pass 1:
- pass 2: ✅ permission-modes.md — "`dontAsk` … Reads and pre-approved tools; anything that would prompt is denied | Locked-down CI and scripts"

### C0281 · quiz · L1 · quiz
> 6. When is plan mode NOT worth it? → When you could describe the diff in one sentence — 💡 Planning has a fixed cost; it pays off for multi-file, uncertain or unfamiliar work. One-sentence diffs: just do it.
- pass 1:
- pass 2: ✅ best-practices.md — "If you could describe the diff in one sentence, skip the plan"

### C0282 · quiz · L1 · quiz
> 7. Claude deleted a file with a Bash rm, then you rewound code to an earlier checkpoint. Is the file back? → No, checkpoints don't track changes made by Bash commands — 💡 Checkpoints track edits made through Claude's file tools. Bash-made changes aren't restored — commit often.
- pass 1:
- pass 2: ✅ checkpointing.md "Bash command changes not tracked" — "Checkpointing does not track files modified by Bash commands"

### C0283 · quiz · L1 · quiz
> 8. You want a /deploy workflow that Claude must never start on its own. Which skill setting? → disable-model-invocation: true — 💡 disable-model-invocation: true hides the skill from Claude until you type /deploy — and costs no context until then.
- pass 1:
- pass 2: ✅ skills.md — "`disable-model-invocation: true` | You: Yes | Claude: No | Description not in context, full skill loads when you invoke"

### C0284 · quiz · L1 · quiz
> 9. Why does a skill library of 50 skills not blow up your context window? → Only names and descriptions load at start; a skill's body loads when it's used — 💡 Progressive disclosure: descriptions every request, full body on use, linked files only if opened.
- pass 1:
- pass 2: ✅ skills.md — "skill descriptions are loaded into context… full skill content only loads when invoked"

### C0285 · quiz · L1 · quiz
> 10. Main benefit of delegating a broad codebase search to a subagent? → The file reading happens in its own context; only a summary returns to yours — 💡 Isolation, not price: the subagent spends its own tokens, but your main context stays clean.
- pass 1:
- pass 2: ✅ sub-agents.md — "the subagent does that work in its own context"; best-practices.md — "Subagents run in separate context windows and report back summaries"

### C0286 · quiz · L1 · quiz
> 11. "Never delete files outside the project" must hold every time. Where do you put it? → In a PreToolUse hook that exits with code 2 on violation (and/or a deny rule) — 💡 CLAUDE.md is a request the model interprets. Hooks and deny rules are enforced by Claude Code itself.
- pass 1:
- pass 2: ✅ features-overview.md — "'never edit .env' in CLAUDE.md… is a request, not a guarantee. A PreToolUse hook that blocks the edit is enforcement"

### C0287 · quiz · L1 · quiz
> 12. You add the same MCP server named "db" at local and project scope. Which one is used? → Local — precedence is local > project > user — 💡 MCP servers override by name: local > project > user.
- pass 1:
- pass 2: ✅ mcp.md "Scope hierarchy and precedence" — "1. Local scope 2. Project scope 3. User scope"; "The three scopes match duplicates by name"

### C0288 · quiz · L1 · quiz
> 13. You need three independent features built in parallel without sessions overwriting each other's files. Use… → Three sessions, each started with claude -w <name> (git worktrees) — 💡 Worktrees give each session its own checkout and branch while sharing history.
- pass 1:
- pass 2: ✅ worktrees.md — "separate working directory with its own files and branch, sharing the same repository history"

### C0289 · quiz · L1 · quiz
> 14. Token costs scale with context size. Which everyday habit therefore cuts cost reliably? → Context hygiene: /clear between tasks, lean CLAUDE.md, subagents for heavy reading — 💡 Token costs scale with context size, so keeping it lean is the first lever the docs list — then match model and effort to the task.
- pass 1:
- pass 2: ✅ costs.md "Reduce token usage" — "Token costs scale with context size"; first subsection is "Manage context proactively" ("Clear between tasks"), followed by model choice, CLAUDE.md→skills, subagents, effort
