---
name: Grim
description: A multiplayer Markdown notebook for people and agents — plain .md files in Git, edited live.
colors:
  paper: "#fcfcfb"
  paper-2: "#f4f4f5"
  paper-3: "#ebebed"
  tint-hover: "#ececee"
  tint-active: "#e4e4e7"
  code-bg: "#f1f1f2"
  ink: "#1d1e22"
  ink-2: "#3f3f46"
  muted: "#62626a"
  grey: "#8b8b93"
  line: "rgba(24, 24, 27, 0.12)"
  line-soft: "rgba(24, 24, 27, 0.07)"
  blue: "#296d9a"
  warn: "#e0a800"
  warn-soft: "rgba(245, 197, 66, 0.26)"
  red: "#c62f28"
  red-hover: "#a8241e"
  cursor-blue: "#007aff"
typography:
  label:
    fontFamily: "-apple-system, BlinkMacSystemFont, Inter, system-ui, Segoe UI, Roboto, Arial, sans-serif"
    fontSize: "12px"
    fontWeight: 600
    lineHeight: "1.2"
    letterSpacing: "0.005em"
  body:
    fontFamily: "-apple-system, BlinkMacSystemFont, Inter, system-ui, Segoe UI, Roboto, Arial, sans-serif"
    fontSize: "14px"
    fontWeight: 400
    lineHeight: "1.45"
  heading:
    fontFamily: "-apple-system, BlinkMacSystemFont, Inter, system-ui, Segoe UI, Roboto, Arial, sans-serif"
    fontSize: "22px"
    fontWeight: 650
    lineHeight: "1.25"
    letterSpacing: "-0.02em"
  note-body:
    fontFamily: "-apple-system, BlinkMacSystemFont, Inter, system-ui, Segoe UI, Roboto, Arial, sans-serif"
    fontSize: "16px"
    fontWeight: 400
    lineHeight: "1.6875"
    letterSpacing: "0em"
  note-h1:
    fontFamily: "-apple-system, BlinkMacSystemFont, Inter, system-ui, Segoe UI, Roboto, Arial, sans-serif"
    fontSize: "32px"
    fontWeight: 700
    lineHeight: "1.125"
    letterSpacing: "-0.024em"
  note-h2:
    fontFamily: "-apple-system, BlinkMacSystemFont, Inter, system-ui, Segoe UI, Roboto, Arial, sans-serif"
    fontSize: "24px"
    fontWeight: 600
    lineHeight: "1.25"
    letterSpacing: "-0.02em"
  mono:
    fontFamily: "ui-monospace, SF Mono, Menlo, Consolas, Liberation Mono, monospace"
    fontSize: "13.5px"
    fontWeight: 400
    lineHeight: "1.63"
rounded:
  sm: "4px"
  md: "6px"
  lg: "8px"
spacing:
  xs: "4px"
  sm: "8px"
  md: "12px"
  lg: "16px"
  xl: "20px"
components:
  button-secondary:
    backgroundColor: "{colors.paper}"
    textColor: "{colors.ink}"
    rounded: "{rounded.md}"
    padding: "0 14px"
    height: "32px"
  button-primary:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.paper}"
    rounded: "{rounded.md}"
    padding: "0 14px"
    height: "32px"
  button-danger:
    backgroundColor: "{colors.red}"
    textColor: "#ffffff"
    rounded: "{rounded.md}"
    padding: "0 14px"
    height: "32px"
  icon-button:
    backgroundColor: "transparent"
    textColor: "{colors.muted}"
    rounded: "{rounded.sm}"
    size: "24px"
  input-text:
    backgroundColor: "{colors.paper}"
    textColor: "{colors.ink}"
    rounded: "{rounded.md}"
    padding: "0 10px"
    height: "34px"
  menu-item:
    backgroundColor: "transparent"
    textColor: "{colors.ink}"
    rounded: "{rounded.sm}"
    padding: "0 10px"
    height: "30px"
  modal:
    backgroundColor: "{colors.paper}"
    textColor: "{colors.ink}"
    rounded: "{rounded.lg}"
    padding: "0"
---

# Design System: Grim

## Overview

**Creative North Star: "Plain Paper"**

Grim's interface is a sheet of paper with ink on it, in a room with other people writing. There is no decoration that isn't structure: surfaces are near-white paper with barely-cool neutral tints, text is near-black ink, structure is drawn with hairlines rather than fills, and the single accent — a muted steel blue — appears only where the system is pointing (links, focus, selection, remote cursors). The one deliberately square-edged, inverted element is the slab logo; everything else is quietly rounded (4–8px). The result should feel like a native text app that happens to live in a browser: whole-pixel layout, the platform's own font on each OS, thin quiet scrollbars, no font-smoothing overrides.

