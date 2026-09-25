# Claims ledger — claude-code-course.html

Every factual claim extracted from the rendered page (`skills/animated-knowledge-page/scripts/extract-claims.cjs`,
one file per chapter; `js_*` files hold figure narrations from the inline script). Checked in September 2026
against the official Claude Code docs (code.claude.com/docs).

- **pass 2** — independent verification: 7 fresh verifier subagents (no access to the page or the author's notes),
  then 3 re-verification rounds on changed claims; round 3–4 verifiers also executed cheap commands in a throwaway repo.
  Final: 362 ✅, 94 n/a (pedagogy / demo data labelled illustrative), 0 open.
- **pass 1** — the author's check was done per chapter while writing (docs grep), not recorded per claim, so these
  lines are empty; `extract-claims.cjs --status` therefore reports pass 1 as open for this page.

Claim IDs are positional and change when the page is re-extracted; match on the quoted text.
