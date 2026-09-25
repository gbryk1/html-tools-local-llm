# Claims ledger — claude-code-course.html — js_4_memory

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0332 · js:4. memory · L- · script
> Nothing is loaded before the session starts.
- pass 1:
- pass 2: n/a (animation start state)

### C0333 · js:4. memory · L- · script
> At launch Claude Code walks from the working directory up and loads every CLAUDE.md it finds, plus user and managed files.
- pass 1:
- pass 2: ✅ memory.md "How CLAUDE.md files load" — "loads `CLAUDE.md` and `CLAUDE.local.md` from your current working directory and every directory above it" (plus user and managed scopes per table)

### C0334 · js:4. memory · L- · script
> your private notes for this repo
- pass 1:
- pass 2: ✅ memory.md table — CLAUDE.local.md "Personal project-specific preferences"

### C0335 · js:4. memory · L- · script
> Five sources, all added together. Note what is not loaded yet: the nested CLAUDE.md and the path-scoped rule.
- pass 1:
- pass 2: ✅ memory.md — "concatenated into context rather than overriding"; subdirectory files "included when Claude reads files in those subdirectories"; path rules "trigger when Claude reads files matching the pattern" (the count of five is the demo's own setup)

### C0336 · js:4. memory · L- · script
> Already loaded — it stays in context (after a compaction it loads again the next time Claude reads a file there).
- pass 1:
- pass 2: ✅ context-window.md "What survives compaction" — "Nested CLAUDE.md in subdirectories | Claude Code reloads them as Claude reads files in that subdirectory" (same for `paths:` rules)

### C0337 · js:4. memory · L- · script
> loaded lazily: Claude read a file in that folder
- pass 1:
- pass 2: ✅ memory.md — "they are included when Claude reads files in those subdirectories"

### C0338 · js:4. memory · L- · script
> Nested CLAUDE.md files load on demand, when Claude reads files in their directory. Frontend rules never cost context in a backend-only session.
- pass 1:
- pass 2: ✅ memory.md — "Files in subdirectories load on demand when Claude reads files in those directories" (backend-only claim follows)

### C0339 · js:4. memory · L- · script
> A rule with paths: frontmatter loads only when Claude works with matching files. That keeps CLAUDE.md short.
- pass 1:
- pass 2: ✅ memory.md "Path-specific rules" — "only load into context when Claude works with matching files, reducing noise and saving context space"

### C0340 · js:4. memory · L- · script
> 900 lines. Every request now carries them, and important rules drown in noise: Claude starts ignoring some. Fix: prune what Claude already does right, move procedures to skills, scope the rest with .claude/rules/, turn must-haves into hooks.
- pass 1:
- pass 2: ✅ best-practices.md — "If your CLAUDE.md is too long, Claude ignores half of it because important rules get lost in the noise"; "If Claude already does something correctly without the instruction, delete it or convert it to a hook"; memory.md — move procedures to skills / path-scoped rules
