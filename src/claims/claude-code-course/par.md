# Claims ledger — claude-code-course.html — par

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0193 · par · L1 · p
> Once one session works well, the next bottleneck is you waiting. Claude Code has several ways to run more than one thing at once. The question that separates them: who holds the plan?
- pass 1:
- pass 2: n/a pedagogy intro — framing matches workflows.md "With subagents, skills, and agent teams, Claude is the orchestrator"

### C0194 · par · L1 · figcaption
> Availability varies: agent teams are experimental (CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1), routines and agent view are in research preview, dynamic workflows need a paid plan or API / cloud-provider access (on Pro, switch them on in /config).
- pass 1:
- pass 2: ✅ agent-teams.md — "experimental and disabled by default. Enable them by setting `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`"; routines.md/agent-view.md — "in research preview"; workflows.md — "available on all paid plans, with Anthropic API access, and on Amazon Bedrock, Google Cloud's Agent Platform, and Microsoft Foundry. On Pro, turn them on from the Dynamic workflows row in `/config`"

### C0195 · par · L1 · tr
> Subagents | “use subagents to…”, /subtask | Claude, turn by turn
- pass 1:
- pass 2: ✅ sub-agents.md/commands.md "/subtask … Spawn a forked subagent"; workflows.md "Claude is the orchestrator: it decides turn by turn what to spawn"

### C0196 · par · L1 · tr
> Worktrees | claude -w feature-auth — own checkout under .claude/worktrees/ | You, one session each
- pass 1:
- pass 2: ✅ cli-reference.md --worktree/-w — "Start Claude in an isolated git worktree at <repo>/.claude/worktrees/<name>"

### C0197 · par · L1 · tr
> Background sessions | /background, claude agents (agent view), Ctrl+B for tasks | You dispatch, check back later
- pass 1:
- pass 2: ✅ commands.md /background "Detach the current session to run as a background agent … Monitor the session with claude agents"; interactive-mode.md "Ctrl+B Background running tasks"

### C0198 · par · L1 · tr
> Agent teams | Lead + teammates with a shared task list and messaging | The lead agent
- pass 1:
- pass 2: ✅ agent-teams.md — "One session acts as the team lead…"; "shared task list"; "Teammates message each other directly"

### C0199 · par · L1 · tr
> Dynamic workflows | Ask for “a workflow” | A script Claude writes
- pass 1:
- pass 2: ✅ workflows.md "Ask for a workflow in your prompt" — "Asking in your own words, for example \"use a workflow\"… also works" (or keyword `ultracode`); "A script the runtime executes… Claude writes the script"

### C0200 · par · L1 · tr
> /batch | Bundled skill: splits a big change across subagents in their own worktrees | Claude, following the skill
- pass 1:
- pass 2: ✅ commands.md `/batch` — "**Skill.** … decomposes the work into 5 to 30 independent units"; agents.md — "`/batch` is a skill that has Claude split one large change into 5 to 30 worktree-isolated subagents"

### C0201 · par · L1 · tr
> /goal | “until all tests pass” — keeps taking turns until a checker says done | A completion condition
- pass 1:
- pass 2: ✅ goal.md — "After each turn, a small fast model checks whether the condition holds. If … not yet met, Claude starts another turn"

### C0202 · par · L1 · tr
> /loop | /loop 5m check the deploy — repeats while the session is open | A timer
- pass 1:
- pass 2: ✅ scheduled-tasks.md — "/loop … run a prompt on repeat while the session stays open"; "/loop 5m check the deploy"

### C0203 · par · L1 · tr
> Routines | /schedule — cloud runs on cron, API or GitHub events, laptop closed | A trigger
- pass 1:
- pass 2: ✅ routines.md — "run on a schedule, trigger on API calls, or react to GitHub events from cloud infrastructure"; "from the CLI with /schedule" (API trigger added on the web)

### C0204 · par · L1 · li
> claude -w search, claude -w billing-fix, claude -w docs in three terminal tabs — each gets its own branch and files.
- pass 1:
- pass 2: ✅ worktrees.md — "separate working directory with its own files and branch"; "-w with a name … on a new branch named worktree-<name>"

### C0205 · par · L1 · li
> Plan each in plan mode, approve, switch to auto or acceptEdits.
- pass 1:
- pass 2: ✅ permission-modes.md — plan "Exploring a codebase before changing it"; acceptEdits/auto modes exist and can be switched any time

### C0206 · par · L1 · li
> Set a Notification hook so you get pinged when one needs you; work the queue.
- pass 1:
- pass 2: ✅ hooks-guide.md — "add a Notification hook … so you get alerted whenever Claude is waiting for your input"

### C0207 · par · L1 · li
> Each session opens its own PR; review with /code-review in a fresh session.
- pass 1:
- pass 2: ✅ best-practices.md "A fresh context improves code review since Claude won't be biased toward code it just wrote"; /code-review is a bundled skill (PR opening is something you ask for)

### C0208 · par · L1 · p
> Parallel agents multiply review work, not only output. Two sessions editing the same files in one checkout will fight — isolate with worktrees. And more agents cost more tokens: agent teams in particular use a separate context per teammate.
- pass 1:
- pass 2: ✅ worktrees.md "edits in one session never touch files in another"; agent-teams.md "Each teammate has its own context window, and token usage scales with the number of active teammates"

### C0209 · par · L1 · li
> Side quest → subagent. Separate features → worktrees. Debate → agent team. Huge cross-checked fan-out → workflow; big mechanical change → /batch.
- pass 1:
- pass 2: ✅ consistent with agents.md/workflows.md comparisons (subagents for side tasks, worktrees for parallel sessions, agent teams for peers that debate, workflows for "cross-checked" fan-out of dozens–hundreds of agents, /batch for large changes); advice framing

### C0210 · par · L1 · li
> Keep going until done → /goal. Poll → /loop. Laptop closed → routine via /schedule.
- pass 1:
- pass 2: ✅ goal.md / scheduled-tasks.md "/loop … while the session stays open" / routines.md "from the CLI with /schedule"
