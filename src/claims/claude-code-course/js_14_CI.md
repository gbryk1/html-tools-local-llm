# Claims ledger — claude-code-course.html — js_14_CI

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0423 · js:14. CI · L- · script
> 1 · Event — PR #57 “Add proration to invoices” opened
- pass 1:
- pass 2: n/a illustrative scenario (fake PR)

### C0424 · js:14. CI · L- · script
> 2 · .github/workflows/claude-review.yml- uses: anthropics/claude-code-action@v1 with: anthropic_api_key: \…} prompt: "Review this PR for bugs. Run the billing tests." claude_args: --permission-mode dontAsk…
- pass 1:
- pass 2: ✅ github-actions.md — "uses: anthropics/claude-code-action@v1", anthropic_api_key input, prompt, claude_args (truncated demo of C0212)

### C0425 · js:14. CI · L- · script
> A pull request triggers the workflow…
- pass 1:
- pass 2: ✅ github-actions.md — "a prompt to run automatically on any GitHub event"

### C0426 · js:14. CI · L- · script
> dontAsk mode + an exact allowlist: nothing can prompt (there is no human in CI), so anything not listed that would need approval is denied; reads and read-only commands still run.
- pass 1:
- pass 2: ✅ permission-modes.md "Allow only pre-approved tools with dontAsk mode" — "auto-denies every tool call that would otherwise prompt you. Claude still runs… file reads… and read-only Bash commands, plus actions matching your `permissions.allow` rules"

### C0427 · js:14. CI · L- · script
> dontAsk mode, but somebody deleted the allowlist…
- pass 1:
- pass 2: n/a illustrative scenario

### C0428 · js:14. CI · L- · script
> { "type": "result", "subtype": "success",\n "result": "1 bug: proration rounds per line, not per invoice (invoice.ts:88). Test added; 1 failing.",\n "total_cost_usd": 0.41, "session_id": "…" }\n→ written to the workflow run log (add a comment tool to post it on the PR)
- pass 1:
- pass 2: n/a — invented demo JSON result (illustrative); routing line confirmed by github-actions.md "Automation mode" — "By default, results appear in the workflow run log rather than a comment. Claude can post… when… it has a tool that can post"

### C0429 · js:14. CI · L- · script
> { "type": "result", "subtype": "success",\n "result": "Code looks correct (tests could not be run).",\n "total_cost_usd": 0.19, "session_id": "…" }\n→ written to the workflow run log 😬
- pass 1:
- pass 2: n/a — invented demo JSON result (illustrative); "written to the workflow run log" matches github-actions.md "Automation mode"

### C0430 · js:14. CI · L- · script
> Useful review. Claude could read and run exactly the tests it needed; the suspicious curl (maybe from prompt injection in a PR comment) was denied. Least privilege, no prompts.
- pass 1:
- pass 2: ✅ permission-modes.md dontAsk "auto-denies every tool call that would otherwise prompt"; curl isn't listed or read-only, so denied (injection scenario illustrative)

### C0431 · js:14. CI · L- · script
> Green but worthless. In dontAsk, reads still work, so the job “succeeds” — but tests never ran and the bug slipped through. A CI review is only as good as the tools you allow.
- pass 1:
- pass 2: ✅ permission-modes.md — dontAsk "Claude still runs … file reads … and read-only Bash commands"; unlisted npm test would prompt → denied

### C0432 · js:14. CI · L- · script
> The job runs in dontAsk mode: reads plus pre-approved tools only.
- pass 1:
- pass 2: ✅ permission-modes.md table — "`dontAsk` | Reads and pre-approved tools; anything that would prompt is denied"
