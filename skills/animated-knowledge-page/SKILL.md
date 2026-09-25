---
name: animated-knowledge-page
description: "Build an animated course, interactive guide, scrollytelling explainer or 'from zero to expert' knowledge page (\"animowany kurs\", \"strona wiedzy\", \"przewodnik\", Head First style) on one technical topic, tool or product. Produces a single self-contained HTML file with scroll-triggered SVG/HTML/Canvas diagrams, Head First boxes, a quiz and a cheat sheet, fact-checked against current docs and verified headless."
---

# Animated Knowledge Page

Builds one self-contained `.html` file that teaches a single technical concept, system or tool through
scroll-triggered, clickable diagrams and Head First-style prose. Examples: "how Cassandra works inside",
"Claude Code from zero to expert", "Copilot for project managers".

- Starter page with the design system, helpers, scroll machinery, an example figure and the quiz: [templates/shell.html](templates/shell.html)
- Patterns, box catalogue, figure archetypes, fact-check workflow, browser setup: [reference.md](reference.md)
- Headless checks: [scripts/check-page.cjs](scripts/check-page.cjs) (smoke test) and [scripts/click-through.cjs](scripts/click-through.cjs) (clicks every control)

## Hard constraints

- One HTML file: inline `<style>` and inline `<script>`, vanilla JS, SVG, HTML and `<canvas>`. No framework, no bundler, no build step.
- No network dependencies. Use system font stacks and emoji as icons. Use a CDN only if a library is truly unavoidable, and pin its version.
- Light and dark themes come from `prefers-color-scheme` on CSS variables. There must be no horizontal page overflow at 390px.
  Under `prefers-reduced-motion`, every animation is instant but still shows its end state.
- The page is readable without JS (`.reveal` only hides content when `html.js` is set) and without the scroll animations.
- Be honest. Every figcaption says what the simulation simplifies, and invented numbers are labelled "illustrative" or "heuristic".

## Steps

0. **Decide the frame.** Write the page in the language of the user's request, unless the user or project says
   otherwise, and write any repo index or README entry in the repo's own language. Decide the audience level and the
   arc: one mechanism deep, or zero → expert across a whole tool. Find where the page will live: the repo's pages or
   docs folder, how the index links pages, and whether a generator copies sources. If there is no repo, put the file
   in the working directory.
   Done when you know the language, the audience, the target path and the ship steps.

1. **Plan the syllabus before writing code.** List 8–18 chapters. Each chapter covers one mechanism and uses only earlier
   chapters. For a zero → expert guide, group the chapters into stages: mental model → daily use → extension layer →
   expert layer. For each chapter write:
   - the one-sentence takeaway,
   - the misconception it kills,
   - the figure that *demonstrates the mechanism itself* (reference §8): what the reader clicks, what moves,
     what state changes, the "break it" action, and the reset.

   Add chapter 0 ("how to read this", ending in an open 🧠 question that the finale answers) and a final chapter
   (quiz + cheat sheet). For tool guides, plan an **Option | What | When** table in each chapter that has options.
   Done when every chapter has a takeaway, a figure spec with at least one user action, and at least one box type.

2. **Check the facts** (reference §10). Defaults, thresholds, formulas, flags, file paths, command names and
   version-dependent *behavior* all need checking. For fast-moving products, download the official docs as markdown
   into scratch and grep them. Don't trust memory. Record the date you checked, for chapter 0 and the footer.
   Done when every command, number and behavior in the planned cheat sheet has a source you checked.

3. **Start from the shell.** Copy `templates/shell.html` to the target path. Fill in `{{…}}`, the TOC, the cover
   icons and the chapter skeletons. Keep the design tokens and helpers. Add per-figure CSS only in the marked slot,
   with **prefixed class names**, and grep the CSS before you introduce a short name like `.sub` or `.card`.
   Done when the page with its cover, TOC and empty chapters renders in light and dark.

4. **Write chapters: prose + boxes.** Use conversational second person, short paragraphs with one idea each, and humor
   that serves the point. Each chapter gets 1–3 boxes (reference §3): 🧠, ❓, ✏️, 🔥, ⚠️, 🤓, 🧰, 😌, and a 📌 summary
   at the end. Show real snippets: config files, commands, frontmatter. Mark text blocks `.reveal`.
   Done when every chapter ends with a 📌 summary or a ✏️ exercise, and no chapter is only prose.