Density is text-first and generous where text lives (16px/27px note body, an 840px measure) and compact where control lives (14px UI, 28–32px rows and buttons, 12px/600 micro-labels). Expression is spent on craft — hover states that are a 4% tint shift, bullets drawn as 5px squares, a checkbox tick drawn with two borders — never on color, gradients, or words.

App surfaces (editor, sidebar, dialogs, history) are **Operate mode**: scanability, native expectations, and restraint outrank expression. The marketing landing page is out of scope for this file.

**Key Characteristics:**
- Paper and ink; neutral tints for secondary surfaces; hairlines instead of borders-as-decoration.
- One accent (steel blue) used only for pointing: links, focus, selection, remote presence. Ink itself is the "primary" color.
- Whole-pixel everything; platform font first (San Francisco with its own tracking, then Inter), system monospace for code.
- Depth only for things that float: menus, modals, toasts. The page itself is flat.
- No explainer or hint text anywhere; controls are icon-only or tersely labelled, and accessibility labels are invisible.

## Colors

A near-monochrome cool-grey system on warm-white paper, with ink doing the work of a brand color and blue strictly rationed.

### Primary
- **Ink** (#1d1e22): the app's true primary. Body UI text, primary (inverted) buttons, the slab logo, toast surfaces, active checkbox fills, menu dots. Hover for primary buttons is pure #000.
- **Ink-2** (#3f3f46): secondary emphasis — folder names, active-state text, secondary text on raised surfaces.

### Secondary
- **Steel Blue** (#296d9a): the only hue with a pointing job. Links (1px underline, offset 2px), `:focus-visible` outlines and input focus rings, text selection, live-caret accents, "current row in a focused tree" tints (18% mix), diff-added shading (9% mix).

### Tertiary
- **Warn Yellow** (#e0a800, soft field rgba(245, 197, 66, 0.26)): warnings, offline/save states, search-match underlines, `mark`. Always a soft field or underline with ink text — never alarm-red.
- **Signal Red** (#c62f28, hover #a8241e): exists for exactly one button — "Delete your account". Nothing else destructive may use it.

### Neutral
- **Paper** (#fcfcfb): the page, the editor, menus, dialogs, inputs.
- **Paper-2** (#f4f4f5): the sidebar, history drawer, hover fill of primary controls' surroundings.
- **Paper-3** (#ebebed): pressed states, deepest tint.
- **Tint Hover / Tint Active** (#ececee / #e4e4e7): hover and selected fills for rows and ghost buttons (neutral, never blue, except the focused tree row).
- **Code Background** (#f1f1f2): inline code pills and code blocks (editor: `--mde-code-bg`).
- **Muted** (#62626a): small grey text and ghost icon buttons; ≥ 4.5:1 on paper, the tints, and the code background.
- **Grey** (#8b8b93): control borders only; ≥ 3:1 on paper.
- **Line / Line Soft** (rgba(24,24,27,0.12 / 0.07)): hairlines around raised surfaces, and the softer separators.
- **Stroke** (#d4d4d8, editor `--mde-stroke`): note-internal rules, table row lines, the 3px quote bar.
- **Marker** (#62626a): the note's collapsed-marker/reveal color and checked-task text.

### Named Rules
**The Ink Accent Rule.** Ink is the primary. Blue never colors a button, a badge, or a background field; it points (link, focus, selection, presence) and nothing else. On any screen, blue covers well under 10% of pixels.

**The One Red Rule.** Red appears exactly once in the product: the Delete-account button. Every other destructive action is a weight-600 menu item or an ink button. A design that adds a second red surface is wrong.

**The Hairline Rule.** Structure is drawn with 1px lines (solid or rgba ink at 7–12%), not with background fills. Tint fills are reserved for *state* (hover, active, selection), never for permanent layout.

## Typography

**Display/Head Font:** the platform face — San Francisco on Apple devices (its own size-specific tracking; the app sets `html.sysfont` to disable Inter's tuning there), else **Inter** (variable, SIL OFL, self-hosted woff2 with `font-display: swap`).
**Body Font:** the same face; UI and note text share it deliberately.
**Mono Font:** the system monospace stack (ui-monospace, SF Mono, Menlo, Consolas, Liberation Mono). IBM Plex Mono 400 exists solely for the landing page's footer.

**Character:** one humanist grotesque carrying everything from 10px gutter labels to 32px headings; hierarchy is made with weight (400 → 550 → 600 → 650/700), size steps, and negative tracking on large sizes. No second UI face, no uppercase shout.

### Hierarchy
- **Heading** (650, 22–24px, 1.25, -0.02em): dialog and empty-state headings; `--head-*` tokens.
- **Note H1** (700, 32px, 36px line, -0.024em) / **H2** (600, 24px, 30px, -0.02em) / **H3** (600, 18px, 24px, -0.01em) / **H4** (600, 16px, 22px) / **H5–H6** (600, 13px, 16px): the note's own scale, mirrored value-for-value in the Mac app (`docs/typography.md`); whole pixels everywhere.
- **Title** (500–600, 14–15px): breadcrumbs (500), commit titles (650 at 15px), history head (600).
- **Body** (400, 14px UI / 16px note, 1.45 / 1.6875): note body targets a comfortable measure — 840px max column with 40px top padding (24px/16px on phones).
- **Label** (600, 12px, 1.2, +0.005em, no uppercase): notebook names, section labels, table heads. Buttons are 550-weight 13px; link-buttons 550-weight 12.5px.
- **Micro** (550–650, 10–11px): presence "+N", badges, agent-badge, cursor labels (600, 10px).

### Named Rules
**The Sentence Case Rule.** No `text-transform: uppercase` anywhere (`--label-case: none`). Labels earn hierarchy with weight and size.

**The Whole-Pixel Rule.** Every size, line height, and padding in the note is a whole pixel so the web app and the Mac app put each line in the same place; UI keeps to whole-pixel line boxes for crisp header rows.

## Layout

One window-tall app shell, a three-column grid that collapses by removing columns:

- **Grid:** `sidebar (272px) | main (1fr) | history (380px, open only)`. Header row 52px inside each pane.
- **Note column:** max 840px, centred in the main pane; 40px top / 24px sides / 40vh bottom padding (phones: 24/16, same 40vh tail so the last line scrolls to a comfortable height). Lists indent 33px per level (the gutter, shared with bullets, heading labels, fold chevrons).
- **Wide blocks:** tables and code blocks grow from the column up to a cap (tables 1400px, code 1000px), centred on the column out into the margins, then scroll sideways inside themselves — the page itself never scrolls horizontally.
- **Breakpoints:** ≤ 900px the history drawer becomes a fixed right overlay; ≤ 640px the sidebar becomes a slide-in overlay (85vw max) over a 30%-ink backdrop, and participants/source badges drop out of the header; ≤ 520px the breadcrumb collapses to the file name and the save status truncates. Touch (`hover: none`) shows hover-revealed row actions permanently, quietly.
- **Rhythm:** compact and even — recurring gaps of 4/6/8/12px, sidebar padding 8–16px, `.pad` = 12px 18px. No card-in-card-in-card stacks; grouping is done with hairlines and tint fields.

## Elevation & Depth

Flat by default; shadow is reserved for things that leave the page. Resting rows, the sidebar, and the note are flat fields separated by hairlines and tint. Buttons carry only a 1px contact shadow (`0 1px 1px rgba(24,24,27,0.04)`).

### Shadow Vocabulary
- **Pop** (`--shadow-pop`: 0 1px 2px rgba(24,24,27,0.06), 0 6px 20px rgba(24,24,27,0.1)): menus, toasts, small floating panels.
- **Modal** (`--shadow-modal`: 0 2px 8px rgba(24,24,27,0.06), 0 24px 64px rgba(24,24,27,0.18)): dialogs, slide-in drawers (mobile sidebar/history), plus a rgba(24,24,27,0.3) backdrop.

### Named Rules
**The Floating Rule.** A shadow appears only when an element floats above the page (menu, modal, toast, drawer) or as a contact hair under a bordered control. Nothing else casts a shadow, and depth is never expressed with darker background fills.

## Shapes

Small, honest radii: 4px (chips, badges, small icon buttons, inputs' inner details), 6px (buttons, inputs, rows, code blocks, search field), 8px (menus, modals, large cards). Two deliberate exceptions: the slab logo is square-edged (the brand's one hard corner), and remote-cursor labels use asymmetric 3px radii that mirror their direction. Selection pills wrap across lines with `box-decoration-break: clone` and square inner corners — only the outer ends of a pill are rounded. Checkbox: 14px, 1.5px ink border, 3px radius, hand-drawn-feel tick. The tree, buttons and rows share the same rounded rectangle so the whole shell reads as one family of 6px rectangles inset from the edges.

## Components

### Buttons
- **Shape:** 6px radius, 32px tall (28px small, 40–46px for sign-in/CTA), inline-flex, 550-weight 13px label.
- **Secondary (default `.btn`):** paper fill, 1px `--line` border, contact shadow; hover darkens border to 18% ink and fills `--paper-2`; active `--paper-3`.
- **Primary (`.btn-primary`):** ink fill, paper text, ink border; hover pure black; active `--ink-2`. Danger inherits this shape in red (Delete account only).
- **Quiet (`.quiet-btn`):** borderless text button, underline on hover; in the sidebar it behaves as a row (tint hover, no underline).
- **Icon buttons (`.icon-btn`):** 24×24 (header/menu variants 28–30px), transparent, muted glyph, `--tint-active` fill + ink glyph on hover/open, 4px radius. Icon-only by design: **an `aria-label` is mandatory; there is no visible text and no hint text** — the glyph must carry the meaning.
- **Link buttons (`.link-btn`):** 12.5px muted text that darkens on hover.

### Icon-only actions (the standing pattern for new controls)
Hover-revealed row actions (rename, menu, add) sit beside/over the row's right edge, fade in on hover/focus, and are **always visible on touch** (`hover: none`) at reduced color. New icon-only controls follow this exactly: muted at rest, ink on hover, tint fill when open, `aria-label` always, `title` allowed, visible text never.

### Inputs / Fields
34px tall, 6px radius, 1px `--grey` border on paper; hover darkens the border; focus turns it blue with a soft blue ring (3px, 22% blue, no outline). Placeholders are muted. Checkboxes/radios use `accent-color: ink`. In-dialog bare inputs drop their border entirely (search files).

### Menus
Fixed-position, min-width 184px (max `min(320px, 100vw−16px)`), 8px radius, paper fill, `--line` hairline, pop shadow, 100ms pop-in. Items 30px tall, 13.5px, 4px-radius hover fill; focus-visible gets an inset 2px blue ring. Destructive items are last, after a separator, set apart by **weight 600 — never red**. Section headers 11.5px muted.

### Dialogs
Native `<dialog>`; width `min(440px, 100vw−32px)` (variants 520–620px), 8px radius, hairline, modal shadow, 0.3-ink backdrop, 140ms rise-and-fade in. Head 650-weight 16px; body a 14px column with 14px gaps; actions right-aligned (`modal-actions`).

### Tree rows (sidebar)
28px minimum, 6px radius, inset 8px from the sidebar edge, 14px-per-level indent. Hover `--tint-hover`; the open note `--tint-active` + 600 weight; while the tree holds focus the current row takes a **blue** 18% tint (the one blue field). Hover-only row buttons fade in (always-on for touch). Labels are the 12px/600 label style for notebooks, 14px for files.

### Toasts
Centered bottom, ink-inverted pill (8px radius, pop shadow, paper text, 13px), optional 7px yellow dot for errors, optional ghost action button. 180ms rise in, fade-and-drop out.

### Badges & presence
Badges: 4px radius tinted chips, 10.5px/550. Avatars: 26px squares (4px radius) or 20px circles in the account row, initial-filled with a per-person color, white 650-weight initials; agents get an inverted mini-badge; guests a dashed ring. Presence dots: 7px rounded squares in the person's color; agents are outlined instead of filled. Remote cursors: 2px colored carets with name labels in the person's color, shown briefly after movement; drag/upload markers use the system blue (#007aff).

### Signature Component — the live-markdown editor (`.mde`)
The product itself. One column of real text where markers collapse and reveal: pipes, fences, and `**` stay invisible until the caret is on their line; bullets are drawn 5px squares; headings show a tiny muted "H1…H5" gutter label only on the active line; quotes get a 3px vertical bar 12px into the gutter with lightened text; tables align as real tables with collapsed pipes; code blocks sit on `--mde-code-bg` with 6px radius; inline code is a 0.875em pill with square inner corners; tags render as small tinted chips. Images render inline below their line, up to 480px tall, and collapse their source. Fold chevrons (10px, muted) live in the gutter left of heading labels, visible on hover/active/when folded; a folded section ends in an "…" pill. Remote carets, drop markers and line-author names (muted 11px at the pane's left edge) overlay the text without ever shifting it. `.mde.readonly` strips all editing affordances (pencils, chips) — this is the foundation for the upcoming read mode. Note tokens live in one block (`--mde-*`) and must match the Mac app value-for-value.

## Upcoming Features (design direction for this fork)

All four features inherit everything above: ink-on-paper tokens, 4/6/8 radii, icon-button pattern, hover-revealed actions with always-visible-on-touch fallback, and the no-explainer-text hard rule. Nothing here introduces a new color, a new radius, or visible helper copy.

### 1. Dark mode toggle (persisted)
- **Approach — token inversion, one source of truth.** Both stylesheets already route every color through custom properties (`:root` in `app.css`; `.mde` in `editor.css`). Dark mode is a `[data-theme="dark"]` (or `class="dark"` on `<html>`) override block redefining those same tokens — no component-level colors anywhere. Editor tokens that duplicate shell values (`--mde-bg` = paper, `--mde-code-bg` = code-bg) should be re-pointed at the shell tokens as part of this work so dark falls out automatically, while preserving whole-pixel sizes (those don't change with theme).
- **Palette — same neutrals, inverted luminance (provisional values, verified ≥ thresholds):** paper #1a1b1e, paper-2 #222327, paper-3/tint-hover #2a2b30, tint-active #33343a, code-bg #232428; ink #e6e6e9 (13.8:1), ink-2 #c6c7cc (10.2:1), muted #93949d (≥ 5.1:1 on paper, paper-2 and code-bg — holds the ≥ 4.5 rule), grey #6d6e78 borders (3.4:1 ≥ 3), line rgba(255,255,255,0.14), line-soft 0.08. Blue lightens for dark ground: **#6aa9d6** (6.8:1 as link text; keep 22%/18% mixes for rings and tree focus). Warn stays #e0a800 (yellow reads well on dark) with warn-soft at ~0.18 alpha; red lightens to #e5605a (5.1:1). Shadows become deeper and slightly stronger; the toast flips to paper-on-ink *stays inverted* (light fill, dark text) so it still reads as the inverted element. Verify each pairing at implementation time; the table above is direction, not license to skip the check.
- **Toggle & persistence.** Persisted in `localStorage`; applied by a tiny inline snippet in the document head **before first paint** (the app already has a splash/no-flash first-load path, `docs/08-first-load.md`) — a wrong-theme flash is a defect. Default follows `prefers-color-scheme` until the user picks explicitly. The control is an **icon-only** button, placed in the account menu (the shell's settings surface) — one item, no label text beyond the menu row's own word, no explanation.
- **Scope:** the app, dialogs, history, editor and toasts. The marketing landing page keeps its own art direction and stays light.
- **Constraint:** `docs/typography.md` parity with the Mac app's `theme.rs` applies to the note's colors. Dark mode must either be mirrored into `theme.rs` or accepted as a documented divergence — decide before shipping (open question, flagged in PRODUCT.md).

### 2. View mode toggle (read-only rendered note)
- **Behavior.** Read mode renders the note with no text cursor: the existing `.mde.readonly` state (built for GitHub copies) is the foundation — collapsed markers, no caret, no pencils/chips. It must be genuinely inert: no text insertion, no accidental checkbox toggles; checking a task is an *edit* and requires switching to edit mode. This keeps "reading can never mutate the file" absolute.
- **Default mode.** Read mode by default on coarse-pointer/small-viewport devices (the keyboard-avoidance case this feature exists for); edit mode by default on fine pointers. The choice is a device default, not a per-note setting.
- **Toggle.** One icon-only button in the note header (eye ⇄ pencil family), `aria-pressed`, next to the existing header controls — the same 24px ghost icon-button pattern. No label, no hint.
- **Multiplayer:** other people's cursors, presence and edits remain fully visible in read mode (multiplayer is ambient); only *your* editing affordances disappear. Remote cursors still render on the read-only note.
- **Mobile behavior:** scrolling a note in read mode never summons the keyboard; a tap does nothing but position focusable scroll (and long-press may offer the system text-selection, which is read-only by nature). Switching to edit is the intentional act that brings the keyboard.

### 3. Inline comments (blockquote-style, plain Markdown)
- **Format convention (decided): a comment is a blockquote line tagged with the existing `#comment` tag**, e.g.
  `> #comment What happened to the third step?`
  Rationale: it is ordinary Markdown (principle 1 — the file is the feature), renders everywhere including the Mac app, GitHub and `curl`, agents can `grep` it, and it needs zero new syntax. Visually it lands on the editor's existing quote treatment — 3px bar, `--mde-text-light` text — which already sets it apart from body text; the `#comment` tag renders as the existing muted tag chip, distinguishing a comment from a genuine quotation. (Alternative considered and rejected for now: GitHub-alert-style `> [!comment]` — reads as a directive, not prose, and would need its own renderer everywhere Grim's Markdown travels. Revisit if comment volume grows features: threads, resolution, etc.)
- **Desktop interaction.** Hovering a line shows a subtle icon-only button (speech-bubble family) at the line's right edge — the exact pattern of the sidebar's hover-revealed row actions: fades in on hover/focus-within, tint fill on hover, muted at rest, never shifting the text (overlay, like the author-names layer). Clicking inserts the blockquote-tagged line at/after that line and places the caret inside it (this is an edit: it goes through the normal Yjs/engine edit path and becomes a normal collaborative edit with cursor, history, and agent visibility).
- **Visual treatment.** No new styling machinery: the comment is a quote line whose tag chip marks it. If a per-theme accent is ever wanted (e.g. warn-soft quote bar for comments), it must be a new token pair in both stylesheets, not an inline style.
- **Mobile behavior.** No hover exists and taps must never cause surprise edits: a **long-press (~500 ms) on a line** is the primary comment path — an intentional hold, not a tap. Everything that isn't a hold cancels it (a scroll — more than a few px of drift before the timer, a second finger/pinch, lifting early), and the hold's system menu is suppressed on the note's surface (no context menu while a finger is down, no text-selection callout on the note only). It opens the same inline input at the pressed line: in edit mode directly; in read mode the hold switches to edit at that line first, since a hold is as intentional as the header toggle. The header's comment icon (always visible in edit mode on touch, ≥ 24px hit area — the same always-on-for-touch rule as row actions) remains the secondary path: it comments the caret's line. Opening the input is the intentional keyboard moment; in read mode otherwise, comments are simply rendered (they're part of the note). No swipe gestures, nothing accidental.

### 4. Icon-only buttons
- **Standing rule:** every new control in this fork is icon-only, in the `.icon-btn` family — 24px ghost (28–30px in header/menu slots), muted glyph at rest, `--tint-active` + ink on hover/open, 4px radius, `aria-label` mandatory, `aria-expanded`/`aria-pressed` where stateful.
- **Glyphs are drawn, not imported:** inline SVG strokes (13–15px, `currentColor`, 1.5px stroke like the fold chevron) or CSS-drawn shapes (the burger, the plus, the chevrons). No icon font, no emoji-as-icon, no text label beside the icon (the existing hard rule).
- **Placement:** the note header (right of the save status/participants, mirroring the existing "⋯" ghost button), row actions, and menus — never a new floating toolbar; integrate into the existing surfaces.
- **Discoverability without words:** because hint text is banned, icon choice must be conventional (eye/pencil for modes, speech bubble for comments, half-moon/sun for theme) and each gets a `title` tooltip as the only affordance aid. If an icon can't be chosen that a first-time user reads correctly, the control's placement — not a caption — must fix it.

## Do's and Don'ts

### Do:
- **Do** route every new color through a token in both `app.css` and the `.mde` block; if a value can't live in a token, it's probably not a value this system wants.
- **Do** keep text ≥ 4.5:1 and control borders ≥ 3:1 against their actual surface (muted sits on paper, tints *and* the code background — check all three).
- **Do** use hover-revealed controls with an always-visible state on `hover: none` devices.
- **Do** draw icons with currentColor SVG/CSS at 1.5px stroke weight and give every icon-only button an `aria-label`.
- **Do** keep the note's whole-pixel scale intact and check any token change against `docs/typography.md` and the Mac app's `theme.rs`.
- **Do** keep new floating surfaces in the existing shadow vocabulary (pop or modal) and new corners in 4/6/8.

### Don't:
- **Don't** put explainer, hint, or caption text in the UI — ever. No "Click here to…", no empty-state tutorials, no onboarding coach marks. If a control needs a caption, redesign the control.
- **Don't** add a second red surface or use red for destructive menu items (weight 600 on ink is the pattern); red is Delete-account only.
- **Don't** use blue as decoration, background field, or button fill; blue points, it doesn't paint.
- **Don't** uppercase labels or introduce a second UI typeface.
- **Don't** widen the page with content (wide blocks scroll inside themselves) or let an overlay element shift note text by a pixel.
- **Don't** add shadows to resting, non-floating elements, and don't express depth with darker fills.
- **Don't** invent spacing values outside the recurring 4/6/8/12/16/20 rhythm or a new radius step.
