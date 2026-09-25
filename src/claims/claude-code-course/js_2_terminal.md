# Claims ledger — claude-code-course.html — js_2_terminal

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0308 · js:2. terminal · L- · script
> The prompt bar at the bottom shows the permission mode — watch it change.
- pass 1:
- pass 2: ✅ permission-modes.md — "The status bar shows the active mode as a gray `⏸ manual mode on` for default, or as `⏵⏵ accept edits on`, `⏸ plan mode on`..."

### C0309 · js:2. terminal · L- · script
> / opens the command menu: built-in commands, bundled skills and your own skills. Type to filter.
- pass 1:
- pass 2: ✅ commands.md — "built-in commands and bundled skills"; "`/` at start | Command or skill"; "Claude Code filters the `/` menu as you type"

### C0310 · js:2. terminal · L- · script
> /compact — summarize conversation/config — settings/context — visualize context usage/code-review — review the diff
- pass 1:
- pass 2: ✅ commands.md — /compact "Free up context by summarizing the conversation"; /config "Open the Settings interface"; /context "Visualize current context usage"; /code-review "Review the current diff"

### C0311 · js:2. terminal · L- · script
> @ autocompletes a file path and puts that file into context directly — no search needed.
- pass 1:
- pass 2: ✅ interactive-mode.md — "`@` | File path mention | Trigger file path autocomplete"; common-workflows.md — "Use @ to quickly include files or directories without waiting for Claude to read them"

### C0312 · js:2. terminal · L- · script
> Tokens refresh 60s before expiry: scheduleRefresh() sets a timer from expiresAt − 60_000…
- pass 1:
- pass 2: n/a simulated Claude answer

### C0313 · js:2. terminal · L- · script
> ! runs a shell command yourself. The output lands in the conversation and Claude responds to it. No permission prompt.
- pass 1:
- pass 2: ✅ interactive-mode.md shell mode — "Adds the command and its output to the conversation context", "Doesn't require Claude to interpret or approve the command", "Claude responds to the command output automatically"

### C0314 · js:2. terminal · L- · script
> ● One modified file (session.ts) and an untracked notes.md. Want me to commit the fix and ignore notes.md?
- pass 1:
- pass 2: n/a simulated Claude answer

### C0315 · js:2. terminal · L- · script
> Manual: Claude asks before edits and commands.
- pass 1:
- pass 2: ✅ permission-modes.md — "In Manual mode, Claude Code stops and asks you before most actions that edit files, run shell commands, or reach the network"

### C0316 · js:2. terminal · L- · script
> Accept edits: file edits and common fs commands run without asking.
- pass 1:
- pass 2: ✅ permission-modes.md — acceptEdits "Reads, file edits, and common filesystem commands (mkdir, touch, mv, cp, etc.)"

### C0317 · js:2. terminal · L- · script
> Auto mode: a classifier model reviews actions instead of you and blocks risky ones. It appears in the cycle when auto mode is available (supported model, not turned off by your org); on Pro, Max and Team it is the default starting mode.
- pass 1:
- pass 2: ✅ permission-modes.md — "In auto mode, a second model, the classifier, reviews actions instead of you"; "`auto`: appears when auto mode is available"; "On Pro, Max, and Team plans, the built-in starting permission mode is auto mode"; disableAutoMode lets orgs turn it off

### C0318 · js:2. terminal · L- · script
> /btw asks a side question. The answer is shown but never enters conversation history — zero context cost later.
- pass 1:
- pass 2: ✅ interactive-mode.md 'Side questions with /btw' — "The question and answer never enter the conversation history"

### C0319 · js:2. terminal · L- · script
> (side answer · not saved) Starts the session in its own git worktree under .claude/worktrees/, on a new branch.
- pass 1:
- pass 2: ✅ worktrees.md — "the worktree is created under .claude/worktrees/<name>/ at your repository root, on a new branch named worktree-<name>"; cli-reference `--worktree, -w` (the side-answer framing is illustrative)

### C0320 · js:2. terminal · L- · script
> On an empty prompt, Esc Esc opens the rewind menu: every prompt is a checkpoint.
- pass 1:
- pass 2: ✅ interactive-mode.md — "When the input is empty, double Esc opens the rewind menu"; checkpointing.md — "Every prompt you send that starts a turn creates a new checkpoint"

### C0321 · js:2. terminal · L- · script
> 1 · explain the auth flow2 · refactor session.ts to classes3 · also rename every file to kebab-case
- pass 1:
- pass 2: n/a illustrative demo prompts

### C0322 · js:2. terminal · L- · script
> ⏪ Restore code and conversation to before “refactor session.ts to classes”? yes
- pass 1:
- pass 2: ✅ checkpointing.md — "Restore code and conversation: revert both code and conversation to that point" (prompt text illustrative)
