# Claims ledger — claude-code-course.html — final

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0250 · final · L1 · p
> 14 questions. Each tests a mechanism from the chapters, not just a command name.
- pass 1:
- pass 2: n/a — page structure

### C0251 · final · L1 · tr
> claude -c / -r / -n | Continue / resume / name a session | Picking work back up
- pass 1:
- pass 2: ✅ cli-reference.md — "`--continue`, `-c`", "`--resume`, `-r`", "`--name`, `-n`"

### C0252 · final · L1 · tr
> /init, CLAUDE.md | Project memory loaded every session | Build commands, conventions (<200 lines)
- pass 1:
- pass 2: ✅ commands.md `/init` — "Initialize project with a CLAUDE.md guide"; memory.md — "target under 200 lines per CLAUDE.md file"

### C0253 · final · L1 · tr
> .claude/rules/*.md | Rules scoped with paths: globs | Folder- or language-specific guidance
- pass 1:
- pass 2: ✅ memory.md "Organize rules with .claude/rules/" — "Rules can also be scoped to specific file paths" via `paths:` frontmatter

### C0254 · final · L1 · tr
> /memory | Edit loaded memory, toggle auto memory | Checking what Claude “knows”
- pass 1:
- pass 2: ✅ commands.md `/memory` — "Edit CLAUDE.md files, enable or disable auto memory, and view auto memory entries"

### C0255 · final · L1 · tr
> Shift+Tab, /plan | Cycle modes / enter plan mode | Explore before editing
- pass 1:
- pass 2: ✅ interactive-mode.md — "`Shift+Tab` … Cycle permission modes"; commands.md `/plan` — "Enter plan mode directly from the prompt"

### C0256 · final · L1 · tr
> --permission-mode | default · acceptEdits · plan · auto · dontAsk · bypassPermissions | Choosing autonomy
- pass 1:
- pass 2: ✅ permission-modes.md mode table — `default` (Manual), `acceptEdits`, `plan`, `auto`, `dontAsk`, `bypassPermissions`; "`claude --permission-mode …`"

### C0257 · final · L1 · tr
> /permissions | allow / ask / deny rules (deny → ask → allow) | Fewer prompts, hard limits
- pass 1:
- pass 2: ✅ commands.md `/permissions` — "Manage allow, ask, and deny rules"; permissions.md — "evaluated in order: deny, then ask, then allow"

### C0258 · final · L1 · tr
> /sandbox | OS-level isolation for Bash | Safer autonomy on your machine
- pass 1:
- pass 2: ✅ commands.md `/sandbox` — "Toggle sandbox mode"; sandboxing.md "OS-level enforcement"

### C0259 · final · L1 · tr
> /context, /usage | Context grid / cost and limits | Sessions getting slow or pricey
- pass 1:
- pass 2: ✅ commands.md `/context` — "Visualize current context usage as a colored grid"; `/usage` — "Show session cost, plan usage limits"

### C0260 · final · L1 · tr
> /clear, /compact [focus] | Reset / summarize context | Between tasks / long tasks
- pass 1:
- pass 2: ✅ commands.md `/clear` — "Start a new conversation with empty context"; `/compact [instructions]` — "summarizing… Optionally pass focus instructions"

### C0261 · final · L1 · tr
> /btw | Side question, not added to history | Quick lookups mid-task
- pass 1:
- pass 2: ✅ commands.md `/btw` — "Ask a side question… without adding to the conversation"

### C0262 · final · L1 · tr
> Esc · Esc Esc · /rewind | Interrupt · rewind code/conversation | Wrong direction, failed experiment
- pass 1:
- pass 2: ✅ best-practices.md — "`Esc`: stop Claude mid-action"; "`Esc + Esc` or `/rewind`… restore previous conversation and code state"

### C0263 · final · L1 · tr
> @file, !cmd, Ctrl+V | Mention file · run shell · paste image | Giving precise context
- pass 1:
- pass 2: ✅ interactive-mode.md — "`@` File path mention", "`!` at start | Shell mode", "`Ctrl+V` … Paste image from clipboard" (Cmd+V in iTerm2, Alt+V on Windows)

### C0264 · final · L1 · tr
> .claude/skills/x/SKILL.md | Reusable skill, /x | Repeated playbooks
- pass 1:
- pass 2: ✅ skills.md — project skills at `.claude/skills/<name>/SKILL.md`, invoked with `/name`

### C0265 · final · L1 · tr
> .claude/agents/x.md | Custom subagent | Isolated research, reviews, roles
- pass 1:
- pass 2: ✅ sub-agents.md — project subagents in `.claude/agents/`; "runs in its own context window"

### C0266 · final · L1 · tr
> settings.json → hooks | Code on lifecycle events; exit 2 blocks | Must-always rules, formatting, alerts
- pass 1:
- pass 2: ✅ hooks.md "Exit code 2" (blocks for blocking events such as PreToolUse); features-overview.md — "A PreToolUse hook that blocks the edit is enforcement"

### C0267 · final · L1 · tr
> claude mcp add, /mcp, .mcp.json | External tools (local > project > user) | GitHub, DBs, browsers, trackers
- pass 1:
- pass 2: ✅ mcp.md "Scope hierarchy and precedence" — "1. Local scope 2. Project scope 3. User scope"; `claude mcp add`, `/mcp`, `.mcp.json`

### C0268 · final · L1 · tr
> /plugin | Install bundles from marketplaces | Sharing a setup across repos
- pass 1:
- pass 2: ✅ commands.md `/plugin` — "Manage Claude Code plugins… `install`"; plugins install from marketplaces

### C0269 · final · L1 · tr
> claude -w name | Session in its own git worktree | Parallel features
- pass 1:
- pass 2: ✅ cli-reference.md `--worktree`, `-w` — "Start Claude in an isolated git worktree"

### C0270 · final · L1 · tr
> /goal · /loop · /schedule | Until done · on interval · cloud routine | Long or recurring work
- pass 1:
- pass 2: ✅ commands.md `/goal` — "keeps working across turns until the condition is met"; `/loop [interval]`; `/schedule` — "routines, which execute in the cloud"

### C0271 · final · L1 · tr
> claude -p … --output-format json | Headless run | Scripts, CI, pipes
- pass 1:
- pass 2: ✅ cli-reference.md `--print`, `-p`; `--output-format` — "options: text, json, stream-json"

### C0272 · final · L1 · tr
> /model · /effort · /fast | Brain · thinking depth · faster output | Hard vs routine tasks
- pass 1:
- pass 2: ✅ commands.md `/model` — "Switch the AI model"; `/effort` — "Set the effort level"; `/fast` — "Toggle fast mode"

### C0273 · final · L1 · tr
> /code-review [ultra] | Review diff / deep cloud multi-agent review | Before merging
- pass 1:
- pass 2: ✅ commands.md `/code-review` — "Review the current diff… or `ultra` to run a deep cloud review"

### C0274 · final · L1 · tr
> /doctor, /release-notes | Diagnose setup / what changed | Something looks off
- pass 1:
- pass 2: ✅ commands.md `/doctor` — "setup checkup that diagnoses issues"; `/release-notes` — "View the changelog"

### C0275 · final · L1 · p
> You went from “what is an agent” through context, memory, permissions, planning, prompting and rewind, to skills, subagents, hooks, MCP, parallel sessions, CI and model choice. Look at the worry list you wrote in chapter 0: wrong edits (plan mode, verification, rewind), deleted files (permissions, sandbox, hooks, git), forgetting (CLAUDE.md, auto memory, specs), bills (context hygiene, effort, budgets). Next step: pick one annoyance from this week and add exactly one piece of setup that removes it. Repeat weekly.
- pass 1:
- pass 2: n/a — recap/advice; referenced mechanisms all exist in docs
