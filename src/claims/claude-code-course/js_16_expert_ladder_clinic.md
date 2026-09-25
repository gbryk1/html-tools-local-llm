# Claims ledger — claude-code-course.html — js_16_expert_ladder_clinic

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0440 · js:16. expert ladder + clinic · L- · script
> I run claude inside a repo and ask it questions
- pass 1:
- pass 2: n/a — self-assessment rung (basic usage)

### C0441 · js:16. expert ladder + clinic · L- · script
> I interrupt with Esc and redirect early
- pass 1:
- pass 2: ✅ best-practices.md — "`Esc`: stop Claude mid-action… Context is preserved, so you can redirect"

### C0442 · js:16. expert ladder + clinic · L- · script
> I use plan mode for multi-file changes
- pass 1:
- pass 2: ✅ best-practices.md — "Planning is most useful… when the change modifies multiple files"

### C0443 · js:16. expert ladder + clinic · L- · script
> I always give Claude a test or command to verify
- pass 1:
- pass 2: ✅ best-practices.md — "Give Claude a check it can run"

### C0444 · js:16. expert ladder + clinic · L- · script
> I /clear between unrelated tasks
- pass 1:
- pass 2: ✅ best-practices.md — "Fix: `/clear` between unrelated tasks"

### C0445 · js:16. expert ladder + clinic · L- · script
> I have allow/ask/deny permission rules
- pass 1:
- pass 2: ✅ permissions.md — allow/ask/deny rules

### C0446 · js:16. expert ladder + clinic · L- · script
> My repeated playbooks are skills
- pass 1:
- pass 2: ✅ skills.md — "Create a skill when you keep pasting the same instructions… or multi-step procedure"

### C0447 · js:16. expert ladder + clinic · L- · script
> I delegate heavy research to subagents
- pass 1:
- pass 2: ✅ best-practices.md — "use subagents to keep research out of it"

### C0448 · js:16. expert ladder + clinic · L- · script
> I connected MCP servers I use daily
- pass 1:
- pass 2: n/a — self-assessment rung; MCP servers exist (mcp.md)

### C0449 · js:16. expert ladder + clinic · L- · script
> I run parallel sessions in worktrees
- pass 1:
- pass 2: ✅ worktrees.md — "Running each Claude Code session in its own worktree means edits in one session never touch files in another"

### C0450 · js:16. expert ladder + clinic · L- · script
> I use /goal, routines or workflows for long jobs
- pass 1:
- pass 2: ✅ goal.md, routines.md, workflows.md exist; commands.md `/goal`, `/schedule`

### C0451 · js:16. expert ladder + clinic · L- · script
> 🎓 All rungs. Now teach it: /team-onboarding drafts an onboarding guide from your usage history.
- pass 1:
- pass 2: ✅ commands.md `/team-onboarding` — "Generate a team onboarding guide from your Claude Code usage history"

### C0452 · js:16. expert ladder + clinic · L- · script
> One task, then an unrelated question, then back. Context full of irrelevant stuff. Fix: /clear between unrelated tasks; /btw for quick lookups.
- pass 1:
- pass 2: ✅ best-practices.md "Avoid common failure patterns" — kitchen sink "Fix: /clear between unrelated tasks"; best-practices.md — "use `/btw`. The answer never enters conversation history"

### C0453 · js:16. expert ladder + clinic · L- · script
> Wrong, corrected, still wrong, corrected again — context polluted with failed approaches. Fix: after two failed corrections, /clear and write a better first prompt with what you learned (or rewind).
- pass 1:
- pass 2: ✅ best-practices.md "Avoid common failure patterns" — "After two failed corrections, `/clear` and write a better initial prompt incorporating what you learned"; rewind in "Course-correct early"

### C0454 · js:16. expert ladder + clinic · L- · script
> So long that important rules get lost in the noise. Fix: prune ruthlessly; if Claude already does it right without the line, delete it or make it a hook.
- pass 1:
- pass 2: ✅ best-practices.md "Avoid common failure patterns" — "important rules get lost in the noise… Ruthlessly prune. If Claude already does something correctly without the instruction, delete it or convert it to a hook"

### C0455 · js:16. expert ladder + clinic · L- · script
> Plausible code that misses edge cases. Fix: always provide verification — tests, scripts, screenshots. If you can't verify it, don't ship it.
- pass 1:
- pass 2: ✅ best-practices.md "Avoid common failure patterns" — "Always provide verification (tests, scripts, screenshots). If you can't verify it, don't ship it"

### C0456 · js:16. expert ladder + clinic · L- · script
> “Investigate X” with no scope; Claude reads hundreds of files. Fix: scope narrowly, or send the investigation to subagents.
- pass 1:
- pass 2: ✅ best-practices.md "Avoid common failure patterns" — "Claude reads hundreds of files… Scope investigations narrowly or use subagents"
