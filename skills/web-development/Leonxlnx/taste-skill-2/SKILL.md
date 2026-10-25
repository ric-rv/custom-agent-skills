---
name: taste-skill-2
description: >-
  tasteskill v2, the anti-slop frontend skill. Art direction for websites, distilled from a study of
  247 curated gallery sites (One Page Love, Awwwards Sites of the Day). Deals researched directions
  (idea, composition, type, palette, photographs, section blueprints) from a library, enforces a strict
  no-slop house style with a real-browser inspector, and runs a look-and-fix loop on screenshots. Use
  this whenever you build, design, redesign, restyle, polish or review a landing page, marketing site,
  portfolio, product page, one-pager, hero or any public-facing web page, in any stack (HTML/CSS, React,
  Next.js, Vue, Svelte, Astro, Tailwind) — also when the user says a page looks generic, templated,
  "AI-made", sloppy, or asks to make it look designed, premium, award-level or less like every other
  site. Also for app screens: dashboards, admin and analytics views, settings, inboxes and other screens
  people work in, with their own run and rules.
  (Part 2 of 2; core workflow in taste-skill-1.)
---
# tasteskill v2 (part 2 of 2)

Continues [taste-skill-1](../taste-skill-1/SKILL.md), which holds the core workflow. This part holds sections references/motion.md, references/scenes.md, references/critique.md, references/tells.md, references/research.md, README.md.

---

## references/motion.md

### Motion

Read this before adding any animation. The static page must already be finished and passing
`inspect.mjs`; motion is the last pass, never a way to rescue a weak layout.

#### Contents

1. The budget
2. What strong pages do with motion
3. Four questions before any animation
4. Tokens
5. Scroll behaviours, ranked
6. Recipes (copy, then adapt)
7. Signature moves
8. Reduced motion and performance
9. What gives generated motion away
10. Rules for motion

#### 1. The budget

A page that does not move reads as a mock-up; the inspector counts what moves while the page loads and
scrolls, and fails it under eight elements. The motion layer has five parts:

- **Two or three scroll scenes:** the big, scroll-driven moments award sites are remembered for (a
  camera flying through a field of pictures, a picture that grows from a window to the whole screen,
  type that crosses a held stage, cards that deal out and stack). The direction sheet deals them from
  `library/scenes.json` when the library has scenes for the brief; `references/scenes.md` says how to
  fill and fit them. They are where the page is bold; everything else stays quiet so they land.

- **One signature moment:** the thing a visitor would describe an hour later: the headline that rises
  out of a mask, the image that opens like a shutter, the wordmark that scales with the scroll. The
  direction sheet from `draw.mjs` names one. Build that one well; it is the only move allowed to be
  loud.
- **Section entrances, choreographed per section:** the parts of each section arrive in reading order
  (heading, text, picture, details), staggered 60–90ms, rising 16–32px with opacity, once. Vary the
  manner with the content instead of stamping one preset everywhere: a list arrives row by row, a
  picture opens from a mask or settles from a slight scale, a figure counts up once, a statement rises
  line by line.
- **Feedback under the hand:** buttons that give on press, links that answer the pointer, cards and
  pictures that respond on hover, a menu that opens from where it was clicked.
- **One moving picture:** a found clip as a muted loop with a poster frame, a slow drift or scale on
  a large photograph, or a scroll-linked move on the hero picture.

What is still banned: the same fade-and-slide-up with the same timing on every block, which is the most
cited motion tell of generated pages; motion that hides content until a script runs, with no fallback;
bounce and elastic easing; anything that animates layout properties. Uniform motion says nobody decided
anything; choreographed motion with one protected moment says somebody did.

#### 2. What strong pages do with motion

Measured on the latest 99 Awwwards Sites of the Day (July to October 2026), at 1440 and 390, with
the transitions, tweens and scroll triggers recorded while each page loaded and was scrolled. Where
the gallery does something the house rules ban, the house version follows.

- **The stack.** Two in three use a smooth-scroll library and three in five ship Three.js; GSAP is
  named on 56. The quiet layer below (reveals, line rises, the ink fill) needs none of it: CSS scroll
  timelines and view transitions do that work, though only 3 and 6 of the sites use them. The big
  scroll scenes are built on GSAP ScrollTrigger, as on the award sites, through the shared stage in
  `assets/scenes/` (`references/scenes.md`).
- **Curves.** The curves that really ran are strong ease-outs: expo out (`.16,1,.3,1` and
  `.19,1,.22,1`) ran on 14 sites, cubic out on 13, quint out on 7, and by number of transitions the
  quint and expo outs lead every chosen curve. In-out curves are kept for wipes and things that
  travel (cubic and quart in-out, about 15 sites each). Ease-in appears only for exits, short, before
  a slow arrival. Colour changes use plain `ease` (46 sites). Overshoot sits in 19 stylesheets and
  ran on 2.
- **Durations.** Hover colour 200-300 ms; small interface moves 300-450 ms; reveals and line rises
  600-1,000 ms; picture openings and wipes 1,100-1,600 ms. The median of everything that ran on a
  site is 420 ms.
- **Staggers.** 20-40 ms between characters, 75-120 ms between lines, 50-100 ms between list items.
- **Scroll-linked motion is locked to the scrollbar.** Of the sites that scrub, 14 of 18 lock it with
  no smoothing; the other four smooth it by 0.1-3 s. Reveals fire when the element's top is 80-95% of the way
  down the viewport, once.
- **How much moves.** A median of 130 elements are moved by script on a page, but they come from a
  few gestures: one split heading is 20-60 elements. The inspector's floor (8, warning under 16) is a
  floor, not a target.
- **Waiting is the most common cost.** 60 of 99 open on a loading screen, 26 of them with a counter.
  Half the usable pages were still unreadable 2.5 s after the browser said the page had loaded, a
  third at 4.5 s. The preloaders were not covering slow pages (their documents loaded faster than the
  rest) and the readers' design marks were the same whatever the wait; only usability fell. House
  version: no preloader, the message readable on the first frame, the load sequence over by 1.2 s.
- **Pins cost length.** Two in three scrolling pages hold something sticky or pinned. Those pages
  are twice as long (a median 16.6 screens against 7.5) for fewer words per screen (27 against 46).
  House version: at most two held stages, about one screen per step, three screens per stage.
- **Reduced motion is mostly missing.** 35 of 99 have any `prefers-reduced-motion` rule, 16 have
  three or more; 5 of 26 scroll-scrubbed scenes have one. Every recipe here keeps the finished state
  as the reduced state.

#### 3. Four questions before any animation

1. **How often will someone see it?** Once per visit (hero load, a section reveal): it can take its
   time. Many times per visit (hover, menu, accordion): fast and small. Hundreds of times (keyboard
   actions, typing): no animation.
2. **What is it for?** Valid answers: it shows where something came from, it confirms an action, it
   keeps a change from being jarring, it explains how the product works, it is the signature moment.
   "It looks nice" is only valid for the signature moment.
3. **Which easing?** Entering or leaving: ease-out, so movement starts the instant the eye arrives.
   Moving between two places on screen: ease-in-out. Colour and opacity on hover: `ease`. Constant
   travel (marquee, progress): `linear`. `ease-in` makes interfaces feel slow because the first frames
   barely move; do not use it. The CSS keyword curves are weak, so use the tokens below.
4. **How long?** Press feedback 100–160ms. Hover 150–200ms. Menus and popovers 150–250ms. Dialogs and
   drawers 250–450ms. Section and hero reveals 500–900ms. Leaving is quicker than arriving (about 70%).

#### 4. Tokens

```css
:root {
  --ease-out: cubic-bezier(0.22, 1, 0.36, 1);        /* entrances, moving hovers, UI under 600ms */
  --ease-expo: cubic-bezier(0.16, 1, 0.3, 1);        /* new: reveals of 800ms and longer, line rises, openings */
  --ease-in-out: cubic-bezier(0.76, 0, 0.24, 1);     /* wipes, panels, things that travel while visible */
  --ease-soft: cubic-bezier(0.33, 1, 0.68, 1);       /* slow scale and drift on photographs */
  --ease-exit: cubic-bezier(0.55, 0.055, 0.675, 0.19); /* new: something leaving for good, short */
  --t-press: 140ms;
  --t-hover: 180ms;
  --t-ui: 240ms;
  --t-reveal: 800ms;
  --t-open: 1200ms;                                  /* new: picture openings and clip wipes */
  --stagger-line: 90ms;                              /* new */
  --stagger-item: 70ms;                              /* new */
}
```

How the study bears on each:

- `--ease-out` (quint out) is in 28 stylesheets with its near twin and is the single most frequent
  chosen curve among transitions that ran. Keep it.
- `--ease-expo` is new. Expo out (`.16,1,.3,1` and `.19,1,.22,1`) is in 28 stylesheets and ran on 14
  sites, more than any other chosen family, and it is the curve the long reveals use: line rises,
  picture openings, card entrances of 0.9-1.6 s. Use it for anything at `--t-reveal` or longer; it
  replaces `--ease-out` in the masked headline and the reveal-on-scroll recipes.
- `--ease-in-out` (quart in-out) matches its family (14 stylesheets, 7 ran). Keep it for wipes,
  shutters, menus and page transitions.
- `--ease-soft` (cubic out) matches the cubic-out family (21 stylesheets, 13 ran), but the study uses it
  for interface moves of 0.3-0.8 s, where `--ease-out` already serves. Narrow it to slow scale and
  drift on photographs.
- `--ease-exit` is new. Ease-in is right for exactly one job: something that leaves for good (an
  outgoing caption, a replaced slide, a closing panel), short, at about 60-70% of the matching
  entrance. Never for anything the visitor is waiting to see.
- Not adopted: `.4,0,.2,1` (38 stylesheets) is a framework default, and overshoot curves (19) stay
  banned on interface elements.
- `--t-hover` stays at 180ms. The study's colour hovers run 200-300ms; a little quicker reads as
  more exact. A hover that moves something (a label roll, an arrow) takes `--t-ui` to 400ms.

#### 5. Scroll behaviours, ranked

| Behaviour | Pages of 99 | What it serves | House version |
| --- | --- | --- | --- |
| Smooth-scroll library | 67 | A feeling of weight; makes scrubbed scenes easier to build | Optional, through `Stage.smooth()`: Lenis at lerp 0.1-0.14, off for touch and reduced motion |
| Held (sticky or pinned) stage | 44 | One picture or object carries several claims; chapters | Yes: the scroll scenes (`references/scenes.md`), two or three per page, one to four screens each; other sticky stages three screens at most |
| Split text | 40 | Lines and words arriving as they are read; hover rolls | Lines for headings and statements; words only for the ink fill; characters only for a heading of one to three words |
| Colour by chapter | 34 | Tells chapters apart without padding bands | Yes, as hard cuts at section edges; the header ink follows in 300ms |
| Scroll-scrubbed scene (camera, object, image sequence) | 26 | Explains a product by moving it | Yes, from the scene library, built on the shared stage with a finished composition for reduced motion |
| Parallax depth | 24 | Depth in collages; pictures drifting inside oversized frames | Travel under 8% of the element, pictures held at 106-110% in their frames |
| Marquee | 21 | Life on a static band | Existing "Edge-to-edge marquee": one per page, pausable |
| Masked line or word rise | 18 | Headings that arrive like set type | Yes: "Masked line reveal" on load, "Lines that rise on scroll" below the fold |
| Wheel drives a scene, no page scroll | 16 | Browsing one object | Not used (see 2.6) |
| Blur-in | 15 | Soft arrival | At most 8px of blur, 600ms, gone once settled; never on body text |
| Picture from inset frame to full-bleed | 14 | The hand-over from a type screen to the big picture | Yes: "Opening window", about one screen of scroll |
| Grey-to-ink text fill | 14 | Paces one statement | Yes, once per page, starting at 45% ink: "Ink fill" |
| Sheet slides over a held layer | 11 | Page-turn rhythm between chapters | Yes: new move "Sheet over a held picture" |
| Scramble or decode | 11 | A "code" voice | Not used (see 2.6) |
| Header ink by chapter | 10 | The fixed header stays legible | Yes, with colour by chapter |
| Horizontal track pinned to vertical scroll | 8 | Walking through rooms or a collection | Native drag row first; pinned only when the row is under three screens long, with keyboard support: "Sideways gallery" |
| Curtain footer | 8 | The page ends as a scene | Existing move |
| Rolling digits | 6 | Figures that arrive | Yes, for pages whose case is a handful of numbers: "Rolling figures" |
| Index with hover preview | 5 | Navigating work by name | Existing move, upgraded recipe |

Text, split by unit: characters on about 20 pages, lines on about 14, words on about 11. Character
splits serve short headings and button rolls; on long statements they leave fragments mid-scroll.

#### 6. Recipes

All recipes keep the content visible when JavaScript is off, put every hidden state inside
`prefers-reduced-motion: no-preference`, and use the tokens above. Two notes that apply to several:

- **Scroll timelines need a scroller to watch.** `animation-timeline: view()` takes the nearest scroll
  container, and `overflow: hidden` makes one. A picture inside an `overflow: hidden` frame therefore
  never animates. Use `overflow: clip` on frames, or name the timeline on the section
  (`view-timeline-name: --hero`) and point the children at that name. This also applies to the
  existing "Scroll-linked progress" recipe.
