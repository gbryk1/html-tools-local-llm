# Claims ledger — claude-code-course.html — prompt

Verdicts: ✅ confirmed · ⚠️ imprecise (give fix) · ❌ wrong (give fix) · ❓ unverifiable (soften or remove) · n/a pedagogy/opinion/labelled illustrative

### C0097 · prompt · L1 · p
> Claude can infer a lot, but not what's in your head. Every fact you leave out becomes a guess, and every guess is a chance to solve the wrong problem. A good prompt is not long — it's specific: where to look, what's wrong, what “done” means, and what not to touch.
- pass 1:
- pass 2: ✅ best-practices.md Provide specific context — "Claude can infer intent, but it can't read your mind. Reference specific files, mention constraints, and point to example patterns"

### C0098 · prompt · L1 · li
> Which file? (Claude greps the whole repo)
- pass 1:
- pass 2: ✅ same as C0098 (pedagogy; fair simplification)

### C0099 · prompt · L1 · li
> What exactly is broken?
- pass 1:
- pass 2: n/a pedagogy (maps to "Describe the symptom")

### C0100 · prompt · L1 · li
> Which approach and style?
- pass 1:
- pass 2: n/a pedagogy (maps to "Reference existing patterns")

### C0101 · prompt · L1 · li
> How do I know I'm done?
- pass 1:
- pass 2: n/a pedagogy (maps to "Give Claude a check it can run")

### C0102 · prompt · L1 · li
> What must not change?
- pass 1:
- pass 2: n/a pedagogy (maps to "mention constraints")

### C0103 · prompt · L1 · figcaption
> Every ingredient maps to a best practice from the official docs: reference files, describe the symptom, point to existing patterns, give a verification command, state constraints.
- pass 1:
- pass 2: ✅ best-practices.md — "Reference specific files, mention constraints, and point to example patterns"; "Describe the symptom"; "Give Claude a check it can run"

### C0104 · prompt · L1 · li
> Onboarding question: “How does logging work here? Trace one request from @src/server.ts to the DB.”
- pass 1:
- pass 2: ✅ best-practices.md — "How does logging work?"; common-workflows.md — "trace the login process from front-end to database" (@ file reference real)

### C0105 · prompt · L1 · li
> Bug with evidence: paste the stack trace or screenshot (Ctrl+V), say how to reproduce, ask for a failing test first.
- pass 1:
- pass 2: ✅ interactive-mode.md — "Ctrl+V or Cmd+V (iTerm2) or Alt+V (Windows and WSL) | Paste image from clipboard"; best-practices.md — "write a failing test that reproduces the issue, then fix it"

### C0106 · prompt · L1 · li
> Follow the pattern: “Add a /invoices endpoint like @src/api/orders.ts.”
- pass 1:
- pass 2: ✅ best-practices.md — "Reference existing patterns ... follow the pattern" (@ file reference real)

### C0107 · prompt · L1 · li
> TDD: “Write tests for X, confirm they fail, commit them. Then implement until they pass without changing the tests.”
- pass 1:
- pass 2: n/a prompt advice (TDD recipe not spelled out in current docs; nearest: best-practices.md "write a failing test that reproduces the issue, then fix it")

### C0108 · prompt · L1 · li
> UI iteration: give a mockup image, ask Claude to screenshot its result and compare, iterate 2–3 times.
- pass 1:
- pass 2: n/a prompt advice; best-practices.md — "[paste screenshot] implement this design. take a screenshot of the result and compare it to the original" ("2–3 times" is the page's own advice, not in docs)

### C0109 · prompt · L1 · li
> Pipe data in: cat error.log | claude -p "find the root cause".
- pass 1:
- pass 2: ✅ best-practices.md — "Pipe in data by running cat error.log | claude"; -p is non-interactive mode

### C0110 · prompt · L1 · p
> You can ask for more thinking in plain words (“think hard about edge cases”) or raise the session's effort level with /effort (chapter 15). Rich context beats clever phrasing: a URL to the docs, an image, @-mentioned files, piped logs. If Claude should fetch docs, allow the domain with a rule like WebFetch(domain:docs.stripe.com).
- pass 1:
- pass 2: ✅ model-config.md — "you can say so directly in your prompt" / "think hard ... passes through as ordinary prompt text"; /effort real; permissions.md — "WebFetch(domain:example.com) Matches fetch requests to example.com"; best-practices.md "Give URLs ... Use /permissions to allowlist frequently-used domains"

### C0111 · prompt · L1 · li
> Where (@file) + symptom + pattern to follow + verification + constraints.
- pass 1:
- pass 2: ✅ best-practices.md Provide specific context table (scope/file, symptom, existing patterns, verification, constraints)

### C0112 · prompt · L1 · li
> Give Claude a finish line it can check itself: a test, a command, a screenshot.
- pass 1:
- pass 2: ✅ best-practices.md — "Give Claude a check it can run: tests, a build, a screenshot to compare"

### C0113 · prompt · L1 · li
> Two failed corrections in a row → /clear and write a better first prompt.
- pass 1:
- pass 2: ✅ best-practices.md — "After two failed corrections, /clear and write a better initial prompt incorporating what you learned"
