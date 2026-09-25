---
name: animated-knowledge-page
description: "Animated course / scrollytelling explainer / interactive knowledge page (\"animowany kurs\", \"strona wiedzy\", Head First style) on one technical topic: builds a single self-contained HTML file with scroll-triggered SVG/Canvas diagrams, Head First boxes, quiz and cheat sheet, verified headless."
---

# Animated Knowledge Page

Builds one self-contained `.html` file that teaches a single technical concept or system (e.g. "how Cassandra works inside")
through scroll-triggered, clickable diagrams and Head First-style prose. Worked example: `docs/cassandra-course.html`
(source `src/cassandra-course.html`, ~2400 lines, 14 chapters, 14 interactive figures, no dependencies).
Code snippets for every step: [reference.md](reference.md). Headless checker: [scripts/check-page.cjs](scripts/check-page.cjs).

## Hard constraints

- One HTML file: inline `<style>` + inline `<script>`, vanilla JS, SVG and `<canvas>`. No framework, no bundler, no build step.
- No network dependencies. System font stacks, emoji as icons. Use a CDN only if a library is truly unavoidable, and pin its version.
- Light and dark via `prefers-color-scheme` on CSS variables; no horizontal page overflow at 390px; `prefers-reduced-motion`
  makes every animation instant but still shows its end state.
- Page is readable without JS (`.reveal` only hides when `html.js` is set) and without scrolling animations.

## Steps

1. **Plan the syllabus before writing code.** List 8–15 chapters, each one mechanism, ordered so every chapter only uses
   earlier ones. For each chapter write: the one-sentence takeaway, the misconception it kills, and the figure that
   *demonstrates the mechanism itself* (not a decorative picture): what the reader clicks, what moves, what number or state
   changes, and the reset. Add chapter 0 ("how to read this") and a final chapter (quiz + cheat sheet).
   Done when every chapter has a takeaway, a figure spec with at least one user action, and at least one box type.

2. **Check the facts that will appear as numbers.** Defaults, thresholds, formulas, version-dependent behavior
   (e.g. `num_tokens` 256 → 16 in 4.0, `gc_grace_seconds` 864000, QUORUM = ⌊RF/2⌋+1). Say in the figcaption what the
   simulation simplifies (e.g. "32-bit hash instead of Murmur3 64-bit, geometry is identical").
   Done when every number in the planned cheat sheet has a source you checked.

3. **Write the shell and design system** (reference §1–3): CSS variables for all colors, dark overrides, `[hidden]{display:none!important}`,
   reduced-motion block, cover with a big title and a small looping SVG, fixed progress bar, fixed TOC shown only ≥1440px
   and only after the cover, `main{max-width:800px}` column, `.fig.wide` that bleeds wider on desktop.
   Done when an empty page with cover, TOC and two dummy chapters renders correctly in light and dark.

4. **Write chapters: prose + boxes.** Conversational second person, short paragraphs, one idea per paragraph, humor that
   serves the point. Per chapter use 1–3 boxes from the catalogue (reference §3): 🧠 brain teaser, ❓ "no dumb questions"
   Q/A, ✏️ exercise with `<details>` answer, 🔥 fireside dialogue between two personified concepts, ⚠️ pitfall,
   🤓 deep-dive, 😌 relax, 📌 bullet summary closing the chapter. Mark text blocks `.reveal`.
   Done when every chapter ends with a 📌 summary or ✏️ exercise and no chapter is only prose.

5. **Build one figure per chapter** (reference §4–7). Structure:
   - Shared helpers once: `S()/T()/H()` element makers, promise-based `tween()`, `sleep()` that is 0 under reduced
     motion, `flyDot()` for "a message travels from A to B", colors read from CSS vars into `C`.
   - One IIFE per figure with local state; register with `registerFig(el, {first, enter, leave})`: `first()` plays an
     auto-demo once when 25% visible, `enter/leave` start and stop loops (`setInterval`, rAF) so off-screen figures cost nothing.
   - Write mechanisms as `await` sequences with a `.status` sentence per step narrating what happens and why.
   - Every figure has buttons (`.btn`, `data-act=…`), at least one "break it" action (kill node, flood partition, delete row)
     and `↺ Reset`. Serialize clicks through an `enqueue()` promise chain; cancel stale runs with a `runId` counter.
   - SVG uses `viewBox` + `width:100%`; SVGs that become illegible when narrow go in `.scroll-x` with a `min-width`.
     Canvas: scale by `devicePixelRatio`, re-layout on `resize` and in `enter()`.
   - Deterministic inputs (hash of a string) for anything the text refers to; if randomness is part of the lesson,
     provide a button that forces the interesting case.
   Done when every figure animates by itself on first view, responds to each button, and resets cleanly.

