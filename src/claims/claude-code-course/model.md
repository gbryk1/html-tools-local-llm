# Claims ledger — claude-code-course.html — model

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0219 · model · L1 · p
> Two dials decide how hard Claude thinks. The model (/model, --model, Option/Alt+P) picks the brain; the effort level (/effort, --effort) picks how much it reasons per step: low, medium, high, xhigh, max. Aliases track the recommended version for your provider: haiku, sonnet, opus, fable, best; plus opusplan (Opus to plan, Sonnet to execute) and [1m] variants for a 1M-token window.
- pass 1:
- pass 2: ✅ model-config.md "Model aliases" + "Adjust effort level"; interactive-mode.md — "`Option+P` (macOS) or `Alt+P`… Switch model"; aliases best/fable/sonnet/opus/haiku/[1m]/opusplan "uses `opus` during plan mode, then switches to `sonnet`"; effort "`low`, `medium`, `high`, `xhigh`, `max`"; "Aliases point to the recommended version for your provider"

### C0220 · model · L1 · tr
> Suggested | sonnet · /effort medium–high
- pass 1:
- pass 2: n/a scenario suggestion (sonnet and medium/high effort are valid values per model-config.md)

### C0221 · model · L1 · tr
> Reasoning depth |
- pass 1:
- pass 2: n/a table label for qualitative bar

### C0222 · model · L1 · tr
> Token spend |
- pass 1:
- pass 2: n/a table label for qualitative bar

### C0223 · model · L1 · figcaption
> Bars are qualitative. Real defaults: effort is high on most models (Opus 5.5 defaults to medium). Fast mode runs the same Opus model with faster output at a higher price, not a smaller model.
- pass 1:
- pass 2: ✅ model-config.md "high on every model that supports effort, except that Opus 5.5 defaults to medium, Opus 4.7 defaults to xhigh"; fast-mode.md "Fast mode is not a different model … up to 2.5x faster at a higher cost per token"

### C0224 · model · L1 · div
> How do I see what I'm spending?
- pass 1:
- pass 2: n/a question heading

### C0225 · model · L1 · div
> /usage (alias /cost) shows session cost and plan limits; /context shows what fills the window; a custom status line (/statusline) can show model, context % and cost all the time.
- pass 1:
- pass 2: ✅ commands.md — "/usage Show session cost, plan usage limits… /cost and /stats are aliases"; "/context Visualize current context usage"; statusline.md "monitor context window usage, costs"

### C0226 · model · L1 · div
> Which cost levers matter?
- pass 1:
- pass 2: n/a — question heading, no factual claim

### C0227 · model · L1 · div
> Context matters as much as the model: token costs scale with context size, so clearing between tasks, lean CLAUDE.md, subagents for heavy reading and fewer idle MCP servers all cut spend. Then pick the smallest model and effort that do the job, and raise them for the hard parts.
- pass 1:
- pass 2: ✅ costs.md "Reduce token usage" — "Token costs scale with context size"; "Clear between tasks"; "Move instructions from CLAUDE.md to skills"; "Delegate verbose operations to subagents"; "Disable unused servers"; "Choose the right model"; effort lowering under "Adjust extended thinking"

### C0228 · model · L1 · li
> Model = which brain; effort = how long it thinks. Raise both for design and hard debugging only.
- pass 1:
- pass 2: n/a advice/mnemonic (model-config.md effort "control adaptive reasoning")

### C0229 · model · L1 · li
> opusplan: strong planning, cheaper execution. Subagents can use model: haiku for search.
- pass 1:
- pass 2: ✅ model-config.md "opusplan … uses opus during plan mode, then switches to sonnet for execution"; sub-agents.md model field "sonnet, opus, haiku…" / "define one with model: haiku to keep exploration on a lower-cost model"

### C0230 · model · L1 · li
> Watch /usage and /context; context hygiene is one of the biggest savings.
- pass 1:
- pass 2: ✅ costs.md "Manage context proactively" — "Use `/usage` to check your current token usage"; "Run `/context` to see what's consuming space"; "The highest-impact habits… clearing between unrelated tasks and matching the model"