- **Scroll-linked means linear.** The scroll is the easing. 14 of the 18 scrubbing sites in the study
  lock motion to the scrollbar, which is what CSS scroll timelines do.

All recipes keep content visible when JavaScript is off or slow: the hidden state only applies under
`html.js`, which a one-line inline script sets.

```html
<script>document.documentElement.classList.add('js')</script>
```

##### Load sequence in 1.2 seconds

Everything is in the HTML and painted on the first frame; the sequence only adds arrival. Nothing
waits for the load event, and nothing in the navigation animates.

```html
<header class="hero">
  <h1 class="display lines">
    <span class="line"><span data-line style="--i:0">Stools for</span></span>
    <span class="line"><span data-line style="--i:1">small kitchens</span></span>
  </h1>
  <p class="lead" data-load style="--d:420ms">…</p>
  <a class="button" data-load style="--d:480ms" href="#stools">See the stools</a>
  <figure class="hero__picture" data-open><img src="stool.jpg" alt="…" fetchpriority="high"></figure>
</header>
```

```css
.hero__picture { overflow: clip; margin: 0; }
@media (prefers-reduced-motion: no-preference) {
  .js .hero [data-line] { transform: translateY(105%); animation: load-line 800ms var(--ease-expo) forwards; animation-delay: calc(100ms + var(--i) * var(--stagger-line)); }
  .js .hero [data-load] { opacity: 0; transform: translateY(12px); animation: load-rise 500ms var(--ease-out) forwards; animation-delay: var(--d); }
  .js .hero [data-open] { clip-path: inset(0 0 100% 0); animation: load-open 1000ms var(--ease-in-out) 150ms forwards; }
  .js .hero [data-open] img { transform: scale(1.08); animation: load-settle 1100ms var(--ease-expo) 100ms forwards; }
}
@keyframes load-line { to { transform: none; } }
@keyframes load-rise { to { opacity: 1; transform: none; } }
@keyframes load-open { to { clip-path: inset(0); } }
@keyframes load-settle { to { transform: none; } }
```

The timeline: the headline's lines rise from 100 to 990 ms, the picture opens from 150 to 1,150 ms,
the sentence and the button arrive from 420 to 980 ms. All settled by 1.2 s, four things at most.
Preload the display font (`<link rel="preload" as="font" type="font/woff2" crossorigin>`) so the lines
rise in the real face, and give the picture `fetchpriority="high"` and a ground colour sampled from it,
so a slow image opens onto its own colour rather than a blank box. Study: 22 of 91 pages were readable
at the first intro frame and 11 more by 1.2 s; the intros the readers called respectful finished in
about 1-1.2 s; a third of the pages were still unreadable at 4.5 s.

##### Masked line reveal (the classic gallery headline)

Each line slides up from behind its own baseline. Because headlines are capped at two lines, you set
the line breaks yourself and wrap each line.

```html
<h1 class="lines">
  <span class="line"><span data-line style="--i:0">Stools for</span></span>
  <span class="line"><span data-line style="--i:1">small kitchens</span></span>
</h1>
```

```css
.lines .line { display: block; overflow: hidden; padding-bottom: 0.08em; margin-bottom: -0.08em; }
.lines [data-line] { display: block; }
@media (prefers-reduced-motion: no-preference) {
  .js .lines [data-line] {
    transform: translateY(105%);
    animation: line-up 900ms var(--ease-out) forwards;
    animation-delay: calc(var(--i) * 110ms + 150ms);
  }
}
@keyframes line-up { to { transform: none; } }
```

The `padding-bottom` / negative margin pair stops descenders (g, y, p) being clipped by the mask.
On a narrow phone the two authored lines may each wrap; check the mobile screenshot, and if they do,
author a shorter mobile break with a `<br class="only-wide">` pattern or reduce the size.

##### Reveal on scroll (once)

For the two or three sections that deserve it, not for every block.

```css
@media (prefers-reduced-motion: no-preference) {
  .js [data-reveal] { opacity: 0; transform: translateY(24px); transition: opacity 700ms var(--ease-out), transform 900ms var(--ease-out); }
  .js [data-reveal].is-in { opacity: 1; transform: none; }
}
```

```js
const io = new IntersectionObserver((entries) => {
  for (const e of entries) if (e.isIntersecting) { e.target.classList.add('is-in'); io.unobserve(e.target); }
}, { rootMargin: '0px 0px -12% 0px', threshold: 0.1 });
document.querySelectorAll('[data-reveal]').forEach((el) => io.observe(el));
```

Never attach reveals with a scroll listener, never replay them when the element re-enters, and never
leave anything at `opacity: 0` if the observer fails to fire (the `html.js` gate handles no-JS; the
`unobserve` handles replays).

##### Image shutter

An image opens from one edge while scaling down slightly inside its frame. Gallery staple; use it for
the one hero or showcase image.

```css
.shutter { overflow: hidden; }
@media (prefers-reduced-motion: no-preference) {
  .js .shutter { clip-path: inset(0 0 100% 0); transition: clip-path 1100ms var(--ease-in-out); }
  .js .shutter img { transform: scale(1.12); transition: transform 1500ms var(--ease-soft); }
  .js .shutter.is-in { clip-path: inset(0); }
  .js .shutter.is-in img { transform: none; }
}
```

##### Press and hover

```css
.button { transition: transform var(--t-press) var(--ease-out), background-color var(--t-hover) ease, color var(--t-hover) ease; }
.button:active { transform: scale(0.97); }
.link { text-decoration: underline; text-decoration-color: transparent; text-underline-offset: 0.2em; text-decoration-thickness: 0.07em; transition: text-decoration-color var(--t-hover) ease; }
@media (hover: hover) and (pointer: fine) {
  .button:hover { background-color: var(--accent-strong); }
  .link:hover { text-decoration-color: currentColor; }
}
```

Hover styles go behind `(hover: hover)` because touch devices fire hover on tap and leave it stuck.
Hover should raise contrast, never lower it. Do not change font weight on hover (the text reflows).
Do not lift or scale every card on hover; one consistent, small response is enough.

##### Scroll-linked progress without JavaScript

For a wordmark that scales as the hero leaves, an image that drifts a few percent, or a progress bar.
Wrap in `@supports` so browsers without scroll timelines get the static state.

```css
@supports (animation-timeline: view()) {
  @media (prefers-reduced-motion: no-preference) {
    .drift { animation: drift linear both; animation-timeline: view(); animation-range: entry 0% exit 100%; }
    @keyframes drift { from { transform: translateY(-4%); } to { transform: translateY(4%); } }
  }
}
```

Keep the travel small (under 8% of the element). Large parallax makes text hard to read and looks
dated.

##### Pinned story

A section whose heading stays put while items pass. Use `position: sticky`; do not hijack scrolling.

```css
.story { display: grid; grid-template-columns: 5fr 7fr; gap: var(--gutter); align-items: start; }
.story__title { position: sticky; top: 18vh; }
@media (max-width: 800px) { .story { grid-template-columns: 1fr; } .story__title { position: static; } }
```

##### Index with preview, anchored to the row

Rows of names; pointing at a row or tabbing to it opens one frame level with that row. The frame
follows the row, never the pointer.

```html
<section class="index">
  <ul class="index__list">
    <li><a class="index__row" href="/work/harbour-house" data-preview="/img/harbour-house.jpg">
      <span class="index__name">Harbour House</span><span class="index__year">2025</span>
      <img class="index__thumb" src="/img/harbour-house-small.jpg" alt="" loading="lazy" width="640" height="400">
    </a></li>
    <!-- … -->
  </ul>
  <div class="index__frame" aria-hidden="true"><img alt=""></div>
</section>
```

```css
.index { position: relative; }
.index__list { list-style: none; margin: 0; padding: 0; }
.index__row { display: flex; flex-wrap: wrap; justify-content: space-between; align-items: baseline; gap: 0 var(--gutter); padding-block: 0.3em; font-size: var(--step-head); color: inherit; text-decoration: none; transition: opacity var(--t-hover) ease; }
.index__thumb { order: -1; flex-basis: 100%; width: 100%; height: auto; margin-bottom: 0.4rem; }
.index__frame { display: none; }
@media (hover: hover) and (pointer: fine) {
  .index__list { max-width: 62%; }
  .index__thumb { display: none; }
  .index__list:has(.index__row:hover, .index__row:focus-visible) .index__row:not(:hover, :focus-visible) { opacity: 0.4; }
  .index__frame { display: block; position: absolute; top: 0; right: var(--margin); width: 30%; aspect-ratio: 4 / 3; z-index: 1; pointer-events: none; clip-path: inset(100% 0 0 0); transition: clip-path 320ms var(--ease-out), transform 360ms var(--ease-out); }
  .index__frame.is-open { clip-path: inset(0); }
  .index__frame img { width: 100%; height: 100%; object-fit: cover; }
}
@media (prefers-reduced-motion: reduce) { .index__frame { transition: none; } }
```

```js
(() => {
  const root = document.querySelector('.index');
  if (!root) return;
  const frame = root.querySelector('.index__frame');
  const picture = frame.querySelector('img');
  const fine = matchMedia('(hover: hover) and (pointer: fine)');
  let warmed = false;
  const show = (row) => {
    if (!fine.matches) return;
    if (!warmed) { warmed = true; root.querySelectorAll('[data-preview]').forEach((a) => { new Image().src = a.dataset.preview; }); }
    picture.src = row.dataset.preview;
    const y = row.offsetTop + row.offsetHeight / 2 - frame.offsetHeight / 2;
    const max = root.offsetHeight - frame.offsetHeight;
    const opening = !frame.classList.contains('is-open');
    if (opening) frame.style.transitionProperty = 'clip-path';   // open in place, do not slide in from the top
    frame.style.transform = `translateY(${Math.min(max, Math.max(0, y))}px)`;
    if (opening) { frame.getBoundingClientRect(); frame.style.transitionProperty = ''; }
    frame.classList.add('is-open');
  };
  const hide = () => frame.classList.remove('is-open');
  root.querySelectorAll('.index__row').forEach((row) => {
    row.addEventListener('pointerenter', () => show(row));
    row.addEventListener('focus', () => show(row));
  });
  root.addEventListener('pointerleave', hide);
  root.addEventListener('focusout', (e) => { if (!root.contains(e.relatedTarget)) hide(); });
})();
```

On touch screens each row shows its own picture above the name. Study: 5 pages navigate work this way;
frames from about 470x270 to large plates behind the list; the other rows dimmed to about 0.3 (0.4 here, the floor for dimmed text). The
image trails and cursor-borne previews seen elsewhere in the study are the gimmick version.

##### Lines that rise on scroll

For a section heading or a statement whose line breaks you do not control. Splits after the fonts
load, reveals once, then gives the plain text back so it rewraps normally. Plain text only (no links or
emphasis inside).

```html
<h2 class="head" data-lines>Turned by hand in one small workshop</h2>
```

```css
[data-lines] .line { display: block; overflow: clip; padding-bottom: 0.12em; margin-bottom: -0.12em; }
[data-lines] .line > span { display: block; }
@media (prefers-reduced-motion: no-preference) {
  .is-split .line > span { transform: translateY(110%); }
  .is-split.is-in .line > span { transform: none; transition: transform 900ms var(--ease-expo) calc(var(--i) * var(--stagger-line)); }
}
```

```js
(() => {
  const els = [...document.querySelectorAll('[data-lines]')];
  if (!els.length || !('IntersectionObserver' in window) || matchMedia('(prefers-reduced-motion: reduce)').matches) return;
  const restore = (el) => { el.textContent = el.dataset.text; el.classList.remove('is-split', 'is-in'); };
  const split = (el) => {
    const text = el.textContent.trim().replace(/\s+/g, ' ');
    el.dataset.text = text;
    el.textContent = '';
    const words = text.split(' ').map((word) => {
      const s = document.createElement('span');
      s.style.display = 'inline-block';
      s.textContent = word;
      el.append(s, ' ');
      return s;
    });
    const lines = [];                                   // group the words by the line they landed on
    for (const w of words) {
      const last = lines.at(-1);
      if (last && Math.abs(last.top - w.offsetTop) < 4) last.words.push(w.textContent);
      else lines.push({ top: w.offsetTop, words: [w.textContent] });
    }
    el.textContent = '';
    lines.forEach((line, i) => {
      const mask = document.createElement('span');
      const inner = document.createElement('span');
      mask.className = 'line';
      inner.style.setProperty('--i', i);
      inner.textContent = line.words.join(' ');
      mask.append(inner);
      el.append(mask, ' ');
    });
    el.classList.add('is-split');
  };
  const io = new IntersectionObserver((entries) => {
    for (const e of entries) {
      if (!e.isIntersecting) continue;
      io.unobserve(e.target);
      e.target.classList.add('is-in');
      e.target.querySelector('.line:last-of-type > span')
        .addEventListener('transitionend', () => restore(e.target), { once: true });
    }
  }, { rootMargin: '0px 0px -12% 0px' });
  document.fonts.ready.then(() => els.forEach((el) => { split(el); io.observe(el); }));
  let width = innerWidth;                               // a width change before the reveal: give the text back
  addEventListener('resize', () => {
    if (innerWidth === width) return;
    width = innerWidth;
    els.filter((el) => el.matches('.is-split:not(.is-in)')).forEach((el) => { io.unobserve(el); restore(el); });
  });
})();
```

