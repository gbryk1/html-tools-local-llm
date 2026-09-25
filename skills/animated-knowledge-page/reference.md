# Reference: code patterns from `docs/cassandra-course.html`

Copy-and-adapt snippets for the steps in `SKILL.md`. All come from the finished course (commit 62026c0).
Line numbers point at `src/cassandra-course.html`.

## 1. Page skeleton

```html
<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>…</title>
<script>document.documentElement.classList.add('js')</script>  <!-- .reveal hides content only when JS runs -->
<style>/* tokens → base → cover → layout → boxes → figures → per-figure → quiz → reduced-motion */</style>
</head>
<body>
<div id="progress"></div>                      <!-- scroll progress bar -->
<nav id="toc">…<a href="#ring">2 · Pierścień</a>…</nav>
<header class="cover">…hero text + decorative animated SVG + scroll hint…</header>
<main>
  <section class="chapter" id="ring">…</section>   <!-- one per concept -->
  …
  <section class="chapter" id="final"><div id="quiz"></div><div class="score" id="score"></div>…cheat sheet…</section>
</main>
<footer>…</footer>
<script>'use strict'; /* helpers → scroll machinery → one IIFE per figure → quiz */</script>
</body></html>
```

## 2. Design tokens with light/dark (lines 10–24)

Every color is a CSS variable; dark mode only overrides variables. Fonts are system stacks — no web fonts.

```css
:root {
  color-scheme: light dark;
  --paper:#fbf8f1; --paper2:#ffffff; --ink:#1c1c22; --mut:#5d5f6b; --line:#d9d3c4; --shadow:#1c1c22;
  --accent:#1b6fa8; --accent2:#e39b2d; --ok:#2f9e63; --bad:#d64545; --warn:#c98a00;
  --pen:#b8431f; --note:#fff4c2; --card:#f1ece0; --code:#f3efe6; --dim:#9aa0ab;
  --hand:"Segoe Print","Bradley Hand","Comic Neue","Comic Sans MS","Chalkboard SE","Marker Felt",cursive;
  --sans:system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  --serif:Charter,"Bitstream Charter","Iowan Old Style",Georgia,"Palatino Linotype",serif;
  --mono:ui-monospace,SFMono-Regular,Menlo,Consolas,monospace;
}
@media (prefers-color-scheme: dark) {
  :root { --paper:#15171c; --paper2:#1d2027; --ink:#e7e5df; --mut:#a3a6b1; --line:#383c49; --shadow:#000;
          --accent:#5aa9e6; --accent2:#f0b34f; --ok:#4cc38a; --bad:#f06b6b; --warn:#f0c040;
          --pen:#ff9a6b; --note:#3a3420; --card:#232730; --code:#22262e; --dim:#5d6270; }
}
[hidden] { display:none !important; }   /* otherwise .ctrl{display:flex} un-hides toggled controls */
.fig svg text { fill:var(--ink); }      /* SVG text follows the theme automatically */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation-duration:.001s !important; animation-iteration-count:1 !important; transition-duration:.001s !important; }
  html { scroll-behavior:auto; }
}
```

JS that paints Canvas or sets inline styles reads the same variables and re-reads on scheme change:

```js
const cssVar = n => getComputedStyle(document.documentElement).getPropertyValue(n).trim();
const C = {};
function readColors() { for (const k of ['ink','paper','paper2','mut','line','accent','accent2','ok','bad','warn','dim','card']) C[k] = cssVar('--' + k); }
readColors();
matchMedia('(prefers-color-scheme: dark)').addEventListener('change', readColors);
```

## 3. Head First box catalogue (CSS lines 76–107)

One `.box` base (2px ink border, offset hard shadow, rotated label tab) plus modifiers:

