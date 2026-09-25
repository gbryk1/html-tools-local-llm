# Claims ledger — claude-code-course.html — js_5_permissions

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0341 · js:5. permissions · L- · script
> Mode set to ……. Now send a call through.
- pass 1:
- pass 2: n/a UI narration

### C0342 · js:5. permissions · L- · script
> No rule matched, so the mode decides: manual mode asks for anything beyond reads.
- pass 1:
- pass 2: ✅ permission-modes.md mode table — "`default` | Reads only"

### C0343 · js:5. permissions · L- · script
> acceptEdits approves file edits in the working directory.
- pass 1:
- pass 2: ✅ permission-modes.md acceptEdits — "auto-approval applies only to paths inside your working directory or additionalDirectories"

### C0344 · js:5. permissions · L- · script
> acceptEdits also approves common filesystem commands (mkdir touch rm rmdir mv cp sed) inside the working directory. Yes, rm too — know it before you use this mode.
- pass 1:
- pass 2: ✅ permission-modes.md acceptEdits — "auto-approves common filesystem Bash commands: mkdir, touch, rm, rmdir, mv, cp, and sed"

### C0345 · js:5. permissions · L- · script
> Plan mode is for research: Claude reads and proposes a plan instead of changing files. Approve the plan to start editing.
- pass 1:
- pass 2: ✅ permission-modes.md plan — "Plan mode tells Claude to research and propose changes without making them ... edits stay blocked until you approve the plan"

### C0346 · js:5. permissions · L- · script
> Auto mode: a background classifier reviews the action in context. A build-folder delete inside the project passes; something destructive or off-task would be blocked.
- pass 1:
- pass 2: ✅ permission-modes.md auto — "A separate classifier model reviews actions before they run, blocking anything that escalates beyond your request" (scenario itself n/a)

### C0347 · js:5. permissions · L- · script
> dontAsk: anything that would prompt is denied. Only reads and pre-approved tools run — perfect for CI.
- pass 1:
- pass 2: ✅ permissions.md dontAsk — "Auto-denies every call that would otherwise prompt; file reads in your working directories ... still run, as do tools pre-approved"; mode table "Locked-down CI and scripts"

### C0348 · js:5. permissions · L- · script
> ⛔ denied — matched deny rule …. Deny is checked first; no mode and no allow rule can override it.
- pass 1:
- pass 2: ✅ permission-modes.md — "Deny rules block in every mode, including bypassPermissions"; permissions.md "An allow rule can't carve an exception out of a deny rule"

### C0349 · js:5. permissions · L- · script
> ⛔ denied — the ask rule wants a prompt, and dontAsk turns every prompt into a denial.
- pass 1:
- pass 2: ✅ permissions.md dontAsk — "Auto-denies every call that would otherwise prompt"

### C0350 · js:5. permissions · L- · script
> ❓ asks you — matched ask rule …. Ask rules prompt even in permissive modes: good for pushes and deploys.
- pass 1:
- pass 2: ✅ permission-modes.md — not auto-approved "in any mode, including bypassPermissions": "Tools matched by an explicit ask rule"

### C0351 · js:5. permissions · L- · script
> ✅ runs — matched allow rule …, in any mode. This is how you stop being asked about npm test 50 times a day.
- pass 1:
- pass 2: ✅ permissions.md — allow rules pre-approve after deny/ask checks; permission-modes.md "Allow rules have no effect in bypassPermissions" (call runs there anyway, so "runs" holds)

### C0352 · js:5. permissions · L- · script
> Pick a tool call to send it through the gate.
- pass 1:
- pass 2: n/a UI narration

### C0353 · js:5. permissions · L- · script
> Shift+Tab → …. (dontAsk is never in the cycle.)
- pass 1:
- pass 2: ✅ permission-modes.md — "dontAsk: never appears in the cycle"