Study: masked rises from 100-120% below the line, 0.6-1.2 s, 75-120 ms between lines, triggered when
the block's top is 80-95% down the viewport. Reduced motion: the script does not run; the text is plain.

##### Opening window

The hand-over from a type screen to the one big picture: the picture first shows as a window in the
middle of a held stage and opens to full-bleed over about one screen of scroll.

```html
<section class="opening">
  <div class="opening__stage">
    <img src="workshop-wide.jpg" alt="The workshop at first light, benches cleared" width="2400" height="1500">
  </div>
</section>
```

```css
.opening__stage { height: 100svh; overflow: clip; }
.opening__stage img { display: block; width: 100%; height: 100%; object-fit: cover; }
@supports (animation-timeline: view()) {
  @media (prefers-reduced-motion: no-preference) {
    .opening { height: 200svh; view-timeline-name: --opening; --inset-y: 20%; --inset-x: 28%; }
    .opening__stage { position: sticky; top: 0; animation: opening-window linear both; animation-timeline: --opening; animation-range: contain 0% contain 75%; }
    .opening__stage img { animation: opening-settle linear both; animation-timeline: --opening; animation-range: contain 0% contain 75%; }
  }
}
@media (max-width: 700px) { .opening { --inset-y: 18%; --inset-x: 8%; } }
@keyframes opening-window { from { clip-path: inset(var(--inset-y) var(--inset-x)); } to { clip-path: inset(0); } }
@keyframes opening-settle { from { transform: scale(1.15); } to { transform: none; } }
```

The section is two screens tall; the stage is held for one, and the window is fully open after three
quarters of it, so the full-bleed picture rests for a moment before the page moves on. Study: 14 pages;
start windows 38-60% of the width; runways 600-1,800 px, and the readers asked for one to two screens.
Without scroll timelines, and under reduced motion, the picture is a full-bleed screen.

##### Held picture, passing captions

The pinned story built for photographs: the picture holds on one side while short captions pass on
the other; the caption at the middle of the screen is lit and its picture is shown.

```html
<section class="steps">
  <figure class="steps__media">
    <div class="steps__pictures">
      <img src="seasoning.jpg" alt="Ash boards stacked to season" class="is-on">
      <img src="turning.jpg" alt="A leg being turned on the lathe">
      <img src="finish.jpg" alt="Oil rubbed into a finished seat">
    </div>
    <figcaption class="steps__count" aria-hidden="true"></figcaption>
  </figure>
  <ol class="steps__list">
    <li class="steps__item"><h3>Seasoned for a year</h3><p>…</p></li>
    <li class="steps__item"><h3>Turned by hand</h3><p>…</p></li>
    <li class="steps__item"><h3>Finished with oil</h3><p>…</p></li>
  </ol>
</section>
```

```css
.steps { display: grid; grid-template-columns: 7fr 5fr; column-gap: var(--gutter); }
.steps__media { margin: 0; align-self: start; }           /* a stretched grid item cannot stick */
.steps__pictures img { display: block; width: 100%; height: auto; }
.steps__list { list-style: none; margin: 0; padding: 0; }
.steps__item { min-height: 80svh; display: flex; flex-direction: column; justify-content: center; }
.js .steps__media { position: sticky; top: 0; height: 100svh; display: flex; flex-direction: column; justify-content: center; gap: 0.75rem; }
.js .steps__pictures { position: relative; aspect-ratio: 4 / 5; max-height: 80svh; }
.js .steps__pictures img { position: absolute; inset: 0; height: 100%; object-fit: cover; opacity: 0; transition: opacity 500ms ease; }
.js .steps__pictures img.is-on { opacity: 1; }
.js .steps__item { opacity: 0.4; transition: opacity var(--t-ui) ease; }
.js .steps__item.is-active { opacity: 1; }
@media (max-width: 800px) {
  .steps { display: block; }                               /* the section, not a grid area, contains the sticky picture */
  .js .steps__media { height: auto; z-index: 1; background: var(--bg); padding-block: 0.5rem; }
  .js .steps__pictures { aspect-ratio: 3 / 2; max-height: 42svh; }
  .steps__item { min-height: 60svh; }
}
@media (prefers-reduced-motion: reduce) { .js .steps__pictures img, .js .steps__item { transition: none; } }
```

```js
(() => {
  const root = document.querySelector('.steps');
  if (!root || !('IntersectionObserver' in window)) return;
  const items = [...root.querySelectorAll('.steps__item')];
  const pictures = [...root.querySelectorAll('.steps__pictures img')];
  const count = root.querySelector('.steps__count');
  const show = (i) => {
    items.forEach((el, k) => el.classList.toggle('is-active', k === i));
    pictures.forEach((el, k) => el.classList.toggle('is-on', k === i));
    if (count) count.textContent = `${i + 1} of ${items.length}`;
  };
  const io = new IntersectionObserver((entries) => {
    for (const e of entries) if (e.isIntersecting) show(items.indexOf(e.target));
  }, { rootMargin: '-45% 0px -45% 0px' });                 // a band across the middle of the screen
  items.forEach((el) => io.observe(el));
  show(0);
})();
```

Without JavaScript the pictures and captions are two plain columns. Study: inactive items at 20-40%
(dims of 10-15% read as missing text, so the floor here is 40%), crossfades of 400-600 ms, about one
screen per step; the readers asked for a visible count on any held sequence of more than two steps.
The count is a plain sentence in the body face, not a zero-padded numeral.

##### Sideways gallery

A row of pictures that the vertical scroll moves sideways while the stage is held, for a short
collection (eight items or fewer). The native drag row is the base; the pinned version is added only
on wide screens with motion allowed, and only when the row is under three screens long.

```html
<section class="gallery">
  <div class="gallery__stage">
    <h2 class="head">Eight kitchens, one stool</h2>
    <ul class="gallery__track">
      <li class="gallery__item"><a href="/kitchens/leith"><img src="leith.jpg" alt="A narrow galley kitchen in Leith" width="1200" height="1500"><span>Leith</span></a></li>
      <!-- … -->
    </ul>
  </div>
</section>
```

```css
.gallery__track { display: flex; gap: var(--gutter); list-style: none; margin: 0; padding: 0 var(--margin); overflow-x: auto; scroll-snap-type: x mandatory; scroll-padding-inline: var(--margin); }
.gallery__item { flex: 0 0 min(72vw, 28rem); scroll-snap-align: start; }
.gallery__item img { display: block; width: 100%; height: auto; aspect-ratio: 4 / 5; object-fit: cover; }
.gallery.is-pinned .gallery__stage { position: sticky; top: 0; height: 100svh; display: flex; flex-direction: column; justify-content: center; gap: 2rem; overflow: clip; }
.gallery.is-pinned .gallery__track { overflow: visible; scroll-snap-type: none; }
.gallery.is-pinned .gallery__item { flex-basis: calc(62svh * 0.8); }
```

```js
(() => {
  const root = document.querySelector('.gallery');
  if (!root) return;
  const track = root.querySelector('.gallery__track');
  const wide = matchMedia('(min-width: 900px) and (prefers-reduced-motion: no-preference)');
  let dx = 0, queued = false;
  const place = () => {
    queued = false;
    if (!root.classList.contains('is-pinned')) return;
    const p = Math.min(1, Math.max(0, -root.getBoundingClientRect().top / dx));
    track.style.transform = `translate3d(${(-p * dx).toFixed(1)}px, 0, 0)`;
  };
  const measure = () => {
    root.classList.add('is-pinned');                     // measure the row as it would be when pinned
    track.style.transform = '';
    dx = track.scrollWidth - track.clientWidth;
    const pin = wide.matches && dx > 0 && dx < innerHeight * 3;
    root.classList.toggle('is-pinned', pin);
    root.style.height = pin ? `${innerHeight + dx}px` : ''; // one pixel of scroll moves the row one pixel
    place();
  };
  track.addEventListener('focusin', (e) => {             // keyboard: bring the focused item into view
    if (!root.classList.contains('is-pinned')) return;
    const item = e.target.closest('.gallery__item');
    const x = Math.min(dx, Math.max(0, item.offsetLeft - parseFloat(getComputedStyle(track).paddingLeft)));
    scrollTo({ top: root.getBoundingClientRect().top + scrollY + x, behavior: 'instant' });
  });
  addEventListener('scroll', () => { if (!queued) { queued = true; requestAnimationFrame(place); } }, { passive: true });
  addEventListener('resize', measure);
  addEventListener('load', measure);
  wide.addEventListener('change', measure);
  measure();
})();
```

Study: 8 pages pinned a horizontal track; their pages ran a median 25 screens, and the readers' worst
cases spent 9 screens on three cards and 10,000-23,000 px of wheel on one track. Here the speed is 1:1
and the hold ends when the last picture reaches the margin. Phones, narrow windows, reduced motion and
long rows all get the native row with snapping, which also works with touch, trackpads and the
keyboard. Never put the only copy of a call to action inside the moving row.

##### Receding hero

As the first screen leaves, its picture sinks a little and darkens while the words lift away a little
faster, so the hero recedes instead of simply scrolling off.

```html
<header class="hero">
  <img class="hero__picture" src="kitchen.jpg" alt="…" width="2400" height="1600" fetchpriority="high">
  <div class="hero__copy"><h1 class="display">…</h1><p class="lead">…</p></div>
</header>
```

```css
.hero { position: relative; min-height: 100svh; overflow: clip; display: grid; align-items: end; view-timeline-name: --hero; }
.hero__picture { position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; }
.hero::after { content: ''; position: absolute; inset: 0; background: var(--ink); opacity: 0; pointer-events: none; }
.hero__copy { position: relative; z-index: 1; padding: var(--margin); }
@supports (animation-timeline: view()) {
  @media (prefers-reduced-motion: no-preference) {
    .hero__picture { animation: hero-sink linear both; animation-timeline: --hero; animation-range: exit 0% exit 100%; }
    .hero::after { animation: hero-dim linear both; animation-timeline: --hero; animation-range: exit 0% exit 100%; }
    .hero__copy { animation: hero-lift linear both; animation-timeline: --hero; animation-range: exit 0% exit 70%; }
  }
}
@keyframes hero-sink { to { transform: translateY(8%) scale(1.06); } }
@keyframes hero-dim { to { opacity: 0.35; } }
@keyframes hero-lift { to { transform: translateY(-6%); opacity: 0; } }
```

The `exit` range runs from the moment the hero's top meets the top of the screen until its bottom
does, which for a first screen is the first screen of scroll. Study: hero pictures that sink and dim as
they leave, a heading scrubbed from 140 to 60 px, a title card that scales down on the phone; the
readers called it quiet and the page "one sheet". Travel stays under 8%; the overlay is a flat ink at
up to 35%, not a gradient. Static where unsupported or reduced.





##### Page to page

Navigation between pages of the site with the browser's own view transitions: the old page fades
quickly, the new one rises in, and the picture the visitor clicked travels into place as the new
page's hero. No library, no full-screen curtain.

```css
/* on every page */
@view-transition { navigation: auto; }
@media (prefers-reduced-motion: reduce) { @view-transition { navigation: none; } }
::view-transition-old(root) { animation: vt-leave 200ms var(--ease-exit) both; }
::view-transition-new(root) { animation: vt-arrive 380ms var(--ease-out) 60ms both; }
::view-transition-group(*) { animation-duration: 480ms; animation-timing-function: var(--ease-in-out); }
::view-transition-image-pair(*.picture) { overflow: clip; }
::view-transition-old(*.picture), ::view-transition-new(*.picture) { height: 100%; object-fit: cover; }
@keyframes vt-leave { to { opacity: 0; } }
@keyframes vt-arrive { from { opacity: 0; transform: translateY(16px); } }
```

```html
<!-- on the index: the card picture of one project -->
<img src="/img/leith.jpg" alt="…" style="view-transition-name: kitchen-leith; view-transition-class: picture">
<!-- on that project's page: its hero picture -->
<img src="/img/leith-wide.jpg" alt="…" style="view-transition-name: kitchen-leith; view-transition-class: picture">
```

Each name may appear once per page. Browsers without cross-document view transitions simply navigate.
Study: 16 pages load a page-transition library and run full-screen curtains of 0.7-2.4 s; 6 use view
transitions. The new page should be readable within half a second.

##### Ink fill

One statement that fills from part-ink to full ink as it rises through the screen, line by line. It is
readable before it fills; the fill only sets the pace.

```html
<p class="statement head" data-fill>Nine people, one workshop, no catalogue: every stool is made for the kitchen it goes to.</p>
```

```css
[data-fill] { --fill: var(--ink); color: var(--fill); }
@supports (animation-timeline: view()) {
  @media (prefers-reduced-motion: no-preference) {
    .is-filling > span { display: inline-block; color: color-mix(in oklab, var(--fill) 45%, transparent); animation: ink-fill linear both; animation-timeline: view(); animation-range: cover 20% cover 45%; }
  }
}
@keyframes ink-fill { to { color: var(--fill); } }
```

```js
(() => {
  if (!CSS.supports('animation-timeline: view()') || matchMedia('(prefers-reduced-motion: reduce)').matches) return;
  document.querySelectorAll('[data-fill]').forEach((el) => {
    const words = el.textContent.trim().split(/\s+/);
    el.textContent = '';
    words.forEach((word, i) => {
      const s = document.createElement('span');
      s.textContent = word;
      el.append(s, i < words.length - 1 ? ' ' : '');
    });
    el.classList.add('is-filling');
  });
})();
```

