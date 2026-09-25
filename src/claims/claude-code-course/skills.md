# Claims ledger — claude-code-course.html — skills

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0128 · skills · L1 · p
> A skill is a folder with a SKILL.md: YAML frontmatter plus markdown instructions, optionally with scripts and reference files next to it. You invoke it as a command (/deploy staging), or Claude loads it by itself when your task matches its description. Custom slash commands were merged into skills: an old .claude/commands/deploy.md still works and creates /deploy too.
- pass 1:
- pass 2: ✅ skills.md — "Every skill needs a `SKILL.md` file with two parts: YAML frontmatter ... and markdown content"; "Custom commands have been merged into skills. A file at `.claude/commands/deploy.md` and a skill at `.claude/skills/deploy/SKILL.md` both create `/deploy`"

### C0129 · skills · L1 · p
> The trick is progressive disclosure. At session start only each skill's name and description sit in context. The full body loads when the skill is used; files it links load only if Claude opens them. So you can have fifty skills and pay for fifty short descriptions.
- pass 1:
- pass 2: ✅ skills.md — "skill descriptions are loaded into context ... but full skill content only loads when invoked"; supporting files "loaded when needed" (listing may shorten descriptions when many skills exist)

### C0130 · skills · L1 · pre
> .claude/skills/release-notes/SKILL.md --- name: release-notes description: Draft release notes from merged PRs since the last tag. Use when asked for a changelog or release notes. disable-model-invocation: true # only I can trigger it (/release-notes) allowed-tools: Bash(git log *) Bash(gh pr list *) context: fork # run in a forked subagent, return a summary --- 1. Find the last tag with `git describe --tags --abbrev=0`. 2. List merged PRs since then … 3. Group by feat / fix / chore. Output markdown. See [template.md](template.md).
- pass 1:
- pass 2: ✅ skills.md frontmatter reference — `disable-model-invocation` "trigger manually with `/name`"; `allowed-tools: Bash(git add *) Bash(git commit *)` same syntax; `context` "Set to `fork` to run in a forked subagent context"

### C0131 · skills · L1 · figcaption
> Token sizes are illustrative. /skills lists your skills; /skill-doctor shows what each one costs in context and how often it triggers.
- pass 1:
- pass 2: ✅ commands.md `/skills` — "List available skills"; `/skill-doctor` — "Show what each of your skills costs in context and how often it gets used" (token sizes n/a)

### C0132 · skills · L1 · tr
> description | How Claude decides to use it. Say what and when. Vague = wrong triggers.
- pass 1:
- pass 2: ✅ skills.md `description` — "What the skill does and when to use it. Claude uses this to decide when to apply the skill"

### C0133 · skills · L1 · tr
> disable-model-invocation: true | Only you can run it. Use for side effects (deploy, publish). Zero context cost until used.
- pass 1:
- pass 2: ✅ skills.md — `disable-model-invocation: true` "Description not in context, full skill loads when you invoke"

### C0134 · skills · L1 · tr
> user-invocable: false | Only Claude uses it (background knowledge); hidden from the / menu.
- pass 1:
- pass 2: ✅ skills.md `user-invocable` — "Set to `false` when only Claude should invoke the skill: Claude Code hides it from the `/` menu ... background knowledge"

### C0135 · skills · L1 · tr
> allowed-tools | Tools pre-approved while the skill runs
- pass 1:
- pass 2: ✅ skills.md `allowed-tools` — "Tools Claude can use without asking permission during the turn that invokes this skill" (grant clears at your next message)

### C0136 · skills · L1 · tr
> context: fork + agent | Run in a forked subagent; only the result returns
- pass 1:
- pass 2: ✅ skills.md `context`/`agent` — "Set to `fork` to run in a forked subagent context"; "Which subagent type to use"; "its result arrives in your conversation"

### C0137 · skills · L1 · tr
> model, effort | Override model / effort while the skill is active
- pass 1:
- pass 2: ✅ skills.md `model` — "Model to use when this skill is active"; `effort` — "Effort level when this skill is active"

### C0138 · skills · L1 · tr
> paths | Auto-load only when working with matching files
- pass 1:
- pass 2: ✅ skills.md `paths` — "Claude loads the skill automatically only when working with files matching the patterns"

### C0139 · skills · L1 · tr
> arguments, argument-hint | Named args ($name) and autocomplete hint
- pass 1:
- pass 2: ✅ skills.md `arguments` — "Named positional arguments for `$name` substitution"; `argument-hint` — "Hint shown during autocomplete"

### C0140 · skills · L1 · tr
> hooks | Hooks registered when the skill is invoked
- pass 1:
- pass 2: ✅ skills.md `hooks` — "Hooks that Claude Code registers when the skill is invoked"

### C0141 · skills · L1 · p
> Where skills live: ~/.claude/skills/ (you, all projects), .claude/skills/ (the repo — commit it), managed (your company), and plugins (namespaced like /my-plugin:review). Claude Code also bundles skills you get for free: /code-review, /simplify, /debug, /batch, /loop, /run, /verify, /doctor, /fewer-permission-prompts and more.
- pass 1:
- pass 2: ✅ skills.md "Choose where skills load" table (Enterprise/managed, Personal `~/.claude/skills/`, Project, Plugin "as `/plugin-name:skill-name`"); commands.md marks /code-review, /simplify, /debug, /batch, /loop, /run, /verify, /doctor, /fewer-permission-prompts as **Skill**

### C0142 · skills · L1 · p
> Tonight's guests: CLAUDE.md and a Skill.
- pass 1:
- pass 2: n/a framing

### C0143 · skills · L1 · div
> CLAUDE.mdI'm loaded in every session. Every single one. People love me.
- pass 1:
- pass 2: ✅ memory/best-practices — "CLAUDE.md is loaded every session" (tone n/a)

### C0144 · skills · L1 · div
> SkillAnd they pay for you every single request. I show up only when I'm useful.
- pass 1:
- pass 2: ✅ best-practices — "Unlike CLAUDE.md content, a skill's body loads only when it's used" (tone n/a)

### C0145 · skills · L1 · div
> CLAUDE.mdSo what should live in me?
- pass 1:
- pass 2: n/a framing question

### C0146 · skills · L1 · div
> SkillFacts needed almost always: build commands, conventions. Procedures and reference docs — the deploy checklist, the API style guide — give them to me.
- pass 1:
- pass 2: ✅ best-practices — "CLAUDE.md is loaded every session, so only include things that apply broadly. For domain knowledge or workflows that are only relevant sometimes, use skills"

### C0147 · skills · L1 · li
> Skill = SKILL.md + optional files. Invoked with /name or auto-loaded by description.
- pass 1:
- pass 2: ✅ skills.md — SKILL.md + supporting files; "invoke it directly with the skill name" or "Claude loads the skill automatically" by description

### C0148 · skills · L1 · li
> Only descriptions cost context until use. Write sharp descriptions.
- pass 1:
- pass 2: ✅ skills.md — "skill descriptions are loaded into context ... full skill content only loads when invoked"; `description` guidance

### C0149 · skills · L1 · li
> Third time you paste the same instructions → make it a skill.
- pass 1:
- pass 2: ✅ best-practices table — "You paste the same playbook or multi-step procedure into chat for the third time | Capture it as a skill"

### C0150 · skills · L1 · li
> Side effects → disable-model-invocation: true. Heavy work → context: fork.
- pass 1:
- pass 2: ✅ skills.md — disable-model-invocation "for workflows you want to trigger manually"; context: fork "run in isolation" (advice)
