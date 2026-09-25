# Claims ledger — claude-code-course.html — plan

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0083 · plan · L1 · p
> The most common beginner move is “implement feature X” as the first prompt. Claude will — and it will solve the problem it guessed, not the one you have. The recommended workflow separates research from execution:
- pass 1:
- pass 2: ✅ best-practices.md Explore first — "Letting Claude jump straight to coding can produce code that solves the wrong problem. Use plan mode to separate exploration from execution" ("most common beginner move" is opinion)

### C0084 · plan · L1 · li
> Explore (plan mode): “read src/auth and explain how sessions are refreshed.” No edits.
- pass 1:
- pass 2: ✅ best-practices.md Explore — "Claude reads files and answers questions without making changes"

### C0085 · plan · L1 · li
> Plan: “plan how to add Google login. Which files change? What's the migration?” Press Ctrl+G to edit the plan yourself in your editor. Approving the plan exits plan mode.
- pass 1:
- pass 2: ✅ best-practices.md Plan — "Press Ctrl+G to open the plan in your text editor"; permission-modes.md — "Approving a plan exits plan mode"

### C0086 · plan · L1 · li
> Code: Claude implements against the plan, checking it off.
- pass 1:
- pass 2: ✅ best-practices.md Implement — "let Claude code, verifying against its plan"

### C0087 · plan · L1 · li
> Verify & commit: tests, typecheck, a look at /diff, then “commit with a clear message and open a PR”.
- pass 1:
- pass 2: ✅ best-practices.md Commit — "commit with a descriptive message and open a PR"; commands.md /diff — "Review the changes in your working tree"

### C0088 · plan · L1 · figcaption
> Minutes are illustrative, but the shape is the lesson: planning has a fixed cost that pays off only when the change spans several files or you're unsure of the approach.
- pass 1:
- pass 2: n/a illustrative minutes; lesson matches best-practices.md — "Planning is most useful when you're uncertain about the approach, when the change modifies multiple files"

### C0089 · plan · L1 · p
> When would you skip plan mode entirely? (Hint: the docs' own rule of thumb — if you can describe the diff in one sentence, skip the plan.)
- pass 1:
- pass 2: ✅ best-practices.md — "If you could describe the diff in one sentence, skip the plan."

### C0090 · plan · L1 · div
> What if I don't know enough to write a good spec?
- pass 1:
- pass 2: n/a question heading

### C0091 · plan · L1 · div
> Let Claude interview you: “I want to add rate limiting. Interview me with questions until you can write a spec to SPEC.md.” Then /clear and start a fresh session that implements SPEC.md. The spec is the handoff — clean context, full intent.
- pass 1:
- pass 2: ✅ best-practices.md Let Claude interview you — "Keep interviewing until we've covered everything, then write a complete spec to SPEC.md" / "start a fresh session to execute it"

### C0092 · plan · L1 · div
> Can I plan with a stronger model and code with a cheaper one?
- pass 1:
- pass 2: n/a question heading

### C0093 · plan · L1 · div
> Yes: the opusplan model setting uses Opus in plan mode and Sonnet for execution.
- pass 1:
- pass 2: ✅ model-config.md — "`opusplan` | Special mode that uses opus during plan mode, then switches to sonnet for execution"

### C0094 · plan · L1 · li
> Explore and plan in plan mode (Shift+Tab or /plan), edit the plan with Ctrl+G.
- pass 1:
- pass 2: ✅ permission-modes.md — "Enter plan mode by pressing Shift+Tab or prefixing a single prompt with /plan"; "Press Ctrl+G to open the proposed plan in your default text editor"

### C0095 · plan · L1 · li
> Planning pays for multi-file or uncertain work; skip it for one-sentence diffs.
- pass 1:
- pass 2: ✅ best-practices.md — "most useful when ... the change modifies multiple files ... If you could describe the diff in one sentence, skip the plan"

### C0096 · plan · L1 · li
> For big features: interview → SPEC.md → /clear → implement.
- pass 1:
- pass 2: ✅ best-practices.md Let Claude interview you — "write a complete spec to SPEC.md ... start a fresh session to execute it"