Each word watches its own position, so the words of a line fill together as the line moves from three
quarters of the way down the screen to just past half way. Set `--fill` on a dark chapter to its ink.
Study: 14 pages scrub a statement from grey to ink; unread words started at about 25-30% and settled
frames still caught statements half pale, which reads as disabled text. Here: one statement per page,
three to five lines, 32px or larger, starting at 45% (about 3:1 against the ground, enough for large
text). Full ink without scroll timelines or under reduced motion.

##### Rolling figures

For pages whose case is a handful of numbers: each digit rolls up to its value once, the columns a
beat apart. The real number stays in the text for screen readers and search.

```html
<p class="figure"><span class="display" data-roll>1987</span> the year the first stool was sold</p>
```

```css
.roll__digits { display: inline-flex; font-variant-numeric: tabular-nums; line-height: 1; }
.roll__col { display: inline-block; height: 1em; overflow: clip; }
.roll__strip { display: flex; flex-direction: column; transform: translateY(calc(var(--d) * -1em)); }
.roll__strip > span { height: 1em; }
@media (prefers-reduced-motion: no-preference) {
  .roll:not(.is-in) .roll__strip { transform: none; }
  .roll.is-in .roll__strip { transition: transform 1100ms var(--ease-expo) calc(var(--i) * var(--stagger-item)); }
}
```

```js
(() => {
  const els = [...document.querySelectorAll('[data-roll]')];
  if (!els.length) return;
  els.forEach((el) => {
    const value = el.textContent.trim();
    const said = Object.assign(document.createElement('span'), { className: 'sr-only', textContent: value });
    const shown = Object.assign(document.createElement('span'), { className: 'roll__digits' });
    shown.setAttribute('aria-hidden', 'true');
    let i = 0;
    for (const ch of value) {
      if (!/\d/.test(ch)) { shown.append(ch); continue; }
      const col = Object.assign(document.createElement('span'), { className: 'roll__col' });
      const strip = Object.assign(document.createElement('span'), { className: 'roll__strip' });
      strip.style.setProperty('--d', ch);
      strip.style.setProperty('--i', i++);
      for (let n = 0; n < 10; n++) strip.append(Object.assign(document.createElement('span'), { textContent: n }));
      col.append(strip);
      shown.append(col);
    }
    el.classList.add('roll');
    el.replaceChildren(said, shown);
  });
  if (!('IntersectionObserver' in window)) { els.forEach((el) => el.classList.add('is-in')); return; }
  const io = new IntersectionObserver((entries) => {
    for (const e of entries) if (e.isIntersecting) { e.target.classList.add('is-in'); io.unobserve(e.target); }
  }, { rootMargin: '0px 0px -15% 0px' });
  els.forEach((el) => io.observe(el));
})();
```

Study: 6 pages roll digit columns (stats, a year, coordinates), about 0.9-1.1 s per column on an
expo-out, staggered by column. Use it for three or four figures at display size, never in running text
and never for a value that changes after load. Reduced motion: the figure is set at its value.

##### Accordion

```css
.acc__panel { display: grid; grid-template-rows: 0fr; transition: grid-template-rows 320ms var(--ease-out); }
.acc__panel > div { overflow: hidden; }
.acc[open] .acc__panel, .acc__item.is-open .acc__panel { grid-template-rows: 1fr; }
```

Animating `grid-template-rows` from `0fr` to `1fr` opens to the content's real height without measuring
it in JavaScript.

##### Menu or dialog

```css
.menu { transform-origin: top right; transition: opacity var(--t-ui) var(--ease-out), transform var(--t-ui) var(--ease-out); }
.menu[hidden], .menu.is-closed { opacity: 0; transform: scale(0.97) translateY(-6px); pointer-events: none; }
```

Things open from where they were triggered (`transform-origin` at the trigger). Nothing enters from
`scale(0)`; start at 0.95–0.98. A centred dialog is the one case that scales from its centre.

#### 7. Signature moves

The direction sheet names one. Each of these was seen repeatedly on the studied gallery sites.

| Move | What happens | Build with |
| --- | --- | --- |
| Masked headline | Lines rise from behind their baselines on load | Masked line reveal recipe |
| Shutter image | Hero or showcase image opens from an edge, settling from 1.12 scale | Image shutter recipe |
| Scaling wordmark | A giant wordmark shrinks or grows a few percent as the hero scrolls out | Scroll-linked recipe on `scale` |
| Pinned story | A heading holds while its items scroll past | Sticky recipe |
| Index with preview | Text rows; the hovered row shows its image | Index with preview, anchored to the row |
| Curtain footer | The last section is revealed from under the page as you reach the end | `position: sticky; bottom: 0` footer under a main with a background and `z-index` |
| Slow crossfade | Hero image crossfades through 3–4 photographs, 5–6s each | Stacked images, opacity keyframes, pause when the tab is hidden |
| Edge-to-edge marquee | One line of very large type travels sideways, slowly | Duplicate the content, `translateX(-50%)` linear loop, pause on hover and under reduced motion |
| Drag row | A horizontally scrollable row of large images with scroll snapping | `overflow-x: auto; scroll-snap-type: x mandatory`, no library |
| Colour by chapter | Each chapter is its own full-bleed colour field, so the ground changes at section edges; a fixed header takes the ink of the chapter beneath | Section backgrounds in CSS; `base.js` sets `--header-ink` from `data-ink`. Never recolour the whole page from an observer |
| Opening window | A type screen hands over to the big picture: a window in the middle of a held stage opens to full-bleed over about one screen | Opening window recipe |
| Ink-fill statement | One statement fills from 45% to full ink as it rises through the screen | Ink fill recipe |
| Sheet over a held picture | A full-bleed photograph holds for one screen; the next chapter slides up over it as an opaque sheet | A 100svh `position: sticky; top: 0` figure followed by a section with its own background and a higher `z-index`; no script |
| Sideways gallery | A short row of pictures moves sideways while the vertical scroll holds the stage | Sideways gallery recipe |
| Pushed line | One line of very large type is pushed sideways by the scroll, reading whole at the middle of its run | `animation-timeline: view()` on the line, `translateX` from 12% to -12%, linear; static where unsupported |
| Rolling figures | The few figures that make the case roll up to their values once | Rolling figures recipe |
| Carried picture | The picture clicked in a list travels into place as the next page's hero | Page to page recipe |

Pick by subject. A portfolio wants the index with preview; a restaurant wants the slow crossfade; a
product wants the shutter on its hero object. If the move says nothing about the subject, it is
decoration and the page is better without it.

Pick by subject, as before: the opening window for a product or a place with one great photograph; the
sheet for chapters that each own a picture; the sideways gallery for a short set of rooms, kitchens or
pieces; the pushed line for a brand whose claim is a word; rolling figures for a report, a fund or a
practice that leads with numbers; the carried picture for a portfolio whose index and case pages are
both built.

#### 8. Reduced motion and performance

- `prefers-reduced-motion: reduce` means fewer and gentler, not none: keep opacity and colour changes,
  drop travel, scale, parallax and autoplay. All recipes above are written inside
  `no-preference` blocks so the reduced state is simply the finished state.
- Animate `transform`, `opacity` and `clip-path`. Animating `width`, `height`, `top`, `left`, `margin`
  or `padding` forces layout on every frame. `grid-template-rows` for accordions is the accepted
  exception because it is short and rare.
- Do not drive many children from one changing CSS variable on a parent; set the transform on the
  element that moves.
- `will-change` only on an element that is about to animate, removed afterwards.
- Pause loops when off screen or when the tab is hidden.
- No scroll hijacking and no custom cursor. They cost usability, which is 30% of an Awwwards score and
  the line most winners score lowest on. Smoothing only through `Stage.smooth()`, which stays off for
  touch and reduced motion.

#### 9. What gives generated motion away

- The same fade-up on every block.
- A dozen staggered entrances in the hero.
- Hover lift or zoom on every card and image.
- Bounce or elastic easing on interface elements.
- Infinite loops that mean nothing: pulsing dots, floating shapes, shimmering text, rotating badges.
- A reveal that never fires and leaves a blank band in the page. Run `inspect.mjs` after the motion
  pass and look at every screenshot for missing content.

##### Seen in the latest Sites of the Day

Seen in the study, with how often, and what the house does instead.

- **Preloaders and counters (60 of 99; 26 with a counter).** Half the usable pages were unreadable
  2.5 s after load, a third at 4.5 s; the preloaders sat mostly on pages that had already loaded, and
  25 of the 29 that loaded in under 3 s still showed nothing readable at 4.5 s. Counters stalled,
  outlasted the load or were tweens with nothing behind them. House: no preloader. If a scene must
  load, the HTML first screen (headline, picture, action) is there at once and the scene fades in
  behind it when ready.
- **Gates (10 of 99): enter, sound, age or gesture before any content.** House: none. Sound is a
  control on the page, off by default.
- **Scroll hijacking (16 wheel-driven scenes, 9 of them endless, plus 14 single screens where the wheel
  does nothing).** The visitor cannot tell where they are, how much is left or how to get out, and the
  keyboard and screen readers get nothing. Usability 6.01 against 6.50 for pages that scroll. House:
  native scroll; any scene is driven by scroll position on a sticky stage that ends, with a count.
- **Smooth-scroll libraries (67 of 99).** They make the scrubbed scenes feel weighted, and they also
  put a delay between the hand and the page; with a long ease the page keeps sliding after the wheel
  stops.
- **Custom cursors (28 of 99).** Followers, image trails, a lens that smears the headline it sits on,
  labels that only exist on hover; 10 of the 28 have any reduced-motion rule. House: the system cursor;
  labels are on the page.
- **Scramble and typewriter text (11 and 5).** The headline unreadable for four seconds, body copy
  garbled mid-scroll, actions held back until the typing ends. House: not used. Real words arrive whole.
- **Long held runways.** Pages with pins average twice the length for fewer words per screen; 17 pages
  are 20 screens or longer, some with whole screens that hold only a slow rotation. House: about one
  screen per step, three per stage, every held screen carries a line of text.
- **Content held at zero opacity.** Reveals that keep text invisible until the scroll settles, inactive
  items dimmed to 10-15%, statements left half pale. House: reveals only below the fold, once, never
  longer than 900 ms in view; dims no lower than 40%; fills start at 45%.
- **Motion over words.** Marquees and drifting objects that cross statements, a sliding line that crops
  its own words, blur left on text mid-move. House: nothing moves across text the visitor is reading;
  a moving line must read whole at some point of its run.
- **Overshoot and bounce (19 stylesheets).** House: still banned on interface elements.
- **Endless loops with no off switch.** Grain, pulsing dots, equalisers, spinning badges, running with no
  reduced-motion rule on most pages. House: loops pause off screen and stop under reduced motion.

Where the study's work does something the house bans, the house version: hairline progress bars and
tick rails on held stages become a plain count in the body face ("2 of 4"); zero-padded counters
("01/08") become a plain count or nothing; crossfading gradient grounds become flat chapter colours with
hard cuts; monospace HUD labels become small text in the text face.

#### 10. Rules for motion

1. **First frame.** The headline, the sentence and the picture are in the HTML and painted on the first
   frame. The load sequence starts without waiting for the load event and is settled by 1.2 s, with
   four elements at most.
2. **No preloader, no counter, no gate, no custom cursor, no wheel capture.** Smoothing only through
   `Stage.smooth()` (Lenis at lerp 0.1-0.14, off for touch and reduced motion): weight, never a page
   that keeps sliding after the hand stops.
3. **Curves.** `--ease-out` for anything under 600ms; `--ease-expo` for reveals of 800ms or more;
   `--ease-in-out` for wipes and things that travel; `--ease-exit` only for things leaving for good;
   `linear` for scroll-linked motion and loops; plain `ease` for colour. No overshoot.
4. **Durations.** Press 140ms; hover colour 180-200ms; hover that moves 300-400ms; menus 240ms; reveals
   700-900ms; picture openings 1,100-1,300ms; exits 60-70% of the matching entrance.
5. **Staggers.** Lines 80-110ms; list items 50-90ms; characters 20-40ms and only in a heading of one to
   three words; four steps at most in any one sequence.
6. **Reveals.** Fire once, when the element's top is 85-90% of the way down the viewport; rise 12-32px
   or from a line mask; nothing in view stays hidden for more than 900ms; nothing above the fold waits
   for scroll.
7. **Scroll scenes are where the page is bold.** The big moves come from the scene library
   (`references/scenes.md`): the direction sheet deals two or three per page, each built on
   `assets/scenes/stage.js`, each held for one to four screens, each with a phone version and a
   finished composition. Inside a scene the scene's own numbers apply (a picture may grow from a
   window to the whole screen, type may cross the stage, a camera may fly through a field of
   pictures); rules 8 and 10 still hold for the text a visitor is reading.
8. **Outside the scenes, scroll-linked travel stays quiet.** Linear and locked to the scrollbar;
   parallax under 8% of the element; scale between 0.94 and 1.15; built with scroll timelines inside
   `@supports`, static without them. Other held stages: sticky, about one screen per step, three
   screens at most, a line of text on every held screen.
9. **One of each.** One signature move (a dealt scene can be it); one moving picture; one marquee at
   most. A quiet section between two scenes, so each one lands.
