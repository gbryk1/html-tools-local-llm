# Claims ledger — claude-code-course.html — loop

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0005 · loop · L1 · p
> A chat model answers. An agent acts. Claude Code wraps a Claude model in a loop with tools: the model reads your request, decides which tool to call (read a file, grep, edit, run a shell command, fetch a URL), sees the result, and decides again. It repeats until it thinks the job is done — or until you interrupt.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "You can interrupt at any point to steer Claude"; "Claude decides what each step requires based on what it learned from the previous step"; tools-reference lists Read/Grep/Edit/Bash/WebFetch

### C0006 · loop · L1 · p
> The docs describe three phases that blend into each other: gather context, take action, verify results. The single most important sentence in this whole guide follows from that loop: Claude is only as good as its ability to check its own work. If there is a test, a build, a linter, or a screenshot it can look at, the loop closes itself. If not, you are the verification step.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "three phases: gather context, take action, and verify results. These phases blend together"; best-practices.md 'Give Claude a way to verify its work' — "you become the verification loop" (the 'most important sentence' line is the guide's own framing)

### C0007 · loop · L1 · figcaption
> Simplified: a real run may batch several read-only tool calls in parallel and stream its reasoning. The tool names are the real ones (Grep, Read, Edit, Bash).
- pass 1:
- pass 2: ✅ tools-reference.md table lists `Grep`, `Read`, `Edit`, `Bash`; hooks.md PostToolBatch — "fires concurrently when Claude makes parallel tool calls"

### C0008 · loop · L1 · div
> Why did it read files before editing? I told it which test fails.
- pass 1:
- pass 2: n/a rhetorical question

### C0009 · loop · L1 · div
> Because the model starts every session knowing nothing about your code. It has no index of your repo in its head. Everything it knows comes from what it read in this session, plus CLAUDE.md and auto memory (chapter 4). Reading first is the correct behavior — you can make it faster by pointing at files with @path.
- pass 1:
- pass 2: ✅ memory.md / how-claude-code-works.md — "Each new session starts with a fresh context window"; CLAUDE.md and auto memory "loaded at the start of every conversation"; common-workflows.md @file "includes the full content of the file" (nuance: a git status snapshot — branch, status, recent commits — also loads at start; optional to mention)

### C0010 · loop · L1 · div
> Can I type while it works?
- pass 1:
- pass 2: n/a rhetorical question

### C0011 · loop · L1 · div
> Yes. Messages you type during a turn are queued and read by Claude at the next step. Press Esc to stop the current step immediately; the work done so far stays, and you can redirect.
- pass 1:
- pass 2: ✅ interactive-mode.md 'Queue messages while Claude works' — "it reads the message as soon as those calls finish, within the same turn"; Esc row — "Stop the current response or tool call mid-turn so you can redirect. Claude keeps the work done so far"

### C0012 · loop · L1 · li
> Claude Code = model + tools + a loop: gather context → act → verify → repeat.
- pass 1:
- pass 2: ✅ how-claude-code-works.md — "gather context, take action, and verify results" (summary of the loop)

### C0013 · loop · L1 · li
> Apart from CLAUDE.md and auto memory, it knows nothing about your repo at start; reading is not wasted time.
- pass 1:
- pass 2: ✅ how-claude-code-works.md "Sessions are independent" — "starts with a fresh context window"; memory.md — both memory systems "loaded at the start of every conversation" (nuance: a git status snapshot also loads at start)

### C0014 · loop · L1 · li
> Give it a way to verify (tests, build, screenshots). No verification ⇒ plausible-looking bugs.
- pass 1:
- pass 2: ✅ best-practices.md 'Give Claude a way to verify its work' — "a test suite, a build exit code, a linter ... or a browser screenshot"; "'looks done' is the only signal available"

### C0015 · loop · L1 · li
> Esc interrupts, typing mid-turn queues a correction. Steer early.
- pass 1:
- pass 2: ✅ interactive-mode.md — Esc "Stop the current response or tool call mid-turn so you can redirect"; "Type a correction and press Enter without stopping Claude. The message shows as queued"