| class | label used | purpose |
|---|---|---|
| `brain` | 🧠 Mózg na wysokich obrotach | open "think about it" question before a concept |
| `nodumb` | ❓ Nie istnieją głupie pytania | P:/O: (Q/A) grid of naive-but-real questions |
| `pencil` | ✏️ Zaostrz ołówek | exercise; answer in `<details><summary>Odpowiedź</summary>` |
| `fireside` | 🔥 Pogawędka przy kominku | dialogue between two personified concepts |
| `watch` | ⚠️ Uwaga, pułapka | anti-pattern / production pitfall (red border) |
| `geek` | 🤓 Dla dociekliwych | optional deep-dive, smaller font |
| `bullets` | 📌 Celne spostrzeżenia | chapter summary on a slightly rotated sticky note |
| `relax` | 😌 Rozluźnij się / 🎓 Gratulacje | "you don't need to memorize this" / finale |

```css
.box { position:relative; margin:2rem 0; padding:1.1rem 1.25rem 1rem; border:2px solid var(--ink); border-radius:6px;
       background:var(--paper2); box-shadow:5px 5px 0 var(--shadow); }
.box > .lbl { position:absolute; top:-1rem; left:1rem; font:800 .82rem var(--sans); letter-spacing:.06em; text-transform:uppercase;
              background:var(--ink); color:var(--paper); padding:.25rem .65rem; border-radius:4px; transform:rotate(-2deg); }
.box.watch { border-color:var(--bad); box-shadow:5px 5px 0 var(--bad); }
.box.bullets { background:var(--note); transform:rotate(-.4deg); }
.qa { display:grid; grid-template-columns:auto 1fr; gap:.4rem .8rem; }
.fire .line { display:grid; grid-template-columns:7.5rem 1fr; gap:.8rem; }
@media (max-width:560px) { .fire .line { grid-template-columns:1fr; gap:.1rem; } }
```

```html
<div class="box nodumb reveal"><span class="lbl">❓ Nie istnieją głupie pytania</span>
  <div class="qa">
    <div class="q">P:</div><div>Skoro nie ma mastera, kto decyduje, na którym serwerze leży mój wiersz?</div>
    <div class="a">O:</div><div><b>Matematyka.</b> … Rozdział 2.</div>
  </div>
</div>

<div class="box pencil reveal"><span class="lbl">✏️ Zaostrz ołówek</span>
  <p>Tokeny A=10, B=40, C=70, D=90. Kto jest właścicielem kluczy 5, 40, 41 i 95?</p>
  <details><summary>Odpowiedź</summary><p>5 → A … 95 → A (zawijamy przez koniec pierścienia).</p></details>
</div>

<div class="box fireside reveal"><span class="lbl">🔥 Pogawędka przy kominku</span>
  <p class="mut">Dzisiejsi goście: <b>Seed Node</b> i <b>Zwykły Węzeł</b>.</p>
  <div class="fire">
    <div class="line l1"><div class="who">Zwykły Węzeł</div><div>Słyszałem, że jesteś kimś ważnym…</div></div>
    <div class="line l2"><div class="who">Seed</div><div>Nie, jestem po prostu adresem, który nowi znają na pamięć…</div></div>
  </div>
</div>
```

Other small devices: chapter header with a rotated number disc and a handwritten `.tag` subtitle;
`.anno` handwritten arrow note under a figure; `.pull` pull-quote.

## 4. Figure markup

```html
<figure class="fig wide" id="fig-ring">
  <div class="ftitle">▶ Pierścień tokenów <span>wpisz dowolny klucz, np. swoje imię</span></div>
  <div class="ctrl">
    <input type="text" placeholder="klucz partycji" aria-label="klucz partycji">
    <button class="btn primary" data-act="add">Wstaw klucz</button>
    <button class="btn" data-act="node">➕ Dodaj węzeł G</button>
    <button class="btn" data-act="reset">↺ Reset</button>
  </div>
  <div class="two"><svg viewBox="0 0 420 420"></svg><div>…table / live status…</div></div>
  <figcaption>What is simplified vs the real system (e.g. 32-bit hash instead of Murmur3 64-bit).</figcaption>
</figure>
```

- `viewBox` + `width:100%;height:auto` makes SVG scale; a figure that must not shrink below legibility goes in
  `<div class="scroll-x"><svg …></div>` with `.scroll-x{overflow-x:auto} .scroll-x>svg{min-width:620px}`.
- `.two` is a 1-column grid on mobile, 2 columns from 720px.
- A `.status` line under each figure narrates what just happened in one sentence (the "teacher's voice").