10. **Text stays readable.** Fills start at 45% ink; dims no lower than 40%; blur at most 8px and gone
    once settled; nothing moves across text being read.
11. **Colour by chapter** as hard cuts at section edges; the fixed header's ink follows in 300ms.
12. **Horizontal motion.** The native drag row first; the pinned sideways gallery only for rows under
    three screens long, with keyboard support.
13. **Page to page.** View transitions, 480ms at most, off under reduced motion.
14. **Reduced motion.** Every hidden state lives inside `prefers-reduced-motion: no-preference`; the
    reduced page is the finished page; loops stop. Two in three award pages skip this, which is a
    reason to do it, not a licence to skip it.

---

## references/scenes.md

### Scroll scenes

The big moments of a page: stretches of scroll where the page stops being a column of sections and
becomes a scene. A camera flies through a field of pictures, a picture grows from a window to the whole
screen, a word buckles under the scroll, a set of photographs orbits and lands in a grid. These are what
visitors remember from award sites, and what a page built from tidy sections alone never has.

The scene library is taken apart from recent Awwwards Sites of the Day (October 2026: 43 sites recorded
frame by frame while scrolling, 261 scenes described, 30 types), rebuilt from scratch in our own code,
tested frame by frame at desktop and phone width and under reduced motion, and reviewed against the
scenes it came from. Nothing a site owns is in them. Until `library/scenes.json` ships the draw deals
none; a page that needs a scene builds one on the stage (section 8), with every rule here.

#### Contents

1. What a scene is
2. Putting a scene on a page
3. Filling it
4. Fitting it to the page
5. The phone, reduced motion, no script
6. Checking it
7. Rules for scenes
8. When no scene in the library fits
9. The catalogue

#### 1. What a scene is

A tall section whose stage holds still while the page scrolls past it. The stage is
`position: sticky`; the section is (hold + 1) screens tall, so the stage is held for `hold` screens;
a GSAP timeline is scrubbed from 0 to 1 by that scroll. Nothing captures the wheel: the scrollbar always
tells the truth, the keyboard and the trackpad work as everywhere else, and the scene ends.

What a scene is not: a fade-up, a small parallax, a sticky footer, a marquee. Those are the quiet layer
(`references/motion.md`). A scene changes the whole screen.

The direction sheet deals two or three (section 9 of the sheet), from different families, each placed
on the section of the argument it can carry. Build them in step 6, with that section: a scene is
composition, not decoration added at the end.

#### 2. Putting a scene on a page

Copy the shared stage and the dealt scene's files into the project (`assets/scenes/stage.css`,
`stage.js`, `<id>.css`, `<id>.js`). Each scene file's header comment lists the markup it expects and
its options; `assets/scenes/demo/<id>.html` is a complete working page to read beside it.

```html
<head>
  <script>document.documentElement.classList.add('js')</script>
  <link rel="stylesheet" href="scenes/stage.css">
  <link rel="stylesheet" href="scenes/<id>.css">
</head>
<body>
  …
  <section class="scene" data-scene="<id>" data-options='{"hold": 3}' aria-label="…">
    <div class="scene-stage">
      <!-- the markup from the scene file's header, filled with this page's content -->
    </div>
  </section>
  …
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.15.0/dist/gsap.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/gsap@3.15.0/dist/ScrollTrigger.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/lenis@1.3.26/dist/lenis.min.js"></script>
  <script src="scenes/stage.js"></script>
  <script src="scenes/<id>.js"></script>
  <script>Stage.smooth(); Stage.init();</script>
</body>
```

- Load SplitText (`gsap@3.15.0/dist/SplitText.min.js`) only when a scene file says it needs it.
- `Stage.smooth()` adds weighted wheel scrolling (Lenis at lerp 0.12). It stays off for touch and for
  reduced motion. Leave it out on a quiet page; the scenes work either way.
- `Stage.init()` starts every `[data-scene]` on the page. A page with two scenes loads both files.
- The versions are pinned. Do not change them to `@latest` or an unpinned major.

#### 3. Filling it

A scene is only as strong as what goes in it. The scene file's header and the sheet's "Content" line
say how many pictures and words it takes; these hold for all of them:

- **Pictures of one family.** Same light, same grade, same kind of subject: a field of mismatched stock
  photographs breaks the illusion of one space faster than any timing error. Real pictures of the
  subject's world (`assets.mjs`), the project's own, or the dealt photographs, in that order
  (`references/imagery.md`). Size each to its largest display size, set `width` and `height`.
- **Words that read in a breath.** A held statement is 4 to 12 words; captions are one to four words in
  the text face, sentence case. One statement on screen at a time.
- **The scene says something about the subject.** A fly-through of the studio's work, the route a
  shipment really takes, the four rooms of the house, the product's change of state. A scene filled
  with unrelated pictures is a gimmick and reads as one.
- **Real content only.** If the scene needs eight pictures of the subject and there are three, take the
  `--redraw scenes`, never pad it with stand-ins.

#### 4. Fitting it to the page

- The scene files read the page's tokens: `--ground`, `--ink`, `--muted`, `--accent`,
  `--font-display`, `--font-text` (with fallbacks). Set them on `:root` from the sheet and the scene
  takes the page's colour and type. Check the demo against your page, not the other way round.
- Display type in a scene uses the dealt display face and the two-line headline rule; statements stay
  at statement size.
- Leave a quiet section between two scenes (a text section, a list, a plain picture) so each one lands.
  Two scenes back to back read as one long ride and the second loses.
- A scene on the first screen must be readable at progress 0: the title, the sentence and the action are
  there on the first frame (motion rule 1), and the scene starts moving only when the visitor scrolls.
- Give the section a heading. If the design has no visible heading in the scene, the section still
  carries one (`aria-label` on the section and a real heading in the finished composition).

#### 5. The phone, reduced motion, no script

- **The phone.** Each scene has a phone plan in its file: the same scene with changed numbers, a
  simpler version, or `phone: 'rest'`, where the phone shows the finished composition. Touch scrolling
  is never smoothed. Look at the phone sheet as carefully as the desktop one.
- **Reduced motion and no script.** The section is an ordinary section showing the finished
  composition: the same content, laid out to read without motion. Nothing is hidden waiting for a
  script. The inspector's `reduced-hidden` check and the reduced sheet of `scenes.mjs` show it.
- **A failed CDN** falls back to the finished composition too (the stage adds `.is-rest`). The
  inspector fails a scene that rests on desktop (`scene-not-live`), so a broken script cannot pass.

#### 6. Checking it

```bash
node <skill>/scripts/scenes.mjs <page>        # every scene at 0, 10 … 100%, desktop and phone, and reduced motion
node <skill>/scripts/inspect.mjs <page>       # the gate; with scenes on the sheet it also films the scroll
```

`scenes.mjs` writes one contact sheet per scene and width to `.taste-skill/scenes/`. Read every one.
At every frame ask: is there one clear thing to look at; can the statement on screen be read; is
anything popping, blank, cut off or crossing the words; is it as bold as it should be? The inspector's
`desktop-film-NN.jpg` shows the whole page's scroll a third of a screen at a time: check that the
scenes and the quiet sections between them make a rhythm, and that nothing between them is empty.

#### 7. Rules for scenes

1. **Two or three per page,** from different families, a quiet section between them. The inspector
   warns over four (`many-scenes`) and when scenes hold more than 60% of the page (`scene-heavy`).
2. **Each holds one to four screens:** about one screen per beat of the story; a hold with nothing new
   to show is cut, not padded.
3. **Native scroll only.** No wheel capture, no locking the page, no scenes that only run on a click.
   Smoothing only through `Stage.smooth()`.
4. **Readable at its rest points.** The statement on screen reads whole; nothing passes over text while
   it is being read; text on a picture has a flat scrim or a calm area under it.
5. **Inside a scene the scene's numbers apply** (motion rule 7): a picture may grow from a window to the
   whole screen, type may cross the stage, a camera may fly through pictures. Outside scenes, the quiet
   limits of `references/motion.md` hold.
6. **Transform, opacity, clip-path.** Nothing that forces layout on every frame. Pictures decoded before
   they move.
7. **The house rules hold inside scenes:** no monospace captions, no 01/07 counters (a plain "3 of 7" if
   a count is needed), no gradients (flat scrims), no shadows or glows, no hairline decoration, no
   decorative particles, no violet.
8. **The finished composition is designed,** not an afterthought: it is what reduced motion, a failed
   script and some phones see.

#### 8. When no scene in the library fits

Redraw first (`--redraw scenes`). If the brief really needs a scene the library does not have, build it
on the same stage so it inherits the guards:

```js
Scenes['my-scene'] = (root, opts = {}) => Stage.scene(root, {
  hold: opts.hold ?? 2,          // screens the stage is held for
  scrub: opts.scrub ?? true,     // true when Lenis runs; 0.4-0.8 without it reads as weight
  phone: 'same',                 // or 'rest', or { hold, build } for a phone plan
  build(tl, { q, phone }) {      // positions are fractions of the scene, 0-1
    tl.fromTo(q('.picture'), { clipPath: 'inset(30% 30% 30% 30%)' }, { clipPath: 'inset(0% 0% 0% 0%)', duration: 0.6 }, 0)
      .to(q('.title'), { yPercent: -40, autoAlpha: 0, duration: 0.25 }, 0.7);
  },
});
```

and write its CSS finished composition first, then the live layout under `.scene.is-live`. Check it
with `scenes.mjs` like any other.

#### 9. The catalogue

(Generated from `library/scenes.json`; the draw deals from it. `node <skill>/scripts/draw.mjs --list
scenes` prints it.)

---

## references/critique.md

### Critique — judging the render

`inspect.mjs` passing means nothing banned or broken was measured. It says nothing about whether the
page is good. This file is how you find out. Use it on the screenshots, never on the code: you wrote
the code, so you will read your intentions into it. The pictures only show what is there.

#### Contents

1. How to look (fourteen passes, a few minutes)
2. The score
3. Caps
4. Writing the critique
5. What to fix first
6. When to stop

#### 1. How to look

Open `desktop-fold.jpg`, then the `desktop-page-*.jpg` sheets, then `mobile-fold.jpg` and the mobile
sheets. Make each pass on its own; do not blend them.

1. **One second, then five.** Glance and look away. What did you see? There should be exactly one
   answer: a word, an image, an object. If the answer is "a website", there is no focal point. Then
   give the first screen five seconds as a stranger: can you say what this is, who it is for and
   what to do next? If the title only makes sense after scrolling, it is not a title.
2. **Squint.** Blur your attention until text becomes grey bars. The page should reduce to two or
   three large masses with clear size differences. Many small similar masses means everything is
   medium and nothing leads.
3. **Cover the logo.** Could this first screen belong to a competitor, or to a different industry?
   If swapping the name and the noun in the headline would produce an equally valid page, the page has
   no idea. Go back to the direction sheet; the idea is written there. Then scroll: does the idea reach
   the pricing, the FAQ and the footer, or does the page turn into stock blocks after the first screen?
4. **Edges.** Follow the left edge of every text block down the page. Count the distinct x positions.
   A composed page has two or three, reused on purpose. Six means things were placed one at a time.
5. **Space and frame.** Are related things close and unrelated things far? Is the gap between sections
   clearly larger than any gap inside a section? Is any region empty by accident (a hole) rather than
   by decision (a rest)? A hole usually sits beside a short column or under a removed decoration.
   Then look at the frame: are the left and right margins of the page the same? Does any section keep
   its text in one half and leave the other half empty? Is there a stretch of nothing taller than half
   a screen? Readers name these first ("it is pushed to the left", "random empty space"), before any
   detail; in the study of 100 Sites of the Day about 1 section in 100 left half the width empty.
6. **Type.** Is the jump from body text to headline decisive (three times or more)? Do you see more
   than five sizes? Any headline with one orphan word on its last line? Any paragraph wider than about
   75 characters or centred over more than three lines?
7. **Colour.** Name the proportions: which colour holds most of the surface, which supports, where is
   the accent? An accent that appears in ten places means nothing. One that appears on the single
   action and one detail means "here".
8. **Images.** Count the real pictures: are there at least four, and is there a moving one? A page of
   drawings only, or of type only, looks unfinished next to one with real photographs and footage.
   Is every image doing a job (showing the thing, setting the place, proving the claim)?
   Do the crops share ratios? Is anything a grey box, a stretched photo, a fake screen made of bars?
   Does the photography share one light and one grade, or is it a stock mix?
9. **Sameness.** Write one word for each section's layout (split, list, full-bleed, grid, statement,
   index …). The same word twice in a row, or three times on the page, is the template showing.
10. **Phone.** Is the mobile screen a composition of its own, with its own crop and its own line
    breaks, or the desktop page squeezed? Is the first screen still one clear thing?
11. **Fullness.** Go through the desktop sheets screen by screen. Is each screen a composed poster, or
    is it a narrow column of small text with dead ground either side? Is any statement held on screen
    for three screens? An austere page is not a restrained one: if the page could be mistaken for an
    unfinished wireframe (grey shapes, grey text, one small column), it is underbuilt. A single motif or
    drawing blown up to fill a whole screen with nothing to read is a hole too, however bold it looks.
12. **Substance.** Does every section the brief asked for deliver its information completely and at a
    readable size (the full menu, each room, every speaker, the price and what it includes)? Would the
    visitor leave knowing what they came to find out? Is the primary action a real button on the first
    screen?
