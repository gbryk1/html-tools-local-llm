# Claims ledger — claude-code-course.html — ctx

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0035 · ctx · L1 · p
> Everything Claude “knows” in a session lives in its context window: the system prompt, tool definitions, your CLAUDE.md, skill descriptions, every message, every file it read, every command output. The window has a fixed size. When it fills, Claude Code compacts: it replaces older history with a summary. Details get lost in summaries.
- pass 1:
- pass 2: ✅ context-window.md intro + "What survives compaction" — "holds everything Claude knows about your session"; "compacts automatically as you approach the limit"; "replaces the conversation with a structured summary ... won't have the exact content"

### C0036 · ctx · L1 · p
> And there is a quieter problem before the window is full: noise. The more irrelevant stuff sits in context — a debugging tangent, three unrelated questions, a 2,000-line log — the worse Claude follows your instructions. Expert users treat context like RAM on a small machine.
- pass 1:
- pass 2: ✅ best-practices.md — "Long sessions with irrelevant context can reduce performance"; "can reduce performance and sometimes distract Claude" (RAM analogy is opinion)

### C0037 · ctx · L1 · figcaption
> Numbers are illustrative. The real window depends on the model (200K is common; some models offer 1M). /context shows your real usage as a colored grid; /autocompact sets when automatic compaction starts.
- pass 1:
- pass 2: ✅ context-window.md + commands.md — "support a 1 million token context window"; `/context` "Visualize current context usage as a colored grid"; `/autocompact` "how full the context window gets before Claude Code compacts automatically"

### C0038 · ctx · L1 · p
> Tonight's guests: /compact and /clear.
- pass 1:
- pass 2: n/a (framing)

### C0039 · ctx · L1 · div
> /compactI'm the gentle one. I summarize the conversation and keep going. You can steer me: /compact focus on the API changes.
- pass 1:
- pass 2: ✅ context-window.md "Compact with a focus" — "run `/compact` with instructions, like `/compact focus on the auth bug fix`"

### C0040 · ctx · L1 · div
> /clearAnd I'm the honest one. A summary still carries the dead ends and the wrong guesses. New task? Start clean.
- pass 1:
- pass 2: ✅ best-practices.md — "the context is cluttered with failed approaches. Run `/clear` and start fresh"; "/clear between unrelated tasks"

### C0041 · ctx · L1 · div
> /compactBut then Claude forgets what we decided!
- pass 1:
- pass 2: n/a (dialogue setup)

### C0042 · ctx · L1 · div
> /clearDecisions belong in files — a plan, a CLAUDE.md line, a commit message. Not in chat history. Then clearing costs nothing.
- pass 1:
- pass 2: n/a (advice; consistent with memory.md "Add conversation-only instructions to CLAUDE.md to make them persist")

### C0043 · ctx · L1 · p
> Not all context is equal. MCP tools load only their names at start; full schemas are fetched when used (tool search). Skills load only their descriptions; the body loads when triggered. Subagents run in their own window and return only a summary. Hooks cost nothing unless they print output. That's why the extension chapters keep asking “where does this land in context?” — it's the design principle behind all of them. For partial compaction, open the rewind menu (Esc Esc), pick a message and choose Summarize from here or Summarize up to here.
- pass 1:
- pass 2: ✅ how-claude-code-works.md/costs.md — "only tool names and server instructions consume context until Claude uses a specific tool"; features-overview.md — skills "Description loads each session; full content loads when used", hooks "Zero unless the hook returns output"; context-window.md — subagent "Only the summary and a small metadata trailer come back"; checkpointing.md — "press `Esc` twice when the prompt input is empty ... Summarize from here / Summarize up to here"

### C0044 · ctx · L1 · li
> Context is finite and noise hurts before it's full. /context to look, /clear between unrelated tasks.
- pass 1:
- pass 2: ✅ best-practices.md — "performance degrades as it fills"; "`/clear`: reset context between unrelated tasks"; commands.md `/context` shows what fills the window

### C0045 · ctx · L1 · li
> /compact [focus] keeps going with a summary; /btw asks without adding to history.
- pass 1:
- pass 2: ✅ commands.md — `/compact` with focus; `/btw` "Ask a side question ... without adding to the conversation"

### C0046 · ctx · L1 · li
> Big searches → subagents: their reading stays in their window.
- pass 1:
- pass 2: ✅ context-window.md — "Delegate large reads: send research to a subagent so the file contents stay in its context window, not yours"

### C0047 · ctx · L1 · li
> Persist decisions in files, not in chat.
- pass 1:
- pass 2: n/a (advice; consistent with memory.md "Add conversation-only instructions to CLAUDE.md to make them persist")