5. **Build one figure per chapter** (reference §4–8).
   - Use one IIFE per figure with local state, registered with `registerFig(el, {first, enter, leave})`. `first()`
     plays an auto-demo once. `enter/leave` start and stop loops.
   - Write mechanisms as `await` sequences, with a `.status` sentence for each step saying what happened and why.
   - Every figure has buttons (`data-act`), at least one "break it" action, and `↺ Reset`. Serialize clicks with
     `makeQueue()`, and cancel stale runs with a `runId`. Each action starts from a state that matches its narration.
   - Prefer HTML-grid figures (bars, cards, logs, timelines) when geometry doesn't matter, because they reflow on mobile.
     SVG uses `viewBox`. Put a wide SVG in `.scroll-x`. Use `wbr()` for CamelCase labels in narrow grids.
   - Use deterministic data. Add a button for any rare random case the text relies on.
   - Build large pages in parts: head, CSS, chapter HTML in 2–3 files, and JS. Concatenate them into the target, then
     extract the `<script>` and run `node --check` before opening a browser.
   Done when every figure animates on first view, responds to each button, and resets cleanly.

6. **Finish with the quiz and cheat sheet.** Write 10–14 questions in the `[question, options, correctIndex, why]`
   array. The wrong options are the chapters' misconceptions. The cheat sheet has the columns
   parameter/command | default/what | when. Close the loop in the 🎓 box: answer chapter 0's question and give one next step.
   Done when every chapter is covered by at least one question or cheat-sheet row.

7. **Verify headless** (reference §11 for browser setup). Scripts live next to this file. Put screenshots in scratch,
   not in the repo.
   ```bash
   node <skill-dir>/scripts/check-page.cjs  path/to/page.html "$SCRATCH/shots"   # light/dark/mobile/reduced
   node <skill-dir>/scripts/click-through.cjs path/to/page.html "$SCRATCH/shots"  # every button, select, checkbox
   ```
   - `check-page.cjs` fails on JS errors, figures that never animate, and horizontal overflow, and it lists the offenders.
   - `click-through.cjs` fails on any JS error after clicking every control.
   - Then **open the screenshots** and look for overlapping labels, clipped text, mid-word breaks, dark-mode
     contrast problems, and narration that contradicts the visible state. Plan at least two screenshot → fix rounds.

   Done when both scripts pass and every figure's screenshot was inspected after the last layout change.

8. **Ship.** Follow the conventions found in step 0:
   - Keep the source where the generator won't wipe it, and register it wherever the generator needs it.
   - If the generator can't run (for example because of missing large inputs), copy the page by hand and patch the
     generated index the same way as its template.
   - Link the page from the index and the README.
   - Commit, and push if that's the repo's workflow. Run the commit or push as a command of its own, never chained after cleanup.

   Done when the page is reachable from the index and the commit exists (on the remote, if pushed).

## Pitfalls

- **Stale facts about fast-moving tools.** The draft said `acceptEdits` auto-approves only `mkdir/touch/mv/cp`, but the docs
  said `rm`, `rmdir` and `sed` too. Commands get removed and renamed, and defaults change per model. Grep the docs for every claim.
- **Blank screenshots / Chromium crashes on `<input>`/`<select>`.** The sandbox had no fonts. A "no JS errors" run with blank
  screenshots is not a pass (reference §11).
- **Missing Chromium libraries, or a browser tool refusing `localhost`.** Use `playwright-core` with `file://` URLs. No server is needed.
- **`pkill -f "http.server 8731"` killed its own command** (exit 144), because the pattern matched its own shell. Kill by PID
  or use a bracket pattern, and never chain cleanup with commit or push.
- **Layout collisions only show up in screenshots.** Ring labels collided, a label covered a node, and the fixed TOC
  overlapped the cover. Put labels on a larger radius than nodes, reserve space for badges, and stack exploded labels
  in a column rather than scattering them.
- **Generic class names collide.** A figure's `.sub` class also matched the cover subtitle `.sub` and `.ctx-bar.sub`.
- **Mobile overflow.** Check the overflow list:
  - grid items need `min-width:0`,
  - long `<select>` options need `max-width:100%`,
  - long unbreakable text in prose needs `overflow-wrap:break-word`. Here the list is empty but `scrollWidth` > 390.
- **CamelCase labels break mid-word** (`SessionStar|t`) in narrow grids. Insert `<wbr>` between words.
- **`hidden` attribute ignored.** `.ctrl{display:flex}` beats the UA `[hidden]` rule, so the template forces it.
- **Narration contradicts state.** A second "break it" action ran on the state the first one left behind. Reset first.
- **Rare random cases look like bugs.** A 13% event was missed by the tests. Force it with a button or seed the demo.
- **Dynamic text grammar.** Interpolated counts need plural rules (Polish: 1 replika / 2–4 repliki / 5+ replik).
- **Dynamically created `.reveal` elements** (quiz questions) stay invisible unless passed to `revealIO.observe()`.
- **Checker false positives.** `<code>` inside `<pre>` sits past the viewport but scrolls inside its block. The checker ignores `pre` and `.scroll-x`.