13. **Collisions.** Is anything lying on top of a headline, a statement or a button at any scroll
    position? Does any element run off the edge of the phone screen? A row that scrolls sideways on
    the phone reads as cut off in a screenshot and to most visitors; wrap it unless the cut is
    plainly deliberate (a partial card showing at the edge).
14. **The competitor and the live thing.** Put the nearest competitor's name on the page: does the
    idea still work? Then name the one live thing (what the visitor can do or what differs each visit).
    If either answer is weak, that is the first problem of the round, ahead of any detail.

A note from testing: in blind comparisons a richer page full of template devices beat a cleaner page
that was thin, every time. The house rules remove the devices; passes 11–13 are where you make sure the
page did not lose its substance with them.

#### 2. The score

Score like an Awwwards juror: four criteria, 1–10 each, weighted **design 40%, usability 30%,
creativity 20%, content 10%**.

**Design (40%)** — composition, typography, colour, imagery, craft.
- 9–10: every screen holds as a poster. Nothing could be removed or moved.
- 8: confident and coherent; one or two soft spots a designer would notice.
- 7: clean and professional, a clear system, little tension.
- 6: tidy but anonymous. Reads as a kit.
- 5 or less: weak hierarchy, accidental spacing, default type, mismatched images.

**Usability (30%)** — orientation in three seconds, readable text, obvious actions, honest mobile.
- 9–10: you know what it is, who it is for and what to do without scrolling; flawless on a phone.
- 8: clear and comfortable; minor friction (a long section, a small target).
- 7: works, with one real problem (weak contrast somewhere, a cramped phone layout).
- 6 or less: you have to hunt, or something breaks.

**Creativity (20%)** — an idea you can state in a sentence, carried through.
- 9–10: a concept specific to this subject that you have not seen applied this way.
- 8: a clear idea with one memorable move.
- 7: a tasteful execution of a known approach.
- 6 or less: the category default.

**Content (10%)** — words and pictures that are specific, true-sounding and edited.
- 9–10: every line could only be about this subject; imagery is the subject.
- 7–8: clear and concrete, some generic lines.
- 6 or less: slogans, filler, stock.

`overall = 0.4·design + 0.3·usability + 0.2·creativity + 0.1·content`

For calibration: real Sites of the Day land around 7.5–8.0 overall from the jury. An honest 8.5 is
rare. If your first score for your own work is 9, score it again as the juror who did not build it.

#### 3. Caps

These override the arithmetic.

- Any `FAIL` still reported by `inspect.mjs`: overall cannot exceed **6.0**.
- A headline of three or more lines at any viewport, an eyebrow label, monospace labels, 01/02/03
  numbering, a decorative gradient, a shadow on a resting element, or a decorative hairline visible in
  a screenshot: overall cannot exceed **6.5**, whatever else is true.
- Pass 3 fails (the page could belong to anyone): creativity cannot exceed **6**.
- The idea passes for the nearest competitor (pass 14): creativity cannot exceed **7**.
- Fewer than four real pictures (photographs, archival images, footage; drawings do not count):
  design cannot exceed **6.5**.
- A page that barely moves (the inspector's `still-page`), or motion that is one identical fade on
  every block: design cannot exceed **7**.
- No live thing (pass 14): creativity cannot exceed **7.5**.
- Any placeholder (grey box, lorem, "Image here"): content cannot exceed **5**.
- Two or more desktop screens that are mostly empty ground, or a page whose running text is small and
  grey: design cannot exceed **6.5**.
- A section the brief asked for that is missing or reduced to a few words: content cannot exceed **6**.
- No real button for the primary action on the first screen: usability cannot exceed **7**.
- The five-second pass fails (no clear title saying what this is on the first screen): usability
  cannot exceed **6**.
- Unequal page margins, a section huddled on one side with the other half empty, or a blank stretch
  taller than half a screen: design cannot exceed **6.5**.
- A section of running text with no heading naming it: usability cannot exceed **7**.
- Anything covering a headline at any scroll position: usability cannot exceed **6**.
- A blank band where a reveal did not fire, or content clipped off-screen: usability cannot exceed **5**.

#### 4. Writing the critique

Write it down; do not just think it. Use exactly this shape so rounds can be compared:

```
ROUND n
Seen in one second: …
Idea (one sentence): …
Live thing: …
Layout words by section: hero=… / …=… / …
Scores: design _ · usability _ · creativity _ · content _ → overall _._
Caps applied: …
Top three problems (most visible first), each with the screenshot it shows in and the fix:
1. …
2. …
3. …
```

Name problems the way a designer would to a colleague: "the supporting paragraph starts 40px left of
the headline's edge", "the testimonial section is the third split layout in a row", "the phone hero
crops the bottle out of frame". "Could be more polished" is not a finding.

#### 5. What to fix first

Fix in this order; later items cannot rescue earlier ones.

1. **The idea.** If pass 3 fails, change the hero concept, not the details.
2. **Hierarchy.** One dominant element per screen. Make the big thing bigger and the small things
   fewer before touching anything else.
3. **Composition.** Shared edges, section spacing, variety of layout between sections, holes.
4. **Typography.** Scale contrast, line breaks, measure, leading.
5. **Imagery.** Replace weak pictures, unify crops and grade.
6. **Colour.** Proportion and accent discipline.
7. **Detail.** States, focus, small alignments, mobile refinements.
8. **Motion.** Last.

When removing something leaves a gap, do not refill it with an ornament. Close the gap, enlarge what
remains, or let a picture or a colour field take the space.

#### 6. When to stop

Run at most three rounds: critique → fix the top three → re-inspect → critique. Stop early when a round
finds no problem a stranger would notice. If round three still scores under 7.5, say so plainly in
your report, with the remaining problems listed; do not round up.

---

## references/tells.md

### Tells — the dated registry

A tell is a device that makes a page read as generated. Tells are not bad design in themselves; most
began as good ideas on good sites. They became tells by being produced by default, everywhere, without
a reason. That is why this registry is dated, and why it never names a replacement font, colour or
component: every published "use this instead" list has become the next wave of tells within months.
Replacements here are procedures (draw from the library, derive from the subject), not products.

`scripts/inspect.mjs` and `scripts/lint.mjs` detect most entries. Status: **banned** means the
inspector fails the page; **warned** means it flags it and you need a reason.

#### Contents

1. First wave (2023–2024)
2. Second wave (2025)
3. Third wave (2025–2026): the "fix" that became the look
4. Gallery fashion, banned as house style
5. Structural tells
6. Copy tells
7. Motion tells
8. Why removal is not enough

#### 1. First wave (2023–2024)

| Tell | Status | Do instead |
| --- | --- | --- |
| Violet / indigo gradients on hero, buttons and glows | banned | The dealt palette; flat colour |
| Gradient-filled headline text | banned | Solid ink |
| Glass panels: backdrop blur, translucent cards | warned (2 or more) | Opaque surfaces one tone step from the ground |
| Glowing or gradient "Get started" button | banned | Flat button named for its action |
| Soft grey drop shadow under every card | banned | Tone step, or no box |
| Three identical feature cards, each with an icon in a rounded square | banned | The dealt section blueprint |
| Emoji as icons or bullets | banned | Words, or a real picture |
| Centred headline, subtitle, two buttons, screenshot below | no rule; the draw avoids it | The dealt hero |
| The same typeface on every generated page | warned (lint: default-font) | The dealt type system |

#### 2. Second wave (2025)

| Tell | Status | Do instead |
| --- | --- | --- |
| Eyebrow / kicker: tiny tracked uppercase label above every heading | banned | Fold it into the heading, or delete |
| Pill badge above the hero headline ("New", "Beta", "Introducing") | banned | Say it in the supporting sentence |
| One word of the headline in italic serif, colour or underline | warned | One face, one colour |
| Bento grid of rounded tiles as the feature section | warned as card rows | A composed section; tiles only in the dense-tiles direction, filled, strict sizes |
| Near-black ground with one neon accent and a glow | banned via shadow, gradient | A dealt dark palette, no glow |
| Floating rounded pill navigation with blur | warned | A plain bar |
| Fake dashboard hero built from grey bars and donut charts | no rule; see imagery.md §7 | A real interface fragment, or no image |
| Decorative status dot ("Available for work", pulsing "live") | lint: bounce | Remove |
| Fade-and-rise on every section | no rule; see motion.md | One signature move |

#### 3. Third wave (2025–2026): the "fix" that became the look

The remedy published for the first two waves was "warm it up and make it editorial". Models adopted
the remedy wholesale and it is now the most recognisable generated look of all.

| Tell | Status | Do instead |
| --- | --- | --- |
| Yellow-cream ground + terracotta / rust / clay accent | banned together; terracotta banned alone; cream warned | The dealt palette. Warmth from a low-chroma stone, a deep ink, a photograph, or a full warm field |
| High-contrast or soft serif display as the shortcut to "premium" | no rule | The dealt type system, whatever class it is |
| Oversized italic serif headline | no rule | As dealt |
| Broadsheet cosplay: hairline rules everywhere, zero radius, dense columns | banned via hairline | Structure from space and tone |
| "Field notes", "Quietly trusted by", "On our desks": performative labels | lint: copy | Plain section names |

#### 4. Gallery fashion, banned as house style

These are common on award sites right now. In the study they appear *more* often on the top-scored
sites than on the weak ones (panel observations: monospace labels 44% against 24%, index numbering 38%
against 21%; measured thin rules 61% against 52%). They are banned here regardless, by the owner's
decision: they are the first things a generator copies from the gallery, they carry no information,
and a page built without them has to find real structure.

| Tell | Status | Do instead |
| --- | --- | --- |
| Monospace micro-labels, mono as a "technical" voice, mono captions | banned | The text face; tabular figures for data |
| Index numbering: 01 / 02 / 03, (001), "Step 02", numbered section markers | banned | Order by position, scale, or the words; `<ol>` when it is truly a list |
| Thin rules: hairline dividers, ruled grids, 1px outlined boxes and tiles | banned (boxes: 3 or more) | Space, tone steps, filled shapes, a thick bar if a bar is the idea |
| Design-tool chrome as ornament: crosshairs, crop marks, selection handles, dashed guides, rulers | banned via hairline, dashed | Remove |
| Agency micro-meta: local time, coordinates, weather, version stamps, "©2026 — Scroll", middle-dot strings | lint: copy; micro-label | Remove |
| Tiny uppercase letter-spaced captions scattered around the viewport | banned (3 or more) | Sentence case at readable size, placed with the content it describes |

Tiny tracked capitals are the one item in this group the data condemns as well: 16% of top sites
against 57% of weak ones.

#### 5. Structural tells

| Tell | Status | Do instead |
| --- | --- | --- |
| Headline as a full sentence at display size, three or four lines | banned (over two lines) | A title of about five words; the rest goes below |
| Stock section order: hero, logos, features, testimonial, pricing, CTA | no rule; see copy.md §1 | The order of the argument |
| Every section the same layout family | critique.md pass 9 | Different composition per section, from the sheet |
| Everything centred | warned over 72% | Left-anchored, one centred moment |
| One medium border radius (12–16px) on everything | none | Square or fully round, chosen once |
| Nine nearly equal font sizes | warned over 9 | Five sizes, far apart |
| Invented social proof: logos, quotes, star rows, "10,000+ teams" | copy.md §5 | Real proof, or none |
| Text or a CSS box where a picture belongs | critique.md cap | A real picture, or a design that needs none |

#### 6. Copy tells

Flagged by `lint.mjs`: the genre's verbs and adjectives (unlock, supercharge, seamless, elevate,
effortless, cutting-edge, all-in-one …); the correction ("not just X, it's Y"); tricolon headlines;
"Get started" and "Learn more" as labels; more than a handful of em dashes; lorem ipsum. See
`copy.md` §6.

#### 7. Motion tells

Identical fade-up on every block; a dozen staggered hero entrances; hover lift on every card; bounce
easing; infinite loops that mean nothing; reveals that fail and leave a blank band. See `motion.md` §9.

#### 8. Why removal is not enough

A page with every tell removed and nothing put in their place is an empty page with good manners, and
that is a tell too (the "avoidance aesthetic": anyone could guess it from the category plus the list of
things to avoid). The tells were filling a gap where an idea should have been. The order of work in
`SKILL.md` exists to fill that gap first: the idea from the subject, the dealt composition, real
pictures or committed type, and only then the checks.

---

## references/research.md

### The study

Everything numeric in this skill comes from here. Cite these figures; do not round them up or invent
others.

#### Contents

1. Method and its limits
2. Scores
3. Where the idea comes from
4. Headlines
5. Type
6. Devices: what separates strong from weak, and what does not
7. Colour and shape
8. Imagery and page structure
9. What the inspector says about the gallery itself
10. The 25 highest-scored sites and their ideas
11. How the skill was tested
12. The October 2026 study: 100 Sites of the Day
13. The app-screen study

#### 1. Method and its limits

- **Sample.** 248 sites collected on 5 October 2026: 156 from One Page Love (the latest gallery pages
  and the category listings) and 92 Awwwards Sites of the Day (the three most recent listing pages).
  247 loaded; 246 were re-measured with the final probe.
- **Capture.** Headless Chrome at 1440×900 and 390×844. For each site: the first viewport, five more
  frames while scrolling with real wheel input, the mobile first viewport, and a measurement pass in
  the page (computed styles, text geometry, colours, fonts actually loaded).