## 5. JS helpers (lines 1068–1160)

```js
const $ = (s, r = document) => r.querySelector(s);
const $$ = (s, r = document) => [...r.querySelectorAll(s)];
const REDUCE = matchMedia('(prefers-reduced-motion: reduce)').matches;
const sleep = ms => new Promise(r => setTimeout(r, REDUCE ? 0 : ms));
function S(tag, attrs = {}, parent) {            // SVG element
  const e = document.createElementNS('http://www.w3.org/2000/svg', tag);
  for (const k in attrs) e.setAttribute(k, attrs[k]);
  if (parent) parent.appendChild(e);
  return e;
}
function T(parent, x, y, text, attrs = {}) {      // SVG text, centered
  const t = S('text', Object.assign({ x, y, 'text-anchor': 'middle' }, attrs), parent);
  t.textContent = text; return t;
}
function H(tag, cls, html, parent) {             // HTML element
  const e = document.createElement(tag);
  if (cls) e.className = cls;
  if (html != null) e.innerHTML = html;
  if (parent) parent.appendChild(e);
  return e;
}
const ease = k => (k < .5 ? 2 * k * k : 1 - Math.pow(-2 * k + 2, 2) / 2);
function tween(ms, fn) {                          // promise-based rAF tween; instant under reduced motion
  return new Promise(res => {
    if (REDUCE || ms <= 0) { fn(1); return res(); }
    const t0 = performance.now();
    const step = t => { const k = Math.min(1, (t - t0) / ms); fn(ease(k)); if (k < 1) requestAnimationFrame(step); else res(); };
    requestAnimationFrame(step);
  });
}
function flyDot(parent, x0, y0, x1, y1, { ms = 600, color = C.accent, r = 5 } = {}) {   // "message" travelling between nodes
  const c = S('circle', { cx: x0, cy: y0, r }, parent); c.style.fill = color;
  return tween(ms, k => { c.setAttribute('cx', x0 + (x1 - x0) * k); c.setAttribute('cy', y0 + (y1 - y0) * k); }).then(() => c.remove());
}
```

Because every step returns a promise, a whole mechanism reads as a script:
`await flyDot(client→coord); say('Krok 1: commit log'); await chip(coord→log); …`.
Deterministic demo data: hash strings (`h32('vnode-3-7')`) instead of `Math.random()` so every visit looks the same.

## 6. Scroll machinery (lines 1159–1195)

```js
// fade-in blocks, once
const revealIO = new IntersectionObserver(es => es.forEach(e => {
  if (e.isIntersecting) { e.target.classList.add('shown'); revealIO.unobserve(e.target); }
}), { threshold: 0.12 });
$$('.reveal').forEach(el => revealIO.observe(el));
// CSS: .js .reveal{opacity:0;transform:translateY(26px);transition:.7s} .js .reveal.shown{opacity:1;transform:none}

// active chapter in TOC
const tocIO = new IntersectionObserver(es => es.forEach(e => { if (e.isIntersecting) /* mark link active */; }),
  { rootMargin: '-35% 0px -60% 0px' });

// figures: first() once, enter()/leave() start/stop loops
const figIO = new IntersectionObserver(es => es.forEach(e => {
  const f = e.target._fig; if (!f) return;
  if (e.isIntersecting) {
    if (f.visible) return;
    f.visible = true;
    if (!f.seen) { f.seen = true; f.first && f.first(); }
    f.enter && f.enter();
  } else if (f.visible) { f.visible = false; f.leave && f.leave(); }
}), { threshold: 0.25 });
function registerFig(el, api) { el._fig = api; figIO.observe(el); return api; }
```

Progress bar + "past cover" flag in one rAF-throttled passive scroll listener; the fixed TOC is
`display:none` below 1440px and `opacity:0` until `body.past-cover` (otherwise it overlaps the cover).

## 7. Figure recipes

One IIFE per figure, all state local:

