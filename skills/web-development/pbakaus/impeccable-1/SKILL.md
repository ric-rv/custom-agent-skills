---
name: impeccable-1
description: "Use when the user wants to design, redesign, shape, critique, audit, polish, simplify, harden, animate, or otherwise improve a frontend interface: websites, landing pages, dashboards, product UI, components, forms, settings, onboarding, empty states, and native iOS or Android screens. Handles UX review, hierarchy, layout, typography, color, motion, UX copy, accessibility, responsive behavior, edge cases, and capturing or documenting design systems (DESIGN.md, tokens). Also for making bland UI bolder, loud UI quieter, or ambitious visual effects. Not for backend-only or non-UI tasks. (Part 1 of 2; continued in impeccable-2.)"
version: 4.7.0
user-invocable: true
argument-hint: "[shape · audit|critique · animate|bolder|colorize|delight|layout|overdrive|quieter|typeset · adapt|clarify|distill · harden|onboard|optimize|polish · init|document|extract|live|generate] [target]"
license: Apache 2.0
---

This skill gives you the tools and permission to make design that earns the name out-of-distribution craft. Work as an award-winning design director would: production-grade code, a clear POV, a deep grasp of what the client and its users need, and exceptional craft.

Core principles:
- Finish the job. No hedging, no shortcuts: the deliverable is complete, except assets the user must provide.
- Scale ambition to the surface's mode (see Modes). Persuade and Experience get full commitment: bold, distinct work with a point of view. On Operate and Read, ambition shows as precision and restraint, and patterns the visitor already knows earn their place.
- Verify by looking at the rendered result at the sizes it ships at, and batch the checks: fix what one look shows before looking again, rather than screenshotting after every tweak.

## Setup