- **Panel.** 21 model reviewers each studied about 12 sites from the screenshots and the measurements,
  described them (idea, hero, type, colour, imagery, layout, sections) and scored them the Awwwards
  way: design 40%, usability 30%, creativity 20%, content 10%. These are model judgements from still
  frames, not human jurors and not the real Awwwards scores. Batches mixed both sources so each
  reviewer saw a spread.
- **Usable sets.** 235 sites were usable for the panel (12 showed only a preloader, an entry gate or a
  bot wall). 202 were measurable for typography (a page with at least 25 words and a detectable
  headline). "Top" below means panel score 7.5 or higher (82 measurable sites); "weak" means under 6.5
  (23 measurable sites).
- **Limits.** One capture per site on one day. Some heroes were caught mid-animation or behind a cookie
  notice. WebGL-heavy sites are under-described by text measurements. The eyebrow detector counts any
  small short label directly above a large heading, so it over-counts against the panel's stricter
  reading (60% measured against 35% observed). Motion was inferred from frames, not watched. The sample
  is whatever the two galleries had recently featured; it is fashion as much as quality.

#### 2. Scores

| | All 235 | One Page Love (151) | Awwwards (84) |
| --- | --- | --- | --- |
| Median overall | 7.2 | 7.1 | 7.5 |
| Middle half | 6.8–7.6 | | |
| 8.0 or higher | 25 sites (11%) | | |
| 7.5 or higher | 90 sites (38%) | | |
| Under 6.5 | 29 sites | | |

Median by criterion: design 8, usability 7, creativity 7, content 7. Among the top 25: design 9,
usability 7, creativity 8, content 8. Usability is the one line that does not rise with the rest: the
best sites are no easier to use than the average one. Do not copy their gates, preloaders, tiny text
or hidden navigation.

#### 3. Where the idea comes from

The clearest pattern in the panel's notes: high scores go with a concept taken from the subject, and
low scores go with its absence. The weakest entries' ideas were recorded in words like "none beyond the
standard dark SaaS launch formula", "no visual idea beyond clarity", "no strong idea". The strongest
were sentences only that subject could own (section 10).

Recurring engines among the 7.3+ sites, each the basis of a direction in the library:

- **The product demonstrates itself.** A colour picker's loupe reads the page's own background; a list
  tool is sold with tiny working lists; a photo app's page is a wall of its own output.
- **The page is an artefact from the subject's world.** A wedding site that is the invitation; an
  archive as tabbed folders; a coupon with a cut line; a portfolio as a contact sheet.
- **The name is the hero.** Wordmarks as wide as the screen, a photograph set inside the name like a
  letter, a name split to opposite corners with the page between.
- **One motif from the subject drives everything.** A tool's octagonal section as button, mask and
  loader; two circles for two accounts; a café's stripes.
- **Dressed as another category.** A money app as a streetwear drop; an industrial roaster as a design
  object; a parcel service as a fairground.
- **The place carries it.** One full-bleed view and a name along the bottom edge.
- **A fixed stage.** A title or object stays put while content swaps beneath it.
- **One section, one colour.** Flat fields as chapters.
- **Radical understatement.** A 27px headline and tiny live demonstrations, carried through completely.

Hero types, by the panel's classification (top sites against weak sites): full-bleed media with type
over it 16% / 10%; giant wordmark 14% / 0%; typographic poster 13% / 7%; text beside media 10% / 3%;
**centred statement with media below 7% / 24%**. The centred headline over a screenshot is the weak
sites' signature layout.

#### 4. Headlines

| Hero headline | All | Top | Weak |
| --- | --- | --- | --- |
| Words, median | 5 | 5 | 5 |
| Words, middle half | 3–9 | 2–8 | 3–8 |
| Characters, median | 32 | | |
| One line at 1440 | 47% | | |
| Two lines or fewer at 1440 | 70% | 71% | 83% |
| Two lines or fewer at 390 | 57% | | |
| Three lines or fewer at 390 | 82% | | |

Awwwards heroes are shorter (median 4 words, 76% within two lines) than One Page Love's (6 words, 66%).
Section headings have a median of 3 words. Length does not separate strong from weak; nearly everyone
in the gallery writes short headlines. The two-line limit in this skill is a house rule that most of
the gallery already meets on desktop and that takes care to meet on a phone.

#### 5. Type

| | All | Top | Weak |
| --- | --- | --- | --- |
| Hero size, median | 72px (5.0vw) | 6.0vw | 4.7vw |
| Hero size, middle half | 3.0–7.6vw | 2.5–9.7vw | 2.7–6.1vw |
| Largest text on the page, median | 6.4vw | 8.4vw | 5.0vw |
| Largest text, upper quarter starts at | 10.4vw | 12.5vw | 6.7vw |
| Hero on a phone, median | 40px | | |
| Hero tracking, median (middle half) | -0.01em (-0.03 to 0) | | |
| Hero leading, median (middle half) | 1.0 (0.95–1.1) | | |
| Body size, median (middle half) | 16px (14–18) | | |
| Headline ÷ body, median | 4.3 | 4.7 | 4.0 |
| Typefaces carrying 3%+ of text | one 31%, two 45%, three 22% | | |
| Distinct font sizes, median | 8 | | |

Hero weight: regular 48%, medium 18%, semibold 6%, bold or heavier 22%, light 6%. Capitals 24%.
Centred 39% overall, 52% on weak sites. Display classes by the panel: neo-grotesk 48%, transitional
serif 11%, geometric sans 10%, condensed 6%, extended 6%, old-style serif 4%, custom lettering 4%.

Strong sites push the extremes: their biggest type is bigger and their range is wider. Weak sites
cluster in the middle.

#### 6. Devices: what separates strong from weak, and what does not

Measured in the page unless marked (panel).

**More common on weak sites (the data supports avoiding them):**

| Device | Top | Weak |
| --- | --- | --- |
| Icon-topped feature cards (panel) | 1% | 28% |
| Rows of identical cards with a small icon (measured) | 7% | 26% |
| Pill badges (panel) | 14% | 34% |
| Pill-shaped label above a heading (measured) | 5% | 26% |
| Tiny uppercase letter-spaced labels, any | 16% | 57% |
| Tiny uppercase letter-spaced labels, three or more | 6% | 43% |
| Gradient fills (not counting scrims) | 22% | 52% |
| Gradient text | 2% | 13% |
| Shadows on resting elements, any | 24% | 48% |
| Shadows, five or more | 10% | 30% |
| Emoji in the page | 10% | 26% |
| Eyebrow labels (panel) | 32% | 45% |

**No real difference:**

| Device | Top | Weak |
| --- | --- | --- |
| Backdrop blur anywhere | 32% | 39% |
| Italic-serif accent word (panel) | 4% | 7% |
| Thin rules, any | 61% | 52% |

**More common on strong sites (banned here anyway, as house style):**

| Device | Top | Weak |
| --- | --- | --- |
| Monospace labels (panel) | 44% | 24% |
| Monospace anywhere outside code (measured) | 45% | 26% |
| Index numbering (panel) | 38% | 21% |

Monospace captions, index numbers and ruled grids are the present fashion of award sites. They are
excluded from this skill by the owner's choice, not by the data: they are the devices generators copy
first, and a page that cannot lean on them has to find structure in space, tone and scale.

#### 7. Colour and shape

- Dark page ground 41%; pure white 25%; pure black 12%; a warm off-white 13%.
- Scheme (panel): monochrome plus one accent 23%, light neutral 22%, dark neutral 14%, several flat
  colours 13%, two-tone 12%, photographic 9%, one colour field 6%.
- Primary buttons are neutral (black, white, grey) on 52% of sites. One site in 246 has a terracotta
  button; none has a violet one.
- Median number of distinct section grounds: 2 on top sites, 1 on weak sites.
- Button shape: top sites square (0–2px) 52%, fully round 23%, small radius 19%, medium (9–16px) 6%.
  Weak sites fully round 59%, medium 24%, square 18%.
- Media corners are square on 73% of sites; where rounded, the median radius is 12px.
- Buttons in the first viewport: none on 55% of top sites and 39% of weak ones.

#### 8. Imagery and page structure

- Hero media covers at least half the first viewport on 60% of sites (top 68%, weak 48%) and nearly
  all of it on 50% (top 56%, weak 39%). No hero media: 15%.
- Video is present on 49% of sites and a canvas element on 49% (top 62%, weak 35%).
- Images per page, median: 24 overall, 37 on top sites, 5 on weak ones.
- Imagery kind (panel): mixed 32%, photography 14%, generative or WebGL 13%, product interface 12%,
  3D render 11%, illustration 9%, video 6%, type only 3%. Median panel score is lowest for
  illustration-led (6.9) and product-interface-led (7.1) pages and highest for video and type-only
  (7.5).
- Page length, median: 8.7 screens and 575 words (middle half 1.6–14.4 screens, 250–956 words). A
  quarter of the sites are a single screen or two.
- Navigation: a median of 3 links; fixed or sticky on 66%.
- Density (panel): airy 46%, balanced 45%, dense 9%. Alignment: centred 33%, mixed 31%, left-anchored
  17%, modular grid 13%, free 6%.
- Asked to describe each site's most interesting sections, the panel picked a pricing, testimonial or
  FAQ section only 7, 12 and 9 times across 235 sites. Where strong sites have them at all, they are
  not where the design effort goes, and they avoid the stock form.

**From the panel's written notes on the 114 sites scoring 7.3 or more** (hand tallies, approximate;
`layout.md` turns these into practice):

- Outer margins of 32px or less on about 45; 80px or more on about 8. A centred 700–1300px container
  on about 15, several of them the pages the panel called stock.
- Text anchored to a fixed off-centre line on about 22. Text docked in corners or at opposite ends of
  a baseline on about 25 and 15.
- Two or three type sizes with nothing between on about 30; no note describes a graded five-step
  scale.
- One thing per screen on about 20. A full background colour per section on about 20; alternating
  light and dark on about 12.
- Every section recomposed on about 14; one planned exception to the page's own system on about 14.
- No conventional top navigation bar on about 45; small corner links on about 22; a single link or
  button on about 10.
- Endings: the name at full width about 18, the hero repeated inverted about 12, a closing scene of
  its own about 14, no footer or a single line about 22. Link-column footers are mentioned only as
  criticism.
- Motion (inferred from frames): autoplaying video about 50; pinned or fixed stages about 40; text
  reveals about 30 (blur-in 10, masked line rises 8, scroll-tied word colouring 7); horizontal strips
  about 27; marquees about 26; media swapped behind a fixed element about 15; scroll-linked scaling
  about 12. Rare: hover effects (4 mentions), parallax (6), accordions (5), bounce or spring motion
  (none). About 10 strong sites show little or no motion at all.
- How weak sites fail (54 sites under 6.8): the category's stock template about 20; centred headline,
  pill badge, two buttons and a screenshot about 9; stock modules after a distinctive hero about 8,
  plus about 17 in the middle band; a characterless default typeface about 13; text too small or too
  faint about 13; never saying what the thing is about 12.
- Faults of the best sites (90 at 7.5 or more), not to be copied: text at 9–13px about 24;
  information hidden behind the concept about 20; the idea running out mid-page about 15; text over
  footage with no scrim about 12; gates, preloaders and blank first paints about 12.

#### 9. What the inspector says about the gallery itself

Running this skill's own `inspect.mjs` rules over the 202 measurable gallery sites: the median site
has 4 `FAIL`s and only 4% have none. The rules that fire most: headline over two lines somewhere on
the page 60%, eyebrow-like label 60%, thin rules 50%, monospace 37%, shadows 32%, gradients 29%, index
numbering 29%.

So the house style is deliberately stricter than the gallery. It is not a description of award sites;
it is a narrower target inside what they do: their scale, their ideas, their imagery and restraint,
without the ornaments that have since become a uniform.

#### 10. The 25 highest-scored sites and their ideas

The panel's one-sentence reading of each. Notice that every one names something only that subject
could own. (Several use devices this skill bans; take the idea, not the ornament.)

