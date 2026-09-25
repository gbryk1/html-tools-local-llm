# Claims ledger — claude-code-course.html — expert

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0231 · expert · L1 · p
> Experts don't know secret commands. They build a setup over time, each piece triggered by a real annoyance, and they keep sessions clean. The official docs list the order most teams add things:
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "most teams add them in roughly this order"

### C0232 · expert · L1 · tr
> Claude gets a convention or command wrong twice | A line in CLAUDE.md
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "Claude gets a convention or command wrong twice | Add it to CLAUDE.md"

### C0233 · expert · L1 · tr
> You keep asking for shorter / more explained answers | An output style (/output-style)
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "keep asking Claude to be shorter, explain more… | Set an output style"; output-styles.md — "run `/output-style` to switch"

### C0234 · expert · L1 · tr
> You type the same starting prompt again | A user-invocable skill
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "keep typing the same prompt to start a task | Save it as a user-invocable skill"

### C0235 · expert · L1 · tr
> You paste the same playbook for the third time | A skill
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "paste the same playbook… for the third time | Capture it as a skill"

### C0236 · expert · L1 · tr
> You copy data from a browser tab Claude can't see | An MCP server
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "copying data from a browser tab Claude can't see | Connect that system as an MCP server"

### C0237 · expert · L1 · tr
> A side task floods the chat with output | A subagent
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "A side task floods your conversation with output… | Route it through a subagent"

### C0238 · expert · L1 · tr
> Something must happen every time | A hook
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "want something to happen every time without asking | Write a hook"

### C0239 · expert · L1 · tr
> A second repo needs the same setup | A plugin
- pass 1:
- pass 2: ✅ features-overview.md "Build your setup over time" table — "A second repository needs the same setup | Package it as a plugin"

### C0240 · expert · L1 · figcaption
> Your ticks are saved only in this browser (localStorage), never sent anywhere.
- pass 1:
- pass 2: n/a — describes the page's own checklist storage, not Claude Code

### C0241 · expert · L1 · li
> Start clean: one task per session, named (claude -n billing-bug).
- pass 1:
- pass 2: ✅ cli-reference.md `--name`, `-n` — "Set a display name for the session"; best-practices.md — "/clear between unrelated tasks"

### C0242 · expert · L1 · li
> Explore in plan mode with @ files; for big work, interview → SPEC.md.
- pass 1:
- pass 2: ✅ best-practices.md "Let Claude interview you" — "write a complete spec to SPEC.md"; "Reference files with `@`"; commands.md `/plan`

### C0243 · expert · L1 · li
> Give a finish line (test / command / screenshot); switch to acceptEdits or auto.
- pass 1:
- pass 2: ✅ best-practices.md — "Give Claude a check it can run: tests, a build, a screenshot"; permission-modes.md lists `acceptEdits`, `auto`

### C0244 · expert · L1 · li
> Steer early with Esc; rewind bad paths instead of arguing with them.
- pass 1:
- pass 2: ✅ best-practices.md "Course-correct early" — "`Esc`: stop Claude mid-action… `Esc + Esc` or `/rewind`"

### C0245 · expert · L1 · li
> Verify: tests, /diff, /code-review in a fresh context. Commit at green.
- pass 1:
- pass 2: ✅ commands.md `/diff` — "Review the changes in your working tree"; best-practices.md — "`/code-review` skill… reviews the current diff for bugs in a fresh subagent"

### C0246 · expert · L1 · li
> Harvest: turn the repeated correction into a CLAUDE.md line, skill or hook. /clear.
- pass 1:
- pass 2: ✅ features-overview.md — "A repeated mistake or a recurring review comment is a CLAUDE.md edit"; commands.md `/clear`

### C0247 · expert · L1 · li
> Grow your setup from real triggers; prune CLAUDE.md ruthlessly.
- pass 1:
- pass 2: ✅ features-overview.md — "Each feature has a recognizable trigger"; best-practices.md — "Ruthlessly prune"

### C0248 · expert · L1 · li
> Kitchen-sink sessions, endless corrections, bloated CLAUDE.md, no verification, unscoped exploration — the five killers.
- pass 1:
- pass 2: ✅ best-practices.md "Avoid common failure patterns" — kitchen sink session, correcting over and over, over-specified CLAUDE.md, trust-then-verify gap, infinite exploration

### C0249 · expert · L1 · li
> Always close the loop: something Claude can run to prove it's done.
- pass 1:
- pass 2: ✅ best-practices.md — "Give Claude a check it can run… you become the verification loop"