6. **Finish with quiz and cheat sheet.** 8–12 multiple-choice questions generated from an array
   `[question, options, correctIndex, why]`; one answer per question, reveal right/wrong plus explanation, sticky score pill.
   Wrong options are the misconceptions from the chapters. Cheat sheet table: parameter | default | what it does.
   Done when every chapter is covered by at least one question or cheat-sheet row.

7. **Verify headless** (reference §9 for the sandbox setup):
   ```bash
   export LD_LIBRARY_PATH=/tmp/libs/root/usr/lib/x86_64-linux-gnu FONTCONFIG_FILE=/tmp/libs/fonts.conf
   node skills/animated-knowledge-page/scripts/check-page.cjs path/to/page.html /tmp/shots
   ```
   On macOS without a downloaded Chromium, install `playwright-core` anywhere (`NODE_PATH` to its `node_modules`) and set
   `CHROME_PATH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"`.
   It loads the page via `file://` in light (1400px), dark, mobile (390px) and reduced-motion; scrolls to every
   `figure[id]`; fails on JS errors (`pageerror` + `console.error`), on figures with no DOM mutation / CSS animation / canvas
   pixels after scroll (animation never started), and on horizontal overflow, listing the overflowing elements.
   Then **open the screenshots** (`view_image` / Read) and look for overlapping labels, clipped text, unreadable
   dark-mode contrast. Click through each figure's buttons with a short Playwright script for interactions the auto-demo does not cover.
   Done when the checker prints `OK` and every figure screenshot was inspected after the last layout change.

8. **Ship.** If the repo has a generator that wipes the output dir (here `build.py --clean` wipes `docs/`), keep the
   source outside it (`src/`) and add a copy step. Link the page from the index and README. Commit and push in a
   command of its own. Done when `git log origin/main -1` shows the commit.

## Pitfalls hit while building the Cassandra course

- **Blank screenshots / Chromium crash on `<input>`/`<select>`**: the sandbox had no fonts. Text rendered as nothing and
  form controls crashed the renderer even with JS disabled. Fix: `fonts-dejavu-core` + `fonts-noto-color-emoji` extracted to
  `/tmp` with a `FONTCONFIG_FILE` (reference §9). A "no JS errors" run with blank screenshots is not a pass.
- **Chromium missing shared libraries, OpenClaw `browser` tool refusing `localhost`**: use `playwright-core` bundled with
  OpenClaw, its downloaded Chromium, libraries extracted with `apt-get download` + `dpkg -x` into `/tmp/libs`, and `file://`
  URLs (no local server needed). Do not install system packages.
- **`pkill -f "http.server 8731"` killed its own command** (exit 144): the pattern also matched the shell running it, so
  the chained `git commit` never ran. Kill by saved PID, or use a bracket pattern (`pkill -f "http.server 873[1]"`), and
  never chain cleanup with commit/push.
- **Layout collisions in diagrams only show up in screenshots**: ring labels collided, a label covered a node, the fixed TOC
  overlapped the cover. Place labels on a larger radius than nodes, reserve space for badges, hide the TOC until
  past the cover, and plan at least two screenshot→fix rounds.
- **13px horizontal overflow on mobile**: find the element with the checker's overflow list (elements whose
  `getBoundingClientRect().right` exceeds the viewport), then wrap it in `.scroll-x` or let it wrap.
- **`hidden` attribute ignored**: `.ctrl{display:flex}` beats the UA `[hidden]` rule, so toggled controls stayed visible.
- **Rare random cases look like bugs**: the stale-read demo hits the stale replica ~13% of the time over 5 reads, so tests
  "failed" to find it. Force the case with a button or seed the first auto-demo.
- **Dynamic text grammar**: interpolated counts need plural rules (Polish: 1 replika / 2–4 repliki / 5+ replik).
- **Dynamically created `.reveal` elements** (quiz questions) stay invisible unless passed to `revealIO.observe()`.
- **Generic class names collide**: a figure's `.sub` card class also matched the cover's `.sub` subtitle and every
  `.ctx-bar.sub`, fading and dashing both. Prefix per-figure classes (`.subag`) and grep the CSS before adding a short name.
- **Long `<select>` options overflow at 390px**: give `.ctrl select` `max-width:100%` and `.two > *` `min-width:0`
  (grid items default to `min-width:auto` and grow to fit `nowrap` content).