| Site | Source | Score | Idea |
| --- | --- | --- | --- |
| PP Neue Montreal | Awwwards | 8.6 | A typeface specimen dressed as a vintage city travel guide: the font named after Montreal is sold through guidebook titling, postcards and old tourist footage. |
| Seasats | Awwwards | 8.4 | Calm, dusk-lit seascapes sell autonomous boats as serene instruments, and the navigation is a column of stacked colour swatches taken from that sea-and-sand palette. |
| AI in Design Report 2026 | Awwwards | 8.4 | A research report laid out like a colour-blocked print annual: a video collage on top, an oversized tight grotesk title, and flat orange, lilac, sage and black blocks carrying stats, quotes and chapters. |
| House of Honey | Awwwards | 8.4 | A block-heavy wordmark pierced by a fine script: the bold-against-delicate contrast is repeated at every scale, with giant pink script behind quiet serif statements. |
| White Desert | Awwwards | 8.4 | One word, the destination, set a third of the screen tall over footage like a film title card; sheer scale stands in for remoteness. |
| Applied Imagination | One Page Love | 8.3 | An essay conceived on a flight is read as a descent: an altimeter ticks from 30,000 ft to zero while you scroll down through clouds to mountains at ground level. |
| Cursor Compile | One Page Love | 8.3 | The event name drawn as seven looping one-line curves in seven colours, more signature than logotype, on an otherwise whisper-quiet off-white page. |
| The New Industrials | One Page Love | 8.3 | A long-read essay laid out inside a drafting grid, where colour fields shift as you read and machine parts drift through the margins and finally assemble into the publisher's initials. |
| Wild | One Page Love | 8.3 | A studio essay in which everything decorative is drawn on one square-pixel grid: the hero heatmap, the icons, the diagrams, the lettering and the footer. |
| Hildén & Kaira | Awwwards | 8.3 | The agency name is cast in liquid chrome across the full width, and the same chrome becomes the objects that float through the page, tying the pitch to one material. |
| PX Push | Awwwards | 8.2 | A design subscription presented as a retro broadcast: the entire site is seen through a CRT screen, with a chrome logo token as its mascot. |
| Illoca | Awwwards | 8.2 | Software for architects sold as a drafting table: a two-colour illustrated studio on graph paper that the scroll pushes into until the drawing fills the screen. |
| Aspen Search | Awwwards | 8.2 | The page is a tile system with no margins: the two-word name is split across cells that alternate type, dithered image, black and one mint green. |
| Dragonfly Redux | Awwwards | 8.2 | A crypto fund presented as a terminal artefact: every picture is rendered in characters, framed by four letters of the name pinned to the viewport corners. |
| Monolog | Awwwards | 8.2 | A studio pitch run as an asymmetric sheet: a narrow left column carries the sales talk while a wide right column stacks a very heavy headline and the proof. |
| The Queue | One Page Love | 8.1 | An essay on queueing where the queue is the ornament: a line of drawn figures stands along the bottom of the hero and returns between chapters in changing period dress. |
| Paul Kalkbrenner | Awwwards | 8.1 | Swiss poster typography for a techno artist: the name as one black line with a photo set inside it like a glyph, then every chapter gets its own flat colour. |
| Vero New York | Awwwards | 8.1 | A keepsake treated like couture: a slow close-up film opens, then a white sculpture of a dress stays pinned at centre while one sentence passes over it. |
| Depo Luxe | Awwwards | 8.1 | A film production roster shown as a full-screen reel in which every step is one film with only a title, a director and a client, set like credits at body size. |
| Longbow | Awwwards | 8.1 | The page is built on a visible four-column construction grid, and cars, cards and a giant condensed marquee are slotted into its cells like objects on an artboard. |
| Mosby's Files | Awwwards | 8.0 | An archive of architects presented as a physical stack of coloured index-tab file folders that you flip through. |
| Sarah & Matt Wedding | One Page Love | 8.0 | The site is the invitation: a letterpress-style card opens the page, and its ornaments and small typographic parts become the components for everything after it. |
| Zara Webb | One Page Love | 8.0 | A one-woman newborn-care practice presented like a hand-made keepsake: a mascot rabbit, scalloped and flower-shaped cut-outs, candid film photographs. |
| Noho | Awwwards | 8.0 | Furniture sold through people misusing it (wearing, balancing on, hiding behind chairs on flat colour backdrops) while the interface stays quiet. |
| Juggle | One Page Love | 8.0 | The headline literally drowns: a flat blue field rises to half height and the lines below the waterline change colour. |

Full notes on any studied site: `node scripts/draw.mjs --site <id>` (ids appear on direction sheets).

#### 11. How the skill was tested

Six client briefs (an invoicing tool, a restaurant, a designer's portfolio, a ceramic product, a
guesthouse, a design conference), each with no photographs. For every brief a fresh agent built the
page three ways: with no skill (baseline), with another published design skill (atelier, three briefs)
and with this skill. Every build was photographed by `inspect.mjs` in the same way and judged blind
by a separate agent with the juror brief (Awwwards weights, anonymous A/B/C folders, screenshots
only). The skill was revised after each round from the jurors' reasons and the builders' notes.

| Round | Briefs | This skill | Baseline | Atelier | Wins |
| --- | --- | --- | --- | --- | --- |
| 1 | 4 | 6.6 | 7.7 | 6.8 | 1 of 4 |
| 2 | 3 | 7.1 | 8.0 | | 0 of 3 |
| 3 | 3 | 7.5 | 7.5 | | 1 of 3 |
| 4 (unseen briefs) | 3 | 6.9 | 7.9 | 7.5 | 0 of 3 |
| 5 (same three) | 3 | 7.7 | 7.8 | 7.2 | 2 of 3 |

Under the inspector, the final builds measured 0 FAIL each; the baselines measured 8 to 13 FAIL each
(eyebrows, monospace labels, 01/02/03 numbering, hairlines, gradients, shadows, three-line headlines,
text under 13px).

What the jurors rewarded, in the order they named it: an idea that belongs to this client and not to
the category (the competitor test); one live thing on the page; full content at a readable size; a
first screen with one dominant element and a real button; drawings of the subject with detail. What
they punished: a quiet page that read as empty, a small headline, text sliding over pictures or cut
at the top, a page recoloured mid-section, rows cut at the right edge, a large sentence over three or
more lines (read as a long headline whatever its markup), navigation that took over the first screen.
Each of these is now a rule in SKILL.md or a check in the inspector.

Limits: one juror per brief per round, so single scores carry about half a point of noise; the round-5
briefs had been seen in round 4; jurors are models, not people.

#### 12. The October 2026 study: 100 Sites of the Day

A second study, made for v2.1, of the latest 100 Awwwards Sites of the Day (10 July to 17 October
2026), with a different aim from the first: where the pictures and footage sit, how pages move, and
the frame (margins, balance, empty space, titles). About three in four of these sites were also in
the first study.

- **Capture.** Headless Chrome at 1440×900 and 390×844 on 18 October 2026: four frames of the first
  4.5 seconds after load, every screen while scrolling with real wheel input (one frame at rest per
  step; the mid-step frames were cut from the top of the document instead of the viewport, so they
  were not used), five phone screens, and a measurement pass in the page: every picture and
  clip with its box, ratio, fit and corners; every section's content edges and pictures; blank runs;
  the CSS that loaded (curves, durations, keyframes, breakpoints, feature counts); the animations,
  transitions and script-driven moves that actually ran; GSAP tweens and scroll triggers where the
  page exposed them. Nothing a site owns (code, copy, pictures) is reproduced in the skill; only
  measurements and descriptions in our own words.
- **Panel.** One model reader per site studied its frames and measurements, described the idea, the
  first screen, the frame, every section, where each picture sits, the motion and what not to copy,
  and scored it the Awwwards way. 91 of 99 captures were usable (the rest showed a gate, a bot wall or
  a firewall page). Scores ran 6.7 to 7.9 (median 7.45); "top" means 7.5 or more (36 sites), "lowest"
  under 7.3 (16).
- **What it changed.** Where pictures and footage go: `imagery.md` §12. What strong pages do with
  motion, new tokens, recipes and the gimmicks to avoid: `motion.md` §2, §4–6 and §9–10. Empty space
  and the frame: `layout.md` §4–5. New compositions in `library/heroes.json` and `sections.json` and
  notes on media and motion in `library/sites.json` (`draw.mjs --site <id>`).
- **Headline numbers.** Pictures fill a median 16% of a scrolled screen, but in whole screens: 42% of
  screens hold none and 19% are 90% picture or more. The median page carries 7 pictures (top 8,
  lowest 2) and 42% carry footage (half of the top sites, one of the 16 lowest). 94% of pictures have
  square corners. Strong ease-outs are the curves that ran (expo and quint out); the median of all
  that ran on a site is 420ms. 60 of 99 open on a loading screen, and a third of the usable pages were
  still unreadable 4.5 seconds after load, with no gain in the design marks. About 1 text section in
  100 leaves half the width empty; the outer margins of strong pages match to a few pixels; 82% of
  text sections open with a heading; 15 of 97 first screens never say what the thing is, and those
  lose usability points.
- **Limits.** One capture per site on one day; a WebGL scene can render blank in a headless browser;
  the scroll-linked frames are partly an artefact of smooth-scroll libraries; one reader per site, so
  single scores carry about half a point of noise.

#### 13. The app-screen study

For dashboards and app screens (v2.1), a separate study of 23 real product screens chosen by the
owner (17 products, 17 light and 6 dark, at 1440–1512px): each screen measured from its pixels by a
reader with full-resolution crops, six cross-cutting reports (shell, data and charts, tables and
forms, visual language, taste, styles), and a synthesis into `references/app-screens.md` and
`library/app.json` (seven styles, five shells, screen patterns). The screenshots stay private; the
skill carries only the measurements and the rules. Blind test rounds of app screens built with and
without the skill then shaped the warnings at the top of that file.

---

## README.md

### tasteskill v2 (`design-taste-frontend`)

A design skill for coding agents, built from a study of 247 curated sites (One Page Love and Awwwards
Sites of the Day, October 2026). It gives an agent an art direction instead of letting it fall back on
the average landing page, holds it to a strict no-ornament house style, and makes it look at its own
render before calling the work done.

#### How it works

1. **Inventory.** The agent lists what only this client has: the name and what it means, the street,
   the numbers, the one constraint, the materials, the hours.
2. **Draw.** `scripts/draw.mjs` deals three of 20 directions (each an idea engine seen on the
   strongest studied sites); the agent picks the one that can carry something from the inventory, and
   the script deals the rest: a hero composition, section compositions, a type system of real free
   fonts, a palette, photographs, a motion, studied references, and under every blueprint a list of
   where it disagrees with the house rules. Recent draws are remembered so projects do not repeat.
3. **Idea and live thing.** One sentence tying the client's own material to the direction's device,
   checked against the nearest competitor, and one thing the visitor can do on the page.
4. **Build** from the sheet, words first, full content. When the project has no photographs of its
   own, `scripts/assets.mjs` finds real pictures of the subject's world in open collections (its
   street in old postcards, old maps, its materials, engravings of its trade, museum objects of its
   kind), downloads them into the project and records their credits; the subject is drawn in code
   only where no honest picture exists.
5. **Gate.** `scripts/lint.mjs` (source) and `scripts/inspect.mjs` (real browser, 1440 / 768 / 390)
   measure the house rules: headlines of two lines or fewer, no eyebrow labels, no monospace, no
   01/02/03, no thin rules, no gradients, no resting shadows, no cream-and-terracotta, no violet, and
   the faults blind jurors punished: no focal point, empty screens, text covered or cut, long pins,
   sideways rows, faded text.
6. **Look.** The inspector saves screenshots; the agent critiques them with an Awwwards-weighted
   rubric, fixes the top three problems and repeats, at most three rounds.

Five rounds of blind tests against a no-skill baseline and another design skill are recorded in
`references/research.md` §11.

#### Contents

```
SKILL.md                 the run, the house rules, the laws
references/              copy, type, colour, layout, imagery, motion, critique, tells, research
scripts/draw.mjs         deal options / a direction / reprint / redraw; --alternatives, --photos, --site
scripts/assets.mjs       search open image collections (Openverse, Wikimedia Commons, Art Institute of
                         Chicago, the Met) and, with --video, real footage (Wikimedia Commons, Internet
                         Archive, NASA); --get downloads with the credit, --credits prints them
scripts/lint.mjs         static scan for banned patterns and stock phrases
scripts/inspect.mjs      render, measure, photograph
scripts/lib/             zero-dependency Chrome DevTools client, the in-page probe, the rules
library/                 directions (20), heroes, sections, type systems, palettes, photographs,
                         studied sites, motions
assets/base.css, base.js an optional neutral foundation
evals/evals.json         six briefs for testing the skill against a no-skill baseline
```

#### Requirements

Node 22 or newer and an installed Chrome, Edge or Chromium for `inspect.mjs` (it drives the browser
over the DevTools protocol with Node's built-in WebSocket; nothing is installed). `draw.mjs`,
`lint.mjs` and `assets.mjs` run on Node 18+; `assets.mjs` needs network access and no API keys. Set
`CHROME_PATH` if the browser is somewhere unusual.

#### Install

Copy this folder to your skills directory, for example `~/.claude/skills/design-taste-frontend/`, or keep it in
a repository under `.claude/skills/`.

#### Notes

- Photographs in the library are served by Lorem Picsum from Unsplash, under the Unsplash licence.
  They are placeholders for atmosphere; replace them with the project's own pictures.
- Pictures found with `assets.mjs` keep their own licences. By default it offers only CC0, public
  domain, CC BY and CC BY-SA, and `--get` records the title, creator, licence and source of every
  download in `assets/credits.json`. The page must carry the credits (`--credits` prints them).
- `assets.mjs --video` finds short clips of the subject's world, takes a 720p-or-smaller rendition,
  refuses files over 25 MB unless `--max-mb` is passed, and saves a poster frame with each clip; how
  to use one on a page (muted loop, poster, stopped under reduced motion) is in
  `references/imagery.md` §11.
- Fonts are loaded from Google Fonts and Fontshare. Check each face's licence for your use.
- The scores in `references/research.md` are model judgements from screenshots, not Awwwards scores.
- The draw history lives in `~/.taste-skill/history.json` (set `TASTE_SKILL_HISTORY` to move it).
  Delete it to reset.
- A build takes an agent roughly 30–45 minutes and a few hundred thousand tokens with the full
  look-and-fix loop; most of that is finding or drawing pictures when a project has no photographs.
