# Claims ledger — claude-code-course.html — mcp

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0182 · mcp · L1 · p
> MCP (Model Context Protocol) connects Claude to external systems as tools: GitHub, Sentry, Linear, Notion, your database, a browser. If you keep copying data from a browser tab into the chat, that system wants to be an MCP server.
- pass 1:
- pass 2: ✅ mcp.md intro — examples incl. Sentry, Notion, databases; "Verify you trust each server" (advice part n/a)

### C0183 · mcp · L1 · pre
> # remote HTTP server (OAuth in /mcp) claude mcp add --transport http notion https://mcp.notion.com/mcp # local stdio server: everything after -- is the server command claude mcp add --transport stdio db -- npx -y @bytebase/dbhub --dsn "postgresql://readonly:…@localhost:5432/app" # share with the team via .mcp.json claude mcp add --scope project --transport http sentry https://mcp.sentry.dev/mcp
- pass 1:
- pass 2: ✅ mcp.md — "claude mcp add --transport http notion https://mcp.notion.com/mcp"; DBHub example "claude mcp add --transport stdio db -- npx -y @bytebase/dbhub --dsn …"; "claude mcp add --transport http sentry https://mcp.sentry.dev/mcp" then "/mcp" to authenticate; "Project scope… storing configurations in a `.mcp.json` file" (`--scope project`)

### C0184 · mcp · L1 · figcaption
> Tool search is on by default: only tool names load at start; a full schema loads when Claude needs that tool. /mcp shows status and handles OAuth; /context all shows how many tokens each loaded MCP tool uses.
- pass 1:
- pass 2: ✅ mcp.md "Scale with MCP tool search" — "Only tool names and server instructions load at session start"; tool search "which is on by default"; features-overview.md — "Run `/mcp` to see each server's connection status. Run `/context all` to see how many tokens each loaded MCP tool uses"

### C0185 · mcp · L1 · p
> MCP scopes override by name: local > project > user. Local and user servers are stored in ~/.claude.json; project servers in .mcp.json at the repo root, which teammates approve on first use. Never commit secrets there — use ${ENV_VAR} expansion.
- pass 1:
- pass 2: ✅ mcp.md "Scope hierarchy and precedence" — "1. Local scope 2. Project scope 3. User scope ... The three scopes match duplicates by name"; local/user in ~/.claude.json; "prompts for approval ... before using project-scoped servers from .mcp.json"; ${VAR} expansion

### C0186 · mcp · L1 · p
> Plugins are the packaging layer: one installable unit bundling skills, subagents, hooks, MCP servers (and LSP code-intelligence servers). Add a marketplace once, then install from it:
- pass 1:
- pass 2: ✅ plugins_overview.md — Skills, Agents, Hooks, MCP servers; plugins/install.md — "commands, agents, skills, hooks, and MCP and LSP servers"; "You add a marketplace once, then install plugins from it by name"

### C0187 · mcp · L1 · pre
> /plugin marketplace add your-org/claude-plugins /plugin install commit-commands@claude-plugins-official /plugin # browse, enable, disable, choose scope
- pass 1:
- pass 2: ✅ plugins/install.md — "/plugin marketplace add ... GitHub repository owner/repo"; "/plugin install commit-commands@claude-plugins-official"; scopes chosen in /plugin panel, enable/disable via /plugin

### C0188 · mcp · L1 · p
> MCP gives access; a skill gives know-how. The strongest combo is both: an MCP server for your database plus a skill that documents your schema, naming and “never query prod without LIMIT” rules. For typed languages, a code intelligence plugin (LSP) lets Claude jump to definitions and see type errors after each edit instead of grepping — fewer file reads, less context.
- pass 1:
- pass 2: ✅ features-overview.md — "MCP connects Claude to external services. Skills extend what Claude knows"; costs.md — code intelligence plugins "reducing unnecessary file reads"; plugins/code-intelligence.md — "catches type errors ... go-to-definition" (combo advice n/a)

### C0189 · mcp · L1 · p
> An MCP server that fetches untrusted content (web pages, issues, emails) can carry prompt injection. Use servers you trust, keep permission prompts on for tools with side effects, and prefer read-only credentials.
- pass 1:
- pass 2: ✅ mcp.md — "Servers that fetch external content can expose you to prompt injection risk"; DBHub "Use a read-only database user" (rest advice)

### C0190 · mcp · L1 · li
> MCP = external tools. claude mcp add, scopes local > project > user, /mcp to manage.
- pass 1:
- pass 2: ✅ mcp.md — claude mcp add; precedence local > project > user; /mcp panel

### C0191 · mcp · L1 · li
> Only tool names cost context until a tool is used.
- pass 1:
- pass 2: ✅ mcp.md "Scale with MCP tool search" — "Only tool names and server instructions load at session start" (tool search on by default)

### C0192 · mcp · L1 · li
> Plugins bundle skills + agents + hooks + MCP; share them through a marketplace when a 2nd repo needs the same setup.
- pass 1:
- pass 2: ✅ features-overview.md — "A plugin bundles skills, hooks, subagents, and MCP servers into a single installable unit ... Use plugins when you want to reuse the same setup"
