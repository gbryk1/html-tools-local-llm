# Claims ledger — claude-code-course.html — js_3_context_window

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0323 · js:3. context window · L- · script
> A fresh session already uses some context for the system prompt, tools and CLAUDE.md.
- pass 1:
- pass 2: ✅ context-window.md — "A lot loads before you type anything. CLAUDE.md, memory, skills, and MCP tools are all in context before your first prompt"

### C0324 · js:3. context window · L- · script
> Auto-compact! The window hit the threshold, so history was replaced by a summary. It happened mid-task, on its own schedule — and the summary may drop details you needed.
- pass 1:
- pass 2: ✅ context-window.md — "Claude Code compacts automatically as you approach the limit"; summary "won't have the exact content"; how-claude-code-works.md "instructions from early in the conversation can get lost"

### C0325 · js:3. context window · L- · script
> /compact: history → summary. You chose the moment and can pass a focus (/compact keep the API decisions). Noise shrinks too, but its traces live on in the summary.
- pass 1:
- pass 2: ✅ context-window.md "Compact with a focus" — "The summary keeps what you choose instead of what the automatic pass guesses is important"

### C0326 · js:3. context window · L- · script
> +45K: three big files. Useful, but big. File reads dominate context usage — name the exact file and function so Claude reads less (note: @file pulls in the whole file).
- pass 1:
- pass 2: ✅ context-window.md tip — "File reads dominate context usage. Be specific in prompts… so Claude reads fewer files"; common-workflows.md — @ reference "includes the full content of the file" (+45K figure is illustrative)

### C0327 · js:3. context window · L- · script
> +14K of noise: an unrelated question and its answer. It stays in context and competes with your real task for attention. New topic → /clear or /btw.
- pass 1:
- pass 2: ✅ best-practices.md — "Long sessions with irrelevant context can reduce performance"; `/btw` "The answer never enters conversation history"

### C0328 · js:3. context window · L- · script
> A subagent does the searching in its own window…
- pass 1:
- pass 2: ✅ context-window.md — "a subagent handles the research in its own separate context window"

### C0329 · js:3. context window · L- · script
> +2K in the main window: only the subagent's summary came back. The 60K of reading stayed over there.
- pass 1:
- pass 2: ✅ context-window.md — "tokens stayed in subagent's context · only the summary returns" (token figures illustrative)

### C0330 · js:3. context window · L- · script
> /btw: the answer appears, but never enters history. Zero tokens added.
- pass 1:
- pass 2: ✅ best-practices.md — "The answer never enters conversation history, so you can check a detail without growing context"

### C0331 · js:3. context window · L- · script
> /clear: back to a fresh window. System prompt and memory reload; everything else is gone. Perfect between unrelated tasks — if decisions were saved in files.
- pass 1:
- pass 2: ✅ commands.md — "`/clear` starts fresh on a new task while keeping project memory"; costs.md "When you want a fresh start instead of continuity, `/clear` costs nothing"