```js
(() => {
  const root = $('#fig-write');
  let queue = Promise.resolve(), pending = 0;
  function enqueue(fn) {                 // serialize animations; ignore button mashing beyond 3
    if (pending >= 3) return;
    pending++;
    queue = queue.then(fn).catch(e => console.error(e)).finally(() => pending--);
  }
  $('[data-act=insert]', root).onclick = () => enqueue(() => doWrite(…));
  $('[data-act=reset]', root).onclick = () => enqueue(async () => { /* clear state, re-render */ });
  registerFig(root, { first() { for (let i = 0; i < 3; i++) enqueue(() => doWrite(…)); } });   // auto-demo
})();
```

Restartable runs (user changes a select mid-animation): bump a `runId` and bail after each `await`:
`const my = ++runId; … await runAlong(…); if (my !== runId) return;`

Loops (gossip ticks, live meters) run only while visible:

```js
registerFig(root, {
  enter() { layout(); draw(); clearInterval(timer); timer = setInterval(tick, REDUCE ? 1500 : 750); },
  leave() { clearInterval(timer); }
});
```

Canvas sized for HiDPI and re-laid-out on resize and on enter (a canvas measured while off-screen may be 0 wide):

```js
function layout() {
  const dpr = devicePixelRatio || 1;
  W = cv.clientWidth || 600;
  cv.width = W * dpr; cv.height = HGT * dpr;
  ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
  /* recompute node positions from W */
}
addEventListener('resize', () => { layout(); draw(); });
```

HTML-element animations (chips flying between boxes laid out with CSS grid) measure both boxes with
`getBoundingClientRect()` relative to the stage and tween a `transform: translate(…)` — this survives
responsive re-layout better than hard-coded SVG coordinates.

## 8. Quiz + cheat sheet (lines 2376–2424)

```js
const Q = [ ['question', ['opt A', 'opt B', 'opt C'], /*correct index*/ 1, 'why the answer is right'], … ];
Q.forEach(([q, opts, ok, why], n) => {
  const d = H('div', 'quiz-q reveal', `<h4>${n + 1}. ${q}</h4><div class="opts"></div><div class="why">💡 ${why}</div>`, box);
  opts.forEach((t, i) => {
    const b = H('button', '', t, $('.opts', d));
    b.onclick = () => {
      if (d.classList.contains('done')) return;
      d.classList.add('done'); answered++;
      if (i === ok) good++; else b.classList.add('wrong');
      $('.opts', d).children[ok].classList.add('right');
      $$('button', d).forEach(x => x.disabled = true);
      upd();                             // sticky "Wynik: 7 / 10" pill
    };
  });
  revealIO.observe(d);                   // dynamically created .reveal must be observed explicitly
});
```

Questions test mechanisms, not trivia; wrong options are the misconceptions the chapters addressed.
Cheat sheet: `table.mini.cheat` (parameter | default | what it does) inside `.scroll-x`, monospace first column.

## 9. Headless test setup that worked on this host

The OpenClaw `browser` tool refused the `localhost` URL of this page, and the system had no
Chromium libraries or fonts. What worked (no sudo, nothing installed system-wide):

```bash
# playwright-core ships inside OpenClaw; its Chromium lives in ~/.cache/ms-playwright/chromium-*
mkdir -p /tmp/libs && cd /tmp/libs
apt-get download libgbm1 libxkbcommon0 libasound2t64 libatk1.0-0t64 libatk-bridge2.0-0t64 libatspi2.0-0t64 \
  libcups2t64 libdrm2 libwayland-server0 libxcomposite1 libxdamage1 libxfixes3 libxi6 libxrandr2 libxrender1 \
  libxres1 libxss1 libxtst6 fonts-dejavu-core fonts-noto-color-emoji
for f in *.deb; do dpkg -x "$f" root; done
cat > fonts.conf <<'EOF'
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig><dir>/tmp/libs/root/usr/share/fonts</dir><cachedir>/tmp/libs/fc-cache</cachedir></fontconfig>
EOF
export LD_LIBRARY_PATH=/tmp/libs/root/usr/lib/x86_64-linux-gnu FONTCONFIG_FILE=/tmp/libs/fonts.conf
node skills/animated-knowledge-page/scripts/check-page.cjs docs/<page>.html /tmp/shots
```

Package names are Ubuntu 24.04+ (`t64` suffixes); if Chromium still fails to start, `ldd` the
`chrome-headless-shell` binary and download whatever reports `not found`.
