# Claims ledger — claude-code-course.html — perm

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0067 · perm · L1 · p
> Every tool call passes a gate. Two things decide the outcome: your permission rules (explicit allow / ask / deny lists) and the session's permission mode (the default behavior for anything no rule matches).
- pass 1:
- pass 2: ✅ permission-modes.md intro — "Modes set the baseline. Layer permission rules on top to pre-approve or block specific tools."

### C0068 · perm · L1 · tr
> default (manual) | Reads only | Sensitive work, learning what Claude does
- pass 1:
- pass 2: ✅ permission-modes.md mode table — "`default` | Reads only | Reviewing every action yourself, sensitive work"

### C0069 · perm · L1 · tr
> acceptEdits | Reads, file edits, and common filesystem commands (mkdir, touch, rm, rmdir, mv, cp, sed) inside the working directories | Iterating on code you review in git
- pass 1:
- pass 2: ✅ permission-modes.md acceptEdits — "auto-approves common filesystem Bash commands: mkdir, touch, rm, rmdir, mv, cp, and sed ... only to paths inside your working directory or additionalDirectories"

### C0070 · perm · L1 · tr
> plan | Reads (research only, no edits) | Exploring and designing before changing
- pass 1:
- pass 2: ✅ permission-modes.md mode table — "`plan` | Reads, plus classifier-approved commands when auto mode is available | Exploring a codebase before changing it" (minor simplification)

### C0071 · perm · L1 · tr
> auto | Everything, with a background safety classifier | Long tasks, less prompt fatigue
- pass 1:
- pass 2: ✅ permission-modes.md mode table — "`auto` | Everything, with background safety checks | Long tasks, reducing prompt fatigue"

### C0072 · perm · L1 · tr
> dontAsk | Reads and pre-approved tools; anything that would prompt is denied | Locked-down CI and scripts
- pass 1:
- pass 2: ✅ permission-modes.md mode table — "`dontAsk` | Reads and pre-approved tools; anything that would prompt is denied | Locked-down CI and scripts"

### C0073 · perm · L1 · tr
> bypassPermissions | Everything, no checks | Isolated containers / VMs only
- pass 1:
- pass 2: ✅ permission-modes.md mode table — "`bypassPermissions` | Everything | Isolated containers and VMs only" (deny rules still apply)

### C0074 · perm · L1 · p
> Shift+Tab cycles default → acceptEdits → plan, and optional modes you have enabled slot in after plan. dontAsk is never in the cycle; start it with --permission-mode dontAsk. Rules live in settings.json under permissions and are checked in a fixed order: deny, then ask, then allow. First match wins; specificity does not matter.
- pass 1:
- pass 2: ✅ permission-modes.md Switch modes + permissions.md — "cycle then runs default → acceptEdits → plan ... Optional modes slot in after plan"; "dontAsk: never appears in the cycle; set it with --permission-mode dontAsk"; "evaluated in order: deny, then ask, then allow ... rule specificity doesn't change the order"

### C0075 · perm · L1 · figcaption
> Simplified: the real auto classifier sees your messages and Claude's actions (not tool output), and writes to protected paths (like .git) have their own rules. Rule syntax is real — try it in /permissions.
- pass 1:
- pass 2: ✅ permission-modes.md "How the classifier evaluates actions" — "the classifier sees user messages, tool calls… and your CLAUDE.md content. Tool results are stripped"; "Protected paths" — "Writes to a small set of paths are never auto-approved… `auto` | Routed to the classifier"

### C0076 · perm · L1 · pre
> // .claude/settings.json (shared with the team — commit it) { "permissions": { "allow": ["Bash(npm run *)", "Bash(git commit *)"], "ask": ["Bash(git push *)"], "deny": ["Read(./.env)", "Read(./secrets/**)", "Bash(curl *)"] } }
- pass 1:
- pass 2: ✅ permissions.md — "Bash(git commit *)", "Bash(git push *)", "Read(./.env) or Read(./secrets/**)"; settings.md — "Commit .claude/settings.json so everyone who clones the repository gets the same permissions"

### C0077 · perm · L1 · p
> Settings come in layers too. For a single key the higher layer wins — but list keys such as permissions.allow and deny are merged across layers: managed policy > command-line flags (--settings) > .claude/settings.local.json (you, this project) > .claude/settings.json (team) > ~/.claude/settings.json (you, everywhere). Not sure where a key belongs? Ask: /update-config allow npm test — or run /fewer-permission-prompts, which scans your history and proposes an allowlist of safe read-only commands.
- pass 1:
- pass 2: ✅ settings.md "Settings precedence" — managed > "Command line arguments" (`--settings`) > `.claude/settings.local.json` > `.claude/settings.json` > `~/.claude/settings.json`; "Lists merge instead of overriding… such as `permissions.allow`"; commands.md `/update-config [request]` and `/fewer-permission-prompts` "Scan your transcripts for common read-only Bash and MCP tool calls, then add a prioritized allowlist"

### C0078 · perm · L1 · p
> An allow rule can't carve an exception out of a deny rule. With deny: Bash(aws *), allow: Bash(aws s3 ls) never fires. And put the * after the subcommand: Bash(git log *) allows only git log …; Bash(git *) allows git push --force too. --dangerously-skip-permissions belongs in a throwaway container, never on your laptop.
- pass 1:
- pass 2: ✅ permissions.md — "An allow rule can't carve an exception out of a deny rule"; "Bash(git log *) allows only git log commands, and Bash(git *) allows every git command"; permission-modes.md — "Run fully unattended inside a container ... --dangerously-skip-permissions"

### C0079 · perm · L1 · p
> For fewer prompts and real safety on your machine, try the Bash sandbox: /sandbox runs shell commands with OS-level filesystem and network isolation (macOS, Linux, WSL2), and its auto-allow mode lets sandboxed commands run without asking. The sandbox limits what a command can do; permissions limit what Claude may try. Defense in depth uses both.
- pass 1:
- pass 2: ✅ sandboxing.md — "runs on macOS, Linux, and WSL2"; "Auto-allow runs sandboxed commands without prompting"; "Sandboxing, permission rules, and permission modes are complementary layers"

### C0080 · perm · L1 · li
> Rules: deny → ask → allow, first match wins. Mode decides everything no rule matched.
- pass 1:
- pass 2: ✅ permissions.md — "Rules are evaluated in order: deny, then ask, then allow. The first match in that order determines the outcome"

### C0081 · perm · L1 · li
> Learn in default, iterate in acceptEdits, design in plan, go long in auto, script in dontAsk.
- pass 1:
- pass 2: n/a advice; mode "best for" column in permission-modes.md is consistent

### C0082 · perm · L1 · li
> Team rules in .claude/settings.json, personal ones in settings.local.json.
- pass 1:
- pass 2: ✅ settings.md — "Commit .claude/settings.json ... Each teammate can still override it for themselves in their own .claude/settings.local.json"
