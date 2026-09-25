# Claims ledger — claude-code-course.html — js_11_hooks

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0383 · js:11. hooks · L- · script
> SessionStart → inject “Sprint 42: billing migration, freeze on legacy/”
- pass 1:
- pass 2: ✅ hooks.md "Exit code 0" — SessionStart plain-text stdout "added as context" (sprint text illustrative)

### C0384 · js:11. hooks · L- · script
> PreToolUse Bash → block rm -rf outside the project (exit 2)
- pass 1:
- pass 2: ✅ hooks.md — "PreToolUse | Yes | Blocks the tool call" on exit 2 (scenario illustrative)

### C0385 · js:11. hooks · L- · script
> PostToolUse Edit|Write → run prettier on the file
- pass 1:
- pass 2: ✅ hooks-guide.md auto-format — PostToolUse with Edit|Write matcher running Prettier

### C0386 · js:11. hooks · L- · script
> Stop → desktop notification “Claude is done”
- pass 1:
- pass 2: ✅ hooks.md — Stop "When Claude finishes responding"; any command (notification) may run (scenario illustrative)

### C0387 · js:11. hooks · L- · script
> The turn: Claude edits a file, then tries rm -rf ./build ~/ (oops — a stray ~/).
- pass 1:
- pass 2: n/a illustrative scenario

### C0388 · js:11. hooks · L- · script
> 🪝 added context: "Sprint 42: billing migration, freeze on legacy/"
- pass 1:
- pass 2: n/a illustrative (consistent with SessionStart stdout-as-context)

### C0389 · js:11. hooks · L- · script
> ▸ UserPromptSubmit: "rename the build step and clean old output"
- pass 1:
- pass 2: n/a illustrative prompt

### C0390 · js:11. hooks · L- · script
> 🪝 block-dangerous.sh → exit 2: "refusing rm -rf outside the project: ~/"
- pass 1:
- pass 2: n/a illustrative (consistent with exit-2 stderr reason)

### C0391 · js:11. hooks · L- · script
> Blocked. Exit code 2 stopped the call, and stderr went back to Claude as the reason.
- pass 1:
- pass 2: ✅ hooks.md "Exit code 2" — "PreToolUse blocks the tool call"; blocking message is "your stderr text otherwise"

### C0392 · js:11. hooks · L- · script
> ⚙ rm -rf ./build ~/ 💥 your home directory is gone (simulated)
- pass 1:
- pass 2: n/a illustrative simulation

### C0393 · js:11. hooks · L- · script
> 🪝 🔔 notification: "Claude is done"
- pass 1:
- pass 2: n/a illustrative

### C0394 · js:11. hooks · L- · script
> The guard held. “Never delete outside the project” in CLAUDE.md would probably have worked. The hook always works — and Claude self-corrected from the reason.
- pass 1:
- pass 2: ✅ pedagogy consistent with hooks.md (exit 2 stderr goes to Claude as reason); self-correction is scenario n/a

### C0395 · js:11. hooks · L- · script
> No guard, no guarantee. A permission prompt might have saved you — unless you were in a permissive mode and clicked through. Turn the PreToolUse hook back on.
- pass 1:
- pass 2: ✅ permission-modes / hooks — permission prompts depend on mode; PreToolUse hook blocks regardless (opinion framing fine)
