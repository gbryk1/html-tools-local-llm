# Claims ledger — claude-code-course.html — term

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0016 · term · L1 · p
> Install with the native installer and start it inside a project directory:
- pass 1:
- pass 2: ✅ quickstart.md/setup.md — native install via install.sh / install.ps1, then run `claude` in a project directory

### C0017 · term · L1 · pre
> # macOS, Linux, WSL curl -fsSL https://claude.ai/install.sh | bash # Windows PowerShell irm https://claude.ai/install.ps1 | iex cd my-project claude # interactive session claude "explain the auth flow" # start with a prompt claude -c # continue the latest conversation in this directory claude -r # pick an older session to resume
- pass 1:
- pass 2: ✅ quickstart.md — "macOS, Linux, WSL: curl -fsSL https://claude.ai/install.sh | bash", "Windows PowerShell: irm https://claude.ai/install.ps1 | iex"; cli-reference.md — `claude "query"` "Start interactive session with initial prompt", `claude -c` "Continue most recent conversation in current directory", `--resume, -r` "...or show an interactive picker to choose a session"

### C0018 · term · L1 · p
> The same engine runs in several surfaces: the terminal CLI, VS Code and JetBrains extensions, the Desktop app, the web at claude.ai/code (cloud sessions in a sandbox), the mobile app, and Slack. They share your repo's CLAUDE.md files, settings and MCP servers. With a claude.ai subscription you can move a session between them: /desktop hands a terminal session to the Desktop app, --teleport pulls a cloud session into your terminal, and /remote-control lets you steer a local session from your phone.
- pass 1:
- pass 2: ✅ platforms.md — "Claude Code runs the same underlying engine everywhere" (CLI, Desktop, VS Code, JetBrains, Web, Mobile, Slack); cloud-environments.md — repo `CLAUDE.md`, `.claude/settings.json`, `.mcp.json` load in cloud sessions; commands.md `/desktop` "Continue the current session in the Claude Code Desktop app… Claude subscription"; cli-reference `--teleport` "Resume a cloud session in your local terminal" (requires claude.ai subscription); remote-control.md `/remote-control` drive a local session from phone/browser

### C0019 · term · L1 · p
> Inside the prompt, a few characters change what you type into something else. Learn these and you already use Claude Code better than most people:
- pass 1:
- pass 2: n/a pedagogy/intro

### C0020 · term · L1 · figcaption
> Output is abbreviated. In a real session / shows every built-in command, bundled skill and your own skills, filtered as you type.
- pass 1:
- pass 2: ✅ commands.md — "Complete reference for commands ... including built-in commands and bundled skills"; "Claude Code filters the `/` menu as you type" (a few hidden commands like /heapdump are omitted by design — negligible)

### C0021 · term · L1 · tr
> Esc | Interrupt the current step | Claude heads the wrong way. Do it early.
- pass 1:
- pass 2: ✅ interactive-mode.md — Esc "Stop the current response or tool call mid-turn so you can redirect"

### C0022 · term · L1 · tr
> Esc Esc | Clear the draft, or on empty input open the rewind menu | Undo the last few prompts (chapter 8)
- pass 1:
- pass 2: ✅ interactive-mode.md `Esc` + `Esc` — "When the prompt input contains text, double Esc clears it ... When the input is empty, double Esc opens the rewind menu"

### C0023 · term · L1 · tr
> Shift+Tab | Cycle permission modes | Switch to plan mode or accept-edits (chapter 5)
- pass 1:
- pass 2: ✅ interactive-mode.md Shift+Tab — "Cycle permission modes ... default (labeled Manual), acceptEdits, plan"

### C0024 · term · L1 · tr
> Ctrl+G | Open the prompt (or plan) in your editor | Long prompts, editing a plan
- pass 1:
- pass 2: ✅ interactive-mode.md — "`Ctrl+G` or `Ctrl+X Ctrl+E` | Open in default text editor"; permission-modes.md — "Press `Ctrl+G` to open the plan in your text editor"

### C0025 · term · L1 · tr
> Ctrl+B | Send running tasks to the background | A long build/test you don't want to wait on
- pass 1:
- pass 2: ✅ interactive-mode.md — "`Ctrl+B` | Background running tasks | Backgrounds Bash commands and agents"

### C0026 · term · L1 · tr
> Ctrl+O | Transcript viewer | See every tool call in detail
- pass 1:
- pass 2: ✅ interactive-mode.md — "`Ctrl+O` | Toggle transcript viewer | Shows detailed tool usage and execution"

### C0027 · term · L1 · tr
> Ctrl+T | Toggle Claude's task checklist | Track progress of a multi-step job
- pass 1:
- pass 2: ✅ interactive-mode.md — "`Ctrl+T` | Toggle Claude's task checklist"

### C0028 · term · L1 · tr
> Ctrl+V | Paste an image | Screenshots of bugs, mockups to implement
- pass 1:
- pass 2: ✅ interactive-mode.md — "`Ctrl+V` or `Cmd+V` (iTerm2) or `Alt+V` (Windows and WSL) | Paste image from clipboard"

### C0029 · term · L1 · tr
> Option/Alt+P · +T · +O | Switch model · toggle thinking · toggle fast mode | Chapter 15
- pass 1:
- pass 2: ✅ interactive-mode.md — "Option+P (macOS) or Alt+P | Switch model", "Option+T ... Toggle extended thinking", "Option+O ... Toggle fast mode"

### C0030 · term · L1 · p
> You want Claude to look at the output of git log --oneline -20 and summarize what changed this week. What is the fastest way that doesn't make Claude ask for permission to run git?
- pass 1:
- pass 2: n/a quiz question

### C0031 · term · L1 · p
> Type ! git log --oneline -20. The ! prefix runs the command yourself, adds its output to the conversation, and Claude responds to it. No permission prompt, because you ran it.
- pass 1:
- pass 2: ✅ interactive-mode.md 'Shell mode with ! prefix' — "Adds the command and its output to the conversation context", "Doesn't require Claude to interpret or approve the command", "Claude responds to the command output automatically"

### C0032 · term · L1 · li
> / commands & skills, @ file mention, ! shell, Esc stop, Esc Esc rewind, Shift+Tab mode.
- pass 1:
- pass 2: ✅ interactive-mode.md — "`/` at start | Command or skill", "`@` | File path mention", "`!` at start | Shell mode", Esc / Esc+Esc rewind / Shift+Tab rows

### C0033 · term · L1 · li
> claude -c continues, claude -r resumes; name sessions with /rename or -n.
- pass 1:
- pass 2: ✅ cli-reference.md — `-c` "Continue most recent conversation", `--resume, -r` "Resume a specific session", `--name, -n` "Set a display name for the session"; commands.md — "`/rename [name]` Rename the current session"

### C0034 · term · L1 · li
> One engine, many surfaces — sessions can move between terminal, desktop, web and phone.
- pass 1:
- pass 2: ✅ overview.md — "Sessions aren't tied to a single surface. Move work between them" (Remote Control, --teleport, /desktop)
