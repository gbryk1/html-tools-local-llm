# Claims ledger — claude-code-course.html — sub

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0151 · sub · L1 · p
> A subagent is a separate Claude instance with its own context window, its own system prompt, and optionally its own tools, model and permissions. The main session hands it a task; it reads, searches, runs things, and returns only a summary. The 40 files it read never enter your main context.
- pass 1:
- pass 2: ✅ sub-agents.md — "Each subagent runs in its own context window with a custom system prompt, specific tool access, and independent permissions"; "returns only the summary" (40 files n/a)

### C0152 · sub · L1 · p
> Claude uses built-in subagents on its own: Explore (read-only codebase search), Plan (research during plan mode) and general-purpose (explore + modify, multi-step). You can also ask: “use subagents to investigate how payments, auth and emails each handle retries.” Several can run in parallel.
- pass 1:
- pass 2: ✅ sub-agents.md "Built-in subagents" — Explore "read-only agent optimized for searching"; Plan "used during plan mode to gather context"; general-purpose "both exploration and modification ... multiple dependent steps"; "Run parallel research"

### C0153 · sub · L1 · figcaption
> Token counts are illustrative. Subagents spend their own tokens — delegation mainly protects your main context (a cheaper subagent model, e.g. Haiku, can also cut cost). Parallel subagents finish sooner than sequential reading.
- pass 1:
- pass 2: ✅ sub-agents.md intro + "Run parallel research"; costs.md "Delegate verbose operations" — "Control costs by routing tasks to faster, cheaper models like Haiku"; "spawn multiple subagents to work simultaneously"

### C0154 · sub · L1 · pre
> .claude/agents/security-reviewer.md --- name: security-reviewer description: Reviews diffs for injection, authz and secret-handling bugs. Use after changes to auth or API code. tools: Read, Grep, Glob, Bash model: opus permissionMode: plan # read-only memory: project # keeps its own notes across sessions --- You are a senior application security engineer. For each finding give file:line, the exploit scenario, and the minimal fix. No style comments.
- pass 1:
- pass 2: ✅ sub-agents.md frontmatter — `tools` "comma-separated string such as `Read, Grep, Bash`"; `model` "`opus`"; `permissionMode` "`plan`" = "Plan mode (read-only exploration)"; `memory` "`project` ... Enables cross-session learning"

### C0155 · sub · L1 · p
> Other useful fields: skills (preload full skills), mcpServers, hooks, maxTurns, effort, isolation: worktree (work on its own copy of the repo), background: true. Put agents in .claude/agents/ (team) or ~/.claude/agents/ (you). The easiest way to write one: ask Claude to create it.
- pass 1:
- pass 2: ✅ sub-agents.md frontmatter table lists skills ("full skill content is injected"), mcpServers, hooks, maxTurns, effort, isolation ("`worktree` ... isolated copy of the repository"), background ("`true`"); scope table `.claude/agents/` / `~/.claude/agents/` "Ask Claude, or create the file manually"

### C0156 · sub · L1 · div
> Skill with context: fork vs subagent — what's the difference?
- pass 1:
- pass 2: n/a question heading

### C0157 · sub · L1 · div
> A skill is content (instructions); a subagent is a worker (a context with a role, tools and model). context: fork runs a skill's content inside a worker; a subagent's skills: field preloads content into a worker. They compose.
- pass 1:
- pass 2: ✅ skills.md "Skills and subagents work together in two directions" table — `context: fork`: task = SKILL.md content; subagent `skills` field: "Preloaded skills"

### C0158 · sub · L1 · div
> Can a subagent see my conversation?
- pass 1:
- pass 2: n/a question heading

### C0159 · sub · L1 · div
> A normal subagent sees only what the lead passes in the prompt (plus CLAUDE.md and git status, except Explore and Plan which skip them). A fork (/fork, /subtask) copies the whole conversation so far.
- pass 1:
- pass 2: ✅ sub-agents.md "What loads at startup" — "doesn't see your conversation history"; task message + CLAUDE.md + git status, "The built-in Explore and Plan agents skip this"; fork "inherits the entire conversation"; commands.md `/subtask`, `/fork` "Copy the current conversation"

### C0160 · sub · L1 · p
> You just finished a feature. Design an “adversarial review” step that doesn't share your session's blind spots.
- pass 1:
- pass 2: n/a exercise prompt

### C0161 · sub · L1 · p
> Spawn a fresh reviewer subagent (or a second session) that sees only the diff and the spec, not your conversation — it can't inherit the assumptions you made while building. Or run /code-review, which does exactly this; /code-review ultra runs a deep multi-agent review in the cloud.
- pass 1:
- pass 2: ✅ code-review.md — "The review runs as a background subagent with its own context window"; ultrareview.md — "Run a deep, multi-agent code review in the cloud with /code-review ultra"

### C0162 · sub · L1 · li
> Subagent = isolated context + role + tools + model. Returns a summary.
- pass 1:
- pass 2: ✅ sub-agents.md — own context window, system prompt, tools, model; "returns only the summary"

### C0163 · sub · L1 · li
> Use for research that reads a lot, parallel independent questions, and unbiased review.
- pass 1:
- pass 2: ✅ best-practices — "Delegate verbose operations to subagents"; sub-agents.md "Run parallel research"; best-practices "verification subagent ... fresh model" (advice)

### C0164 · sub · L1 · li
> Define in .claude/agents/*.md; restrict tools and permissionMode for safety.
- pass 1:
- pass 2: ✅ sub-agents.md — `.claude/agents/` scope; `tools` and `permissionMode` frontmatter fields
