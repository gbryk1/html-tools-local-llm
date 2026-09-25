# Claims ledger — claude-code-course.html — hooks

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0165 · hooks · L1 · p
> Everything so far is advice the model interprets. A hook is different: Claude Code itself runs your shell command (or HTTP call, MCP tool, prompt, or subagent) when a lifecycle event fires. It always runs. It can block actions, inject context, or just log. Configure hooks in settings.json; /hooks lets you browse them (read-only).
- pass 1:
- pass 2: ✅ hooks.md handler fields — `type` "`command`, `http`, `mcp_tool`, `prompt`, or `agent`"; hooks-guide.md — "The `/hooks` menu is read-only. To add, modify, or remove hooks, edit your settings JSON"; exit 2 blocks, `additionalContext` injects context

### C0166 · hooks · L1 · pre
> { "hooks": { "PreToolUse": [{ "matcher": "Bash", "hooks": [{ "type": "command", "command": "\"$CLAUDE_PROJECT_DIR\"/.claude/hooks/block-dangerous.sh" }] }], "PostToolUse": [{ "matcher": "Edit|Write", "hooks": [{ "type": "command", "command": "npx prettier --write \"$(jq -r .tool_input.file_path)\"" }] }] } }
- pass 1:
- pass 2: ✅ hooks-guide.md block-rm-rf / auto-format examples — "\"$CLAUDE_PROJECT_DIR\"/.claude/hooks/..." and "jq -r '.tool_input.file_path' | xargs npx prettier --write" (page variant reads stdin via $(jq ...), equivalent)

### C0167 · hooks · L1 · p
> The hook gets a JSON payload on stdin (tool name, input, session info). Exit code 0 = go on; exit code 2 = block, and stderr goes back as the reason (for PreToolUse, Claude reads it and adjusts). For finer control, print JSON with a decision.
- pass 1:
- pass 2: ✅ hooks.md "Exit code 2" — "The blocking message is the reason from your JSON's blocking decision when it makes one, and your stderr text otherwise ... PreToolUse blocks the tool call"; "Command hooks receive JSON data via stdin"

### C0168 · hooks · L1 · figcaption
> Simplified to the main events. The full list also has PermissionRequest, PostToolUseFailure, SubagentStart/Stop, PreCompact/PostCompact, Notification, FileChanged, CwdChanged, WorktreeCreate and more.
- pass 1:
- pass 2: ✅ hooks.md event table — PermissionRequest, PostToolUseFailure, SubagentStart/Stop, PreCompact/PostCompact, Notification, FileChanged, CwdChanged, WorktreeCreate all listed

### C0169 · hooks · L1 · tr
> SessionStart | Inject context: current sprint, open issues, env setup
- pass 1:
- pass 2: ✅ hooks.md "Exit code 0" — "UserPromptSubmit, UserPromptExpansion, SessionStart ... adds plain-text stdout as context"; CLAUDE_ENV_FILE "available for SessionStart"

### C0170 · hooks · L1 · tr
> UserPromptSubmit | Add context or reject prompts (e.g. leaked secrets)
- pass 1:
- pass 2: ✅ hooks.md UserPromptSubmit — "add additional context based on the prompt/conversation, validate prompts, or block certain types of prompts"

### C0171 · hooks · L1 · tr
> PreToolUse | Block dangerous commands, protect files, enforce rules
- pass 1:
- pass 2: ✅ hooks.md exit-2 table — "PreToolUse | Yes | Blocks the tool call"; hooks-guide "Prevent Claude from modifying sensitive files"

### C0172 · hooks · L1 · tr
> PermissionRequest | Auto-approve or deny a permission prompt by policy
- pass 1:
- pass 2: ✅ hooks.md — "PermissionRequest | When a tool call needs a permission decision"; deny/allow "through the decision object"

### C0173 · hooks · L1 · tr
> PostToolUse | Format, lint, typecheck after edits — exit 2 (stderr) or JSON additionalContext feeds problems back to Claude
- pass 1:
- pass 2: ✅ hooks.md "Exit code 2 behavior per event" — "`PostToolUse` | No | Shows stderr to Claude; the tool already ran"; "additionalContext" supported for PostToolUse; hooks-guide.md — format files after edits

### C0174 · hooks · L1 · tr
> Stop | Run tests before Claude may finish; notify you
- pass 1:
- pass 2: ✅ hooks.md exit-2 table — "Stop | Yes | Prevents Claude from stopping, continues the conversation"; any command (e.g. notify) can run

### C0175 · hooks · L1 · tr
> Notification | Desktop / phone ping when Claude waits for input
- pass 1:
- pass 2: ✅ hooks-guide.md — "Notification event, which Claude Code fires when Claude is waiting for input or permission" (osascript/notify-send examples)

### C0176 · hooks · L1 · tr
> PreCompact | Save a transcript backup before compaction
- pass 1:
- pass 2: ✅ hooks.md PreCompact — "Runs before Claude Code is about to run a compact operation"; common input includes transcript_path (backup is a plausible use)

### C0177 · hooks · L1 · tr
> SessionEnd | Cleanup, logging, metrics
- pass 1:
- pass 2: ✅ hooks.md SessionEnd — "Useful for cleanup tasks, logging session statistics"

### C0178 · hooks · L1 · p
> Hooks run with your user's permissions, automatically, on every matching event. Review any hook you copy (and any plugin that ships hooks) like you'd review a script you pipe into bash. Quote variables, use absolute paths via $CLAUDE_PROJECT_DIR, and keep them fast — a slow PostToolUse hook slows every edit.
- pass 1:
- pass 2: ✅ hooks.md "Security considerations" — "Command hooks execute shell commands with your full user permissions ... Review and test all hook commands"; "Always quote shell variables"; "Use absolute paths"; plugins ship hooks/hooks.json

### C0179 · hooks · L1 · li
> Hook = deterministic code on a lifecycle event. CLAUDE.md = a request; hook = a guarantee.
- pass 1:
- pass 2: ✅ hooks-guide.md intro — hooks run code at lifecycle points deterministically (pedagogical contrast with CLAUDE.md)

### C0180 · hooks · L1 · li
> Exit 2 blocks (PreToolUse) and stderr becomes Claude's feedback; JSON output can add context. Plain stdout of most events goes only to the debug log.
- pass 1:
- pass 2: ✅ hooks.md "Exit code 2" — "`PreToolUse` blocks the tool call"; blocking message is "your stderr text"; "For most events, Claude Code writes stdout to the debug log and doesn't show it in the transcript" (exceptions UserPromptSubmit, SessionStart…)

### C0181 · hooks · L1 · li
> Best starter hooks: format after edit, block dangerous Bash, notify when waiting.
- pass 1:
- pass 2: n/a advice; matches hooks-guide.md — "format files after edits, block commands before they execute, send notifications when Claude needs input"