1. Run `"${CLAUDE_SKILL_DIR}/scripts/impeccable" context` once per session, where `${CLAUDE_SKILL_DIR}` is the directory that contains this SKILL.md (the skill folder, not a plugin root two levels above it); keep cwd at the user's project. Every `"${CLAUDE_SKILL_DIR}/scripts/impeccable" <verb>` command in this skill and its references resolves against that base directory. In reference files, replace the skill-base-dir placeholder with this directory before running commands; it is not a shell variable. On a Windows shell without `sh`, call `& "${CLAUDE_SKILL_DIR}/scripts/impeccable.cmd"` instead. The launcher runs a self-contained binary that ships next to it or is downloaded once on first run; no Node or other runtime is required. Pass a named source file or route as `--target <path>`. It loads PRODUCT.md, DESIGN.md, the matching surface brief, and native-platform guidance when applicable; follow its directives and do not rerun it.
2. Load the request's playbook: its Commands-table reference for an explicit/implied sub-command, or [reference/new-work.md](../impeccable-2/SKILL.md#referencenew-workmd) for a new surface or replacement visual world. Inspect target and incumbent visual truth before editing. When the app cannot run, start with committed visual-regression goldens or screenshot fixtures; verify target and freshness against current tokens, CSS, components, or assets, resolve conflicts, and compare theme/variant captures.
3. After resolving analysis and direction, read [reference/craft-floor.md](#referencecraft-floormd) immediately before any UI edit, including small refinements. It carries the quality floor, the absolute bans, and the reflexes no detector catches. Do not load it for planning-only work.

**Launcher unavailable:** On refusal or failure, send a separate message **before the next tool call**: “Context loading did not run; I’ll read the existing project context directly.” Then read existing PRODUCT.md and DESIGN.md without inventing missing context, follow applicable steps 2–3, and continue through permitted tools. This applies to planning and editing; launcher failure alone does not block either.

## How to design

- **The brief wins.** Honor pinned aesthetics, eras, materials, fonts, and palettes even when they conflict with a saturated-pattern warning. Redirecting a clear brief toward your taste is failure.
- **Refinement preserves; redesign replaces.** Refinement keeps the incumbent identity, behavior, copy, and everything outside scope. Ask before replacing factual copy or adding claims. Redesign keeps product truth, content, function, native affordances, and constraints, but treats the old look as evidence and anti-reference; choose a replacement world in new-work and replace DESIGN.md. Never split the difference into polish on the discarded look.
- **Loaded symbols stay out of the decoration.** A subject's world does not license emblems tied to militarism, supremacy, or hate movements as motifs, badges, or ornament, such as the Rising Sun flag's rays, the Confederate battle flag, or Nazi-era insignia and their stylised variants; reach for that world's neutral forms instead. Content that documents such a symbol as fact stays as it is.
- **Visual authority is evidence, not a filename.** Missing DESIGN.md alone does not make a project greenfield; new-work decides whether to preserve, expand, or replace the incumbent world.

## Modes

The mode names what the visitor's success looks like on this surface.

- **Persuade:** the visitor decides and acts; design is the product. Landing pages, marketing, campaigns, pricing. Earn attention and action. Ship real imagery when the brief needs it; follow the committed world, not category habit.
- **Operate:** the visitor completes a task. App UI, dashboards, editors, admin, settings, tools. Scanability, consistency, native expectations, and the real usage scene outrank expression. Brand lives in precise details.
- **Read:** the visitor understands something. Docs, articles, guides, help, changelogs. Structure for comprehension, then make the reading experience worth staying in.
- **Experience:** the visitor is inside the work itself. Portfolios, galleries, showcases. Let the artifact lead from the first viewport; the interface recedes.

Choose the mode from the requested surface, not the product, and persist it only in that surface brief. A tool's landing page is still Persuade; a fashion house's documentation is still Read; a docs index is Read, not Persuade. See [new-work.md](../impeccable-2/SKILL.md#referencenew-workmd) for new surfaces and [operate.md](../impeccable-2/SKILL.md#referenceoperatemd) for deeper Operate/Read guidance.

## Commands

| Command | Category | Description | Reference |
|---|---|---|---|
| `craft [feature]` | Build | Deprecated alias for an ordinary new-work request | [reference/craft.md](#referencecraftmd) |
| `shape [feature]` | Build | Plan UX/UI before writing code | [reference/shape.md](../impeccable-2/SKILL.md#referenceshapemd) |
| `init` | Build | Capture durable product context in PRODUCT.md | [reference/init.md](#referenceinitmd) |
| `document` | Build | Generate DESIGN.md from existing project code | [reference/document.md](#referencedocumentmd) |
| `extract [target]` | Build | Pull reusable tokens and components into design system | [reference/extract.md](#referenceextractmd) |
| `critique [target]` | Evaluate | UX design review with heuristic scoring | [reference/critique.md](#referencecritiquemd) |
| `audit [target]` | Evaluate | Technical quality checks (a11y, perf, responsive) | [reference/audit.md](#referenceauditmd) · native: [reference/audit.native.md](#referenceauditnativemd) |
| `polish [target]` | Refine | Final quality pass before shipping | [reference/polish.md](../impeccable-2/SKILL.md#referencepolishmd) |
| `bolder [target]` | Refine | Amplify safe or bland designs | [reference/bolder.md](#referenceboldermd) |
| `quieter [target]` | Refine | Tone down aggressive or overstimulating designs | [reference/quieter.md](../impeccable-2/SKILL.md#referencequietermd) |
| `distill [target]` | Refine | Strip to essence, remove complexity | [reference/distill.md](#referencedistillmd) |
| `harden [target]` | Refine | Production-ready: errors, i18n, edge cases | [reference/harden.md](#referencehardenmd) |
| `onboard [target]` | Refine | Design first-run flows, empty states, activation | [reference/onboard.md](../impeccable-2/SKILL.md#referenceonboardmd) |
| `animate [target]` | Enhance | Add purposeful animations and motion | [reference/animate.md](#referenceanimatemd) |
| `colorize [target]` | Enhance | Add strategic color to monochromatic UIs | [reference/colorize.md](#referencecolorizemd) |
| `typeset [target]` | Enhance | Improve typography hierarchy and fonts | [reference/typeset.md](../impeccable-2/SKILL.md#referencetypesetmd) |
| `layout [target]` | Enhance | Fix spacing, rhythm, and visual hierarchy | [reference/layout.md](#referencelayoutmd) |
| `delight [target]` | Enhance | Add personality and memorable touches | [reference/delight.md](#referencedelightmd) |
| `overdrive [target]` | Enhance | Push past conventional limits | [reference/overdrive.md](../impeccable-2/SKILL.md#referenceoverdrivemd) |
| `clarify [target]` | Fix | Improve UX copy, labels, and error messages | [reference/clarify.md](#referenceclarifymd) |
| `adapt [target]` | Fix | Adapt for different devices and screen sizes | [reference/adapt.md](#referenceadaptmd) · native: [reference/adapt.native.md](#referenceadaptnativemd) |
| `optimize [target]` | Fix | Diagnose and fix UI performance | [reference/optimize.md](../impeccable-2/SKILL.md#referenceoptimizemd) |
| `live` | Iterate | Visual variant mode: pick elements in the browser, iterate on alternatives | [reference/live.md](../impeccable-2/SKILL.md#referencelivemd) |
| `generate [n] [action] [element]` | Iterate | Variants, versions, or alternatives of a named element to choose from in the live browser; no manual picking | [reference/generate.md](#referencegeneratemd) |

Routing:

- **No argument:** read [routing.md](../impeccable-2/SKILL.md#referenceroutingmd) and present its context-aware menu; never auto-run a command.
- **Explicit or clearly implied request to run a command:** load its reference (native variant on native platforms) and follow it. Ask once if two commands fit.
- **Workflow or command-selection question:** read [Workflow questions](../impeccable-2/SKILL.md#workflow-questions).
- **Otherwise:** treat the request as general design work. Missing PRODUCT.md routes a new surface or replacement world through init, then new-work; a narrow refinement of existing code proceeds on the incumbent implementation as `impeccable context` directs, offering init afterward rather than blocking on it.
- `teach` aliases `init`. `craft` is a deprecated alias for ordinary new-work and adds nothing. `shape` owns task discovery, then enters new-work only for visual-world and surface-concept decisions.

After init writes PRODUCT.md, resume without rerunning `impeccable context`; init loads the native platform reference itself when the platform it recorded is `ios`, `android`, or `adaptive`.

**Pin / Unpin:** `"${CLAUDE_SKILL_DIR}/scripts/impeccable" pin <pin|unpin> <command>` creates or removes a standalone `/<command>` shortcut. Report the script's result concisely; relay stderr verbatim on error.

**Hooks:** `/impeccable hooks <on|off|status|ignore-rule|ignore-file|ignore-value|reset>` manages the design detector hook for this project (auto-runs the detector after UI file edits and surfaces findings). Load [reference/hooks.md](#referencehooksmd) when the user invokes it with any argument.

**Doctor:** `/impeccable doctor` reports and repairs drift between this project's Impeccable artifacts (PRODUCT.md, DESIGN.md and its sidecar, config, surface briefs, the hook) and what this version reads. Load [reference/doctor.md](#referencedoctormd) when the user invokes it, or when they ask what is out of date, stale, or needs refreshing. A `CONTEXT_STALE` directive in Setup's output is the cheap subset of the same report; act on it there per its own instructions rather than running doctor unasked.

**Never repair drift as a side effect of a design task.** A `CONTEXT_STALE` finding is reported, not acted on, unless the user asks. The one exception is a finding marked `auto`, which the next write to that file performs anyway.

---

## reference/adapt.md

> **Additional context needed**: target platforms/devices and usage contexts.

Adapt an existing design to a different context: another screen size, device, platform, or use case. The trap is treating adaptation as scaling. The job is rethinking the experience for the new context.

**Web only** (mobile web included). Native platforms (`ios` / `android` / `adaptive`) route to [adapt.native.md](#referenceadaptnativemd) instead; if the project is native, switch to it now.

---

#### Assess Adaptation Challenge

Understand what needs adaptation and why:

1. **Identify the source context**:
   - What was it designed for originally? (Desktop web? Mobile app?)
   - What assumptions were made? (Large screen? Mouse input? Fast connection?)
   - What works well in current context?

2. **Understand target context**:
   - **Device**: Mobile, tablet, desktop, TV, watch, print?
   - **Input method**: Touch, mouse, keyboard, voice, gamepad?
   - **Screen constraints**: Size, resolution, orientation?
   - **Connection**: Fast wifi, slow 3G, offline?
   - **Usage context**: On-the-go vs desk, quick glance vs focused reading?
   - **User expectations**: What do users expect on this platform?

3. **Identify adaptation challenges**:
   - What won't fit? (Content, navigation, features)
   - What won't work? (Hover states on touch, tiny touch targets)
   - What's inappropriate? (Desktop patterns on mobile, mobile patterns on desktop)

Adaptation is rethinking the experience for the new context, not scaling pixels.

#### Plan Adaptation Strategy

Create context-appropriate strategy:

##### Mobile Adaptation (Desktop → Mobile)

**Layout Strategy**:
- Single column instead of multi-column
- Vertical stacking instead of side-by-side
- Full-width components instead of fixed widths
- Bottom navigation instead of top/side navigation

**Interaction Strategy**:
- Touch targets 44x44px minimum (not hover-dependent)
- Swipe gestures where appropriate (lists, carousels)
- Bottom sheets instead of dropdowns
- Thumbs-first design (controls within thumb reach)
- Larger tap areas with more spacing

**Content Strategy**:
- Progressive disclosure (don't show everything at once)
- Prioritize primary content (secondary content in tabs/accordions)
- Shorter text (more concise)
- Larger text (16px minimum)

**Navigation Strategy**:
- Hamburger menu or bottom navigation
- Reduce navigation complexity
- Sticky headers for context
- Back button in navigation flow

##### Tablet Adaptation (Hybrid Approach)

**Layout Strategy**:
- Two-column layouts (not single or three-column)
- Side panels for secondary content
- Master-detail views (list + detail)
- Adaptive based on orientation (portrait vs landscape)

**Interaction Strategy**:
- Support both touch and pointer
- Touch targets 44x44px but allow denser layouts than phone
- Side navigation drawers
- Multi-column forms where appropriate

##### Desktop Adaptation (Mobile → Desktop)

**Layout Strategy**:
- Multi-column layouts (use horizontal space)
- Side navigation always visible
- Multiple information panels simultaneously
- Fixed widths with max-width constraints (don't stretch to 4K)

**Interaction Strategy**:
- Hover states for additional information
- Keyboard shortcuts
- Right-click context menus
- Drag and drop where helpful
- Multi-select with Shift/Cmd

**Content Strategy**:
- Show more information upfront (less progressive disclosure)
- Data tables with many columns
- Richer visualizations
- More detailed descriptions

##### Print Adaptation (Screen → Print)

**Layout Strategy**:
- Page breaks at logical points
- Remove navigation, footer, interactive elements
- Black and white (or limited color)
- Proper margins for binding

**Content Strategy**:
- Expand shortened content (show full URLs, hidden sections)
- Add page numbers, headers, footers
- Include metadata (print date, page title)
- Convert charts to print-friendly versions

##### Email Adaptation (Web → Email)

**Layout Strategy**:
- Narrow width (600px max)
- Single column only
- Inline CSS (no external stylesheets)
- Table-based layouts (for email client compatibility)

**Interaction Strategy**:
- Large, obvious CTAs (buttons not text links)
- No hover states (not reliable)
- Deep links to web app for complex interactions

#### Implement Adaptations

Apply changes systematically:

##### Responsive Breakpoints

Choose appropriate breakpoints:
- Mobile: 320px-767px
- Tablet: 768px-1023px
- Desktop: 1024px+
- Or content-driven breakpoints (where design breaks)

##### Layout Adaptation Techniques

- **CSS Grid/Flexbox**: Reflow layouts automatically
- **Container Queries**: Adapt based on container, not viewport
- **`clamp()`**: Fluid sizing between min and max
- **Media queries**: Different styles for different contexts
- **Display properties**: Show/hide elements per context

##### Touch Adaptation

- Increase touch target sizes (44x44px minimum)
- Add more spacing between interactive elements
- Remove hover-dependent interactions
- Add touch feedback (ripples, highlights)
- Consider thumb zones (easier to reach bottom than top)

##### Content Adaptation

- Use `display: none` sparingly (still downloads)
- Progressive enhancement (core content first, enhancements on larger screens)
- Lazy loading for off-screen content
- Responsive images (`srcset`, `picture` element)

##### Navigation Adaptation

- Transform complex nav to hamburger/drawer on mobile
- Bottom nav bar for mobile apps
- Persistent side navigation on desktop
- Breadcrumbs on smaller screens for context

Test on real devices. DevTools emulation is a useful first pass but misses real touch, performance, and browser chrome.

**Avoid**:
- Hide core functionality on mobile (if it matters, make it work)
- Assume desktop = powerful device (consider accessibility, older machines)
- Use different information architecture across contexts (confusing)
- Break user expectations for platform (mobile users expect mobile patterns)
- Forget landscape orientation on mobile/tablet
- Use generic breakpoints blindly (use content-driven breakpoints)
- Ignore touch on desktop (many desktop devices have touch)

#### Verify Adaptations

Test thoroughly across contexts:

- **Real devices**: Test on actual phones, tablets, desktops
- **Different orientations**: Portrait and landscape
- **Different browsers**: Safari, Chrome, Firefox, Edge
- **Different OS**: iOS, Android, Windows, macOS
- **Different input methods**: Touch, mouse, keyboard
- **Edge cases**: Very small screens (320px), very large screens (4K)
- **Slow connections**: Test on throttled network

**Custom controls** (sliders, drag surfaces, scrollable control strips): a before/after slider can pass every width check above and still refuse to drag on iOS, so exercise each one in scope in the same batched round as the checks above:

- **Primary gesture**: Tap it and confirm it responds as designed, then drag it with the target input method; the drag must complete, not just start
- **Scroll across it**: A swipe along the page's scroll axis across the control scrolls the page or container without activating it; a drag that starts on the control along its axis moves the control, not the page. Neither failure throws an error, so try both
- **Evidence**: Say what produced the evidence: an emulated viewport, synthesized touch input through a browser tool, which engine ran it (Chromium is not Safari), or a physical device. Screenshots and resized viewports verify layout, never a gesture. Name what stayed untested and move on; unreachable hardware is a reported gap, not a blocker

When the adaptation feels native to each context, hand off to `/impeccable polish` for the final pass.

---

#### Reference Material

The sections below were previously `responsive-design.md` and live inline now so the adapt flow has its deep responsive reference in one place.

##### Responsive Design

###### Mobile-First: Write It Right

Start with base styles for mobile, use `min-width` queries to layer complexity. Desktop-first (`max-width`) means mobile loads unnecessary styles first.

###### Breakpoints: Content-Driven

Don't chase device sizes; let content tell you where to break. Start narrow, stretch until design breaks, add breakpoint there. Three breakpoints usually suffice (640, 768, 1024px). Use `clamp()` for fluid values without breakpoints.

###### Detect Input Method, Not Just Screen Size

**Screen size doesn't tell you input method.** A laptop with touchscreen, a tablet with keyboard. Use pointer and hover queries:

```css
/* Fine pointer (mouse, trackpad) */
@media (pointer: fine) {
  .button { padding: 8px 16px; }
}

/* Coarse pointer (touch, stylus) */
@media (pointer: coarse) {
  .button { padding: 12px 20px; }  /* Larger touch target */
}

/* Device supports hover */
@media (hover: hover) {
  .card:hover { transform: translateY(-2px); }
}

/* Device doesn't support hover (touch) */
@media (hover: none) {
  .card { /* No hover state - use active instead */ }
}
```

**Critical**: Don't rely on hover for functionality. Touch users can't hover.

###### Safe Areas: Handle the Notch

Modern phones have notches, rounded corners, and home indicators. Use `env()`:

```css
body {
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
  padding-left: env(safe-area-inset-left);
  padding-right: env(safe-area-inset-right);
}

/* With fallback */
.footer {
  padding-bottom: max(1rem, env(safe-area-inset-bottom));
}
```

**Enable viewport-fit** in your meta tag:
```html
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
```

###### Responsive Images: Get It Right

###### srcset with Width Descriptors

```html
<img
  src="hero-800.jpg"
  srcset="
    hero-400.jpg 400w,
    hero-800.jpg 800w,
    hero-1200.jpg 1200w
  "
  sizes="(max-width: 768px) 100vw, 50vw"
  alt="Hero image"
>
```

**How it works**:
- `srcset` lists available images with their actual widths (`w` descriptors)
- `sizes` tells the browser how wide the image will display
- Browser picks the best file based on viewport width AND device pixel ratio

###### Picture Element for Art Direction

When you need different crops/compositions (not just resolutions):

```html
<picture>
  <source media="(min-width: 768px)" srcset="wide.jpg">
  <source media="(max-width: 767px)" srcset="tall.jpg">
  <img src="fallback.jpg" alt="...">
</picture>
```

###### Layout Adaptation Patterns

**Navigation**: Three stages: hamburger + drawer on mobile, horizontal compact on tablet, full with labels on desktop. **Tables**: Transform to cards on mobile using `display: block` and `data-label` attributes. **Progressive disclosure**: Use `<details>/<summary>` for content that can collapse on mobile.

###### Testing: Don't Trust DevTools Alone

DevTools device emulation is useful for layout but misses:

- Actual touch interactions
- Real CPU/memory constraints
- Network latency patterns
- Font rendering differences
- Browser chrome/keyboard appearances

**Test on at least**: One real iPhone, one real Android, a tablet if relevant. Cheap Android phones reveal performance issues you'll never see on simulators.

---

**Avoid**: Desktop-first design. Device detection instead of feature detection. Separate mobile/desktop codebases. Ignoring tablet and landscape. Assuming all mobile devices are powerful.

---

## reference/adapt.native.md

> **Additional context needed**: target platforms/devices and usage contexts.

Adapt an existing **native** design (`ios` / `android` / `adaptive`) to a different context: another device class, orientation, platform, or origin. The trap is treating adaptation as scaling. The job is rethinking the experience for the new context, inside the platform conventions of [ios.md](#referenceiosmd) / [android.md](#referenceandroidmd); read the target platform's reference before planning if Setup hasn't already.

#### Assess Adaptation Challenge

1. **Source context**: what was it designed for, and what assumptions did it make? (Phone-only? Portrait-only? One platform's idioms? A website?)
2. **Target context**: which device class (phone, tablet, foldable), orientation, platform, and usage posture (one-handed on the go vs two-handed at rest)?
3. **What breaks**: navigation that doesn't fit the target, layouts that stretch instead of restructure, gestures or controls that don't exist there?

#### Adaptation Strategies

##### Phone → Tablet (iPad / large screens)

- **Restructure, don't stretch.** A scaled-up phone UI on a tablet is the failure mode. Use size classes (iOS) / window size classes (Android) to switch structure.
- **Navigation changes shape**: tab bar stays or becomes a sidebar on iPad; Android navigation bar becomes a rail or drawer on expanded width.
- **Use the width**: split view / master-detail (list + detail side by side), multi-column grids, popovers where phones used sheets.
- **Multitasking is a size, not an edge case**: iPad Split View and Android multi-window can hand you a phone-width window on a tablet; size-class-driven layout handles both for free.

##### Orientation & foldables

- Landscape restructures (side-by-side panes, repositioned controls); never clip or letterbox. Lock orientation only when the task truly demands it.
- Foldables (Android): react to posture and hinge via window size classes; test folded, unfolded, and tabletop.

##### Platform → platform (iOS ↔ Android)

Translate idioms; never transplant them:

| iOS | Android |
|---|---|
| Tab bar | Navigation bar / rail / drawer |
| Edge-swipe back, back chevron | Predictive Back gesture / button |
| Switch, segmented control, system pickers | Material switch, chips, Material pickers |
| Action sheet | Bottom sheet / Material dialog |
| SF Symbols, SF Pro, Dynamic Type | Material Symbols, Roboto, sp scaling |
| Semantic system colors, materials | Material color roles, tonal elevation |
| System push/sheet transitions | Container transform, shared-axis, fade-through |

Rebuild navigation and controls in the target's vocabulary; carry over the brand's expressive layer (palette intent, type accent, motion personality) through the target's theming system.

##### Web → native (porting a website or web app)

Reconform, don't reflow. Replace web navigation with the platform's model, HTML-shaped controls with platform controls, hover affordances with touch-first ones, and px-based type with Dynamic Type / sp. Then treat the result to the full platform reference; the slop test there is the acceptance bar.

#### Implement & Verify

- Drive structure from **size classes / window size classes**, never from device-model checks.
- Respect safe areas and window insets in every new configuration (notch, hinge, status bar, keyboard).
- Test on simulators for breadth, then real hardware for truth: at least one phone and one tablet per shipped platform, both orientations, split-screen where supported.

When the adaptation feels native to each context, hand off to `/impeccable polish` for the final pass.

**Avoid**:
- Ship a stretched phone layout on a tablet
- Port one platform's controls or navigation onto the other
- Hide core functionality on smaller devices (if it matters, make it work)
- Lock orientation to dodge a layout bug
- Trust simulators alone (posture, gestures, and performance need hardware)

---

## reference/android.md

### Android platform

For native Android apps: Jetpack Compose, Android Views, React Native, Expo, Flutter shipping to Android hardware.

On native, the visitor mode narrows what expression may override. Material Design 3 governs structure, navigation, and interaction in every mode; brand expresses through Material's theming (color roles, type scale, shape, motion). A Material-everywhere cross-platform app that also ships to iPhone still owes iOS its OS guarantees on that hardware: safe-area insets, Reduce Motion, edge-swipe back.

#### The Android slop test

Would a fluent Android user trust this app, or trip on off-spec components? The most common tell is an iOS app wearing Android's skin: a bottom-only navigation copied from iPhone, a back arrow that ignores the system Back gesture, Cupertino-shaped switches and dialogs. Material 3 is the rulebook; follow its components and theme the brand through it.

#### Layout & structure

- **Material navigation, matched to size.** Navigation bar (bottom, 3–5 destinations) on compact width; navigation rail or drawer on expanded width. Never ship a phone bottom-bar untouched on a tablet.
- **System Back always works.** Honor the predictive Back gesture and Back button; never trap the user or hijack the gesture.
- **Edge-to-edge with window insets.** Apply the status bar, navigation bar, display cutout, and IME insets so content never hides behind system bars or the keyboard.
- **Top app bar for screen context**; pair with a FAB when the screen has a single primary action.

#### Touch targets

- **48×48 dp minimum** for every touch target, with at least 8 dp between them.

#### Typography

- **Material type scale.** Display, Headline, Title, Body, Label roles (large/medium/small each). Map text to roles; never hand-pick sizes per screen.
- **Roboto is the system face**; theme a brand face in through the type scale, keeping body, labels, and controls legible and consistent.
- **sp units, never fixed px**, so type follows the system font-size setting.

#### Color & theming

- **Material color roles** (primary, on-primary, surface, surface-variant, secondary-container, outline, error). Role tokens resolve light/dark and contrast variants automatically; raw hex breaks there.
- **Dynamic Color (Material You)** where it fits: derive the scheme from the user's wallpaper on Android 12+, with a static fallback.
- **Dark theme is a first-class scheme.** Design and test it; never a quick invert.
- **Tonal elevation.** Convey elevation through the standard surface tonal levels (plus shadow where appropriate); no arbitrary drop shadows.

#### Components & motion

- **Material components.** Buttons (filled / tonal / outlined / text), FAB, switches, chips, snackbars, bottom sheets, Material dialogs, navigation bar/rail/drawer. Never port iOS controls or invent equivalents.
- **One FAB, one primary action.** Never stack FABs or spend one on a secondary task.
- **Snackbars for transient feedback** (actionable when useful, never a toast for that); dialogs only for decisions that must interrupt.
- **Material motion patterns.** Container transform, shared-axis, fade-through, with standard easing and durations; honor the system Remove animations setting with a crossfade or instant cut.

#### Verifying the build

- **Screenshots come from the emulator or a connected device, never a browser.** Build and install, then capture with `adb exec-out screencap -p > <path>` (pick a device with `adb -s <serial>` when several are attached). Capture every device class the app ships to, at least one phone and, when tablets are a target, one tablet, and write the files where the review flow expects them.
- **Dark theme and font scale belong in the pass.** `adb shell cmd uimode night yes` flips the theme; `adb shell settings put system font_scale 1.3` (restore `1.0` after) catches the clipped labels a fixed layout hides; with several targets attached, the capture's `-s <serial>` goes on these commands too.
- **Emulators give breadth; gestures, refresh rates, and performance need hardware.** Say which one produced the evidence.

---

## reference/animate.md

> **Additional context needed**: performance constraints.

Use motion to explain state, relationship, and hierarchy, or to create one authored moment the surface has earned. Decoration without purpose is animation debt.

---

#### Visitor mode

- **Persuade + Experience:** motion may carry the voice. Prefer one rehearsed focal sequence to repeated section reveals.
- **Operate + Read:** motion serves feedback, state, and continuity. Keep routine transitions fast and do not make users wait through page-load choreography.
- **Native (`ios` / `android` / `adaptive`):** follow the Motion section of [ios.md](#referenceiosmd) or [android.md](#referenceandroidmd), including the platform's Reduce Motion behavior. Do not apply the web tooling below.

#### Find the job

Inspect the existing motion language, interaction states, target devices, and performance budget. Find only the places where motion would:

- acknowledge an action;
- make a state change or spatial relationship legible;
- preserve continuity through navigation or layout change;
- direct attention at a meaningful moment;
- embody the selected visual world.

Ask only when a material constraint cannot be inferred. Do not animate a static area merely because it exists.

#### Set the motion thesis

Write a short plan before implementation:

- **Focal moment:** the one sequence or interaction that deserves authorship, if any.
- **Continuity:** the state, layout, or navigation changes that need explanation.
- **Feedback:** the controls and outcomes that need acknowledgment.
- **Budget:** which effects may be expensive and how often they run.

The focal moment must come from this product and surface concept. A generic fade-and-rise, hover lift, parallax layer, or scroll reveal is not a thesis.

#### Choose material by meaning

Transform and opacity are reliable foundations, not the entire palette. Choose properties for what the transition communicates:

- **Continuity and relationship:** shared-element motion, FLIP-style transforms, view transitions, or deliberate spatial movement.
- **Focus and depth:** bounded blur, filter, backdrop, light, or shadow changes.
- **Reveal and composition:** masks, clip paths, cropping, or controlled occlusion.
- **Material and energy:** color, gradient position, texture, distortion, or shader effects when the world and runtime support them.
- **State and feedback:** the smallest change that makes cause and result unmistakable.

Do not stack techniques for spectacle. One strong material idea, carried through the focal sequence and quiet supporting states, is usually enough.

Sibling stagger is appropriate when a list appears as a list. Cap the total delay, and never reinterpret every scrolled section as a staggered list.

#### Timing and easing

Timing should express distance and consequence:

| Duration | Typical use |
|---|---|
| 100–150 ms | immediate feedback |
| 150–300 ms | routine state change |
| 300–500 ms | layout, overlay, or view transition |
| 500–800 ms | a deliberately authored focal entrance |

Exit faster than entrance. Use natural deceleration such as `cubic-bezier(0.16, 1, 0.3, 1)` for confident arrivals; do not use bounce or elastic curves by reflex. Long feedback feels like latency.

#### Implement to the runtime

- Use CSS transitions and keyframes for declarative state and bounded sequences.
- Use Web Animations API or the project's existing motion library for interruption, sequencing, and dynamic values.
- Use View Transitions or shared-element techniques when continuity across states is the point.
- Use scroll-driven motion only when the scroll relationship itself carries meaning, with a robust fallback.
- Do not add a dependency for an effect the existing stack can express cleanly.

Keep content visible in the default state so failed scripts do not hide the page. Avoid casually animating layout-driving properties such as `width`, `height`, `top`, `left`, and margins; use FLIP, transforms, or grid techniques when appropriate. Bound blur, filter, shadow, canvas, and shader work to isolated regions. Apply `will-change` only during known animation. Measure on target viewports and devices rather than assuming transform means fast.

#### Accessibility and control

Respect autoplay and sound preferences. Any nonessential loop must stop when offscreen or hidden.

Every web animation needs a `prefers-reduced-motion` path with an intentional alternative. Remove or reduce spatial movement while preserving opacity, color, and state transitions that carry meaning. Reduced motion means fewer and gentler animations, not disabling all motion; feedback that confirms an action should remain legible.

#### Verify

- The focal motion is specific to the selected world and surface.
- Every supporting animation explains feedback, state, or relationship.
- Interruption and repeated use behave correctly.
- Desktop, mobile, and keyboard paths remain usable.
- The `prefers-reduced-motion` path reduces movement without erasing meaningful feedback or state changes.
- Expensive effects stay smooth on the target device.
- Removing an animation would lose meaning or authored character, not merely decoration.

When motion earns its place, hand off to `/impeccable polish` for the final pass.

---

## reference/audit.md

Run systematic **technical** quality checks and generate a comprehensive report. Don't fix issues; document them for other commands to address.

This is a code-level audit, not a design critique. Check what's measurable and verifiable in the implementation.

**Web only.** Native platforms (`ios` / `android` / `adaptive`) route to [audit.native.md](#referenceauditnativemd) instead; if the project is native, switch to it now.

#### Diagnostic Scan

Run comprehensive checks across 5 dimensions. Score each dimension 0-4 using the criteria below.

##### 1. Accessibility (A11y)

**Check for**:
- **Contrast issues**: Text contrast ratios < 4.5:1 (or 7:1 for AAA)
- **Motion sensitivity**: `prefers-reduced-motion` needs an intentional alternative that preserves state change and hierarchy; flag a global `0.01ms` kill that destroys useful feedback, flashing above threshold, and motion that blocks focus, reading, or task completion
- **Missing ARIA**: Interactive elements without proper roles, labels, or states
- **Keyboard navigation**: Missing focus indicators, illogical tab order, keyboard traps
- **Semantic HTML**: Improper heading hierarchy, missing landmarks, divs instead of buttons
- **Alt text**: Missing or poor image descriptions
- **Form issues**: Inputs without labels, poor error messaging, missing required indicators

**Score 0-4**: 0=Inaccessible (fails WCAG A), 1=Major gaps (few ARIA labels, no keyboard nav), 2=Partial (some a11y effort, significant gaps), 3=Good (WCAG AA mostly met, minor gaps), 4=Excellent (WCAG AA fully met, approaches AAA)

##### 2. Performance

**Check for**:
- **Layout thrashing**: Reading/writing layout properties in loops
- **Expensive animations**: Casual layout-property animation, unbounded blur/filter/shadow effects, or effects that visibly drop frames
- **Missing optimization**: Images without lazy loading, unoptimized assets
- **will-change overuse**: `will-change` applied broadly or left on at rest (it is a targeted hint for known expensive animations, not a baseline requirement)
- **Bundle size**: Unnecessary imports, unused dependencies
- **Render performance**: Unnecessary re-renders, missing memoization

**Score 0-4**: 0=Severe issues (layout thrash, unoptimized everything), 1=Major problems (no lazy loading, expensive animations), 2=Partial (some optimization, gaps remain), 3=Good (mostly optimized, minor improvements possible), 4=Excellent (fast, lean, well-optimized)

##### 3. Theming

**Check for**:
- **Hard-coded colors**: Colors not using design tokens
- **Broken dark mode**: Missing dark mode variants, poor contrast in dark theme
- **Inconsistent tokens**: Using wrong tokens, mixing token types
- **Theme switching issues**: Values that don't update on theme change

**Score 0-4**: 0=No theming (hard-coded everything), 1=Minimal tokens (mostly hard-coded), 2=Partial (tokens exist but inconsistently used), 3=Good (tokens used, minor hard-coded values), 4=Excellent (full token system, dark mode works perfectly)

##### 4. Responsive Design

**Check for**:
- **Fixed widths**: Hard-coded widths that break on mobile
- **Touch targets**: Interactive elements < 44x44px
- **Broken touch interaction**: Custom sliders, drag surfaces, and scrollable control strips whose primary gesture fails under touch, that swallow page scroll or lose the drag to it, or that stay stuck after an interrupted gesture. Code tells: mouse-only handlers, no `touch-action` on a pointer-event drag surface, drag state that nothing clears on cancel, lost capture, or blur. Exercise the gesture when a browser tool can synthesize touch (a rendered viewport proves layout, not the gesture), then say what produced the evidence (emulated viewport, synthesized touch, which engine, physical device) and what stayed untested
- **Horizontal scroll**: Content overflow on narrow viewports
- **Text scaling**: Layouts that break when text size increases
- **Missing breakpoints**: No mobile/tablet variants

**Score 0-4**: 0=Desktop-only (breaks on mobile), 1=Major issues (some breakpoints, many failures), 2=Partial (works on mobile, rough edges), 3=Good (responsive, minor touch target or overflow issues), 4=Excellent (fluid, all viewports, proper touch targets, gestures work under touch)

##### 5. Implementation Integrity (CRITICAL)

Run the bundled detector and verify each finding in context. Look for repeated implementation shortcuts, design-system drift, misleading or decorative content, and structure that is interchangeable with an unrelated product. Keep deterministic findings separate from visual judgment and call out false positives.

**Desktop apps** (Electron, NW.js, CEF, WebView2): launch the app with a local DevTools port (`--remote-debugging-port=9222`, or `WEBVIEW2_ADDITIONAL_BROWSER_ARGUMENTS=--remote-debugging-port=9222` for WebView2; keep it on 127.0.0.1, never exposed), seed the state to audit, keep the window on screen (a hidden one skips the pixel contrast reads), then run `"<skill-base-dir>/scripts/impeccable" detect --cdp 9222 --target <part of the page URL or title> --json`. It returns the same JSON as a URL scan and leaves the window as found. Take screenshots through the harness's CDP tooling, and leave the window as you found it too. Tauri on macOS (WKWebView) and on Linux (WebKitGTK) expose no CDP: scan the source and say the rendered check did not run.

**Score 0-4**: 0=systemic drift, 1=major repeated failures, 2=several verified issues, 3=minor isolated issues, 4=coherent and intentional

#### Generate Report

##### Audit Health Score

| # | Dimension | Score | Key Finding |
|---|-----------|-------|-------------|
| 1 | Accessibility | ? | [most critical a11y issue or "--"] |
| 2 | Performance | ? | |
| 3 | Theming | ? | |
| 4 | Responsive Design | ? | |
| 5 | Implementation Integrity | ? | |
| **Total** | | **??/20** | **[Rating band]** |

**Rating bands**: 18-20 Excellent (minor polish), 14-17 Good (address weak dimensions), 10-13 Acceptable (significant work needed), 6-9 Poor (major overhaul), 0-5 Critical (fundamental issues)

##### Implementation Integrity Verdict
**Start here.** Pass/fail: does the implementation express a coherent product-specific system? Cite verified evidence and detector findings.

##### Executive Summary
- Audit Health Score: **??/20** ([rating band])
- Total issues found (count by severity: P0/P1/P2/P3)
- Top 3-5 critical issues
- Recommended next steps

##### Detailed Findings by Severity

Tag every issue with **P0-P3 severity**:
- **P0 Blocking**: Prevents task completion. Fix immediately
- **P1 Major**: Significant difficulty or WCAG AA violation. Fix before release
- **P2 Minor**: Annoyance, workaround exists. Fix in next pass
- **P3 Polish**: Nice-to-fix, no real user impact. Fix if time permits

For each issue, document:
- **[P?] Issue name**
- **Location**: Component, file, line
- **Category**: Accessibility / Performance / Theming / Responsive / Implementation Integrity
- **Impact**: How it affects users
- **WCAG/Standard**: Which standard it violates (if applicable)
- **Recommendation**: How to fix it
- **Suggested command**: Which command to use (prefer: /impeccable adapt, /impeccable animate, /impeccable audit, /impeccable bolder, /impeccable clarify, /impeccable colorize, /impeccable critique, /impeccable delight, /impeccable distill, /impeccable document, /impeccable harden, /impeccable layout, /impeccable onboard, /impeccable optimize, /impeccable overdrive, /impeccable polish, /impeccable quieter, /impeccable shape, /impeccable typeset)

##### Patterns & Systemic Issues

Identify recurring problems that indicate systemic gaps rather than one-off mistakes:
- "Hard-coded colors appear in 15+ components, should use design tokens"
- "Touch targets consistently too small (<44px) throughout mobile experience"

##### Positive Findings

Note what's working well: good practices to maintain and replicate.

#### Recommended Actions

List recommended commands in priority order (P0 first, then P1, then P2):

1. **[P?] `/command-name`**: Brief description (specific context from audit findings)
2. **[P?] `/command-name`**: Brief description (specific context)

**Rules**: Only recommend commands from: /impeccable adapt, /impeccable animate, /impeccable audit, /impeccable bolder, /impeccable clarify, /impeccable colorize, /impeccable critique, /impeccable delight, /impeccable distill, /impeccable document, /impeccable harden, /impeccable layout, /impeccable onboard, /impeccable optimize, /impeccable overdrive, /impeccable polish, /impeccable quieter, /impeccable shape, /impeccable typeset. Map findings to the most appropriate command. End with `/impeccable polish` as the final step if any fixes were recommended.

After presenting the summary, tell the user:

> You can ask me to run these one at a time, all at once, or in any order you prefer.
>
> Re-run `/impeccable audit` after fixes to see your score improve.

Keep P3s few: a long tail of minor issues buries the ones that matter.

**Avoid**:
- Report issues without explaining impact (why does this matter?)
- Provide generic recommendations (be specific and actionable)
- Skip positive findings (celebrate what works)
- Forget to prioritize (everything can't be P0)
- Report false positives without verification

---

## reference/audit.native.md

Run systematic **technical** quality checks on a native app (`ios` / `android` / `adaptive`) and generate a comprehensive report. Don't fix issues; document them for other commands to address.

This is a code-level audit, not a design critique. Audit from source (SwiftUI / UIKit / Compose / React Native / Flutter); no browser tooling or `impeccable detect` applies. Score against the platform reference(s): [ios.md](#referenceiosmd) / [android.md](#referenceandroidmd), both for `adaptive`. Read them before scoring if Setup hasn't already. The report skeleton mirrors [audit.md](#referenceauditmd); keep the two in sync when changing it.

#### Diagnostic Scan

Run comprehensive checks across 5 dimensions. Score each dimension 0-4 using the criteria below.

##### 1. Accessibility (VoiceOver / TalkBack)

**Check for**:
- **Missing labels**: interactive elements without accessibility labels, traits/roles, or state announcements
- **Reading and focus order**: illogical traversal, unreachable controls, focus lost on navigation
- **Text scaling**: fixed point sizes defeating Dynamic Type (iOS) or px instead of sp (Android); layouts that clip or overlap at large sizes
- **Touch targets**: below 44 pt (iOS) / 48 dp (Android), or crammed without spacing
- **Reduce Motion ignored**: parallax and large slides with no crossfade alternative
- **Contrast**: text failing contrast in either appearance, light or dark

**Score 0-4**: 0=Screen reader unusable, 1=Major gaps (unlabeled controls, no scaling), 2=Partial (labels exist, order or scaling breaks), 3=Good (minor gaps), 4=Excellent (labeled, ordered, scales cleanly, Reduce Motion honored)

##### 2. Performance

**Check for**:
- **Slow startup**: heavy work on launch before first frame
- **Unvirtualized lists**: long content without FlatList / LazyColumn / List recycling
- **Main-thread jank**: synchronous work in scroll or gesture paths, dropped frames on 60/120 Hz
- **Wasted rendering**: unnecessary re-renders (React Native) or recompositions (Compose); missing memoization/keys
- **Image handling**: full-size images decoded for thumbnails, no caching
- **App weight**: bloated JS bundle or binary, unused dependencies

**Score 0-4**: 0=Janky everywhere, 1=Major problems (unvirtualized lists, slow launch), 2=Partial, 3=Good (minor improvements possible), 4=Excellent (fast launch, smooth scroll, lean)

##### 3. Appearance & Theming

**Check for**:
- **Hard-coded colors**: raw hex instead of semantic system colors (iOS) / Material color roles (Android) / design tokens
- **Broken dark appearance**: missing dark variants, poor contrast in dark, quick inverts
- **Dynamic Color** (Android 12+): no static fallback scheme, or ignored where it fits
- **Off-platform materials**: hand-rolled visual materials where system materials or tonal elevation are expected

**Score 0-4**: 0=Hard-coded everything, 1=Minimal tokens, 2=Partial (tokens exist, inconsistently used), 3=Good (minor hard-coded values), 4=Excellent (semantic throughout, both appearances first-class)

##### 4. Platform Conformance (CRITICAL)

Score against the loaded platform reference(s), including their slop tests. **Check for**:
- **Broken system gestures**: edge-swipe back disabled (iOS), predictive Back hijacked (Android)
- **Inset violations**: content under the notch, Dynamic Island, home indicator, status bar, or keyboard
- **Off-platform navigation**: custom global nav, overloaded tab bars, iOS patterns on Android or vice versa
- **Web-shaped controls**: HTML-style buttons, custom toggles, hover-dependent affordances
- **Icon drift**: mixed icon sets instead of SF Symbols / Material Symbols
- **System drift**: repeated shortcuts or decorative patterns that conflict with the product, platform, or established design system

**Score 0-4**: 0=Web port (nothing native), 1=Heavy violations (3-4 kinds), 2=Some (1-2 noticeable), 3=Mostly conformant (subtle issues), 4=Fully native (a fluent user trusts every screen)

##### 5. Adaptivity

**Check for**:
- **Stretched phone layouts**: tablet/iPad rendering a scaled-up phone UI instead of using size classes / window size classes
- **Orientation breakage**: landscape clipping, ignored, or locked without reason
- **Keyboard/IME handling**: inputs hidden behind the keyboard, no inset adjustment
- **Multitasking**: iPad Split View / Android multi-window breaking layout
- **Foldables**: hinge-unaware layouts on posture change (Android)

**Score 0-4**: 0=One screen size only, 1=Major breakage (landscape or tablet broken), 2=Partial, 3=Good (minor edge cases), 4=Excellent (adapts across sizes, orientations, and windowing)

#### Generate Report

##### Audit Health Score

| # | Dimension | Score | Key Finding |
|---|-----------|-------|-------------|
| 1 | Accessibility | ? | [most critical issue or "--"] |
| 2 | Performance | ? | |
| 3 | Appearance & Theming | ? | |
| 4 | Platform Conformance | ? | |
| 5 | Adaptivity | ? | |
| **Total** | | **??/20** | **[Rating band]** |

**Rating bands**: 18-20 Excellent (minor polish), 14-17 Good (address weak dimensions), 10-13 Acceptable (significant work needed), 6-9 Poor (major overhaul), 0-5 Critical (fundamental issues)

##### Platform Conformance Verdict
**Start here.** Pass/fail: does this read as a native app or a ported website? List specific violations. Be brutally honest.

##### Executive Summary
- Audit Health Score: **??/20** ([rating band])
- Total issues found (count by severity: P0/P1/P2/P3)
- Top 3-5 critical issues
- Recommended next steps

##### Detailed Findings by Severity

Tag every issue with **P0-P3 severity**:
- **P0 Blocking**: Prevents task completion. Fix immediately
- **P1 Major**: Significant difficulty or platform-guideline violation. Fix before release
- **P2 Minor**: Annoyance, workaround exists. Fix in next pass
- **P3 Polish**: Nice-to-fix, no real user impact. Fix if time permits

For each issue, document:
- **[P?] Issue name**
- **Location**: Screen, file, line
- **Category**: Accessibility / Performance / Theming / Conformance / Adaptivity
- **Impact**: How it affects users
- **Guideline**: The HIG / Material rule it violates (if applicable)
- **Recommendation**: How to fix it
- **Suggested command**: Which command to use (prefer: /impeccable adapt, /impeccable animate, /impeccable audit, /impeccable bolder, /impeccable clarify, /impeccable colorize, /impeccable critique, /impeccable delight, /impeccable distill, /impeccable document, /impeccable harden, /impeccable layout, /impeccable onboard, /impeccable optimize, /impeccable overdrive, /impeccable polish, /impeccable quieter, /impeccable shape, /impeccable typeset)

##### Patterns & Systemic Issues

Identify recurring problems that indicate systemic gaps rather than one-off mistakes:
- "Hard-coded colors appear in 15+ screens, should use semantic colors"
- "Touch targets consistently below 44 pt throughout the tab bar and list rows"

##### Positive Findings

Note what's working well: good practices to maintain and replicate.

#### Recommended Actions

List recommended commands in priority order (P0 first, then P1, then P2):

1. **[P?] `/command-name`**: Brief description (specific context from audit findings)
2. **[P?] `/command-name`**: Brief description (specific context)

**Rules**: Only recommend commands from: /impeccable adapt, /impeccable animate, /impeccable audit, /impeccable bolder, /impeccable clarify, /impeccable colorize, /impeccable critique, /impeccable delight, /impeccable distill, /impeccable document, /impeccable harden, /impeccable layout, /impeccable onboard, /impeccable optimize, /impeccable overdrive, /impeccable polish, /impeccable quieter, /impeccable shape, /impeccable typeset. Map findings to the most appropriate command. End with `/impeccable polish` as the final step if any fixes were recommended.

After presenting the summary, tell the user:

> You can ask me to run these one at a time, all at once, or in any order you prefer.
>
> Re-run `/impeccable audit` after fixes to see your score improve.

Keep P3s few: a long tail of minor issues buries the ones that matter.

**Avoid**:
- Report issues without explaining impact (why does this matter?)
- Provide generic recommendations (be specific and actionable)
- Skip positive findings (celebrate what works)
- Forget to prioritize (everything can't be P0)
- Report false positives without verification

---

## reference/bolder.md

> **Additional context needed**: which section is the target, and what must stay untouched.

An open direction round owns the word first: "bolder" said while a direction decision is on the table is the Bolder hand register steer, a fresh deal of foreign forms (see new-work.md), not this command. This command refines a surface whose world already shipped.

"Bolder" is an amplification request, and almost always it is scoped to something that already exists. The surrounding page, its system, and its conventions are the given. Your job is to raise one part to the conviction the rest already implies, without rebuilding anything the brief did not name. The reflex answer, reaching for more effects, is the opposite of bold; reject it first.

#### Scope is sovereign

"Everything else stays" is a literal instruction. Touch only the named target. Do not restyle its neighbors, do not migrate the page to a new idea, do not add colors, fonts, radii, shadows, or system primitives the surface does not already own. If the existing system genuinely cannot express the direction, do not expand it on your own. Ask with the AskUserQuestion tool and wait for the answer before continuing. Name the exact addition and the job it would do.

#### Why it reads flat

A section usually reads flat for reasons its neighbors have already solved. Look at what the rest of the page does that this section does not: the display type at full strength, the structural devices that carry meaning, the signature motif, the density and pacing. A flat section is typically one that quietly opts out of the system's own strongest moves. The most reliable bolder pass brings the target up to the expressive level its neighbors already reach, in the system's own vocabulary rather than a new one.

#### The amplification

- **Amplify what the system already owns.** Reuse its motif and its type scale at full strength, turned up for this section rather than invented for it. The bolder version should look more like the same brand, not less.
- **Keep content true.** Existing claims are part of the scope: preserve them unless the user supplies replacements. If real evidence is essential to the direction but absent, ask for it.
- **Commit, then clarify.** Half-measures read as noise. Make the one decisive move completely, then quiet everything around it so the move is legible. If every element got louder, the section got flatter.
- **Give it its own rhythm.** The target should read as a peak in the scroll, a shift in density or pace from what surrounds it, not simply more of the same.

#### The skeleton test

Strip the copy out of your planned section and study the bare structure. Does the skeleton still say what this section is and why it matters, through hierarchy and the system's devices alone? If it only works once the words return, the boldness is in the text size, not the design. A placeholder for an image or artifact names a job, an anchor and a piece of evidence, not a cue to drop in a decorative photo; fill that job with whatever the subject actually has.

#### Before you finish

- Everything outside the named target is unchanged.
- No new color, font, or system primitive appeared without being asked for.
- The conventions the section carried, including anything that drives an action, still work the same way.
- The section is unmistakably the same brand, only more sure of itself.

When the target holds its own without pulling the page apart, hand off to `/impeccable polish` for the final pass.

---

## reference/clarify.md

> **Additional context needed**: audience knowledge and emotional state.

Rewrite unclear interface text so users understand what happened, what matters, and what to do next. Preserve factual meaning, product terminology, and brand voice.

#### Audit the language

Read the entire interaction path, not isolated strings. Identify:

- ambiguous nouns, verbs, and actions;
- internal jargon or assumed knowledge;
- vague labels, outcomes, and system states;
- missing consequences, recovery, or timing;
- inconsistent terminology and capitalization;
- redundant headings, intros, helper text, and confirmations;
- text that breaks at realistic widths or in translation;
- tone that ignores stress, risk, success, or urgency.

Infer audience and task from product context and surrounding UI. Ask before changing factual claims, legal meaning, or a term that may be domain-specific.

#### Set the message hierarchy

For each state, decide:

1. the one fact the user needs now;
2. the action available next;
3. supporting context that changes the decision;
4. the appropriate tone for this moment.

Say each idea once. If the heading already explains the state, the introduction should add new information or disappear.

#### Rewrite by function

##### Actions and navigation

Use a specific verb and object when the outcome is not already obvious. Labels should describe what will happen, not the gesture used to trigger it. Keep the same noun and verb for the same concept throughout the product.

For destructive actions, name the object and consequence. Prefer undo over confirmation when recovery is safe. When confirmation is necessary, name the action on both the message and button instead of using `Yes`, `No`, `OK`, or `Submit`.

##### Forms

Use persistent labels; placeholders are examples, not labels. Put format and eligibility requirements before submission. Explain why information is requested only when it is not obvious. Required and optional treatment should be consistent.

Validation says what needs attention and how to correct it without blaming the user. Keep related instructions near the field and announce errors accessibly.

##### Errors and permissions

An actionable error answers:

1. what failed;
2. why, when known and useful;
3. how to recover or what alternative remains.

Do not expose internal codes as the primary message. Do not promise a cause or resolution the system cannot know. Treat privacy, payment, deletion, access loss, and blocked work seriously; warmth is welcome, jokes are not.

##### Loading, empty, and success states

Loading text names the real operation and sets an honest expectation when the wait is meaningful. Show determinate progress when available; never invent progress.

An empty state distinguishes first use, no results, filters, permissions, and failure. Explain the state and provide the next useful action.

Success confirms the completed outcome and mentions the next consequence only when it changes what the user should do. Routine success should be brief.

##### Help and instructional text

Helper text answers an implicit question instead of restating the control. Use progressive disclosure for uncommon detail. Link text must make sense out of context; icon-only controls need accessible names.

#### Voice, accessibility, and localization

Voice stays consistent; tone adapts to the moment. Use plain language without flattening terminology the audience genuinely knows.

- Write complete translatable messages rather than concatenated fragments.
- Keep variables and numbers structured so translators can reorder them.
- Allow expansion instead of abbreviating prematurely.
- Make alt text convey the image's information; use empty alt for decoration.
- Keep screen-reader names aligned with visible labels and outcomes.
- Do not rely on punctuation, color, or iconography to carry the message alone.

Maintain a short terminology glossary when inconsistency spans the product. Do not vary words for literary effect in an interface.

#### Verify

Read the flow in context and test:

- comprehension without hidden product knowledge;
- actionability at errors, empty states, and decision points;
- factual accuracy and consistent terminology;
- scanability at target widths and 200% zoom;
- long names, localization expansion, pluralization, and dynamic values;
- accessible names and announced state changes;
- tone appropriate to consequence and emotional context.

The final copy is as short as it can be without removing meaning or recovery.

When the language reads cleanly, hand off to `/impeccable polish` for the final pass.

---

## reference/colorize.md

> **Additional context needed**: existing brand colors.

Introduce color as hierarchy, meaning, and atmosphere. Preserve confirmed brand and semantic conventions; do not replace a visual world under the guise of colorizing it.

---

#### Visitor mode

- **Persuade + Experience:** color may carry the voice and own large regions when the selected world calls for it.
- **Operate + Read:** color primarily encodes action, selection, status, wayfinding, and reading hierarchy. Rarity gives an accent force.

#### Audit before choosing

Read DESIGN.md, tokens, assets, current themes, and representative states. Identify:

- which colors are confirmed brand commitments;
- current surface, text, action, and semantic roles;
- places where grayscale obscures hierarchy or state;
- contrast failures and color-only communication;
- light/dark or data-visualization requirements;
- whether the task asks for more color or a new identity.

If a new identity is required, use [new-work.md](../impeccable-2/SKILL.md#referencenew-workmd). Ask only when a binding brand decision cannot be inferred.

#### Choose a strategy

Name the intended emotional temperature, dominant relationship, contrast range, and color dosage before editing. The strategy may be restrained or immersive; it must follow the brief and selected world rather than a fixed percentage rule.

Build roles, not a bag of swatches:

- canvas and elevated surfaces;
- primary and secondary text;
- action, focus, and selection;
- borders and separators;
- success, warning, error, and information;
- data categories or scales when needed.

Use the project's existing color space. For a new web palette, prefer OKLCH because lightness and chroma can be adjusted predictably. Choose hue from product meaning and visual direction, never from a default category association.

#### Apply at system scale

- Let the strongest color own a deliberate region or role instead of scattering tiny accents.
- Keep the primary action easy to find; do not spend its color on decoration.
- Tint neutrals only when the brand hue genuinely creates cohesion. Neutral gray is valid when it serves the world.
- On colored surfaces, derive secondary text from the foreground or surface hue rather than using washed-out generic gray.
- Keep semantic meanings consistent, but respect platform and domain conventions instead of assuming fixed hues.
- For data, use distinct lightness, chroma, shape, label, or pattern so color is not the only code.
- In dark mode, design surface elevation and contrast explicitly; do not invert the light theme mechanically.
- Define primitive values and semantic tokens when the project has a token system. Theme changes should normally remap semantic roles.

Decoration without a relationship to hierarchy, state, content, or the visual world is not a color strategy.

#### Contrast and perception

Verify computed foreground/background pairs:

| Content | WCAG AA minimum |
|---|---|
| body text | 4.5:1 |
| large text | 3:1 |
| controls, icons, focus indicators | 3:1 |

Do not rely on eyesight alone. Check interactive states, overlays, text on images, disabled content, and both themes. Simulate common vision deficiencies. Information conveyed by color also needs text, shape, iconography, or position.

When deriving OKLCH ramps, vary lightness and reduce chroma near white and black. Do not keep high chroma at extreme lightness merely to make the math uniform. Prefer explicit colors over chains of translucent overlays when alpha would make contrast context-dependent.

#### Verify

- Every color has a stable role or a world-specific atmospheric purpose.
- Attention lands on the intended action, content, or state.
- The palette works across quiet, dense, interactive, error, and empty states.
- Light and dark themes are each composed, not mechanically inverted.
- Contrast and non-color cues pass in all relevant states.
- The result is recognizably this product, not a generic “colorful” treatment.

When the palette earns its place, hand off to `/impeccable polish` for the final pass.

#### Live-mode signature params

When invoked from live mode, every variant declares a `color-amount` parameter. Author CSS against `var(--p-color-amount, 0.5)` so the user can move from neutral to the variant's full color strategy without regeneration.

```json
{"id":"color-amount","kind":"range","min":0,"max":1,"step":0.05,"default":0.5,"label":"Color amount"}
```

Add at most two variant-specific parameters, such as palette, temperature, or tint behavior. Follow [live.md](../impeccable-2/SKILL.md#referencelivemd)'s parameter contract.

---

## reference/component-review.md

### Plan and asset review

Use this checkpoint on comp-led builds once every raster region has its plate and the plates gate has scored them, before any page code exists. The approved comp is the reference. The user reviews two things: the plates that will ship, and the production plan for everything else, meaning which regions code draws. A painted region planned as code is the most expensive mistake a comp-led build makes, and this is where the user catches it. Text, controls and chrome are judged later, in the assembled first viewport.

#### Plan, capture, serve

Run `"<skill-base-dir>/scripts/impeccable" component-review plan`. It writes `.impeccable/review/components.json` from the measured spec, the comp and the plate files, and refuses, naming each one, while any raster region lacks its plate. Never write or edit that file for this stage: the packet is derived from the spec, so every change belongs in the regions file.

If the harness exposes `component_review`, call it with `manifest_path` set to `.impeccable/review/components.json`. The host captures, presents the review and returns the user's decisions. A suspended request is waiting for the user; it is not a failed build or an approval.

Otherwise run `"<skill-base-dir>/scripts/impeccable" component-review capture --manifest .impeccable/review/components.json`, then start `"<skill-base-dir>/scripts/impeccable" component-review serve --session <returned session>` in the background. Open the URL it prints in the available browser and wait for the user; `serve` exits 0 once they submit. Read the decisions with `"<skill-base-dir>/scripts/impeccable" component-review status --session <id>`; `"<skill-base-dir>/scripts/impeccable" component-review verify --manifest .impeccable/review/components.json` confirms approval and refuses pending, needs-work and stale input. Never submit the page or write a receipt on the user's behalf.

`serve` exits 2 when this session has no browser (the same signal as the decision page) and 4 when it closes after 30 idle minutes without a decision. Either way no one is reviewing: stop waiting, do not approve anything yourself, and do not build past this checkpoint. End the run and report the plan and asset review as pending with its session ID, so the user can resume it. A waiting review is pending work, not a completed build.

#### Act on the receipt

Apply the user's decisions as given, never your own favorable verdict in their place.

- **approve**: once every item is approved and the inventory is confirmed, advance to the hero.
- **revise** (a plate): regenerate that plate at the same path with the user's feedback.
- **revise with split** (an asset): replace that region in the regions file with its layers: a frame plate with a transparent opening (kind `plate`, same box), the content as its own `image` region at the opening's box, and each moving part (a shutter, a door) as its own plate. Name each layer after the original region, as `<id>-frame`, `<id>-view` or `<id>-shutter-left`, so the next round shows it as part of the user's request. Rerun `"<skill-base-dir>/scripts/impeccable" comp-spec --comp <comp.png> --regions <regions.json>` and produce the plates.
- **revise** (a plan item): change the regions file as the feedback says (resize or extend a raster region, split material into its own plate region, or adjust the code region), rerun `"<skill-base-dir>/scripts/impeccable" comp-spec --comp <comp.png> --regions <regions.json>`, and produce any new plates.
- **reclassify** (a code region): in the regions file, change that region's `kind` to the one the user chose and rewrite its `note` to describe the material. Rerun `"<skill-base-dir>/scripts/impeccable" comp-spec --comp <comp.png> --regions <regions.json>`, then produce the new plates, with the asset producer when subagents are available.
- **missing**: add the region to the regions file, rerun `"<skill-base-dir>/scripts/impeccable" comp-spec --comp <comp.png> --regions <regions.json>`, and produce its plate if it is raster.

Then run `plan`, `capture` and `serve` again. Unchanged decisions carry over, so the user sees only what changed. Any spec change, or a plate replaced after acceptance, needs a new round; the build-phase gate stays closed until the review of the current spec is accepted.

#### Assemble and review

Build the first viewport from the approved plates and plan, and run the hero gate. Human review does not waive its integrity checks. After three failed hero attempts, or three failed responsive attempts before any first viewport is accepted, stop iterating and present the first-viewport review with the current build; the user's eye settles what the readings could not.

Present a second manifest at `.impeccable/review/hero.json`. You write this one, and its shape is fixed:

```json
{
  "schemaVersion": 2,
  "stage": "hero",
  "id": "hero",
  "title": "First viewport",
  "comp": {"path": ".impeccable/mocks/comp.png", "width": 1536, "height": 1024},
  "components": [{
    "id": "first-viewport",
    "name": "First viewport",
    "medium": "HTML / CSS",
    "note": "Assembled first viewport",
    "box": {"x": 0, "y": 0, "w": 1, "h": 1},
    "preview": {"kind": "page", "path": "index.html"},
    "dependencies": ["styles.css", "assets/plates/sky.png", "fonts/display.woff2"]
  }]
}
```

- `schemaVersion` is 2. Version 3 is the plan review packet and requires stage `components`. `codeRegions` and `specSha256` exist only in version 3 and are refused here. `reviewGroup` is refused too: version 3 rejects it, and any other version accepts it only on a page preview in a `components`-stage manifest, never in a hero manifest.
- `comp.path` is the `comp` value in `.impeccable/build/spec.json`, and `width` and `height` are that PNG's pixel size.
- Exactly one component, with `box` exactly `{"x": 0, "y": 0, "w": 1, "h": 1}` and `name`, `medium` and `note` as strings.
- `preview.path` is the page entry the build gates (`artifact` in `.impeccable/build/state.json`).
- `dependencies` lists every other file the page loads (stylesheets, scripts, plates, images, fonts) as bare strings. Every path, here and above, is project-relative and plain: no leading `./` or `/`, no `..`, no URL, no `?`, `#`, `%`, `:` or backslash. A request to a file missing from this list, or to another host, fails the capture.

The reference stays the approved comp. Call the same host review tool, or run `capture`, `serve` and `verify` with this manifest. Needs-work feedback starts another assembly round.

Acceptance closes human review for this build: never request plan, asset or assembly approval again. While the page renders what the user accepted, the hero score, the palette check and every numeric reading are advisories; material vetoes still hold (a missing or unreferenced plate, an SVG illustration, an organic clip, a clipped plate, invented ink, failed rendered presence). A text, control or chrome region the accepted screenshot also lacks is settled by the acceptance; a plate it lacks is a question for the user that the gate's reason spells out: do not move off what they accepted on your own, but carry out their answer, including placing the plate. When the capture no longer matches the accepted screenshot, restore what the user accepted; until then the readings apply. Complete the rest of the page, responsive behavior, finish checks and documentation with the accepted first viewport as the visual direction. This is first-viewport calibration, not a claim that the user reviewed the rest of the page. Shared stylesheet edits do not reopen approval. Preserve the accepted direction; a later explicit user change is a new task.

Assembled-page capture executes inline and declared local scripts from the pinned inputs. Network APIs, frames and workers are unavailable; the initial viewport must settle before capture. Keep the real page and declare its scripts rather than removing behavior to pass review.

---

## reference/craft-floor.md

### Craft floor

Load this after the direction is settled, and build without announcing the checklist. A pinned brief or the committed visual world overrides anything here; your own habit does not. When the design hook is active it already enforces the mechanical checks below as you edit: act on its findings instead of re-auditing each rule.

#### Verify

Each of these is a check on the built result, not an intention. Run them together in each batched look at the render, not as separate screenshot trips; the checks share one render.

- **Contrast:** body and placeholder text ≥4.5:1, large text ≥3:1. On colored surfaces tint secondary text from that hue or the foreground; never gray.
- **Depth:** shadows carry an offset and a soft blur. A zero-offset colored halo is decoration.
- **Spacing:** tight groups, generous separation, more space above a heading than below it. Read the computed values.
- **Type:** body measure 65–75ch, display max 6rem, tracking floor -0.04em, balanced headings, obvious scale and weight steps. Run the real copy at every breakpoint and fix what overflows.
- **Motion:** one authored moment, not scattered effects and not one identical entrance on every section. Exponential ease-out from an already-visible default. Reach past transform and opacity: blur, backdrop-filter, clip-path, mask, and shadow belong to the palette when they stay smooth.
- **States:** hover, disabled, loading, error, empty. Plus real content, working controls, responsive composition, keyboard focus.
- **Browser surfaces:** the parts you did not draw still carry the design. Text selection, the caret, custom scrollbars, focus rings, underline offset, and the numerals in tabular data all ship with browser defaults that belong to no design system. Theme them from the palette. This is the cheapest signal that a page was built rather than assembled, and the one models skip most reliably.
- **Copy:** the product's own language. Controls name their action; errors name the problem and the recovery.
- **Coverage:** every brief requirement present and findable within seconds.

#### Refuse

These are the category's defaults, not bans: the brief's own words can earn any of them. Reaching for one when the axis is free means you were not deciding; recognizing that means rewriting the element, not softening it.

Page scaffolds:

- Same-size cards of icon plus heading plus text as the page structure. Cards are the lazy container; nested cards are always wrong.
- The hero-metric template: big number, small label, supporting stats, accent.
- A kicker or eyebrow above a heading. This one is a ban, not a default: no brief earns it back. The heading carries its own weight; delete the label and let the heading speak.
- Section numbers (01 / 02 / 03) unless the sequence itself carries information the reader needs.
- A modal for a task that needs neither interruption nor protected focus.

Surface habits:

- Gradient text. Emphasis comes from weight or size.
- Glass and blur as decoration rather than as a specific effect.
- A colored `border-left` or `border-right` above 1px on cards, list items, callouts, or alerts.
- Hard offset shadows (`box-shadow: 4px 4px 0`) outside a world that is actually neobrutalist. The zero-blur block shadow is a costume, not a depth system; a world that did not choose it never earns it as a default.
- Sparklines, progress rings, and soft-shadowed rounded rectangles standing in for content.
- Monospace as a costume for "technical" rather than for code, data, or measurement.
- A system display face (Impact, Arial Black, the platform sans) as the display voice of an own-world page. Source and self-host a face whose character matches the approved lettering; the closest installed font is a failure, not a fallback.
- Unicode glyphs or emoji standing in for an icon system. Icons are drawn, from a real library or authored SVG, in one consistent stroke and weight.
- Geometric masks standing in for organic contours. A circle, polygon, or radial-gradient cutout approximating a photographic subject's edge is the cheap version of the effect and reads worse than omitting it. Derive an alpha matte from the actual image, or produce a cut-out asset.
- Light or dark picked by category. Pick it from the use scene: who, where, under what ambient light.

The floor holds the mechanics; it never picks the direction. With every check green, spend the page on the committed world, and when torn between refined and committed, commit.

---

## reference/craft.md

### Craft (deprecated alias)

`craft` is a deprecated alias for an ordinary request to make new visual work. It adds no setup, interview, checkpoint, tool, or quality behavior. Apply SKILL.md's normal routing: create missing PRODUCT.md through [init.md](#referenceinitmd), then follow [new-work.md](../impeccable-2/SKILL.md#referencenew-workmd) for visual authority, world and surface decisions, implementation, and finish.

Do not tell users they need to invoke `craft`. Natural requests such as “build this feature,” “make a landing page,” or “redesign this screen” use the same flow.

---

## reference/critique.md

##### Purpose

Resolve one stable target, run two independent assessments, synthesize a design critique, persist a snapshot, and ask the user what to improve next. The chat response is the primary deliverable; the snapshot is an archive of that run.

##### Hard Invariants

- Assessment A (design review) and Assessment B (detector/browser evidence) are both required, except on a native platform (see Assessment Orchestration).
- Assessment A and B MUST run as two isolated sub-agents whenever a sub-agent/Task tool is exposed. Running them inline in this context is "possible" but is NOT permitted; it is a degraded run. Inline is allowed ONLY when no sub-agent tool exists (or the user declined, on harnesses that ask). Native platforms run A alone (see Assessment Orchestration).
- If you degrade for any reason, the report's first line MUST be a banner: `⚠️ DEGRADED: single-context (<reason>)`. A silent degraded critique is a failed critique.
- Assessment A must finish before detector findings enter the parent synthesis context. Detector output is deterministic, but it still anchors judgment.
- A skipped detector is a failed critique run unless `impeccable detect` is missing or crashes after a real attempt, or the platform is native (see Assessment Orchestration).
- Viewable targets require browser inspection when available.
- Any local server started only for critique visualization must run in the background, have a recorded stop method, and be stopped before final reporting unless the user asks to keep it.
- Do not claim a user-visible overlay exists unless script injection succeeded and the detector ran in the page.
- The question is the LAST thing in the response. Write the entire report out first, then ask; nothing follows the question. Prose emitted after a structured question is withheld until the user answers it, so a report written after the question reads as if the critique never ran.
- A run that ends with neither the targeted questions nor a literal `Questions skipped: <reason>` line is an incomplete run. The report is not the finish; the close is.

##### Setup

1. **Resolve the target** to a concrete file path or URL. Prefer a source path over a dev-server URL when both identify the same surface; ports drift, paths do not.
   - "the homepage" -> `site/pages/index.astro` or `index.html`
   - "the settings modal" -> the primary component file
   - "this page" -> the current URL or source file
2. **Confirm the target slugs cleanly**:
   ```bash
   "<skill-base-dir>/scripts/impeccable" critique-storage slug "<resolved-path-or-url>"
   ```
   Every later command also accepts the resolved target directly and derives the same slug internally; never hand-write a slug. If this exits non-zero, skip persistence and trend for this run, but continue the critique.
3. **Read `.impeccable/critique/ignore.md`** if it exists. Drop matching findings silently; it is the only prior-run input critique consumes.

##### Assessment Orchestration

**Native platforms** (`ios` / `android` / `adaptive`): Assessment B does not apply, because `impeccable detect` and the browser overlay read only web markup. Run Assessment A alone in this context and skip both sub-agent gates below, the Codex permission question included: with no B there is nothing to isolate A from, so this is the complete native method and carries no degraded banner. Do not run `impeccable detect` on native source; its empty result reads as clean.

Delegate Assessment A and Assessment B to separate sub-agents. They must not see each other's output. Do not show findings to the user until synthesis.

Sub-agent gate (all harnesses):
- Unless a harness-specific gate below overrides this, spawn A and B as two isolated, parallel sub-agents whenever a sub-agent/Task tool is exposed. This is the default and is mandatory; do not run them inline because it is faster.
- Desktop apps (see **Desktop apps** under Assessment B) are the one exception to parallel: both sub-agents would drive the app's single window at once. Seed the window, spawn A, wait until it has finished and put the window back, then spawn B. They are still two isolated sub-agents, so this is not the degraded path.
- "Unavailable" means exactly one thing: no sub-agent/Task tool is exposed in this session (or, on harnesses that ask, the user declined). It does not mean inconvenient.
- If and only if sub-agents are unavailable, fall back sequentially: finish and record Assessment A, then run Assessment B, then synthesize, and emit the degraded banner.
- Whichever path you take, declare it in the report header (see Report header provenance). Skipping sub-agents without the banner is the most common failure of this command.

If browser automation is available, each assessment creates its own new tab. Never reuse an existing tab, even if it is already at the right URL. Desktop apps are the exception (see **Desktop apps** under Assessment B).

##### Assessment A: Design Review

Read relevant source files and visually inspect the live page when browser automation is available. Think like a design director.

Evaluate:
- **Design specificity**: Is the composition, interaction, and visual language grounded in this product, or could an unrelated product use it unchanged? Make this judgment before seeing detector output.
- **Holistic design**: hierarchy, IA, emotional fit, discoverability, composition, typography, color, accessibility, states, copy, and edge cases.
- **Cognitive load**: consult the [Cognitive Load Assessment](#cognitive-load-assessment) section below; report checklist failures and decision points with >4 visible options.
- **Emotional journey**: peak-end rule, emotional valleys, reassurance at high-stakes moments.
- **Nielsen heuristics**: consult the [Heuristics Scoring Guide](#heuristics-scoring-guide) section below; score all 10 heuristics 0-4, marking any heuristic the mode-applicability rule allows as `n/a` instead of forcing a number.

Return: design-specificity verdict, heuristic scores, cognitive load, emotional journey, 2-3 strengths, 3-5 priority issues, persona red flags, minor observations, and provocative questions.

##### Assessment B: Detector + Browser Evidence

Run the bundled detector and browser visualization evidence. On web, Assessment B is mandatory and must remain isolated from Assessment A until both are complete.

CLI scan:
```bash
"<skill-base-dir>/scripts/impeccable" detect --json [target]
```

- Pass markup files/directories as `[target]`; do not pass CSS-only files.
- For URLs, skip CLI scan and use browser visualization.
- For very large trees (500+ scannable files), narrow scope or ask.
- Exit code 0 = clean; 2 = findings.
- If the detector entrypoint is missing or fails to load, report deterministic scan unavailable and continue with browser/manual review.

Browser visualization is required for a viewable target when browser automation is available. Use a localhost dev/static URL for local files; avoid `file://` unless the available browser explicitly supports this workflow. Overlay flow:

1. Create a fresh tab and navigate. Prefer the harness's native/browser-canvas screenshot path before hand-rolling a Playwright/Puppeteer script; only fall back to a custom script when no native browser tool is exposed.
2. Preflight mutable injection by setting `document.title` and appending a `<script>` tag. Read-only evaluate APIs do not count.
3. If mutation is unavailable, skip live server, browser presentation, and injection; report fallback signal.
4. If mutation is available, start `"<skill-base-dir>/scripts/impeccable" live-server --background`, present the browser if supported, label `[Human]`, scroll top, inject `http://localhost:PORT/detect.js`, wait 2-3 seconds, read `impeccable` console messages, then run `"<skill-base-dir>/scripts/impeccable" live-server stop --keep-inject`. The overlay went in through the browser, so the project's HTML has no script tag to strip; a bare `stop` also runs `live-inject --remove` against the project's entry file, an edit a read-only critique should not make.
5. For multi-view targets, inject on 3-5 representative pages.

**Desktop apps** (Electron, NW.js, CEF, WebView2): there is no URL to open, so Assessment B attaches to the running app instead.

1. Launch the app with a local DevTools port: `--remote-debugging-port=9222` (Electron, NW.js, CEF), or `WEBVIEW2_ADDITIONAL_BROWSER_ARGUMENTS=--remote-debugging-port=9222` for WebView2. Keep the port on 127.0.0.1 and never expose it beyond this machine; prefer a test profile and test data.
2. Seed the state under review (route, open panel, theme, data). The scan reads the window as it stands. Keep the window on screen: a minimized or hidden window scans without the pixel contrast reads.
3. Run `"<skill-base-dir>/scripts/impeccable" detect --cdp 9222 --target <part of the page URL or title> --json`. It returns the same JSON as a URL scan and leaves the page as found. With several pages open it fails and lists them; rerun with a `--target` that names one.
4. Take screenshots through the harness's CDP tooling (`Page.captureScreenshot` on the same target). Skip the live-server overlay: there is no `[Human]` tab.

The app has one window, so the assessments take turns in it instead of opening tabs (A, then B; see the sub-agent gate), and each must leave it as found: put back any route, scroll, theme, or panel it changed. Tauri on macOS (WKWebView) and on Linux (WebKitGTK) expose no CDP: run Assessment A and the source scan only, and say so in Run Notes.

Return: CLI findings JSON/counts, browser console findings if applicable, false positives, and skipped/failed browser steps with concrete reasons.

After Assessment B returns usable CLI findings, reuse them. Do not rerun `impeccable detect` in the parent unless Assessment B failed, was truncated, or omitted count, rule names, or file locations.

##### Generate Combined Critique Report

Synthesize both assessments into a single report. Do not simply concatenate. Weave the findings together, noting where the LLM review and detector agree, where the detector caught issues the LLM missed, and where detector findings are false positives.

The chat response is the primary user-facing deliverable. Present the full structured critique below in chat; do not replace it with a summary and a link. The persisted snapshot is an archive of that run.

Structure your feedback as a design director would:

###### Report header provenance

The report's first line MUST declare how the assessments were run, so a degraded run is never silent:
- Dual-agent: `Method: dual-agent (A: <agent-id> · B: <agent-id>)`
- Degraded: `⚠️ DEGRADED: single-context (<reason, e.g. no sub-agent tool exposed>)`
- Native: `Method: design review only (detector not applicable, native platform)`

###### Design Health Score
> *Consult the [Heuristics Scoring Guide](#heuristics-scoring-guide) section below.*

Present the Nielsen's 10 heuristics scores as a table:

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | ? | [specific finding or "n/a" if solid] |
| 2 | Match System / Real World | ? | |
| 3 | User Control and Freedom | ? | |
| 4 | Consistency and Standards | ? | |
| 5 | Error Prevention | ? | |
| 6 | Recognition Rather Than Recall | ? | |
| 7 | Flexibility and Efficiency | ? | |
| 8 | Aesthetic and Minimalist Design | ? | |
| 9 | Error Recovery | ? | |
| 10 | Help and Documentation | ? | |
| **Total** | | **??/[applicable max]** | **[Rating band]** |

The applicable maximum is 4 times the number of heuristics you actually scored: **/40** when all ten apply, **/32** when two are `n/a`. Never print `/40` over a partial set.

Be honest with scores. A 4 means genuinely excellent. Most real interfaces score 20-32 out of 40.

**Mode applicability**: heuristics 7 (Flexibility and Efficiency) and 10 (Help and Documentation) may be scored `n/a` on Persuade and Experience surfaces (landing pages, campaigns, portfolios, bodies of work), as may any other heuristic that genuinely cannot apply to the surface under review. Write `n/a` in the Score cell with a one-line reason, and renormalize the total to the applicable maximum (e.g. **24/32** when two heuristics are n/a) so the rating band stays proportional. The persisted snapshot must record the applicable maximum and which heuristics were scored n/a.

###### Design Specificity Verdict

**Start here.** Does the result feel authored for this product, or category-interchangeable?

**LLM assessment**: Your unanchored evaluation of design specificity. Cover overall coherence, structural sameness, category-interchangeable choices, and missed opportunities for product character.

**Deterministic scan**: Summarize what the automated detector found, with counts and file locations. Note any additional issues the detector caught that you missed, and flag any false positives. On a native platform, write `not applicable (native platform)` instead.

**Visual overlays** (if injection succeeded): Tell the user that overlays are now visible in the **[Human]** tab in their browser, highlighting the detected issues. Summarize what the console output reported. If browser visualization was attempted but injection failed, say that no reliable user-visible overlay is available and report the fallback signal instead.

###### Overall Impression
A brief gut reaction: what works, what doesn't, and the single biggest opportunity.

###### What's Working
Highlight 2-3 things done well. Be specific about why they work.

###### Priority Issues
The 3-5 most impactful design problems, ordered by importance.

For each issue, tag with **P0-P3 severity** (see [Issue Severity below](#issue-severity-p0p3) for definitions):
- **[P?] What**: Name the problem clearly
- **Why it matters**: How this hurts users or undermines goals
- **Fix**: What to do about it (be concrete)
- **Suggested command**: Which command could address this (from: /impeccable adapt, /impeccable animate, /impeccable audit, /impeccable bolder, /impeccable clarify, /impeccable colorize, /impeccable critique, /impeccable delight, /impeccable distill, /impeccable document, /impeccable harden, /impeccable layout, /impeccable onboard, /impeccable optimize, /impeccable overdrive, /impeccable polish, /impeccable quieter, /impeccable shape, /impeccable typeset)

###### Persona Red Flags
> *Consult the [Personas reference](#persona-based-design-testing) below.*

Auto-select 2-3 personas most relevant to this interface type (use the selection table in the reference). If `CLAUDE.md` contains a `## Design Context` section from `impeccable init`, also generate 1-2 project-specific personas from the audience/brand info.

For each selected persona, walk through the primary user action and list specific red flags found:

**Alex (Power User)**: No keyboard shortcuts detected. Form requires 8 clicks for primary action. Forced modal onboarding. High abandonment risk.

**Jordan (First-Timer)**: Icon-only nav in sidebar. Technical jargon in error messages ("404 Not Found"). No visible help. Will abandon at step 2.

Be specific. Name the exact elements and interactions that fail each persona. Don't write generic persona descriptions; write what broke for them.

###### Minor Observations
Quick notes on smaller issues worth addressing.

###### Questions to Consider
Provocative questions that might unlock better solutions:
- "What if the primary action were more prominent?"
- "Does this need to feel this complex?"
- "What would a confident version of this look like?"

**Remember**:
- Be direct. Vague feedback wastes everyone's time.
- Be specific. "The submit button," not "some elements."
- Say what's wrong AND why it matters to users.
- Give concrete suggestions. Cut "consider exploring..." entirely.
- Prioritize ruthlessly. If everything is important, nothing is.
- Don't soften criticism. Developers need honest feedback to ship great design.

##### Deliver the Report

Write the full report into the chat response now, before any persistence work. This is the deliverable; everything below it is bookkeeping.

Do this first because the alternative is the most common way this command fails: the report gets composed once, straight into the persistence heredoc, and the run ends with a perfect archive nobody has read. Composing it into a file is not delivering it. If the report exists only in `.impeccable/critique/`, the run produced nothing.

Persistence is not the end of the run. After it, the response continues with the trend line and the close.

##### Persist the Snapshot

Once the report above is finalized, write it to `.impeccable/critique/` so the user can refer back, and so `/impeccable polish` can pick up the priority issues without a copy-paste.

Skip this step if the Setup slug was null (vague or root-level target).

1. **Write the body to a temp file** so you can pipe it to the helper. Use the full critique report (heuristic table, design-specificity verdict, priority issues, persona red flags, minor observations, and questions), but stop before the "Ask the User" / "Recommended Actions" sections that come later.

   This is a copy of the report you already delivered above, for later commands to read. It is not delivery. If you find yourself composing the report for the first time inside this heredoc, you have skipped Deliver the Report; go back and send it.

2. **Pass the structured metadata** through `IMPECCABLE_CRITIQUE_META` (JSON), then run the write command:
   ```bash
   IMPECCABLE_CRITIQUE_META='{"target":"<user phrasing>","total_score":<n>,"max_score":<n>,"na_heuristics":"<comma-separated numbers, or empty>","p0_count":<n>,"p1_count":<n>}' \
     "<skill-base-dir>/scripts/impeccable" critique-storage write "<resolved target>" <body-file>
   ```
   `max_score` is the applicable maximum from the heuristic table (40 when every heuristic applied), so a later run can tell a renormalized total from a full one. For a local file target, the helper also records an exact content fingerprint so polish can distinguish the assessed bytes from later edits without relying on Git state or timestamps. The helper prints the absolute path it wrote. Leave that file on disk. Polish closes it; this run does not.

3. **Delete the temp body file** after the write attempt completes, whether the write succeeded or failed. If deletion fails, mention `temp-file cleanup failed: <reason>` briefly in the final output, but do not block the critique.

4. **Read the trend** for context:
   ```bash
   "<skill-base-dir>/scripts/impeccable" critique-storage trend "<resolved target>" 5
   ```
   This returns a JSON array of the last 5 frontmatter entries (including the one you just wrote).

5. **Append a single line to the user-visible output**, after the report and before the questions:

   > **Trend for `<slug>` (last 5 runs): 24 → 28 → 32 → 29 → 32 (out of 40)**
   > Wrote `.impeccable/critique/<filename>`.

   Read `max_score` on each trend entry. When every entry shares one maximum, state it once as above. When they differ, print each score with its own denominator (`24/32 → 30/40`) and note that the runs scored different heuristic sets, so the line is not a like-for-like comparison. Treat a missing `max_score` on an older entry as 40.

   If this is the first run for the slug, the trend is just one score; say so: "First run for this target, no trend yet."

6. **Close the run.** Go to Ask the User below and emit the questions, or the `Questions skipped: <reason>` line when the count allows it. The run is not complete until you do. Persistence is bookkeeping and cleanup is not an ending; stopping here leaves the user with a report and no way forward, and leaves `/impeccable polish` with no priorities to inherit.

This is fire-and-forget. Do not show the user the helper's JSON output; only the human-readable trend line and the written path. Failures here should not block the rest of the flow; print the error and move on.

##### Ask the User

**After presenting findings**, use targeted questions based on what was actually found. Ask with the AskUserQuestion tool and wait for the answer before continuing. These answers will shape the action plan.

Ask in the same message that carries the report, with the report written out first and the question last. Do not split the two across turns: a turn that ends on the report is a turn that ends, and the questions never arrive. Order within the message is what matters, because prose emitted after a structured question is withheld until the user answers.

Ask questions along these lines (adapt to the specific findings; do not ask generic questions):

1. **Priority direction**: Based on the issues found, ask which category matters most to the user right now. For example: "I found problems with visual hierarchy, color usage, and information overload. Which area should we tackle first?" Offer the top 2-3 issue categories as options.

2. **Design intent**: If the critique found a tonal mismatch, ask whether it was intentional. For example: "The interface feels clinical and corporate. Is that the intended tone, or should it feel warmer/bolder/more playful?" Offer 2-3 tonal directions as options based on what would fix the issues found.

3. **Scope**: Ask how much the user wants to take on. For example: "I found N issues. Want to address everything, or focus on the top 3?" Offer scope options like "Top 3 only", "All issues", "Critical issues only".

4. **Constraints** (optional; only ask if relevant): If the findings touch many areas, ask if anything is off-limits. For example: "Should any sections stay as-is?" This prevents the plan from touching things the user considers done.

**Rules for questions**:
- Every question must reference specific findings from the report. Never ask generic "who is your audience?" questions.
- Keep it to 2-4 questions maximum. Respect the user's time.
- Offer concrete options, not open-ended prompts.
- Skipping is allowed only when the report listed **fewer than 3 Priority Issues**. Count them; do not judge the findings "straightforward" by feel. At 3 or more, the questions are required.

**Final-question gate.** The user-visible response must either include the targeted questions or carry the literal line `Questions skipped: <reason>` naming the count that permitted the skip. Each question must include 2-3 concrete answer options tied to the actual critique findings. Do not end with only open-ended questions, and do not end with neither: stopping after the report, having asked nothing and printed no skip line, is the most common way this command fails.

##### Recommended Actions

**After receiving the user's answers**, present a prioritized action summary reflecting the user's priorities and scope from Ask the User.

###### Action Summary

List recommended commands in priority order, based on the user's answers:

1. **`/command-name`**: Brief description of what to fix (specific context from critique findings)
2. **`/command-name`**: Brief description (specific context)
...

**Rules for recommendations**:
- Only recommend commands from: /impeccable adapt, /impeccable animate, /impeccable audit, /impeccable bolder, /impeccable clarify, /impeccable colorize, /impeccable critique, /impeccable delight, /impeccable distill, /impeccable document, /impeccable harden, /impeccable layout, /impeccable onboard, /impeccable optimize, /impeccable overdrive, /impeccable polish, /impeccable quieter, /impeccable shape, /impeccable typeset
- Order by the user's stated priorities first, then by impact
- Each item's description should carry enough context that the command knows what to focus on
- Map each Priority Issue to the appropriate command
- Skip commands that would address zero issues
- If the user chose a limited scope, only include items within that scope
- If the user marked areas as off-limits, exclude commands that would touch those areas
- End with `/impeccable polish` as the final step if any fixes were recommended

After presenting the summary, tell the user:

> You can ask me to run these one at a time, all at once, or in any order you prefer.
>
> Re-run `/impeccable critique` after fixes to see your score improve.

---

#### Reference Material

The sections below were previously separate reference files (`cognitive-load.md`, `heuristics-scoring.md`, `personas.md`). They live inline now so the critique flow has all its deep context in one place.

##### Cognitive Load Assessment

Cognitive load is the total mental effort required to use an interface. Overloaded users make mistakes, get frustrated, and leave. This reference helps identify and fix cognitive overload.

---

###### Three Types of Cognitive Load

###### Intrinsic Load: The Task Itself
Complexity inherent to what the user is trying to do. You can't eliminate this, but you can structure it.

**Manage it by**:
- Breaking complex tasks into discrete steps
- Providing scaffolding (templates, defaults, examples)
- Progressive disclosure: show what's needed now, hide the rest
- Grouping related decisions together

###### Extraneous Load: Bad Design
Mental effort caused by poor design choices. **Eliminate this ruthlessly.** It's pure waste.

**Common sources**:
- Confusing navigation that requires mental mapping
- Unclear labels that force users to guess meaning
- Visual clutter competing for attention
- Inconsistent patterns that prevent learning
- Unnecessary steps between user intent and result

###### Germane Load: Learning Effort
Mental effort spent building understanding. This is *good* cognitive load; it leads to mastery.

**Support it by**:
- Progressive disclosure that reveals complexity gradually
- Consistent patterns that reward learning
- Feedback that confirms correct understanding
- Onboarding that teaches through action, not walls of text

---

###### Cognitive Load Checklist

Evaluate the interface against these 8 items:

- [ ] **Single focus**: Can the user complete their primary task without distraction from competing elements?
- [ ] **Chunking**: Is information presented in digestible groups (≤4 items per group)?
- [ ] **Grouping**: Are related items visually grouped together (proximity, borders, shared background)?
- [ ] **Visual hierarchy**: Is it immediately clear what's most important on the screen?
- [ ] **One thing at a time**: Can the user focus on a single decision before moving to the next?
- [ ] **Minimal choices**: Are decisions simplified (≤4 visible options at any decision point)?
- [ ] **Working memory**: Does the user need to remember information from a previous screen to act on the current one?
- [ ] **Progressive disclosure**: Is complexity revealed only when the user needs it?

**Scoring**: Count the failed items. 0–1 failures = low cognitive load (good). 2–3 = moderate (address soon). 4+ = high cognitive load (critical fix needed).

---

###### The Working Memory Rule

**Humans can hold ≤4 items in working memory at once** (Miller's Law revised by Cowan, 2001).

At any decision point, count the number of distinct options, actions, or pieces of information a user must simultaneously consider:
- **≤4 items**: Within working memory limits, manageable
- **5–7 items**: Pushing the boundary; consider grouping or progressive disclosure
- **8+ items**: Overloaded; users will skip, misclick, or abandon

**Practical applications**:
- Action buttons: 1 primary, 1–2 secondary, group the rest in a menu
- Navigation menus: ≤5 top-level items (group the rest under clear categories)
- Long-form articles: one reading path; gather related links into a single block at the end instead of scattering them mid-flow
- Documentation sidebars: ≤4 sibling choices visible per level before grouping kicks in
- Portfolio and gallery indexes: one decision per screen (which piece to open), not filter, sort, and tag controls all at once

---

###### Common Cognitive Load Violations

###### 1. The Wall of Options
**Problem**: Presenting 10+ choices at once with no hierarchy.
**Fix**: Group into categories, highlight recommended, use progressive disclosure.

###### 2. The Memory Bridge
**Problem**: User must remember info from step 1 to complete step 3.
**Fix**: Keep relevant context visible, or repeat it where it's needed.

###### 3. The Hidden Navigation
**Problem**: User must build a mental map of where things are.
**Fix**: Always show current location (breadcrumbs, active states, progress indicators).

###### 4. The Jargon Barrier
**Problem**: Technical or domain language forces translation effort.
**Fix**: Use plain language. If domain terms are unavoidable, define them inline.

###### 5. The Visual Noise Floor
**Problem**: Every element has the same visual weight; nothing stands out.
**Fix**: Establish clear hierarchy: one primary element, 2–3 secondary, everything else muted.

###### 6. The Inconsistent Pattern
**Problem**: Similar actions work differently in different places.
**Fix**: Standardize interaction patterns. Same type of action = same type of UI.

###### 7. The Multi-Task Demand
**Problem**: Interface requires processing multiple simultaneous inputs (reading + deciding + navigating).
**Fix**: Sequence the steps. Let the user do one thing at a time.

###### 8. The Context Switch
**Problem**: User must jump between screens/tabs/modals to gather info for a single decision.
**Fix**: Co-locate the information needed for each decision. Reduce back-and-forth.

---

##### Heuristics Scoring Guide

Score each of Nielsen's 10 Usability Heuristics on a 0–4 scale. Be honest: a 4 means genuinely excellent, not "good enough."

###### Nielsen's 10 Heuristics

###### 1. Visibility of System Status

Keep users informed about what's happening through timely, appropriate feedback.

**Check for**:
- Loading indicators during async operations
- Confirmation of user actions (save, submit, delete)
- Progress indicators for multi-step processes
- Current location in navigation (breadcrumbs, active states)
- Form validation feedback (inline, not just on submit)

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | No feedback; user is guessing what happened |
| 1 | Rare feedback; most actions produce no visible response |
| 2 | Partial; some states communicated, major gaps remain |
| 3 | Good; most operations give clear feedback, minor gaps |
| 4 | Excellent; every action confirms, progress is always visible |

###### 2. Match Between System and Real World

Speak the user's language. Follow real-world conventions. Information appears in natural, logical order.

**Check for**:
- Familiar terminology (no unexplained jargon)
- Logical information order matching user expectations
- Recognizable icons and metaphors
- Domain-appropriate language for the target audience
- Natural reading flow (left-to-right, top-to-bottom priority)

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Pure tech jargon, alien to users |
| 1 | Mostly confusing; requires domain expertise to navigate |
| 2 | Mixed; some plain language, some jargon leaks through |
| 3 | Mostly natural; occasional term needs context |
| 4 | Speaks the user's language fluently throughout |

###### 3. User Control and Freedom

Users need a clear "emergency exit" from unwanted states without extended dialogue.

**Check for**:
- Undo/redo functionality
- Cancel buttons on forms and modals
- Clear navigation back to safety (home, previous)
- Easy way to clear filters, search, selections
- Escape from long or multi-step processes

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Users get trapped; no way out without refreshing |
| 1 | Difficult exits; must find obscure paths to escape |
| 2 | Some exits; main flows have escape, edge cases don't |
| 3 | Good control; users can exit and undo most actions |
| 4 | Full control; undo, cancel, back, and escape everywhere |

###### 4. Consistency and Standards

Users shouldn't wonder whether different words, situations, or actions mean the same thing.

**Check for**:
- Consistent terminology throughout the interface
- Same actions produce same results everywhere
- Platform conventions followed (standard UI patterns)
- Visual consistency (colors, typography, spacing, components)
- Consistent interaction patterns (same gesture = same behavior)

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Inconsistent everywhere; feels like different products stitched together |
| 1 | Many inconsistencies; similar things look/behave differently |
| 2 | Partially consistent; main flows match, details diverge |
| 3 | Mostly consistent; occasional deviation, nothing confusing |
| 4 | Fully consistent; cohesive system, predictable behavior |

###### 5. Error Prevention

Better than good error messages is a design that prevents problems in the first place.

**Check for**:
- Confirmation before destructive actions (delete, overwrite)
- Constraints preventing invalid input (date pickers, dropdowns)
- Smart defaults that reduce errors
- Clear labels that prevent misunderstanding
- Autosave and draft recovery

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Errors easy to make; no guardrails anywhere |
| 1 | Few safeguards; some inputs validated, most aren't |
| 2 | Partial prevention; common errors caught, edge cases slip |
| 3 | Good prevention; most error paths blocked proactively |
| 4 | Excellent; errors nearly impossible through smart constraints |

###### 6. Recognition Rather Than Recall

Minimize memory load. Make objects, actions, and options visible or easily retrievable.

**Check for**:
- Visible options (not buried in hidden menus)
- Contextual help when needed (tooltips, inline hints)
- Recent items and history
- Autocomplete and suggestions
- Labels on icons (not icon-only navigation)

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Heavy memorization; users must remember paths and commands |
| 1 | Mostly recall; many hidden features, few visible cues |
| 2 | Some aids; main actions visible, secondary features hidden |
| 3 | Good recognition; most things discoverable, few memory demands |
| 4 | Everything discoverable; users never need to memorize |

###### 7. Flexibility and Efficiency of Use

Accelerators, invisible to novices, speed up expert interaction.

**Check for**:
- Keyboard shortcuts for common actions
- Customizable interface elements
- Recent items and favorites
- Bulk/batch actions
- Power user features that don't complicate the basics

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | One rigid path; no shortcuts or alternatives |
| 1 | Limited flexibility; few alternatives to the main path |
| 2 | Some shortcuts; basic keyboard support, limited bulk actions |
| 3 | Good accelerators; keyboard nav, some customization |
| 4 | Highly flexible; multiple paths, power features, customizable |

###### 8. Aesthetic and Minimalist Design

Interfaces should not contain irrelevant or rarely needed information. Every element should serve a purpose.

**Check for**:
- Only necessary information visible at each step
- Clear visual hierarchy directing attention
- Purposeful use of color and emphasis
- No decorative clutter competing for attention
- Focused, uncluttered layouts

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Overwhelming; everything competes for attention equally |
| 1 | Cluttered; too much noise, hard to find what matters |
| 2 | Some clutter; main content clear, periphery noisy |
| 3 | Mostly clean; focused design, minor visual noise |
| 4 | Perfectly minimal; every element earns its pixel |

###### 9. Help Users Recognize, Diagnose, and Recover from Errors

Error messages should use plain language, precisely indicate the problem, and constructively suggest a solution.

**Check for**:
- Plain language error messages (no error codes for users)
- Specific problem identification ("Email is missing @" not "Invalid input")
- Actionable recovery suggestions
- Errors displayed near the source of the problem
- Non-blocking error handling (don't wipe the form)

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | Cryptic errors; codes, jargon, or no message at all |
| 1 | Vague errors; "Something went wrong" with no guidance |
| 2 | Clear but unhelpful; names the problem but not the fix |
| 3 | Clear with suggestions; identifies problem and offers next steps |
| 4 | Perfect recovery; pinpoints issue, suggests fix, preserves user work |

###### 10. Help and Documentation

Even if the system is usable without docs, help should be easy to find, task-focused, and concise.

**Check for**:
- Searchable help or documentation
- Contextual help (tooltips, inline hints, guided tours)
- Task-focused organization (not feature-organized)
- Concise, scannable content
- Easy access without leaving current context

**Scoring**:
| Score | Criteria |
|-------|----------|
| 0 | No help available anywhere |
| 1 | Help exists but hard to find or irrelevant |
| 2 | Basic help; FAQ or docs exist, not contextual |
| 3 | Good documentation; searchable, mostly task-focused |
| 4 | Excellent contextual help; right info at the right moment |

---

###### Score Summary

**Total possible**: 40 points (10 heuristics × 4 max)

| Score Range | Rating | What It Means |
|-------------|--------|---------------|
| 36–40 | Excellent | Minor polish only; ship it |
| 28–35 | Good | Address weak areas, solid foundation |
| 20–27 | Acceptable | Significant improvements needed before users are happy |
| 12–19 | Poor | Major UX overhaul required; core experience broken |
| 0–11 | Critical | Redesign needed; unusable in current state |

When heuristics were scored `n/a`, the maximum is lower than 40; read the band off the percentage instead of the raw number (90%+ Excellent, 70%+ Good, 50%+ Acceptable, 30%+ Poor, below that Critical). 24/32 is 75%, so Good.

---

###### Issue Severity (P0–P3)

Tag each individual issue found during scoring with a priority level:

| Priority | Name | Description | Action |
|----------|------|-------------|--------|
| **P0** | Blocking | Prevents task completion entirely | Fix immediately; this is a showstopper |
| **P1** | Major | Causes significant difficulty or confusion | Fix before release |
| **P2** | Minor | Annoyance, but workaround exists | Fix in next pass |
| **P3** | Polish | Nice-to-fix, no real user impact | Fix if time permits |

**Tip**: If you're unsure between two levels, ask: "Would a user contact support about this?" If yes, it's at least P1.

---

##### Persona-Based Design Testing

Test the interface through the eyes of 5 distinct user archetypes. Each persona exposes different failure modes that a single "design director" perspective would miss.

**How to use**: Select 2–3 personas most relevant to the interface being critiqued. Walk through the primary user action as each persona. Report specific red flags, not generic concerns.

---

###### 1. Impatient Power User: "Alex"

**Profile**: Expert with similar products. Expects efficiency, hates hand-holding. Will find shortcuts or leave.

**Behaviors**:
- Skips all onboarding and instructions
- Looks for keyboard shortcuts immediately
- Tries to bulk-select, batch-edit, and automate
- Gets frustrated by required steps that feel unnecessary
- Abandons if anything feels slow or patronizing

**Test Questions**:
- Can Alex complete the core task in under 60 seconds?
- Are there keyboard shortcuts for common actions?
- Can onboarding be skipped entirely?
- Do modals have keyboard dismiss (Esc)?
- Is there a "power user" path (shortcuts, bulk actions)?

**Red Flags** (report these specifically):
- Forced tutorials or unskippable onboarding
- No keyboard navigation for primary actions
- Slow animations that can't be skipped
- One-item-at-a-time workflows where batch would be natural
- Redundant confirmation steps for low-risk actions

---

###### 2. Confused First-Timer: "Jordan"

**Profile**: Never used this type of product. Needs guidance at every step. Will abandon rather than figure it out.

**Behaviors**:
- Reads all instructions carefully
- Hesitates before clicking anything unfamiliar
- Looks for help or support constantly
- Misunderstands jargon and abbreviations
- Takes the most literal interpretation of any label

**Test Questions**:
- Is the first action obviously clear within 5 seconds?
- Are all icons labeled with text?
- Is there contextual help at decision points?
- Does terminology assume prior knowledge?
- Is there a clear "back" or "undo" at every step?

**Red Flags** (report these specifically):
- Icon-only navigation with no labels
- Technical jargon without explanation
- No visible help option or guidance
- Ambiguous next steps after completing an action
- No confirmation that an action succeeded

---

###### 3. Accessibility-Dependent User: "Sam"

**Profile**: Uses screen reader (VoiceOver/NVDA), keyboard-only navigation. May have low vision, motor impairment, or cognitive differences.

**Behaviors**:
- Tabs through the interface linearly
- Relies on ARIA labels and heading structure
- Cannot see hover states or visual-only indicators
- Needs adequate color contrast (4.5:1 minimum)
- May use browser zoom up to 200%

**Test Questions**:
- Can the entire primary flow be completed keyboard-only?
- Are all interactive elements focusable with visible focus indicators?
- Do images have meaningful alt text?
- Is color contrast WCAG AA compliant (4.5:1 for text)?
- Does the screen reader announce state changes (loading, success, errors)?

**Red Flags** (report these specifically):
- Click-only interactions with no keyboard alternative
- Missing or invisible focus indicators
- Meaning conveyed by color alone (red = error, green = success)
- Unlabeled form fields or buttons
- Time-limited actions without extension option
- Custom components that break screen reader flow

---

###### 4. Deliberate Stress Tester: "Riley"

**Profile**: Methodical user who pushes interfaces beyond the happy path. Tests edge cases, tries unexpected inputs, and probes for gaps in the experience.

**Behaviors**:
- Tests edge cases intentionally (empty states, long strings, special characters)
- Submits forms with unexpected data (emoji, RTL text, very long values)
- Tries to break workflows by navigating backwards, refreshing mid-flow, or opening in multiple tabs
- Looks for inconsistencies between what the UI promises and what actually happens
- Documents problems methodically

**Test Questions**:
- What happens at the edges (0 items, 1000 items, very long text)?
- Do error states recover gracefully or leave the UI in a broken state?
- What happens on refresh mid-workflow? Is state preserved?
- Are there features that appear to work but produce broken results?
- How does the UI handle unexpected input (emoji, special chars, paste from Excel)?

**Red Flags** (report these specifically):
- Features that appear to work but silently fail or produce wrong results
- Error handling that exposes technical details or leaves UI in a broken state
- Empty states that show nothing useful ("No results" with no guidance)
- Workflows that lose user data on refresh or navigation
- Inconsistent behavior between similar interactions in different parts of the UI

---

###### 5. Distracted Mobile User: "Casey"

**Profile**: Using phone one-handed on the go. Frequently interrupted. Possibly on a slow connection.

**Behaviors**:
- Uses thumb only; prefers bottom-of-screen actions
- Gets interrupted mid-flow and returns later
- Switches between apps frequently
- Has limited attention span and low patience
- Types as little as possible, prefers taps and selections

**Test Questions**:
- Are primary actions in the thumb zone (bottom half of screen)?
- Is state preserved if the user leaves and returns?
- Does it work on slow connections (3G)?
- Can forms use autocomplete and smart defaults?
- Are touch targets at least 44×44pt?

**Red Flags** (report these specifically):
- Important actions positioned at the top of the screen (unreachable by thumb)
- No state persistence; progress lost on tab switch or interruption
- Large text inputs required where selection would work
- Heavy assets loading on every page (no lazy loading)
- Tiny tap targets or targets too close together

---

###### Selecting Personas

Choose personas based on the interface type:

| Interface Type | Primary Personas | Why |
|---------------|-----------------|-----|
| Landing page / marketing | Jordan, Riley, Casey | First impressions, trust, mobile |
| Dashboard / admin | Alex, Sam | Power users, accessibility |
| E-commerce / checkout | Casey, Riley, Jordan | Mobile, edge cases, clarity |
| Onboarding flow | Jordan, Casey | Confusion, interruption |
| Data-heavy / analytics | Alex, Sam | Efficiency, keyboard nav |
| Form-heavy / wizard | Jordan, Sam, Casey | Clarity, accessibility, mobile |

---

###### Project-Specific Personas

If `CLAUDE.md` contains a `## Design Context` section (generated by `impeccable init`), derive 1–2 additional personas from the audience and brand information:

1. Read the target audience description
2. Identify the primary user archetype not covered by the 5 predefined personas
3. Create a persona following this template:

```
##### [Role]: "[Name]"

**Profile**: [2-3 key characteristics derived from Design Context]

**Behaviors**: [3-4 specific behaviors based on the described audience]

**Red Flags**: [3-4 things that would alienate this specific user type]
```

Only generate project-specific personas when real Design Context data is available. Don't invent audience details; use the 5 predefined personas when no context exists.

---

## reference/delight.md

> **Additional context needed**: the brand's emotional range.

Make the experience memorable at moments that earn it. Delight is not a layer of generic whimsy; it is product character revealed through a useful interaction, a humane response, or an unexpectedly considered detail.

---

#### Visitor mode

- **Persuade + Experience:** personality may run through voice, composition, motion, and discovery, provided the artifact remains the focus.
- **Operate + Read:** concentrate delight at meaningful moments such as first use, completion, recovery, or mastery. Reliability carries everything else.

#### Find the opportunity

Inspect the target, DESIGN.md, product voice, repeated-use frequency, and emotional context. Look for:

- effort worth acknowledging;
- waiting that can become informative;
- an empty or first-use state that can orient;
- an error or recovery moment that needs empathy;
- an interaction whose physical or verbal response could express the brand;
- a useful capability people might enjoy discovering.

Do not manufacture a celebration for an ordinary click. Ask only when the brand's emotional range or the stakes cannot be inferred.

#### Define one delight thesis

State in one sentence what the user should feel and why that feeling belongs to this product. Then choose the smallest system that can deliver it:

- a distinctive response to a meaningful action;
- product-specific language that clarifies while carrying voice;
- an interaction or transition with a recognizable material behavior;
- an illustration, sound, haptic, or environmental detail grounded in the product world;
- a discovery reward that reveals real utility.

Derive the treatment from product mechanism and visual world, not a stock catalog.

#### Build for the emotional moment

- **Success:** match the response to the effort and consequence. Major milestones can expand; routine saves should simply feel certain.
- **Waiting:** show truthful progress, useful context, or product-specific activity. Never fake work or delay completion to stage a flourish.
- **Empty and first use:** make the next action clear before adding personality.
- **Error and recovery:** lead with the problem and recovery. Warmth may reduce stress; jokes must not trivialize loss, money, privacy, or blocked work.
- **Repeated interaction:** keep the response satisfying after the hundredth use. Variation is useful only when it remains coherent and predictable enough to trust.
- **Discovery:** reward curiosity without hiding required functionality.

Copy must use the product's language. Generic whimsy is worse than neutral clarity.

#### Protect the experience

Delight must not:

- delay, block, or obscure the primary task;
- override platform conventions or accessibility;
- add unrequested factual claims;
- play sound without consent or ignore mute settings;
- become mandatory, unskippable, or exhausting on repeat;
- add a dependency or asset cost disproportionate to the moment.

For authored motion, load [animate.md](#referenceanimatemd). Respect screen readers, keyboard use, touch, localization, and cultural context. Nonessential loops stop when hidden. Make celebration intensity proportional to frequency and consequence.

#### Verify

- The moment is specific enough that a neighboring product could not use it unchanged.
- It improves comprehension, confidence, motivation, or emotional recovery.
- The interface remains fast and obvious without the flourish.
- Repetition does not turn charm into friction.
- Muted, keyboard, touch, and localized paths work.
- The result feels like the selected world, not a generic “delight” treatment.

When the personality feels earned, hand off to `/impeccable polish` for the final pass.

---

## reference/distill.md

Strip a design to its essence. Remove anything that doesn't earn its place: redundant elements, repeated information, decorative noise, cosmetic complexity.


---

#### Assess Current State

Analyze what makes the design feel complex or cluttered:

1. **Identify complexity sources**:
   - **Too many elements**: Competing buttons, redundant information, visual clutter
   - **Excessive variation**: Too many colors, fonts, sizes, styles without purpose
   - **Information overload**: Everything visible at once, no progressive disclosure
   - **Visual noise**: Unnecessary borders, shadows, backgrounds, decorations
   - **Confusing hierarchy**: Unclear what matters most
   - **Feature creep**: Too many options, actions, or paths forward

2. **Find the essence**:
   - What's the primary user goal? (There should be ONE)
   - What's actually necessary vs nice-to-have?
   - What can be removed, hidden, or combined?
   - What's the 20% that delivers 80% of value?

If any of these are unclear from the codebase, do not guess. Ask with the AskUserQuestion tool and wait for the answer before continuing.

Simplicity is not about removing features. It's about removing obstacles between users and their goals. Every element should justify its existence.

#### Plan Simplification

Create a ruthless editing strategy:

- **Core purpose**: What's the ONE thing this should accomplish?
- **Essential elements**: What's truly necessary to achieve that purpose?
- **Progressive disclosure**: What can be hidden until needed?
- **Consolidation opportunities**: What can be combined or integrated?

Expect to say no to good ideas to make room for great execution.

#### Simplify the Design

Systematically remove complexity across these dimensions:

##### Information Architecture
- **Reduce scope**: Remove secondary actions, optional features, redundant information
- **Progressive disclosure**: Hide complexity behind clear entry points (accordions, modals, step-through flows)
- **Combine related actions**: Merge similar buttons, consolidate forms, group related content
- **Clear hierarchy**: ONE primary action, few secondary actions, everything else tertiary or hidden
- **Remove redundancy**: If it's said elsewhere, don't repeat it here

##### Visual Simplification
- **Reduce color palette**: Use 1-2 colors plus neutrals, not 5-7 colors
- **Limit typography**: One font family, 3-4 sizes maximum, 2-3 weights
- **Remove decorations**: Eliminate borders, shadows, backgrounds that don't serve hierarchy or function
- **Flatten structure**: Reduce nesting, remove unnecessary containers; never nest cards inside cards
- **Remove unnecessary cards**: Cards aren't needed for basic layout; use spacing and alignment instead
- **Consistent spacing**: Use one spacing scale, remove arbitrary gaps

##### Layout Simplification
- **Linear flow**: Replace complex grids with simple vertical flow where possible
- **Remove sidebars**: Move secondary content inline or hide it
- **Full-width**: Use available space generously instead of complex multi-column layouts
- **Consistent alignment**: Pick left or center, stick with it
- **Generous white space**: Let content breathe, don't pack everything tight

##### Interaction Simplification
- **Reduce choices**: Fewer buttons, fewer options, clearer path forward (paradox of choice is real)
- **Smart defaults**: Make common choices automatic, only ask when necessary
- **Inline actions**: Replace modal flows with inline editing where possible
- **Remove steps**: Can the flow lose a step?
- **Clear next action**: ONE obvious next action, not five competing ones

##### Content Simplification
- **Shorter copy**: Cut every sentence in half, then do it again
- **Active voice**: "Save changes" not "Changes will be saved"
- **Remove jargon**: Plain language always wins
- **Scannable structure**: Short paragraphs, bullet points, clear headings
- **Essential information only**: Remove marketing fluff, legalese, hedging
- **Remove redundant copy**: No headers restating intros, no repeated explanations, say it once

##### Code Simplification
- **Remove unused code**: Dead CSS, unused components, orphaned files
- **Flatten component trees**: Reduce nesting depth
- **Consolidate styles**: Merge similar styles, use utilities consistently
- **Reduce variants**: Does that component need 12 variations, or can 3 cover 90% of cases?

**Avoid**:
- Remove necessary functionality (simplicity ≠ feature-less)
- Sacrifice accessibility for simplicity (clear labels and ARIA still required)
- Make things so simple they're unclear (mystery ≠ minimalism)
- Remove information users need to make decisions
- Eliminate hierarchy completely (some things should stand out)
- Oversimplify complex domains (match complexity to actual task complexity)

#### Verify Simplification

Ensure simplification improves usability:

- **Faster task completion**: Can users accomplish goals more quickly?
- **Reduced cognitive load**: Is it easier to understand what to do?
- **Still complete**: Are all necessary features still accessible?
- **Clearer hierarchy**: Is it obvious what matters most?
- **Better performance**: Does simpler design load faster?

#### Document Removed Complexity

If you removed features or options:
- Document why they were removed
- Consider if they need alternative access points
- Note any user feedback to monitor

When the cuts feel right, hand off to `/impeccable polish` for the final pass. As Antoine de Saint-Exupéry put it: "Perfection is achieved not when there is nothing more to add, but when there is nothing left to take away."

---

## reference/doctor.md

Report and repair drift between this project's Impeccable artifacts and what the installed version reads: PRODUCT.md, DESIGN.md and its `.impeccable/design.json` sidecar, `.impeccable/config.json`, persisted surface briefs, and the design hook.

This is maintenance, not design. Do not redesign anything, do not open files outside the ones the report names, and do not run any other command as a side effect.

#### What this owns, and what it does not

Three kinds of drift travel under "out of date". Keep them apart:

- **Tool version.** The installed skill is older than the published one. `impeccable context` reports that at boot as `UPDATE_AVAILABLE` and `npx impeccable update` fixes it. Not this command's job.
- **Schema drift.** An artifact was written by an older Impeccable: fields nothing reads, fields now expected, files in retired locations. Mechanical, and this command repairs most of it.
- **Truth drift.** The code moved on and the document no longer describes it. No file comparison settles this. `document` owns DESIGN.md, `init` owns PRODUCT.md, and this command's job is to hand them a specific gap rather than a vague suspicion.

#### Step 1: Run the pass

```
"<skill-base-dir>/scripts/impeccable" doctor --json
```

Add `--target <path>` when the user named a workspace, file, or route in a monorepo. Without it the report describes the repo root, and in a monorepo that is often the wrong project.

The output carries `findings` (each with `id`, `artifact`, `path`, `severity`, `summary`, `fix`) and, in a monorepo, `workspaces` with each app's product and design resolution. `ruleRegistryAvailable: false` means ignored rule ids could not be validated; say so rather than implying that list is clean.

An empty `findings` array is the good outcome. Say so in one line and stop.

#### Step 2: Act by severity

The severity says what should happen, not how bad it is.

- **`auto`** carries no decision. Run `"<skill-base-dir>/scripts/impeccable" doctor --fix` once to apply these, then report what it moved in one line. Do not ask permission first, and do not ask about them afterward.
- **`mention`** needs the user to know but not to decide anything now. State each one in a sentence with its offered fix.
- **`route`** needs a specific command. Name the command and the gap it would close. Run it only if the user asks in this turn; `init` and `document` are conversations, not repairs you perform unattended.

Report all three groups in one pass. Findings are not errors and the command does not fail on them.

#### Step 3: Deprecated fields are binding

A finding that reports a deprecated field (`## Register` is the current one) is not a style note. Treat that field as absent for every decision from here on, whatever value it holds, and offer to delete the section. Preserving it "just in case" is how a retired axis keeps steering current output.

#### Step 4: Do not overclaim on truth drift

`design-md-drift` counts commits to the visual source directories since DESIGN.md was last edited. A commit count is not a contradiction. Report the number, say what it measures, and if the user wants to know whether the document is actually wrong, read DESIGN.md against the current tokens and components and answer from that. Never assert that DESIGN.md is stale because the number is large.

The same restraint applies to `workspace-context-inherited`. Inheritance is a designed behavior. Whether one product record truthfully describes several apps is a question for the user, not a defect to fix.

#### Monorepo notes

- `workspace-platform-native-evidence` is the finding that matters most here: a workspace carrying native build files while inheriting a root record that resolves to web gets web guidance for its whole life and never loads [ios.md](#referenceiosmd) or [android.md](#referenceandroidmd). The repair is a child PRODUCT.md in that workspace, because one inherited record cannot hold two platforms.
- `config-project-roots-match-nothing` means every `projectRoots` glob missed, so the repo root is silently standing in as the active project. A renamed workspace directory is the usual cause. Report the patterns and ask which directories they should name.
- `config-invalid-build-path` and `config-build-path-unset` both concern one key, `buildPath` in `.impeccable/config.json` (or the gitignored `.impeccable/config.local.json`, which wins for that developer). It holds `comp` or `code` and sets whether new Persuade and Experience surfaces are built from a generated comp or straight in code; Operate and Read surfaces are code-led whatever it holds. An unread value does not fall back to the opposite path, so a project meaning `code` has been building comp-led; report the exact value. The unset finding fires only where a project has done direction work and never recorded a preference, and the offer belongs in it only when image generation exists in your tool surface. Without image generation there is nothing to choose and nothing to say.
- Use the `workspaces` table to show the user which apps carry their own context, which inherit, and which have none, before proposing any change.

#### Opting out of the boot check

`impeccable context` reports the cheap subset of these findings at session start, throttled to once a week per project. Set `"stalenessCheck": false` in `.impeccable/config.json` to silence that, or `IMPECCABLE_NO_STALENESS_CHECK=1` for one session. This command still works with the check disabled, and that is the combination to suggest for a user who wants the report only when they ask for it.

---

## reference/document.md

Generate a `DESIGN.md` file at the project root that captures the current visual design system, so AI agents generating new screens stay on-brand.

DESIGN.md follows the [official DESIGN.md format spec](https://raw.githubusercontent.com/google-labs-code/design.md/main/docs/spec.md): optional YAML frontmatter carrying machine-readable design tokens, followed by up to eight markdown sections in a fixed order. **Tokens are normative; prose provides context for how to apply them.** Sections may be omitted when not relevant, but those present stay in the specified order. Use the canonical headings below so the file remains portable across DESIGN.md-aware tools.

#### The frontmatter: token schema

The YAML frontmatter is the machine-readable layer. It's what Stitch's linter validates and what the live panel renders tiles from. Keep it tight; every entry should correspond to a token the project actually uses.

```yaml
---
name: <project title>
description: <one-line tagline>
colors:
  primary: "#b8422e"
  neutral-bg: "#faf7f2"
  # ...one entry per extracted color; key = descriptive slug
typography:
  display:
    fontFamily: "Cormorant Garamond, Georgia, serif"
    fontSize: "clamp(2.5rem, 7vw, 4.5rem)"
    fontWeight: 300
    lineHeight: 1
    letterSpacing: "normal"
  body:
    # ...
rounded:
  sm: "4px"
  md: "8px"
spacing:
  sm: "8px"
  md: "16px"
components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.neutral-bg}"
    rounded: "{rounded.sm}"
    padding: "16px 48px"
  button-primary-hover:
    backgroundColor: "{colors.primary-deep}"
---
```

Rules that matter:

- **Token refs** use `{path.to.token}` (e.g. `{colors.primary}`, `{rounded.md}`). Components may reference primitives; primitives may not reference each other.
- **Colors accept any valid CSS color string.** Hex is the recommended default for portability, but preserve an incumbent `rgb()`, `hsl()`, `oklch()`, wide-gamut, or mixed-color value when it is the project's normative source. Never split the source of truth without explicit reason.
- **Component sub-tokens** are limited to 8 props: `backgroundColor`, `textColor`, `typography`, `rounded`, `padding`, `size`, `height`, `width`. Shadows, motion, focus rings, backdrop-filter: none of those fit. Carry them in the sidecar (Step 4b).
- **Scale keys are open-ended.** Use whatever names the project already uses (`oxblood-deep`, `surface-container-low`). Don't rename to Material defaults.
- **Variants are naming convention, not schema.** `button-primary` / `button-primary-hover` / `button-primary-active` as sibling keys.

#### The markdown body: eight sections (canonical order)

1. `## Overview`
2. `## Colors`
3. `## Typography`
4. `## Layout`
5. `## Elevation & Depth`
6. `## Shapes`
7. `## Components`
8. `## Do's and Don'ts`

Omit irrelevant sections rather than filling them with invented rules. Put responsive layout in Layout, depth in Elevation & Depth, radius and form language in Shapes, and per-component behavior in Components. Unknown sections are preserved by the format, but new visual guidance should use the canonical structure whenever it fits.

#### When to run

- New-work found a coherent incumbent visual system but no `DESIGN.md`.
- The first implementation of a new world is complete and its provisional decisions need to be carbonized.
- An existing `DESIGN.md` is stale (the design has drifted).
- Before a large redesign, to capture the current state as a reference.

If a `DESIGN.md` already exists, **do not silently overwrite it**. Show the user the existing file first. Ask with the AskUserQuestion tool and wait for the answer before continuing. The choice is refresh, overwrite, or merge.

#### Two paths

- **Scan mode** (default): the project has design tokens, components, or rendered output. Extract, then confirm descriptive language. Use when there's code to analyze.
- **Seed mode**: the project is pre-implementation. Ensure PRODUCT.md exists, then reuse new-work's visual-world workshop and write its directional DESIGN.md seed. Re-run in scan mode once there's code.

Decide by scanning first (Scan mode Step 1). If the scan finds no tokens, no component files, and no rendered site, offer seed mode; don't silently switch. `/impeccable document --seed` requests new-work's world workshop, but it does not authorize replacing coherent code: when an incumbent system exists, offer scan mode or route an explicit identity-replacement request through new-work.

#### Scan mode (approach C: auto-extract, then confirm descriptive language)

##### Step 1: Find the design assets

Search the codebase in priority order:

1. **CSS custom properties**: grep for `--color-`, `--font-`, `--spacing-`, `--radius-`, `--shadow-`, `--ease-`, `--duration-` declarations in CSS files (usually `src/styles/`, `public/css/`, `app/globals.css`, etc.). Record name, value, and the file it's defined in.
2. **Tailwind config**: if `tailwind.config.{js,ts,mjs}` exists, read the `theme.extend` block for colors, fontFamily, spacing, borderRadius, boxShadow.
3. **CSS-in-JS theme files**: styled-components, emotion, vanilla-extract, stitches; look for `theme.ts`, `tokens.ts`, or equivalent.
4. **Design token files**: `tokens.json`, `design-tokens.json`, Style Dictionary output, W3C token community group format.
5. **Component library**: scan the main button, card, input, navigation, dialog components. Note their variant APIs and default styles.
6. **Global stylesheet**: the root CSS file usually has the base typography and color assignments.
7. **Visible rendered output**: if browser automation tools are available, load the live site and sample computed styles from key elements (body, h1, a, button, .card). This catches values that tokens miss.

##### Step 2: Auto-extract what can be auto-extracted

Build a structured draft from the discovered tokens. For each token class:

- **Colors**: Group into Primary / Secondary / Tertiary / Neutral (the Material-derived roles Stitch uses). If the project only has one accent, express it as Primary + Neutral; omit Secondary and Tertiary rather than inventing them.
- **Typography**: Map observed sizes and weights to the Material hierarchy (display / headline / title / body / label). Note font-family stacks and the scale ratio.
- **Elevation**: Catalogue the shadow vocabulary. If the project is flat and uses tonal layering instead, that's a valid answer; state it explicitly.
- **Components**: For each common component (button, card, input, chip, list item, tooltip, nav), extract shape (radius), color assignment, hover/focus treatment, internal padding.
- **Layout + spacing**: Extract grid, container, breakpoint, rhythm, and density behavior into Layout.
- **Shapes**: Extract radius, corner, border, clipping, and recurring form behavior into Shapes.

##### Step 2b: Stage the frontmatter

From the auto-extracted tokens, draft the YAML frontmatter now (you'll write it at the top of DESIGN.md in Step 4). This is the machine-readable layer: what the live panel and Stitch's linter consume.

- **Colors**: one entry per extracted color. Key = descriptive slug (`oxblood-deep`, `editorial-magenta`, not `blue-800`). Value = whichever format the project treats as canonical (OKLCH or hex; see the frontmatter rules above). Don't split the source of truth: one format in the frontmatter, don't redefine the same token in prose with a different value.
- **Typography**: one entry per role (`display`, `headline`, `title`, `body`, `label`). Typography is an object; include only the props that are real for the project (`fontFamily`, `fontSize`, `fontWeight`, `lineHeight`, `letterSpacing`, `fontFeature`, `fontVariation`).
- **Rounded / Spacing**: whatever scale steps the project actually uses, keyed by whatever scale name the project uses (`sm` / `md` / `lg`, or `surface-sm`, or numeric steps).
- **Components**: one entry per variant (`button-primary`, `button-primary-hover`, `button-ghost`). Reference primitives via `{colors.X}`, `{rounded.Y}`. If a variant needs a property Stitch's 8-prop set doesn't cover (shadow, focus ring, backdrop-filter), carry the full snippet in the sidecar instead.

Skip anything the project doesn't have. Empty scale keys or fabricated tokens pollute the spec.

##### Step 3: Ask the user for qualitative language

The following require creative input that cannot be auto-extracted. Ask them in two structured rounds of no more than three questions each (or the harness's lower limit), waiting between rounds:

- **Creative North Star**: a single named metaphor for the whole system ("The Editorial Sanctuary", "The Golden State Curator", "The Lab Notebook"). Offer 2-3 options that honor PRODUCT.md's brand personality.
- **Overview voice**: mood adjectives, aesthetic philosophy in 2-3 sentences, and any confirmed visual anti-reference.
- **Color character** (for auto-extracted colors): descriptive names ("Deep Muted Teal-Navy", not "blue-800"). Suggest 2-3 options per key color based on hue/saturation.
- **Elevation philosophy**: flat/layered/lifted. If shadows exist, is their role ambient or structural?
- **Component philosophy**: the feel of buttons, cards, inputs in one phrase ("tactile and confident" vs. "refined and restrained").

Carry a line from PRODUCT.md only when it is a durable brand commitment that actually constrains the visual system. Page strategy and surface concepts do not belong here.

##### Step 4: Write DESIGN.md

The file opens with the YAML frontmatter staged in Step 2b (schema documented at the top of this reference), then the markdown body using the canonical structure below.

```markdown
---
name: [Project Title]
description: [one-line tagline]
colors:
  # ... staged frontmatter from Step 2b
---

# Design System: [Project Title]

## Overview

**Creative North Star: "[Named metaphor in quotes]"**

[2-3 paragraph holistic description: personality, density, and aesthetic philosophy. Start from the North Star and work outward. State only confirmed visual rejections. End with a short **Key Characteristics:** bullet list.]

## Colors

[Describe the palette character in one sentence.]

### Primary
- **[Descriptive Name]** (#HEX / oklch(...)): [Where and why this color is used. Be specific about context, not just role.]

### Secondary (optional; omit if the project has only one accent)
- **[Descriptive Name]** (#HEX): [Role.]

### Tertiary (optional)
- **[Descriptive Name]** (#HEX): [Role.]

### Neutral
- **[Descriptive Name]** (#HEX): [Text / background / border / divider role.]
- [...]

### Named Rules (optional, powerful)
**The [Rule Name] Rule.** [Short, forceful prohibition or doctrine, e.g. "The One Voice Rule. The primary accent is used on ≤10% of any given screen. Its rarity is the point."]

## Typography

**Display Font:** [Family] (with [fallback])
**Body Font:** [Family] (with [fallback])
**Label/Mono Font:** [Family, if distinct]

**Character:** [1-2 sentence personality description of the pairing.]

### Hierarchy
- **Display** ([weight], [size/clamp], [line-height]): [Purpose; where it appears.]
- **Headline** ([weight], [size], [line-height]): [Purpose.]
- **Title** ([weight], [size], [line-height]): [Purpose.]
- **Body** ([weight], [size], [line-height]): [Purpose. Include max line length like 65–75ch if relevant.]
- **Label** ([weight], [size], [letter-spacing], [case if uppercase]): [Purpose.]

### Named Rules (optional)
**The [Rule Name] Rule.** [Short doctrine about type use.]

## Layout

[Describe the grid or spatial model, container behavior, density, responsive changes, and the spacing rhythm. Include exact values only when observed.]

## Elevation & Depth

[One paragraph: does this system use shadows, tonal layering, or a hybrid? If "no shadows", say so explicitly and describe how depth is conveyed instead.]

### Shadow Vocabulary (if applicable)
- **[Role name]** (`box-shadow: [exact value]`): [When to use it.]
- [...]

### Named Rules (optional)
**The [Rule Name] Rule.** [e.g. "The Flat-By-Default Rule. Surfaces are flat at rest. Shadows appear only as a response to state (hover, elevation, focus)."]

## Shapes

[Describe the form language: corner/radius strategy, borders, clipping, and any recurring silhouette or geometry.]

## Components

For each component, lead with a short character line, then specify shape, color assignment, states, and any distinctive behavior.

### Buttons
- **Shape:** [radius described, exact value in parens]
- **Primary:** [color assignment + padding, in semantic + exact terms]
- **Hover / Focus:** [transitions, treatments]
- **Secondary / Ghost / Tertiary (if applicable):** [brief description]

### Chips (if used)
- **Style:** [background, text color, border treatment]
- **State:** [selected / unselected, filter / action variants]

### Cards / Containers
- **Corner Style:** [radius]
- **Background:** [colors used]
- **Shadow Strategy:** [reference Elevation section]
- **Border:** [if any]
- **Internal Padding:** [scale]

### Inputs / Fields
- **Style:** [stroke, background, radius]
- **Focus:** [treatment, e.g. glow, border shift, etc.]
- **Error / Disabled:** [if applicable]

### Navigation
- **Style, typography, default/hover/active states, mobile treatment.**

### [Signature Component] (optional; if the project has a distinctive custom component worth documenting)
[Description.]

## Do's and Don'ts

Concrete visual guardrails grounded in the incumbent implementation or the user's chosen world. Lead each with "Do" or "Don't" and include exact values only when established. Do not turn a task-specific concept or surface strategy into a system-wide prohibition.

### Do:
- **Do** [specific prescription with exact values / named rule].
- **Do** [...]

### Don't:
- **Don't** [specific prohibition confirmed by the incumbent system or the user].
- **Don't** [...]
- **Don't** [...]
```

##### Step 4b: Write .impeccable/design.json sidecar (extensions only)

The frontmatter owns token primitives (colors, typography, rounded, spacing, components). The sidecar at `.impeccable/design.json` carries **what Stitch's schema can't hold**: tonal ramps per color, shadow/elevation tokens, motion tokens, breakpoints, full component HTML/CSS snippets (the panel renders these into a shadow DOM), and narrative (north star, rules, do's/don'ts). It extends the frontmatter, it doesn't duplicate it.

Regenerate the sidecar whenever you regenerate root `DESIGN.md`. If the user only asks to refresh the sidecar (e.g., from the live panel's stale-hint), preserve `DESIGN.md` and write only `.impeccable/design.json`.

###### Schema

```json
{
  "schemaVersion": 2,
  "generatedAt": "ISO-8601 string",
  "title": "Design System: [Project Title]",
  "extensions": {
    "colorMeta": {
      "primary":        { "role": "primary",  "displayName": "Editorial Magenta", "canonical": "oklch(60% 0.25 350)", "tonalRamp": ["...", "...", "..."] },
      "cool-paper": { "role": "neutral",  "displayName": "Cool Paper",    "canonical": "oklch(96% 0.005 230)", "tonalRamp": ["...", "...", "..."] }
    },
    "typographyMeta": {
      "display": { "displayName": "Display", "purpose": "Hero headlines only." }
    },
    "shadows": [
      { "name": "ambient-low", "value": "0 4px 24px rgba(0,0,0,0.12)", "purpose": "Diffuse hover glow under accent elements." }
    ],
    "motion": [
      { "name": "ease-standard", "value": "cubic-bezier(0.4, 0, 0.2, 1)", "purpose": "Default easing for state transitions." }
    ],
    "breakpoints": [
      { "name": "sm", "value": "640px" }
    ]
  },
  "components": [
    {
      "name": "Primary Button",
      "kind": "button | input | nav | chip | card | custom",
      "refersTo": "button-primary",
      "description": "One-line what and when.",
      "html": "<button class=\"ds-btn-primary\">SAVE CHANGES</button>",
      "css": ".ds-btn-primary { background: #191c1d; color: #fff; padding: 16px 48px; letter-spacing: 0.05em; text-transform: uppercase; font-weight: 500; border: none; border-radius: 0; transition: background 0.2s, transform 0.2s; } .ds-btn-primary:hover { background: oklch(60% 0.25 350); transform: translateY(-2px); }"
    }
  ],
  "narrative": {
    "northStar": "The Editorial Sanctuary",
    "overview": "2-3 paragraphs of the philosophy, pulled from DESIGN.md Overview section.",
    "keyCharacteristics": ["...", "..."],
    "rules": [{ "name": "The One Voice Rule", "body": "...", "section": "colors|typography|elevation" }],
    "dos":   ["Do use ..."],
    "donts": ["Don't use ..."]
  }
}
```

**What changed from schemaVersion 1.** The old sidecar carried token primitive arrays (`tokens.colors[]`, `tokens.typography[]`, etc.). Those values now live in the frontmatter. The sidecar only carries metadata that can't live in the frontmatter (tonal ramps, canonical OKLCH when the hex is an approximation, display names, role hints), keyed by the frontmatter token name (`colorMeta.<token-name>`, `typographyMeta.<token-name>`). Components still carry full HTML/CSS because Stitch's 8-prop set can't hold them.

###### Component translation rules

The `html` and `css` fields must be **self-contained, drop-in snippets** that render correctly when injected into a shadow DOM. The panel applies them directly: no post-processing, no framework runtime.

1. **Tailwind expansion.** If the source uses Tailwind (className="bg-primary text-white rounded-lg px-6 py-3"), expand every utility to literal CSS properties in the `css` string. Do **not** reference Tailwind classes; do **not** assume a Tailwind CSS bundle is loaded. Each component is self-contained.
2. **Token resolution.** If the project exposes tokens as CSS custom properties on `:root` (e.g. `--color-primary`, `--radius-md`), reference them via `var(--color-primary)`; they inherit through the shadow DOM and stay live-bound. If tokens live only in JS theme objects (styled-components, CSS-in-JS), resolve to literal values at generation time.
3. **Icons.** Inline as SVG. Do not reference Lucide/Heroicons packages, icon fonts, or `<img src="...">`. A typical icon is 16-24px; copy the SVG path data directly.
4. **States.** Include `:hover`, `:focus-visible`, and (if meaningful) `:active` rules inline. A static default-only snapshot makes the panel feel dead. Hover + focus rules in the CSS make it feel alive.
5. **Reset bloat.** Extract only the component's *distinctive* CSS (background, color, padding, border-radius, typography, transition). Skip universal resets (`box-sizing: border-box`, `line-height: inherit`, `-webkit-font-smoothing`). The panel already has a neutral canvas; don't re-ship resets.
6. **Scoped class names.** Prefix every class with `ds-` (e.g. `ds-btn-primary`, `ds-input-search`) so component CSS doesn't collide with other components' CSS in the same shadow DOM.

###### What to include

Aim for a tight set of **5-10 components** that best represent the visual system:

- **Canonical primitives (always include if the project has them):** button (each variant as a separate component entry), input/text field, navigation, chip/tag, card.
- **Signature components (include if distinctive):** the recurring custom patterns that actually define the implemented system.
- **Skip the rest.** Utility components, form building blocks, wrapper layouts: not worth documenting unless visually distinctive.

If the project has **no component library yet** (bare landing page, new project), synthesize canonical primitives from the tokens using best-practice defaults consistent with the DESIGN.md's rules. Every `.impeccable/design.json` has *something* to render, even on day zero.

###### Tonal ramps

For each color token, generate an 8-step `tonalRamp` array: dark to light, same hue and chroma, stepped lightness from ~15% to ~95%. The panel renders this as a strip under the swatch. If the project already defines a tonal scale (Material `surface-container-low` family, Tailwind-style `blue-50..blue-900`), use those values. Otherwise synthesize in OKLCH.

###### Narrative mapping

Pull directly from the DESIGN.md you just wrote:

- `narrative.northStar` → the `**Creative North Star: "..."**` line from Overview
- `narrative.overview` → the philosophy paragraphs from Overview
- `narrative.keyCharacteristics` → the bulleted `**Key Characteristics:**` list
- `narrative.rules` → every `**The [Name] Rule.** [body]` across all sections, tagged with `section`
- `narrative.dos` / `narrative.donts` → the bullet lists from Do's and Don'ts verbatim

Do not reword. The panel shows these as secondary collapsible context; the same voice that's in the Markdown carries through.

##### Step 5: Confirm and refine

1. Show the user the full DESIGN.md you wrote. Briefly highlight the non-obvious creative choices (descriptive color names, atmosphere language, named rules).
2. Mention that `.impeccable/design.json` was also written alongside; the live panel will now render this project's actual button/input/nav primitives instead of generic approximations.
3. Offer to refine any section: "Want me to revise a section, add component patterns I missed, or adjust the atmosphere language?"

Your own write is the freshest source; subsequent commands in this session don't need a reload.

#### Seed mode

For projects with no visual system to extract yet. Produces a user-chosen visual-world scaffold, not a fabricated token spec.

##### Step 1: Route through new-work's workshop

PRODUCT.md is the prerequisite. If it is missing, load [init.md](#referenceinitmd) and complete its product interview first. Do not create a visual identity without durable product context.

If PRODUCT.md exists, load [new-work.md](../impeccable-2/SKILL.md#referencenew-workmd) and resolve visual authority. Seed mode requires a concrete first surface: use the target the user named, or ask what they want to make first. Run new-work's **Create or replace the visual world** flow, then **Commit the world**, so the visual world and its first expression are chosen together. Stop after the directional DESIGN.md seed and surface brief; do not implement. A structured simulated user counts as the user and must get the same choice.

If new-work already completed the workshop in this session, use its chosen direction directly. Do not ask again.

##### Step 2: Write seed DESIGN.md

Use the canonical section order from Scan mode. Populate the selected workshop direction and leave unresolved implementation facts as honest placeholders. The seed commits a world and its invariants; it does not pretend implementation tokens already exist.

Lead the file with:

```markdown
<!-- SEED: established with the user before implementation; re-run /impeccable document once there's code to capture the actual tokens and components. -->
```

Per-section guidance in seed mode:

- **Overview**: the chosen design thesis, layout behavior, material character, imagery stance, motion grammar, and reusable signature. Keep the selected first-surface expression in its surface brief; do not promote its composition into the global world.
- **Colors**: the selected palette strategy and roles. Include values only when the user, an existing asset, or new-work's exploration established them; otherwise mark them `[to be resolved during implementation]`.
- **Typography**: the selected type character and role relationship. Include font names only when established; otherwise mark the pairing `[to be resolved during implementation]`.
- **Layout**: the selected spatial grammar and responsive behavior, without pretending exact measurements are settled.
- **Elevation & Depth**: the selected material and depth behavior, stated as an invariant rather than inferred from a generic preset.
- **Shapes**: the selected form and corner language.
- **Components**: omit entirely; no components exist yet.
- **Do's and Don'ts**: record the durable guardrails confirmed during the world choice, not task-local refusals.

Seed mode writes a minimal frontmatter with `name` and `description` only; no colors, typography, rounded, spacing, or components yet. Real tokens land on the next Scan-mode run. Skip the `.impeccable/design.json` sidecar in seed mode for the same reason: nothing to render.

##### Step 3: Confirm

1. Show the seed DESIGN.md. Call out that it is a seed (the marker is the literal commitment).
2. Tell the user: "Re-run `/impeccable document` once you have some code. That pass will extract real tokens and generate the sidecar."

Your own write is the freshest source; no reload needed.

#### Style guidelines

- **Frontmatter first, prose second.** Tokens go in the YAML frontmatter; prose contextualizes them. Don't redefine a token value in two places; the frontmatter is normative.
- **Carry only durable product constraints.** A binding logo, identity asset, accessibility need, or brand commitment from PRODUCT.md may constrain DESIGN.md. Surface strategy stays in its surface brief.
- **Match the spec.** Use its eight canonical sections in order and omit any that are irrelevant. Put motion guidance with the world or component it affects rather than creating a token group the schema does not support.
- **Descriptive > technical**: "Gently curved edges (8px radius)" > "rounded-lg". Include the technical value in parens, lead with the description.
- **Functional > decorative**: for each token, explain WHERE and WHY it's used, not just WHAT it is.
- **Exact values in parens**: hex codes, px/rem values, font weights; always the number in parens alongside the description.
- **Use Named Rules**: `**The [Name] Rule.** [short doctrine]`. These are memorable, citable, and much stickier for AI consumers than bullet lists. Stitch's own outputs use them heavily ("The No-Line Rule", "The Ghost Border Fallback"). Aim for 1-3 per section.
- **Be decisive where evidence is decisive.** Use hard language for actual invariants and softer language for provisional guidance.
- **Use concrete audit tests only when they are grounded in the observed system or a confirmed user decision.** A one-sentence test beats a paragraph of principle.
- **Reference PRODUCT.md selectively.** Product truth explains why the world fits; it does not supply page composition or a visual don't-list by default.
- **Group colors by role**, not by hex-order or hue-order. Primary / Secondary / Tertiary / Neutral is the spec ordering.

#### Pitfalls

- Don't paste raw CSS class names. Translate to descriptive language.
- Don't extract every token. Stop at what's actually reused; one-offs pollute the system.
- Don't invent components that don't exist. If the project only has buttons and cards, only document those.
- Don't overwrite an existing DESIGN.md without asking.
- Don't duplicate content from PRODUCT.md. DESIGN.md is strictly visual.
- Don't replace canonical sections with near-synonyms. Put layout and responsive behavior in `Layout`; put motion with the affected world or component.
- Don't rename sections even slightly. "Colors" not "Color Palette & Roles". "Typography" not "Typography Rules". Tooling parsing depends on exact headers.
- Don't duplicate token values between frontmatter and prose. If a color is in `colors.primary` as hex, the prose can name it and describe its role but should not reassert a different hex. The frontmatter is normative.
- Don't invent frontmatter token groups outside Stitch's schema (no `motion:`, `breakpoints:`, `shadows:` at the top level). Stitch's Zod schema only accepts `colors`, `typography`, `rounded`, `spacing`, `components`. Anything else belongs in the sidecar's `extensions`.

---

## reference/extract.md

### Extract Flow

Identify reusable patterns, components, and design tokens, then extract and consolidate them into the design system for systematic reuse.

#### Step 1: Discover the Design System

Find the design system, component library, or shared UI directory. Understand its structure: component organization, naming conventions, design token structure, import/export conventions.

If no design system exists, do not create one yet. Ask with the AskUserQuestion tool and wait for the answer before continuing. Understand the preferred location and structure first.

#### Step 2: Identify Patterns

Look for extraction opportunities in the target area:

- **Repeated components**: Similar UI patterns used 3+ times (buttons, cards, inputs)
- **Hard-coded values**: Colors, spacing, typography, shadows that should be tokens
- **Inconsistent variations**: Multiple implementations of the same concept
- **Composition patterns**: Layout or interaction patterns that repeat (form rows, toolbar groups, empty states)
- **Type styles**: Repeated font-size + weight + line-height combinations
- **Animation patterns**: Repeated easing, duration, or keyframe combinations

Assess value: only extract things used 3+ times with the same intent. Premature abstraction is worse than duplication.

#### Step 3: Plan Extraction

Create a systematic plan:

- **Components to extract**: Which UI elements become reusable components?
- **Tokens to create**: Which hard-coded values become design tokens?
- **Variants to support**: What variations does each component need?
- **Naming conventions**: Component names, token names, prop names that match existing patterns
- **Migration path**: How to refactor existing uses to consume the new shared versions

Design systems grow incrementally. Extract what is clearly reusable now, not everything that might someday be reusable.

#### Step 4: Extract & Enrich

Build improved, reusable versions:

- **Components**: Clear props API with sensible defaults, proper variants for different use cases, accessibility built in (ARIA, keyboard navigation, focus management), documentation and usage examples
- **Design tokens**: Clear naming (primitive vs semantic), proper hierarchy and organization, documentation of when to use each token
- **Patterns**: When to use this pattern, code examples, variations and combinations

#### Step 5: Migrate

Replace existing uses with the new shared versions:

- **Find all instances**: Search for the patterns you extracted
- **Replace systematically**: Update each use to consume the shared version
- **Test thoroughly**: Ensure visual and functional parity
- **Delete dead code**: Remove the old implementations

#### Step 6: Document

Update design system documentation:

- Add new components to the component library
- Document token usage and values
- Add examples and guidelines
- Update any Storybook or component catalog

**Avoid**:
- Extract one-off, context-specific implementations without generalization
- Create components so generic they are useless
- Extract without considering existing design system conventions
- Skip proper TypeScript types or prop documentation
- Create tokens for every single value (tokens should have semantic meaning)
- Extract things that differ in intent (two buttons that look similar but serve different purposes should stay separate)

---

## reference/generate.md

> **Additional context needed**: only the target element, when the request does not name one that resolves uniquely on the page.

Generate is the fast lane into live mode: the user names an element, a direction, and a count in one sentence, and within a minute they are cycling through variants in their browser. One command boots the helper, hands the element to the overlay in the page your harness already shows (it scrolls to it, selects it, and fires the same Go a click fires) and returns the generate event; one edit writes the variants; one call replies and waits for the user's choice, which the helper bakes into source itself. This file owns the lane's plumbing; from the event onward the design work is [live.md](../impeccable-2/SKILL.md#referencelivemd)'s, unchanged, so read it in full now if you have not this session.

**Web only.** Live mode's browser overlay has no native equivalent; on `ios` / `android` / `adaptive` projects, decline this command and offer `bolder` or `quieter` on the source instead.

The plumbing is where the lane saves time: one command starts the session around the page your harness already shows, one call replies and waits, and nothing here is a browser you have to babysit. The design work is not where it saves time. Setup runs as for any command (`impeccable context`, this reference, craft-floor.md before the edit), and the variants are planned, written, and accepted exactly the way a live session plans, writes, and accepts them.

Three prohibitions cover the known ways this command goes wrong:

- **Never run init or document, and never ask for PRODUCT.md or DESIGN.md.** When they exist, the start command prints them under `boot` and you use them. When they do not, it says so (`contextMissing`, `contextNote`) and you extract the identity from the event (Step 3). A missing file is never a reason to interview the user inside this command; offer `init` in one line after the session ends.
- **Never hand-write a variants wrapper or invent a session id.** Only the browser mints session ids (8 hex characters, at Go). A missing event is fixed by rerunning Step 2, never with a direct source edit.
- **Do not act on hook findings while live markers are in the file**, and do not restyle variants to appease them; the accept verifies the file once the variant is permanent.

#### Step 1: Parse the request

Three parts, all from the user's sentence:

- **A number in the request**: that is the count. **No number**: 3. The protocol caps count at 8.
- **The direction wording** maps onto the live action vocabulary; never invent a new action value:
  - **bold, bolder, stronger, punchier**: `bolder`
  - **quiet, calmer, softer, toned down**: `quieter`
  - **simpler, minimal, stripped**: `distill`
  - **refined, tightened, polished**: `polish`
  - **font and type words**: `typeset`
  - **color words**: `colorize`
  - **arrangement and spacing words**: `layout`
  - **device and breakpoint words**: `adapt`
  - **motion words**: `animate`
  - **playful words**: `delight`
  - **rule-breaking words**: `overdrive`
  - **Wording that carries intent but no vocabulary word** ("make it feel like a bank", "warmer", "more premium"): `impeccable`, with the user's wording passed as the prompt.
  - **An action fits AND extra intent rides along** ("bolder, but keep it monochrome"): that action, with the rest as the prompt.
  - **The wording names no direction at all** ("better", "improve", "nicer", "different", "fresh", "new", "redesign", "fix", "some options", "ideas", "alternatives", or just "variants" with nothing else): Ask with the AskUserQuestion tool and wait for the answer before continuing. Ask one question, offering the vocabulary: *"Which direction should the variants take? bolder, quieter, simpler (distill), polished, typography (typeset), color (colorize), layout, motion (animate), playful (delight), or rule-breaking (overdrive)."* Map the answer with this list; an answer that is still open ("surprise me", "you pick") is `impeccable` with the user's original wording as the prompt, and Step 2 starts on that answer.
- **The element description** ("the pricing cards", "the hero heading"): Step 2 resolves it to a selector.

Done when you hold an action from the vocabulary (asked for, when the request named no direction), a count from 1 to 8, and the element description.

#### Step 2: Reuse the page, then start

**Reuse** the dev server already running and the tab your harness already shows it in; a second server or a second browser window is the failure this step prevents.

1. **Find the dev server**, cheapest source first, and stop at the first hit: the user's message, a browser tab already on the app (Claude Code: an origin in `tabs_context`), a server your harness started (Claude Code: `preview_list`), a terminal that printed its URL. Its origin is your `--dev-url`. **No hit**: leave `--dev-url` off and run the start command with no wait; the boot probes for a running server and its verdict names the move. `browser_needed` carries the `devUrl` it found: open it as in 2, then rerun with `--dev-url <devUrl> --wait-for-browser 60000`. `no_dev_server` means nothing serves the app: start the dev script the way the verdict says (Claude Code: `preview_start`; Cursor: a background terminal; Codex: an exec you yield from), wait for its URL, then rerun with `--dev-url <url>`.
2. **Open the page that renders the element in your browser, then start.** The route the request names, else the one `--target` serves; `--dev-url` takes only the origin.
   - **Cursor** (`browser_navigate`) and **Claude Code** (`navigate`, which opens the Browser pane when it is closed and takes the `tabId` from `tabs_context` when a tab is already on that origin): open the URL, then run the start command with `--dev-url <url> --wait-for-browser 60000`. The boot injects the overlay and the page reloads into it while the command waits. Your browser tool is the only opener on these harnesses; the engine ignores `--open` there.
   - **No browser tool** (Codex, others): run the start command with `--open --wait-for-browser 120000`; it opens the system browser, and the longer wait covers the user finding the tab. **`browser_open_failed` back**: tell the user the `url` in one line and rerun with `--wait-for-browser 120000`.

```bash
"<skill-base-dir>/scripts/impeccable" live-generate --target src/App.jsx --dev-url http://127.0.0.1:5173/ --selector ".pricing-grid" --action bolder --count 3 --boot --wait-for-browser 60000
```

Run it in the foreground in Cursor and Claude Code (it returns within the wait); on Codex, in an exec you yield from, the way Step 3 runs the poll.

- `--target`: the file that renders the element when the request or the project makes it obvious; skip it otherwise.
- `--dev-url`: the origin from 1; omit it and the boot probes.
- `--selector`: a unique class first, then a landmark tag plus class, an id last (every variant mounts a copy of the element, so an id repeats in the DOM). **The request names a repeated component in plural** ("the pricing cards"): target the container that holds the set, so one scoped stylesheet restyles every instance. One read of the source file that renders the element is allowed when the selector is not obvious; `--dry-run` resolves and reports without starting anything when it is not certain.
- `--boot`: runs the lane's boot (PRODUCT.md and DESIGN.md loaded again for the helper, missing files tolerated, dev URL found, bottom bar hidden for the helper's lifetime) and reuses a helper that is already running. Its result rides along as `boot`.
- Also available: `--prompt`, `--text` (keep only matches whose visible text contains a snippet), `--index` (1-based pick among matches).

Read the output in this order: `boot` (or `boot.contextMissing` with `boot.contextNote`: the page is the source of truth, per the note), then `event`, the generate event for `sessionId`, with the same `_instructions` a user's Go gets. Every verdict carries `_instructions`, and they win over your recollection of this file; the ones whose move is a decision of yours:

- **`ambiguous`**: the candidates are listed; target their common container, or rerun with `--text "<visible text>"` or `--index <n>`.
- **`dev_server_gone`**: the dev server stopped answering while the command waited for the page (on Cursor, a server another chat started dies with that chat). Start it the way the verdict says, then rerun with `--dev-url <url>`.
- **`no_match`**: the tab is on a route that does not render the element (navigate to the right route, rerun), or the selector is wrong (derive a better one from the source, or add `--text`).
- **`config_missing` / `config_invalid`** under `bootError`: follow [live-setup.md](#referencelive-setupmd) first, then rerun.
- **`event: null`** with `ok: true`: the event was slower than the wait; run `"<skill-base-dir>/scripts/impeccable" live-poll` once to collect it, then continue.

Done when the output shows `ok: true`, a `sessionId`, and an `event`, reached with at most one server started and one tab opened by you.

#### Step 3: Generate

The event is a standard `generate` event: the picked element's context, a preflighted scaffold, and `_instructions` naming the action's reference, the planning section, and the exact splice. Handle it exactly per live.md's **Handle generate**, which owns everything from the identity lock to the done reply: read the action's reference and craft-floor.md as it says, plan per section 4 (identity first, then mode, then three different primary axes, then the squint test), declare knobs per section 7, and deliver per section 6 (a complete replacement of the element per variant, the preview CSS plus every variant in one edit at the scaffold's splice). The lane changes nothing about what a variant may be: the moves a live session would make on this element (a promoted tier, a restructured set, a reordered card, a different surface) are open here too. Never screenshot the page; the overlay preview is the review channel until accept.

**Reply and wait in one call**, with the file you wrote:

```bash
"<skill-base-dir>/scripts/impeccable" live-poll --reply EVENT_ID done --file src/App.jsx --then-poll
```

This replies done (the browser mounts the variants) and then blocks until the user's choice arrives, so run it the way your harness runs a long wait: **Claude Code** in the foreground with your tool's longest timeout (600000 ms), so you are paused until the choice arrives; **Codex** in a yielded foreground exec; **Cursor** in a background terminal with notify on `"type":"(accept|discard|variant_mount_failed|exit)"`. Never pass a short `--timeout=`. While it runs there is nothing else to do: never sleep and never poll its output on a timer; a harness that backgrounds it wakes you when it returns. `{"type":"timeout"}` means the user has not chosen yet: run `live-poll` again and keep waiting. If the edit fails after the browser flipped to GENERATING, `--reply EVENT_ID error "Short reason"` (without `--then-poll`) so the bar resets.

Then tell the user, in one line, where their variants are: *"Three [bolder] variants are live on [the pricing cards]: cycle with the floating bar's arrows, adjust the Tune knobs, and Accept the keeper."*

Outside the replace path, read the matching live.md section before acting: `scaffold.previewMode: "svelte-component"` (Svelte previews are edited as components, and their accept is mechanical), `mode: "insert"`, `variant_mount_failed`, `steer`, `manual_edit_apply`, and any `fallback: "agent-driven"` wrap error.

#### Step 4: Accept and close

The call from Step 3 returns the user's choice. **`discard`**: nothing to do. **`accept`**: `_acceptResult.carbonize: true` is the normal case, and the cleanup is live.md's **Required after accept**, unchanged: move the accepted variant's rules into the stylesheet that already owns the element with real selectors, bake the chosen knob values in, unwrap the element and drop every `data-impeccable-*` attribute, delete the inline `<style>` block and both `impeccable-carbonize` markers, then `"<skill-base-dir>/scripts/impeccable" live-complete --id SESSION_ID` and confirm `phase: "completed"`. (`baked: true` appears only when the accept was run with `--bake`; then the helper already made the variant permanent and no `live-complete` is owed.)

Close without being asked, the moment the choice is handled:

```bash
"<skill-base-dir>/scripts/impeccable" live-server stop
```

Stopping removes the injected script and reloads the page once: the user sees the accepted design with no overlay chrome, still served by their dev server. **Never kill or restart the dev server**, including one you started in Step 2.

- **The user asks for more variants before you closed**: skip the close, run Step 2 again for the next element (the helper is reused), and close after the last choice.
- **Interrupted or unsure of the state**: `"<skill-base-dir>/scripts/impeccable" live-status`, then `live-resume`; the journal under `.impeccable/live/sessions/` is canonical.

Done when the helper is stopped and the dev site still answers with the accepted design.

---

## reference/harden.md

Designs that only work with perfect data aren't production-ready. Harden the interface against the inputs, errors, languages, and network conditions that real users will throw at it.

#### Assess Hardening Needs

Identify weaknesses and edge cases:

1. **Test with extreme inputs**:
   - Very long text (names, descriptions, titles)
   - Very short text (empty, single character)
   - Special characters (emoji, RTL text, accents)
   - Large numbers (millions, billions)
   - Many items (1000+ list items, 50+ options)
   - No data (empty states)

2. **Test error scenarios**:
   - Network failures (offline, slow, timeout)
   - API errors (400, 401, 403, 404, 500)
   - Validation errors
   - Permission errors
   - Rate limiting
   - Concurrent operations

3. **Test internationalization**:
   - Long translations (German is often 30% longer than English)
   - RTL languages (Arabic, Hebrew)
   - Character sets (Chinese, Japanese, Korean, emoji)
   - Date/time formats
   - Number formats (1,000 vs 1.000)
   - Currency symbols

Designs that only work with perfect data aren't production-ready.

#### Hardening Dimensions

Systematically improve resilience:

##### Text Overflow & Wrapping

**Long text handling**:
```css
/* Single line with ellipsis */
.truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

/* Multi-line with clamp */
.line-clamp {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* Allow wrapping */
.wrap {
  word-wrap: break-word;
  overflow-wrap: break-word;
  hyphens: auto;
}
```

**Flex/Grid overflow**:
```css
/* Prevent flex items from overflowing */
.flex-item {
  min-width: 0; /* Allow shrinking below content size */
  overflow: hidden;
}

/* Prevent grid items from overflowing */
.grid-item {
  min-width: 0;
  min-height: 0;
}
```

**Responsive text sizing**:
- Use `clamp()` for fluid typography
- Set minimum readable sizes (16px body on mobile, the same floor the typography guidance sets; 14px only for genuinely secondary text. iOS Safari force-zooms focused inputs under 16px, which breaks form layouts)
- Test text scaling (zoom to 200%)
- Ensure containers expand with text

##### Internationalization (i18n)

**Text expansion**:
- Add 30-40% space budget for translations
- Use flexbox/grid that adapts to content
- Test with longest language (usually German)
- Avoid fixed widths on text containers

```jsx
// ❌ Bad: Assumes short English text
<button className="w-24">Submit</button>

// ✅ Good: Adapts to content
<button className="px-4 py-2">Submit</button>
```

**RTL (Right-to-Left) support**:
```css
/* Use logical properties */
margin-inline-start: 1rem; /* Not margin-left */
padding-inline: 1rem; /* Not padding-left/right */
border-inline-end: 1px solid; /* Not border-right */

/* Or use dir attribute */
[dir="rtl"] .arrow { transform: scaleX(-1); }
```

**Arabic-script specifics** (Arabic, Persian, Urdu, Pashto, Kurdish):
- Preserve Zero-Width Non-Joiner (U+200C). Persian and Kurdish use ZWNJ between compound-word parts to break cursive joining while keeping the word together. A filter or sanitizer that strips it changes meaning. Never normalize it away.
- Handle Yeh and Kaf variants. Persian uses ی (U+06CC) and ک (U+06A9), while Arabic uses ي (U+064A) and ك (U+0643). Preserve the original form in storage. For search and validation, treat the corresponding letters as equivalent so that Arabic-keyboard input matches Persian text. Rejecting one variant locks out users whose keyboard sends the other.
- Support locale-aware digits. Persian (`fa-IR`) and Arabic locales use Eastern Arabic-Indic numerals (۰-۹ and ٠-٩). Use `Intl.NumberFormat` with the correct locale rather than hardcoding Western digits.

```javascript
// ✅ Locale-aware digit formatting
new Intl.NumberFormat('fa-IR').format(1234); // ۱٬۲۳۴
new Intl.NumberFormat('ar-SA').format(1234); // ١٬٢٣٤
```

- Respect calendar systems. Persian users expect the Solar Hijri (Jalali) calendar; many Arabic-speaking users expect the Hijri (Islamic) calendar. Use `Intl.DateTimeFormat` with the appropriate locale or calendar parameter.

```javascript
// ✅ Locale-appropriate calendar
new Intl.DateTimeFormat('fa-IR').format(new Date());
new Intl.DateTimeFormat('ar-SA-u-ca-islamic').format(new Date());
```

**Character set support**:
- Use UTF-8 encoding everywhere
- Test with Chinese/Japanese/Korean (CJK) characters
- Test with emoji (they can be 2-4 bytes)
- Handle different scripts (Latin, Cyrillic, Arabic, etc.)

**Date/Time formatting**:
```javascript
// ✅ Use Intl API for proper formatting
new Intl.DateTimeFormat('en-US').format(date); // 1/15/2024
new Intl.DateTimeFormat('de-DE').format(date); // 15.1.2024

new Intl.NumberFormat('en-US', { 
  style: 'currency', 
  currency: 'USD' 
}).format(1234.56); // $1,234.56
```

**Pluralization**:
```javascript
// ❌ Bad: Assumes English pluralization
`${count} item${count !== 1 ? 's' : ''}`

// ✅ Good: Use proper i18n library
t('items', { count }) // Handles complex plural rules
```

##### Error Handling

**Network errors**:
- Show clear error messages
- Provide retry button
- Explain what happened
- Offer offline mode (if applicable)
- Handle timeout scenarios

```jsx
// Error states with recovery
{error && (
  <ErrorMessage>
    <p>Failed to load data. {error.message}</p>
    <button onClick={retry}>Try again</button>
  </ErrorMessage>
)}
```

**Form validation errors**:
- Inline errors near fields
- Clear, specific messages
- Suggest corrections
- Don't block submission unnecessarily
- Preserve user input on error

**API errors**:
- Handle each status code appropriately
  - 400: Show validation errors
  - 401: Redirect to login
  - 403: Show permission error
  - 404: Show not found state
  - 429: Show rate limit message
  - 500: Show generic error, offer support

**Graceful degradation**:
- Core functionality works without JavaScript
- Images have alt text
- Progressive enhancement
- Fallbacks for unsupported features

##### Edge Cases & Boundary Conditions

**Empty states**:
- No items in list
- No search results
- No notifications
- No data to display
- Provide clear next action

**Loading states**:
- Initial load
- Pagination load
- Refresh
- Show what's loading ("Loading your projects...")
- Time estimates for long operations

**Large datasets**:
- Pagination or virtual scrolling
- Search/filter capabilities
- Performance optimization
- Don't load all 10,000 items at once

**Concurrent operations**:
- Prevent double-submission (disable button while loading)
- Handle race conditions
- Optimistic updates with rollback
- Conflict resolution

**Interrupted gestures** (custom sliders, drag surfaces, scrollable control strips):
- A second finger or pointer lands mid-drag: the first drag keeps its pointer or ends cleanly, never jumps to the new one
- The browser cancels the gesture to scroll (`pointercancel`), capture is lost (`lostpointercapture`), the pointer is released outside the control, or the window loses focus (`blur`) mid-drag: clear the dragging state and release capture
- After each of these, the next tap or drag works without a reload

**Permission states**:
- No permission to view
- No permission to edit
- Read-only mode
- Clear explanation of why

**Browser compatibility**:
- Polyfills for modern features
- Fallbacks for unsupported CSS
- Feature detection (not browser detection)
- Test in target browsers

##### Input Validation & Sanitization

**Client-side validation**:
- Required fields
- Format validation (email, phone, URL)
- Length limits
- Pattern matching
- Custom validation rules

**Server-side validation** (always):
- Never trust client-side only
- Validate and sanitize all inputs
- Protect against injection attacks
- Rate limiting

**Constraint handling**:
```html
<!-- Set clear constraints -->
<input 
  type="text"
  maxlength="100"
  pattern="[A-Za-z0-9]+"
  required
  aria-describedby="username-hint"
/>
<small id="username-hint">
  Letters and numbers only, up to 100 characters
</small>
```

##### Accessibility Resilience

**Keyboard navigation**:
- All functionality accessible via keyboard
- Logical tab order
- Focus management in modals
- Skip links for long content

**Screen reader support**:
- Proper ARIA labels
- Announce dynamic changes (live regions)
- Descriptive alt text
- Semantic HTML

**High contrast mode**:
- Test in Windows high contrast mode
- Don't rely only on color
- Provide alternative visual cues

##### Performance Resilience

**Slow connections**:
- Progressive image loading
- Skeleton screens
- Optimistic UI updates
- Offline support (service workers)

**Memory leaks**:
- Clean up event listeners
- Cancel subscriptions
- Clear timers/intervals
- Abort pending requests on unmount

**Throttling & Debouncing**:
```javascript
// Debounce search input
const debouncedSearch = debounce(handleSearch, 300);

// Throttle scroll handler
const throttledScroll = throttle(handleScroll, 100);
```

#### Testing Strategies

**Manual testing**:
- Test with extreme data (very long, very short, empty)
- Test in different languages
- Test offline
- Test slow connection (throttle to 3G)
- Test with screen reader
- Test keyboard-only navigation
- Test on old browsers

**Automated testing**:
- Unit tests for edge cases
- Integration tests for error scenarios
- E2E tests for critical paths
- A behavioral regression for each confirmed gesture fix, when the project's test runner can drive input
- Visual regression tests
- Accessibility tests (axe, WAVE)

**Avoid**:
- Assume perfect input (validate everything)
- Ignore internationalization (design for global)
- Leave error messages generic ("Error occurred")
- Forget offline scenarios
- Trust client-side validation alone
- Use fixed widths for text
- Assume English-length text
- Block entire interface when one component errors

#### Verify Hardening

Test thoroughly with edge cases:

- **Long text**: Try names with 100+ characters
- **Emoji**: Use emoji in all text fields
- **RTL**: Test with Arabic or Hebrew
- **CJK**: Test with Chinese/Japanese/Korean
- **Network issues**: Disable internet, throttle connection
- **Large datasets**: Test with 1000+ items
- **Concurrent actions**: Click submit 10 times rapidly
- **Interrupted gestures**: Add a second finger mid-drag, scroll across the control, release outside it, switch windows mid-drag; then drag again
- **Errors**: Force API errors, test all error states
- **Empty**: Remove all data, test empty states

For gestures, say what produced the evidence (emulated viewport, synthesized touch, which engine, physical device) and name what stayed untested.

When edge cases are covered, hand off to `/impeccable polish` for the final pass.

---

## reference/hooks.md

### /impeccable hooks

Manage the **design detector hook** for the current project.

The hook runs the impeccable design detector on direct file edits to design-relevant files (`.tsx`, `.jsx`, `.html`, `.vue`, `.svelte`, `.astro`, `.css`, `.scss`, `.sass`, `.less`, `.ts`, `.js`). Claude Code, Codex, and GitHub Copilot use a post-tool-use hook and push a short system reminder into the agent's context after the edit; findings get a correction prompt, pending issues get a re-nudge, and clean UI-ish files get a short ack unless quiet mode is on (`hook.quiet` in config). Plain `.ts` and `.js` files are still scanned, but stay quiet unless the detector finds something. Cursor uses `preToolUse` to block bad proposed writes before they land and stays silent when it allows a clean write. Grok Build fires the same PostToolUse scan to mark touched files, then surfaces findings on Stop `additionalContext`. Do not expect a Grok per-edit reminder: Grok discards that stdout.

The detector rules run in two tiers. The per-edit hook surfaces only the immediate tier: mechanical, unambiguous problems worth interrupting an edit for, such as broken images, overflowing content, contrast and legibility failures, gradient text, glow shadows, and design-system drift. Everything else (copy cadence, palette and typography taste, layout rhythm) is deferred to a deep pass on the `Stop` hook event, which runs the full rule set over every UI file touched in the session and surfaces the remaining findings once, deduplicated against what the per-edit pass already reported. A session with nothing left to report stops silently. Set `hook.perEditRules` to `"all"` in `.impeccable/config.json` to restore the full rule set on every edit. The Stop deep pass is wired for Claude Code, Codex, and Grok Build, which dispatch a native `Stop` hook event. Cursor does not get one (its stop hook is not consistently dispatched; the pre-write gate covers it), and GitHub Copilot's stop-style events do not feed context back to the model, so they keep the full detector per edit. Grok also fires an observe-only Stop with `reason: "shutdown"` after `end_turn`; skip that one, scan only `end_turn`.

Every hook is a mechanical pass. The reflexes no scanner catches live in [craft-floor.md](#referencecraft-floormd), which the skill loads before it edits UI, so they apply whether or not a hook is wired. A session with no automatic hook gets one `MANUAL_DETECTOR_REQUIRED` directive from `impeccable context` asking for a single detector run at the end.

This command toggles the hook **per project** by editing `.impeccable/config.json` (the unified Impeccable config; hook runtime settings live under its `hook` key, and shared detector ignores live under `detector`). Per-developer overrides, including the install consent decision (`hook.consent`) the CLI records, live in the gitignored `.impeccable/config.local.json`. Set `hook.enabled: false` to turn the hook off, `hook.quiet: true` to silence the clean/pending acks, or `hook.auditLog` to a file path for an NDJSON log. The legacy `IMPECCABLE_HOOK_DISABLED`, `IMPECCABLE_HOOK_QUIET`, and `IMPECCABLE_HOOK_LOG` env vars are still honored and override these config values when set.

Declare server-side template extensions under **`detector.extensions`** when the project uses Blade, Twig, ERB, or Handlebars files; the hook skips them otherwise because they sit outside the built-in extension list. One entry per extension, `{ "ext": ".blade.php", "engine": "html" }`. `engine` picks the analyzer (`html` for markup templates, `text` for JS/TS/CSS-like files) and defaults to `html`. Match against the end of the filename, so double extensions like `.blade.php` and `.html.erb` work. Config only adds extensions; the built-in list always applies.

Manual `"<skill-base-dir>/scripts/impeccable" detect` scans use the same project filter config by default: `detector.ignoreRules`, `detector.ignoreFiles`, `detector.ignoreValues`, and `detector.designSystem.enabled`. `hook.enabled` only controls automatic hook execution, not manual CLI scans. Use `"<skill-base-dir>/scripts/impeccable" detect --no-config ...` for a raw detector run that ignores project config/context. Use `"<skill-base-dir>/scripts/impeccable" ignores ...` for direct CLI CRUD on the same detector ignores.

Supported harnesses: Claude Code (`.claude/settings.local.json` for a project-scope install; `~/.claude/settings.json` for a user-scope install; a project hook moved into shared `.claude/settings.json` is honored in place too), Codex (`.codex/hooks.json` in the project), Cursor (`.cursor/hooks.json` in the project), Grok Build (`.grok/hooks/impeccable.json` in the project; requires `/hooks-trust` or `--trust`), and GitHub Copilot (`.github/hooks/impeccable.json` in the project, a team-shared committed file that both the Copilot CLI and the cloud agent read). For the Copilot CLI, repo-level hooks fire once `.github/hooks/impeccable.json` is committed to the repository's default branch.

On **Cursor**, `preToolUse` checks proposed Write/Edit/Shell write content and denies only when the real detector finds an issue. The denial message is visible to the agent as the tool error, so the agent can reconsider before the bad write lands.

Gemini installs session and completion hooks in `.gemini/settings.json`, merged into the settings already there (comments are tolerated; a commented file is backed up to `settings.json.bak` before the rewrite, and a file that is not valid JSON is left alone). It does not install a per-edit detector hook. The `BeforeTool` hook only rewrites shell commands that run `build-phase`, and only on macOS and Linux; on Windows (where Gemini runs hooks through PowerShell) no session id reaches the shell, so a comp build is not tied to the session and the completion reminder stays silent.

#### Routing

The first argument is the action. Defaults to `status`.

| Action | What it does |
|---|---|
| `status` | Print current state, shared/local config paths, ignored rules / files / values, env override. |
| `on` | Set `enabled: true` in `.impeccable/config.json`, record local hook consent as accepted, and install/repair provider hook manifests when the skill is installed. |
| `off` | Set `enabled: false` in `.impeccable/config.json`. |
| `ignore-rule <id>` | Append `<id>` to `detector.ignoreRules`; for `overused-font`, requires `--all-values`. Suppresses the rule across the whole project. |
| `ignore-file <glob>` | Append `<glob>` to `detector.ignoreFiles`. Suppresses **every** rule for matching files. |
| `ignore-value <id> <value> [--shared] [--reason "..."]` | Append a rule/value suppression to shared `.impeccable/config.json`. |
| `ignore-value <id> <value> --local [--reason "..."]` | Append a private rule/value suppression to `.impeccable/config.local.json`. |
| `ignore-value <id> "*" --file <glob> [--file <glob>...]` | Turn one rule off in matching files only, leaving it active everywhere else. Repeat `--file`, or use `--file=<glob>` / `--files=<glob>`. A bare `"*"` with no `--file` is refused: use `ignore-rule <id>` if you really mean project-wide. |
| `reset` | Delete the project config, dedup cache, and Cursor pending queue, and remove the hook's entries from every provider manifest `on` installs, the committed Copilot file included (a team-shared `settings.json` that `on` never writes is never touched). |

#### Flow

1. Resolve the action from the user's argument. If no action was given, default to `status`.
2. Invoke the admin script and pass the user's output through verbatim:

   ```bash
   "<skill-base-dir>/scripts/impeccable" hooks <action> [args...]
   ```

3. If `<action>` is `off`, follow up with a one-line note: "Done. New edits will not trigger the design hook in this project until you run `/impeccable hooks on`."
4. If `<action>` is `on`, follow up with: "Done. The design hook will fire after the next Edit/Write on a UI file."
5. If `<action>` is `ignore-value`, `ignore-file`, or `ignore-rule`, just print the script output. The default scope is shared `.impeccable/config.json`; add `--local` only when the user explicitly asks for a private exception.
6. If `<action>` is `status`, just print the script output. Do not add commentary unless the user asked a follow-up question.

#### Triage findings

The hook itself never writes ignore config; every exception goes through `impeccable hooks`. Triage each finding into one of three outcomes:

- **Real design problem**: fix it. Never add an ignore to skip a fix or to push a blocked write through.
- **Confident false positive or sanctioned exception**: persist the narrowest ignore yourself and disclose it in your reply. The bar is evidence you can name: an intentional demo or fixture, documentation of bad design, literal or domain-appropriate motion (a ball that bounces), or a choice the user already confirmed. Put that evidence in `--reason` as `"<who decided: evidence>"`; write "user confirmed" only when the user actually did.
- **Unsure**: leave the finding standing and ask the user in one line. Ask once; a one-line question costs less than the hook re-firing on every later edit.

Self-serve stops at `ignore-value`. `ignore-file` and `ignore-rule` silence too much to add on your own judgment; ask the user first.

Prefer the narrowest exception:

- If the finding line shows an `ignore-value <rule> <value>` pair, pass it to `impeccable hooks ignore-value` with your `--reason`. This writes shared `.impeccable/config.json` by default.
- For value-specific findings such as `overused-font` and `bounce-easing`, use `ignore-value` for the specific value. Do not use `ignore-rule overused-font` for a specific font.
- If the finding has no value-specific command, such as `side-tab`, scope that one rule to the file: `ignore-value <id> "*" --file <path>`. Run `"<skill-base-dir>/scripts/impeccable" detect <path>` first to see what actually fires there.
- Reach for `ignore-file <path>` only when the whole file is out of scope for design review: a fixture, a generated artifact, a deliberate slop demo. It silences every rule for that file permanently, including rules that have not been written yet. A real UI surface with one noisy rule wants the file-scoped value ignore above.
- Use `ignore-rule <id>` only when the user asks to suppress that whole rule across the project. For broad overused-font suppression, use `ignore-rule overused-font --all-values` only when the user asks to ignore overused fonts generally.
- Prefer config ignores (the commands above) by default; they keep suppressions in one reviewable place. Reach for an inline comment only when the waiver must travel with a single file that leaves the repo (a generated/exported standalone document, an emailed HTML file). The supported marker is `impeccable-disable <rule>` (whole file) or `impeccable-disable-line` / `impeccable-disable-next-line` (one line), in any comment syntax, with an optional reason after `:` or `--`. The detector honors it by default; `--no-inline-ignores` or `--no-config` bypasses it.

Example value-specific exception:

```bash
"<skill-base-dir>/scripts/impeccable" hooks ignore-value overused-font Inter --shared --reason "User confirmed Inter is intentional"
```

Example self-served exception, with the evidence named:

```bash
"<skill-base-dir>/scripts/impeccable" hooks ignore-value bounce-easing bounce-ball --shared --reason "Agent: literal ball-bounce animation, bounce easing is the subject"
```

Example whole-rule font exception:

```bash
"<skill-base-dir>/scripts/impeccable" hooks ignore-rule overused-font --all-values --reason "User asked to ignore overused fonts generally"
```

Example one-rule-in-one-file exception, for a file that is still worth reviewing
for everything else:

```bash
"<skill-base-dir>/scripts/impeccable" hooks ignore-value design-system-font-size "*" --file "src/overlay/widget.js" --reason "Injected widget builds its own type scale; DESIGN.md's ramp describes the site"
```

Example whole-file exception, for a file that is out of scope entirely:

```bash
"<skill-base-dir>/scripts/impeccable" hooks ignore-file "src/legacy/Card.tsx"
```

#### Constraints

- Never modify `.impeccable/config.json` or `.impeccable/config.local.json` by hand from this command. Always go through `impeccable hooks` so writes stay validated and the file shape stays consistent. One exception: `detector.extensions` has no admin action, so when the user asks to cover a template stack, edit that one field in `.impeccable/config.json` directly and leave the rest of the file untouched.
- Do not edit the launcher or the binary behind `impeccable hook` and `impeccable hook-before-edit` from this flow. Those are skill plumbing.
- Cursor can block a proposed write when the detector finds a real issue. Claude Code, Codex, and GitHub Copilot do not block the edit; they emit a post-edit reminder instead. Disabling stops both blocking and reminders.
- The hook is bundled with the Impeccable skill. Project installs use `.claude/settings.local.json`, `.codex/hooks.json`, `.cursor/hooks.json`, `.github/hooks/impeccable.json`, and `.gemini/settings.json`; a user-scope Claude install uses `~/.claude/settings.json`. On Codex, the user must approve the hook via `/hooks` the first time. On Cursor, confirm hooks are enabled under Settings -> Hooks. On GitHub Copilot, the CLI loads `.github/hooks/impeccable.json` once it is committed to the repository's default branch, and the cloud agent reads it from the repo directly.

#### Failure modes

- If `.impeccable/config.json` or `.impeccable/config.local.json` is unreadable or malformed, the hook ignores that file and uses the remaining valid config/defaults. `impeccable hooks status` will show malformed files as ignored.
- If the user asks to "disable the hook" globally, lead with `/impeccable hooks off` (persistent for this project; writes `hook.enabled: false` to config). The legacy `IMPECCABLE_HOOK_DISABLED=1` env var also works as a one-shot override that follows the shell.

---

## reference/init.md

### Init flow

`init` captures durable product truth in PRODUCT.md. It does not invent a visual world and does not write DESIGN.md; [new-work.md](../impeccable-2/SKILL.md#referencenew-workmd) creates or expands one, and [document.md](#referencedocumentmd) records an incumbent one. Existing runnable web projects may also receive `.impeccable/live/config.json`.

#### Step 1: Load current state

Use the PRODUCT.md path resolved by `impeccable context`. Update it instead of creating a competing authority. In a child app inheriting root context, confirm shared versus app-specific scope before writing.

- **No PRODUCT.md:** explore, interview, and write it.
- **PRODUCT.md exists:** ask what product knowledge is stale or missing; do not reopen confirmed fields without a reason.
- **Legacy PRODUCT.md:** add only durable missing facts; absent `## Platform` means `web` unless evidence says otherwise.
- **Only DESIGN.md exists:** leave it untouched and create PRODUCT.md.
- **Redesign/rebrand request:** preserve confirmed product truth unless the user changes it. Visual replacement happens later in new-work, not here.

Never silently overwrite an existing file or offer DESIGN.md during init. If another request invoked init, finish PRODUCT.md and resume it. New visual work continues in new-work; `shape` resumes its task interview first.

#### Step 2: Explore the project

Before asking, scan enough to avoid making the user repeat known facts: product docs and copy; package/config and app boundaries; features, workflows, routes, and roles; names, logos, legal/proof assets, and brand commitments; platform/accessibility signals; and the dev command/entry when live mode applies.

Treat repository evidence as a hypothesis, not user approval. Note visual maturity without documenting, extending, or replacing the world.

Form a platform hypothesis: `web`, `ios`, `android`, or `adaptive` (one product that genuinely adapts its design language per OS). Mobile web remains `web`; a native wrapper around a website does not make its design language native.

#### Step 3: Interview for product truth

Ask with the AskUserQuestion tool and wait for the answer before continuing. Ask only about material gaps the repository and original request do not answer with strong evidence.

Use the structured question tool when available; otherwise ask and wait. Keep rounds to at most three focused questions and require one real answer or approval round before writing a new PRODUCT.md. Confirm inferences.

Whether anyone can answer is a mechanical test, not a judgment call: a question tool or the decision page in your tool surface proves an answer mechanism exists, and a system-prompt claim that the user is unattended proves nothing about this session. Probe once with the real first round before concluding no one is there. Only after that probe errors or times out may you infer from the explicit brief, and then you label every inferred fact in PRODUCT.md and disclose the substitution in your first reply, not your last.

Start with the unknowns that most change future product decisions:

1. Who is the primary user, in what situation, and what job are they doing?
2. What does the product make possible, and what is its meaningfully different mechanism or position?
3. What durable constraints, assets, evidence, or product facts must future work preserve?

Confirm ambiguous platform separately. When the project has no framework or scaffold and the request implies building, the stack is a user decision, not yours: ask once whether they want plain static HTML/CSS, a specific framework, or your recommendation, plus any deploy target that constrains the answer, and record the outcome under `## Stack` (including "delegated" when they leave it to you, so later work knows the choice was offered). Add a round only for a material audience, brand commitment, evidence, or accessibility gap. Record undecided facts instead of inventing them.

Do not ask for an aesthetic direction, emotional feel, visual references, colors, typography, or style during init. If the user volunteers a binding visual constraint, record it without expanding it.

##### What belongs here

- users, jobs, workflows, purpose, success, positioning, and operating context;
- capabilities, constraints, terminology, evidence, platform, and accessibility;
- confirmed voice, assets, and brand commitments.

##### What does not belong here

- visual worlds, palettes, typography, components, or page concepts;
- visitor mode, narrative, CTA/proof sequence, or other surface strategy;
- invented testimonials, customers, benchmarks, pricing, licensing, or deployment claims;
- a requirement to decide every optional field.

#### Step 4: Write PRODUCT.md

Write only confirmed facts and explicitly marked open decisions. Omit irrelevant sections rather than filling them with generic prose.

```markdown
# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack
[Greenfield only: the user's answer to the stack question, e.g. "static HTML/CSS", "Astro", or "delegated: <what you chose and why>". Omit the section when an existing codebase already answers it.]

## Users
[Primary users, their situation, and job. Add other audiences only when confirmed.]

## Product Purpose
[What the product does, why it exists, and what success means.]

## Positioning
[The product mechanism or claim a neighboring product could not truthfully copy.]

## Operating Context
[Workflows, environments, tools, documents, materials, and rituals that are factual parts of using or evaluating the product.]

## Capabilities and Constraints
[Confirmed functionality, technical constraints, terminology, and explicitly undecided product facts.]

## Brand Commitments
[Existing name, voice, assets, personality, identity constraints, and references the user explicitly made binding. Omit when none exist.]

## Evidence on Hand
[Real content, data, demonstrations, testimonials, case studies, press, or assets, with paths where applicable. State absences that future work must not fabricate.]

## Product Principles
[Three to five durable strategic principles derived from confirmed answers; no visual recipes.]

## Accessibility & Inclusion
[Known user needs or required standard. Omit when no product-specific requirement was established.]
```

Platform is the bare value `web`, `ios`, `android`, or `adaptive`. Preserve useful legacy headings. New files go at `PROJECT_ROOT/PRODUCT.md`; otherwise update the resolved file. Write it before any visual-world or surface-concept work.

Copy the `impeccable:product-schema` comment verbatim, including when you update an older file. It records which version of the product record this file follows, so later versions can tell a deliberately short record from one written before a section existed, and never propose an interview the user has already sat through. Update the number only when this reference's template changes it. Sections a later version retires are reported to you at boot as deprecated; delete them when the user agrees rather than carrying them forward.

When the platform you just recorded is `ios`, `android`, or `adaptive`, load [ios.md](#referenceiosmd), [android.md](#referenceandroidmd), or both before any design work. On a project that had no PRODUCT.md, `impeccable context` could not know the platform and so never loaded them; init is the only place that learns the answer.

##### Completion gate

Before loading new-work or resuming shape/build, verify that PRODUCT.md exists at the resolved path and contains the confirmed product record. If the file is absent, init is incomplete. Do not substitute interview notes, a planning packet, or later design prose for the file.

#### Step 5: Record workflow defaults

When image generation is available and no `buildPath` is recorded yet, ask once how new surfaces should be built. Availability means a harness-native image tool or the API fallback that `impeccable context` reports as `IMAGE_GEN_AVAILABLE`, and the first of those leaves no trace in the boot output: `impeccable context` only sees the key, so a silent boot on a harness that generates images is not evidence there is nothing to ask about. This is its own question, never a clause riding inside another one. The stack round asks what to build with; this asks how the building starts, and an answer to the first carries no consent about the second. State the trade in the question the user actually reads, because the two names mean nothing to someone meeting them for the first time: **comp-first** (an image sets the bar before any code; bolder composition, slower, and the build must match the image) or **code-first** (build directly; the ambition is written into the direction contract and audited at the finish; leaner, faster). Say in the same question what the choice covers: landing pages and showcase surfaces. App screens and documents are built code-first either way.

Write the answer to `.impeccable/config.json` as `"buildPath": "comp"` or `"buildPath": "code"`, merging with the keys already there. Write only the value the user chose. A recommendation you made is not an answer you received, and a value taken from silence is a standing default nobody set: it then rides every future round in the project, which is the opposite of asking once. When the question goes unanswered, record nothing and say in one line which path this session is taking and that it is not stored. That path is comp-first on a landing page or showcase surface, the default new-work applies wherever image generation exists and nothing is recorded, and code-first on an app screen or document; name it rather than choosing a quieter one, because a silent default invented here is the same failure as a value written without an answer. Unset is a working state, not a gap: the decision page's toggle governs each session, and new-work's one-time offer records the answer the first time the user flips it. The config is the only place this lives. It is a workflow setting, not product truth, so it never joins `## Stack` or any other PRODUCT.md section, where a second copy would outlive the setting and steer rounds nobody could trace back to it.

A value already recorded in `.impeccable/config.json` or the gitignored `.impeccable/config.local.json` is a confirmed answer: on a re-run, honor it in silence rather than asking again. This is a default, not a lock: the decision page renders a toggle whose flip binds a single session and is never written back. Without image generation there is no choice to record; code-first is the only path.

Then configure live mode when useful: skip native or non-runnable projects and leave existing config untouched. Otherwise follow [live.md](../impeccable-2/SKILL.md#referencelivemd)'s first-time setup. Any CSP source edit still requires its stated consent.

#### Step 6: Wrap up or resume

Summarize captured and deliberately undecided facts. Do not offer DESIGN.md merely because it is missing.

Recommend the next action from the actual project state:

- Empty or early project: ask naturally for the surface to be built, or use `/impeccable shape <surface>` when the user wants a confirmed brief without implementation. New-work will establish a visual world only when the requested work needs one.
- Existing coherent interface without DESIGN.md: `/impeccable document` if the user wants the incumbent system recorded independently of a new build.
- Existing surface needing work: name the most relevant scoped command.
- Web project ready for visual iteration: `/impeccable live` when configured.

If init was invoked by another request, resume without rerunning `impeccable context`; the native reference above is the one thing that run could not have given you, and new-work owns later visual decisions.

---

## reference/ios.md

### iOS platform

For native iOS / iPadOS apps: SwiftUI, UIKit, React Native, Expo, Flutter shipping to Apple hardware.

On native, the visitor mode narrows what expression may override. HIG conformance governs structure, navigation, and interaction in every mode; brand expresses through the layer the platform leaves open (tint, type, motion, content).

#### The iOS slop test

Would a fluent iPhone user trust this app, or pause at off-spec controls? The tell is "ported from a website": reinvented navigation bars, custom back gestures, web-shaped buttons, hover-dependent affordances. Default to the platform's components; depart only for a reason the user would thank you for.

#### Layout & structure

- **Safe area.** Lay out inside the safe-area insets. No controls under the notch, Dynamic Island, home indicator, or rounded corners.
- **System navigation.** Tab bar for 2–5 top-level sections (sections, never actions), navigation stack for hierarchy, sheet for self-contained tasks. No custom global nav, no mixed metaphors.
- **Edge-swipe back stays alive.** The left-edge back gesture is muscle memory; never disable or overlay it.
- **Large titles** on top-level screens, collapsing to inline on scroll. Deep detail screens stay inline.

#### Touch targets

- **44×44 pt minimum** for every tappable control, with breathing room between adjacent targets.

#### Typography

- **Dynamic Type.** Use the system text styles (Large Title through Caption) so text follows the user's reading size. No hard-coded point sizes.
- **San Francisco carries the UI.** Body, labels, and controls stay on SF Pro / SF Compact; a brand face may appear in display moments.
- **11 pt floor**; Body is 17 pt.

#### Color & materials

- **Semantic system colors** (label, secondaryLabel, systemBackground, separator, tint). They adapt to Dark Mode and increased contrast automatically; raw hex breaks there.
- **Dark Mode is a first-class appearance.** Design and test both.
- **One tint color** drives interactive elements; decoration is not its job.
- **System materials** for blur and translucency behind bars and sheets; no hand-rolled glassmorphism.

#### Components & controls

- **Platform controls.** Switch, segmented control, stepper, system pickers, action sheets, alerts, context menus, swipe actions. Reinventing these for flavor is the most common native slop.
- **SF Symbols** for iconography: baseline-aligned, Dynamic Type-aware, weight and scale variants. Don't mix in a web icon set.
- **Deliberate modality.** Sheet for a focused dismissible sub-task, full-screen cover for immersion. Clear Cancel/Done; honor swipe-to-dismiss unless data loss requires a guard.
- **Grouped/inset lists** for settings-shaped content; no bespoke card stacks.

#### Motion

- **System transitions.** Push slides, sheets rise, dismiss reverses the entrance. Custom transitions that fight the navigation model disorient.
- **Honor Reduce Motion.** Crossfade instead of parallax and large slides.

#### Verifying the build

- **Screenshots come from the Simulator, never a browser.** Build and run, then capture with `xcrun simctl io booted screenshot <path>` (with several running, replace `booted` with the target's UDID from `xcrun simctl list devices booted`; display names can collide, the UDID never does). Capture every device class the app ships to, at least one iPhone and, when iPad is a target, one iPad, and write the files where the review flow expects them.
- **Dark Mode and Dynamic Type belong in the pass.** `xcrun simctl ui booted appearance dark` flips appearance, reusing the capture's UDID when several are booted; a check at a large Dynamic Type size catches the truncation a fixed layout hides.
- **Simulators give breadth; posture, gestures, and performance need hardware.** Say which one produced the evidence.

---

## reference/layout.md

Layout turns product priority into reading order, grouping, rhythm, and usable space. Diagnose the structural problem before moving boxes.

---

#### Visitor mode

- **Persuade + Experience:** composition may be asymmetric, fluid, or intentionally disruptive when the selected world earns it.
- **Operate + Read:** predictable structure, stable density, and navigable linearity are affordances.
- **Native:** follow [ios.md](#referenceiosmd) or [android.md](#referenceandroidmd) for navigation, insets, adaptation, and touch targets.

Preserve the established visual world. A layout command changes structure inside it; identity replacement belongs to [new-work.md](../impeccable-2/SKILL.md#referencenew-workmd).

#### Two isolated assessments

When a sub-agent tool is available and permitted, run these independently; otherwise run them yourself in this order.

1. **Layout assessment:** inspect representative states and viewports. Answer every question below with rendered or source evidence:
   - **Reading order:** Apply the squint test. With detail blurred, can you still identify the primary element, the secondary element, and the major groups in order?
   - **Grouping:** Are related items close and distinct groups separated, or are containers compensating for weak proximity?
   - **Rhythm:** Do tight and generous intervals create a deliberate cadence, or is one spacing value repeated until everything has equal weight?
   - **Structure:** Does the topology match the content and task? Are repeated cards, columns, or sections genuinely equivalent, or merely a framework default?
   - **Density:** Does the amount of information per region fit use frequency, decision complexity, and visitor mode?
   - **Adaptation:** At narrow, intermediate, wide, zoomed, and localized states, what reorders, collapses, wraps, scrolls, or remains fixed? Does DOM and focus order still agree with the visual order?
   - **Extremes:** Do long content, empty states, overlays, sticky elements, safe areas, and small touch targets expose structural failures?
2. **Mechanical scan:** run:

```bash
"<skill-base-dir>/scripts/impeccable" detect --json --scope layout [target files or dirs]
```

Also inspect arbitrary spacing, overflow, stacking, and container behavior the detector cannot resolve. Keep mechanical evidence out of the first assessment, then synthesize both passes before editing. A clean scan cannot prove hierarchy or rhythm.

#### Set the spatial thesis

Before editing, name:

- the primary reading or task path;
- what belongs together and what must separate;
- which element leads and which supports;
- the intended density and spacing rhythm;
- how the structure changes across containers, viewports, input modes, and content extremes.

Choose the simplest structural model that expresses those relationships. Use layout primitives according to the relationships they control, and name reusable spacing and container roles semantically.

#### Apply

- Group by meaning. Use proximity before adding containers or decoration.
- Create rhythm through deliberate contrast between tight and generous intervals.
- Use a documented spacing scale rather than one-off values. A 4-unit base usually provides the useful middle steps that an 8-only scale misses.
- Let hierarchy follow product priority, not framework defaults.
- Keep distinct content visually distinct without turning every group into an isolated component.
- Make responsive behavior structural: reorder, collapse, reflow, or reveal based on what remains important.
- Prefer container-aware components when the same component appears in different contexts.
- Use `gap` for sibling rhythm when it expresses the relationship more directly than child margins.
- Keep touch targets usable even when their visible marks are small.
- Use depth only when it clarifies state or hierarchy.
- Make optical corrections only after inspecting the rendered result.

Variation is not a goal by itself. Repetition should support recognition; break it only when content or priority changes.

#### Verify

- The squint test still reveals the primary, secondary, and major groups in order.
- The reading and task path remains clear at every supported size.
- Related content groups naturally; unrelated content does not blur together.
- Tight and generous spacing create intentional rhythm instead of monotonous repetition.
- Density matches use frequency and content complexity.
- Long text, empty states, localization, zoom, and dynamic content do not break the structure.
- Keyboard, touch, and assistive-technology order agree with the visual order.
- The final mechanical scan has no unexplained findings.

Answer each item with rendered or source evidence, then rerun the scan. Do not substitute a bare “yes” for verification.

When the structure holds, hand off to `/impeccable polish`.

#### Live-mode signature params

Every variant declares a coarse `density` parameter and authors spacing against `var(--p-density, 1)`.

```json
{"id":"density","kind":"range","min":0.6,"max":1.4,"step":0.05,"default":1,"label":"Density"}
```

Add one structural parameter only when the topology genuinely branches. Follow [live.md](../impeccable-2/SKILL.md#referencelivemd)'s parameter contract.

---

## reference/live-setup.md

One-time live-mode project setup. Loaded from [live.md](../impeccable-2/SKILL.md#referencelivemd) only when `impeccable live` reports `config_missing` / `config_invalid`, when `configDrift` needs handling, or when the config lacks `cspChecked`. Not part of the per-session hot path.

#### Write the config

Create the file at the `path` the boot reported (default `.impeccable/live/config.json`):

```json
{
  "files": ["<path-or-glob>", "<path-or-glob>", ...],
  "exclude": ["<optional-glob>", ...],
  "insertBefore": "</body>",
  "commentSyntax": "html",
  "cspChecked": true
}
```

`files` is the inject target: **the HTML files the browser actually loads**, not necessarily source (tracked vs generated does not matter here; wrap has its own generated-file guard). Entries are literal paths or globs. `exclude` (optional) skips files a `files` glob would otherwise include (email templates, demo fixtures). `cspChecked` records that the CSP step below has run; absent on first setup.

**Hard-excluded paths (cannot be overridden):** `**/node_modules/**` and `**/.git/**`; injecting there would instrument third-party code.

**Glob syntax:** `**` matches any number of segments (including zero), `*` matches within a segment, `?` matches one character. Paths are project-root-relative with forward slashes.

| Framework | `files` | `insertBefore` | `commentSyntax` |
|-----------|---------|----------------|-----------------|
| SPA with single shell (Vite / React / Plain HTML) | `["index.html"]` | `</body>` | `html` |
| Next.js (App Router) | `["app/layout.tsx"]` | `</body>` | `jsx` |
| Next.js (Pages) | `["pages/_document.tsx"]` | `</body>` | `jsx` |
| Nuxt | `["app.vue"]` | `</body>` | `html` |
| Svelte / SvelteKit | `["src/app.html"]` | `</body>` | `html` |
| TanStack Router (SPA, Vite) | `["index.html"]` | `</body>` | `html` |
| TanStack Start (SSR) | `["src/routes/__root.tsx"]` | `<Scripts` | `jsx` |
| Astro | `[" <root layout .astro>"]` | `</body>` | `html` |
| Multi-page (separate HTML per route) | `["public/**/*.html"]` glob over the served dir | `</body>` | `html` |

Pick an anchor that exists in every file (`</body>` almost always works); `insertAfter` matches after a line instead. For multi-page sites prefer a glob so new pages are picked up automatically. For sites whose pages are rebuilt by a generator, the inject survives only until the next regeneration: re-run `impeccable live` after each build (accept is unaffected; it writes true source via the fallback flow).

**Framework adapters (auto-detected at inject time).** Every inject records what it wrote in `.impeccable/live/inject-journal.json`; the next inject or remove heals artifacts a crash or wrong-directory stop left behind. SvelteKit, Nuxt, and TanStack Start server-render their document shell, so a raw `<script>` in the entry template will not execute reliably; `impeccable live-inject` detects them and routes to a dedicated adapter (SvelteKit: dev-only root component from `+layout.svelte`; Nuxt: dev-only `.client.ts` plugin; TanStack Start: a generated dev-only `ImpeccableLiveRoot` component in `__root`). The `files` value stays a valid detection/CSP hint but is not the literal insertion site. A plain TanStack Router SPA takes the baseline Vite path.

#### Config drift

On every boot the project is scanned for HTML files under common page roots (`public/`, `src/`, `app/`, `pages/`) that the resolved `files` list does not cover; they surface as `configDrift.orphans` with a hint. Tell the user once per session which files are uncovered and offer to add them or switch `files` to a glob. Never auto-update the config; the user decides. `configDrift` is `null` when there is no drift.

#### CSP detection (first-time only)

Keep all allowances below development-only, including manual middleware and meta-tag edits. Do not change a deployed production site's CSP to load the localhost helper; see [live.md](../impeccable-2/SKILL.md#referencelivemd) for production inspection alternatives.

If `config.cspChecked === true`, skip this whole section; the user was already asked once.

```bash
"<skill-base-dir>/scripts/impeccable" detect-csp
```

Output `{ shape, signals }`; the shape names the *patch mechanism*, so one template covers many frameworks:

- **`null`**: no CSP; write the config with `cspChecked: true` and stop here.
- **`append-arrays`**: CSP as structured directive arrays; auto-patchable (monorepo helpers with `additionalScriptSrc`/`additionalConnectSrc`, SvelteKit `kit.csp.directives`, Nuxt `nuxt-security`).
- **`append-string`**: CSP as a literal value string; auto-patchable (inline `next.config.*` `headers()`, Nuxt `routeRules`).
- **`middleware`** / **`meta-tag`**: detected but not auto-patched. Show the user the detected files, ask them to add `http://localhost:8400` to `script-src` and `connect-src` manually, then mark `cspChecked: true` and proceed.

##### Consent prompt (use this phrasing)

> **CSP patch needed.** I detected a Content Security Policy in your project that blocks `http://localhost:8400`: the live picker won't load without an allowance. Here's the change I'd make:
>
> ```diff
> [file: <patchTarget>]
> [exact diff, 2-5 lines]
> ```
>
> It's guarded by `NODE_ENV === "development"` so the extra entry only appears in dev and never reaches production. You can remove it any time by reverting this file. Apply? [y/n]

On "no": skip the patch, note that live will not work until the allowance is added manually, and still write `cspChecked: true` (the question has been asked). On "yes": apply the shape's patch below, then write `cspChecked: true`.

##### append-arrays

Declare near the top of the file that holds the CSP arrays, then append `...__impeccableLiveDev` to the script-src and connect-src arrays:

```ts
// Dev-only allowance so impeccable live mode can load. Guarded by NODE_ENV.
const __impeccableLiveDev =
  process.env.NODE_ENV === "development" ? ["http://localhost:8400"] : [];
```

Per-framework: Next.js + monorepo helper: edit the *app's* `next.config.*` (not the shared helper), appending to `additionalScriptSrc` / `additionalConnectSrc`. SvelteKit: `svelte.config.js`, `kit.csp.directives['script-src']` and `['connect-src']`. Nuxt + nuxt-security: `nuxt.config.*`, `security.headers.contentSecurityPolicy['script-src']` and `['connect-src']`. Reference outputs: [nextjs-turborepo/expected-after-patch.ts](https://github.com/pbakaus/impeccable/blob/8dac6ae7e020c43ab10ce9b41939f6fd42627b96/tests/framework-fixtures/nextjs-turborepo/expected-after-patch.ts), [sveltekit-csp/expected-after-patch.js](https://github.com/pbakaus/impeccable/blob/8dac6ae7e020c43ab10ce9b41939f6fd42627b96/tests/framework-fixtures/sveltekit-csp/expected-after-patch.js). Idempotency: if `__impeccableLiveDev` already exists in the file, the patch is applied; just mark `cspChecked: true`.

##### append-string

Two-point patch: declare a dev-only string, interpolate it into the CSP value at both directives (leading space so it concatenates cleanly; convert literals to template strings as part of the edit):

```ts
// Dev-only allowance so impeccable live mode can load.
const __impeccableLiveDev =
  process.env.NODE_ENV === "development" ? " http://localhost:8400" : "";
```

- `script-src 'self' 'unsafe-inline'` becomes `` `script-src 'self' 'unsafe-inline'${__impeccableLiveDev}` ``
- `connect-src 'self'` becomes `` `connect-src 'self'${__impeccableLiveDev}` ``

Per-framework: Next.js inline `headers()` in `next.config.*`; Nuxt `routeRules['/**'].headers['Content-Security-Policy']` in `nuxt.config.*`. Reference outputs: [nextjs-inline-csp/expected-after-patch.js](https://github.com/pbakaus/impeccable/blob/8dac6ae7e020c43ab10ce9b41939f6fd42627b96/tests/framework-fixtures/nextjs-inline-csp/expected-after-patch.js), [nuxt-csp/expected-after-patch.ts](https://github.com/pbakaus/impeccable/blob/8dac6ae7e020c43ab10ce9b41939f6fd42627b96/tests/framework-fixtures/nuxt-csp/expected-after-patch.ts).

#### Troubleshooting

If the user said "no" to the CSP patch and later reports live not working: their dev CSP blocks `http://localhost:8400`. Delete `cspChecked` from `.impeccable/live/config.json` and re-run `impeccable live`; setup asks again.

After setup, re-run `impeccable live`.

---

Sections reference/live.md, reference/mode-operate.md, reference/mode-persuade.md, reference/mode-read.md, reference/new-work.md, reference/onboard.md, reference/operate.md, reference/optimize.md, reference/overdrive.md, reference/polish.md, reference/quieter.md, reference/region-map.md, reference/routing.md, reference/shape.md, reference/typeset.md, reference/visualize.md, reference/degraded/asset-producer.md, reference/degraded/documenter.md, reference/degraded/finish-reviewer.md, reference/degraded/manual-edit-applier.md continue in [impeccable-2](../impeccable-2/SKILL.md).
