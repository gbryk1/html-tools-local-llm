# Claims ledger — claude-code-course.html — mem

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0048 · mem · L1 · p
> Each session starts blank — except for files Claude Code loads automatically. The main one is CLAUDE.md: plain markdown with build commands, conventions and “never do X” rules. Run /init once and Claude writes a first version by reading your repo. There are several levels, and they add up (they don't override each other):
- pass 1:
- pass 2: ✅ memory.md — "Each Claude Code session begins with a fresh context window"; "Run `/init` to generate a starting CLAUDE.md automatically"; "All discovered files are concatenated into context rather than overriding each other"

### C0049 · mem · L1 · tr
> Managed policy | /Library/Application Support/ClaudeCode/CLAUDE.md (macOS), /etc/claude-code/CLAUDE.md (Linux) | Company-wide rules set by IT
- pass 1:
- pass 2: ✅ memory.md "Choose where to put CLAUDE.md files" — "macOS: `/Library/Application Support/ClaudeCode/CLAUDE.md` • Linux and WSL: `/etc/claude-code/CLAUDE.md`"; "Organization-wide instructions managed by IT/DevOps"

### C0050 · mem · L1 · tr
> User | ~/.claude/CLAUDE.md | Your personal preferences, all projects
- pass 1:
- pass 2: ✅ memory.md table — "`~/.claude/CLAUDE.md` | Personal preferences for all projects"

### C0051 · mem · L1 · tr
> Project | ./CLAUDE.md or ./.claude/CLAUDE.md | Team conventions — commit it
- pass 1:
- pass 2: ✅ memory.md table — "`./CLAUDE.md` or `./.claude/CLAUDE.md` | Team-shared instructions ... Team members via source control"

### C0052 · mem · L1 · tr
> Local | ./CLAUDE.local.md | Your private notes for this repo — gitignore it
- pass 1:
- pass 2: ✅ memory.md table — "`./CLAUDE.local.md` | Personal project-specific preferences; add to `.gitignore`"

### C0053 · mem · L1 · tr
> Nested | packages/web/CLAUDE.md | Loaded lazily when Claude reads files in that folder
- pass 1:
- pass 2: ✅ memory.md "How CLAUDE.md files load" — "Instead of loading them at launch, they are included when Claude reads files in those subdirectories"

### C0054 · mem · L1 · tr
> Rules | .claude/rules/*.md with paths: globs | Load only when matching files are touched
- pass 1:
- pass 2: ✅ memory.md "Path-specific rules" — "Path-scoped rules trigger when Claude reads files matching the pattern"

### C0055 · mem · L1 · tr
> Auto memory | written by Claude per repo (MEMORY.md index) | Corrections and preferences Claude learned; first 200 lines / 25KB load each session
- pass 1:
- pass 2: ✅ memory.md "Auto memory" — "`MEMORY.md` # Index ... loaded into every session"; "Every session (first 200 lines or 25KB)"; "Per repository"; "corrections you give Claude"

### C0056 · mem · L1 · figcaption
> The adherence meter is a teaching device, not a measurement. The docs' guidance behind it is real: keep each CLAUDE.md under ~200 lines; longer files consume more context and reduce adherence.
- pass 1:
- pass 2: ✅ memory.md "Write effective instructions" — "target under 200 lines per CLAUDE.md file. Longer files consume more context and reduce adherence"

### C0057 · mem · L1 · p
> What goes in a good project CLAUDE.md? Only what Claude can't guess and will need in most sessions:
- pass 1:
- pass 2: ✅ best-practices.md — "Bash commands Claude can't guess"; "only include things that apply broadly"

### C0058 · mem · L1 · pre
> # Build & test - `pnpm dev` starts the app, `pnpm test -- path/to/file` runs one test file - Always run `pnpm typecheck` after changing types # Conventions - Use pnpm, never npm. ES modules only. - API handlers live in src/api/, one file per resource. See @docs/api-style.md # Gotchas - The `legacy/` folder is frozen. Never edit it. - When compacting, preserve the list of modified files and test commands.
- pass 1:
- pass 2: n/a (illustrative example file; the "When compacting, preserve..." line matches best-practices.md "When compacting, always preserve the full list of modified files and any test commands", @-import syntax per memory.md)

### C0059 · mem · L1 · p
> CLAUDE.md is advice, not enforcement. “Never edit .env” in CLAUDE.md usually works; a deny permission rule (chapter 5) or a PreToolUse hook (chapter 11) always works. If a rule must hold every time, don't write it as prose.
- pass 1:
- pass 2: ✅ best-practices.md — "Unlike CLAUDE.md instructions which are advisory, hooks are deterministic"; memory.md — "To block an action regardless of what Claude decides, use a PreToolUse hook"

### C0060 · mem · L1 · div
> My repo already has an AGENTS.md for other tools. Duplicate it?
- pass 1:
- pass 2: n/a (question)

### C0061 · mem · L1 · div
> No. Claude Code can read AGENTS.md on its own or alongside CLAUDE.md, or you can import it from CLAUDE.md with @AGENTS.md. Imports work with relative and absolute paths, up to four hops deep.
- pass 1:
- pass 2: ✅ memory.md intro + "Import additional files" — "Claude can also read a repository's AGENTS.md files, on their own or alongside CLAUDE.md"; "Both relative and absolute paths are allowed"; "maximum depth of four hops" (note: default reads AGENTS.md only when no CLAUDE.md exists; "alongside" needs the Project instructions setting — acceptable simplification)

### C0062 · mem · L1 · div
> How do I see or edit what's loaded?
- pass 1:
- pass 2: n/a (question)

### C0063 · mem · L1 · div
> /memory lists the loaded files, opens them in your editor, and toggles auto memory. /context shows how many tokens they cost.
- pass 1:
- pass 2: ✅ memory.md — "The `/memory` command lists your CLAUDE.md, CLAUDE.local.md, and other memory file locations ... toggle auto memory ... Select any file to open it in your editor"; "run `/context` ... check the list under Memory files"

### C0064 · mem · L1 · li
> Levels add up: managed + user + project + local + nested + rules + auto memory.
- pass 1:
- pass 2: ✅ memory.md — "concatenated into context rather than overriding each other" (nested/rules/auto memory each add per their own load rules)

### C0065 · mem · L1 · li
> Keep each CLAUDE.md short (<200 lines). Move procedures to skills, folder-specific rules to .claude/rules/.
- pass 1:
- pass 2: ✅ memory.md — "target under 200 lines"; "If an entry is a multi-step procedure or only matters for one part of the codebase, move it to a skill or a path-scoped rule"

### C0066 · mem · L1 · li
> A mistake Claude makes twice → one line in CLAUDE.md. A rule that must never break → hook or deny rule.
- pass 1:
- pass 2: ✅ memory.md "When to add to CLAUDE.md" — "Claude makes the same mistake a second time"; best-practices.md — "Use hooks for actions that must happen every time with zero exceptions"
