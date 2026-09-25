# Claims ledger — claude-code-course.html — js_12_MCP

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0396 · js:12. MCP · L- · script
> .mcp.json (commit it; teammates approve on first use)\n{ "mcpServers": { "…": { "type": "…", …"` : `"command": "…", …`} } } }
- pass 1:
- pass 2: ✅ mcp.md project scope — .mcp.json with "mcpServers" entries (type/url or command/args); "prompts for approval ... before using project-scoped servers from .mcp.json"

### C0397 · js:12. MCP · L- · script
> ~/.claude.json → mcpServers.…\n(you, every project on this machine)
- pass 1:
- pass 2: ✅ mcp.md user scope — "User-scoped servers are stored in ~/.claude.json ... available across all projects on your machine" (top level of ~/.claude.json)

### C0398 · js:12. MCP · L- · script
> ~/.claude.json → projects["/repo"].mcpServers.…\n(you, this project only — the default scope)
- pass 1:
- pass 2: ✅ mcp.md local scope — "Local scope is the default ... stores it in ~/.claude.json under that project's path"

### C0399 · js:12. MCP · L- · script
> No servers yet. Claude can only use its built-in tools.
- pass 1:
- pass 2: ✅ no MCP servers → only built-in tools (tools-reference.md; claude.ai connectors aside) — simulation text

### C0400 · js:12. MCP · L- · script
> … connected. Only its tool names entered context (… short entries). Full JSON schemas stay deferred until Claude actually uses a tool.
- pass 1:
- pass 2: ✅ mcp.md tool search — "Only tool names and server instructions load at session start"; definitions deferred "until Claude needs them"

### C0401 · js:12. MCP · L- · script
> Claude has no way to see GitHub. Best case it asks you to paste the PR list; worst case it guesses. Add the GitHub server first.
- pass 1:
- pass 2: n/a illustrative scenario

### C0402 · js:12. MCP · L- · script
> Claude picks list_pull_requests — its full schema loads now (tool search)…
- pass 1:
- pass 2: ✅ mcp.md tool search — tools "discovered on demand" (tool name illustrative)

### C0403 · js:12. MCP · L- · script
> “#412, #418 and #421 touch src/billing/” (demo data). Two tools used, two schemas loaded; the other tools still cost only their names. Run /context all to see how many tokens each MCP tool uses.
- pass 1:
- pass 2: ✅ mcp.md tool search — tool definitions deferred, "Only tool names and server instructions load at session start" until used; features-overview.md — "Run `/context all` to see how many tokens each loaded MCP tool uses" (PR numbers are demo data)

### C0404 · js:12. MCP · L- · script
> /plugin install acme-tools@your-org — one package…
- pass 1:
- pass 2: ✅ plugins/install.md — install by "plugin@marketplace" (names illustrative); "/plugin install" opens details to review and choose scope

### C0405 · js:12. MCP · L- · script
> …unpacks into a namespaced skill, a subagent, a hook and an MCP server. That is how a team shares one setup across many repos.
- pass 1:
- pass 2: ✅ plugins_overview.md components (skills, agents, hooks, MCP servers); skills.md "plugin skills are namespaced as /plugin-name:skill-name"; features-overview "reuse the same setup"
