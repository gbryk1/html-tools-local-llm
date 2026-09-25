# Claims ledger — claude-code-course.html — ci

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0211 · ci · L1 · p
> claude -p "prompt" runs one task non-interactively and prints the result. Everything you learned still applies — CLAUDE.md, skills, hooks, MCP — so it slots into scripts, pre-commit checks, and CI.
- pass 1:
- pass 2: ✅ headless.md — "Without [--bare], claude -p loads the same context an interactive session would" (CLAUDE.md, hooks, skills, MCP)

### C0212 · ci · L1 · pre
> # one-off, pipe in, JSON out git diff main | claude -p "review for bugs; reply as a list" --output-format json # structured output validated against a schema claude -p "list TODOs as JSON" --json-schema '{"type":"array","items":{"type":"string"}}' # locked down for CI: listed tools + reads only; anything that would prompt is denied claude -p "run the tests and fix failures" \ --permission-mode dontAsk --allowedTools "Read" "Edit" "Bash(npm test *)" \ --max-turns 20 --max-budget-usd 5 # fan out over files for f in $(git ls-files 'src/**/*.js'); do claude -p "migrate $f from CommonJS to ESM, keep behavior" --allowedTools "Read" "Edit" done
- pass 1:
- pass 2: ✅ round 4 (fresh verifier, executed in gittest): headless.md:92,132-138,158-161, cli-reference.md:65,102,103,110; array-root schema → API Error 400, object root works; loop tested with echo incl. spaces; stdin-consumption bug fixed with </dev/null (verifier simulation: all 4 files processed)

### C0213 · ci · L1 · pre
> - uses: anthropics/claude-code-action@v1 with: anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }} prompt: "Review this PR for bugs. Run the billing tests." claude_args: --permission-mode dontAsk --allowedTools "Read" "Bash(npm test *)"
- pass 1:
- pass 2: ✅ github-actions.md — "uses: anthropics/claude-code-action@v1"; "pass the secret to … anthropic_api_key"; prompt input = automation mode; "grant the tools … with --allowedTools in claude_args"

### C0214 · ci · L1 · figcaption
> Based on anthropics/claude-code-action@v1. Run /install-github-app once: it installs the app, adds the secret and opens a PR with the workflow files; after merging, @claude in an issue or PR comment triggers Claude too. A workflow with a prompt runs in automation mode and writes results to the run log unless Claude has a tool that can comment.
- pass 1:
- pass 2: ✅ round 4 (fresh verifier): github-actions.md:22,40,151,191 — "pushes a branch with the workflow files … pull request ready to create"; automation mode posts only "when the prompt directs it to and it has a tool that can post"

### C0215 · ci · L1 · p
> --output-format stream-json emits events as they happen (for dashboards and bots). --bare skips auto-discovery of hooks, skills, plugins, MCP and CLAUDE.md for reproducible scripts. --append-system-prompt adds instructions. -c -p continues a conversation in a script. For full control (tool approval callbacks, native objects) use the Agent SDK in Python or TypeScript — it is the same engine.
- pass 1:
- pass 2: ✅ headless.md "stream-json: newline-delimited JSON for real-time streaming"; cli-reference --bare "skip auto-discovery of hooks, skills, … plugins, MCP servers, auto memory, and CLAUDE.md"; --append-system-prompt; "claude -p … --continue"; headless.md "Agent SDK … tool approval callbacks, and native message objects"

### C0216 · ci · L1 · li
> -p + --output-format json|stream-json + --json-schema for machines.
- pass 1:
- pass 2: ✅ cli-reference.md — --output-format "text, json, stream-json"; --json-schema "(print mode only)"

### C0217 · ci · L1 · li
> CI: --permission-mode dontAsk + an exact --allowedTools list + --max-turns/--max-budget-usd.
- pass 1:
- pass 2: ✅ permission-modes.md — "Run in CI with an exact allowlist: claude -p … --permission-mode dontAsk --allowedTools …"; cli-reference --max-turns / --max-budget-usd

### C0218 · ci · L1 · li
> GitHub: /install-github-app; scheduled or event-driven cloud runs: routines.
- pass 1:
- pass 2: ✅ github-actions.md "Quick setup: run /install-github-app"; routines.md "run on a schedule, trigger on API calls, or react to GitHub events"
