# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

(A native Mac app shares the product and its design language, token for token; this record governs the web app, which is where all fork work happens.)

## Users

- **People writing notes together**: two to ten people per note — pairs planning a trip, small teams keeping a running doc, a person and their AI agent. They open a link and type; there is nothing to set up and no mode to learn. Mobile is a first-class surface: much reading and editing happens one-handed on a phone.
- **Agents**, invited by URL or MCP: they read and edit the same live notes, show up as participants with their own cursor, and commit like people do.
- **Self-hosters**, who run Grim on their own machine or server for privacy. The product must stay excellent with sign-in off and no outside services.

## Product Purpose

Grim is a multiplayer Markdown notebook. Open a note and start typing: everyone who has it open sees your words and your cursor live. Every note is a plain Markdown file in a Git repo — saved automatically a few seconds after you stop typing, with full History — so nothing is ever locked in. Success is a reader becoming a writer within seconds of opening a link, and nobody ever worrying about the save button, the format, or the sync.

## Positioning

The storage format *is* the product: the thing you edit in the browser is the exact `.md` file in a Git repo, live and multiplayer, and the same URL a person opens is a working API for an agent. A competitor can copy collaborative editing or copy Markdown; copying "the editor renders and edits the literal Git file, and the agent's shell is the same URL" means adopting the whole architecture.

## Operating Context

- **Hosted (grimnotes.app):** Cloudflare Workers; workspaces are public by link; Google/GitHub sign-in (guests read and edit); a public demo workspace partitioned into rooms of ≤ 10 people that reset on a timer.
- **Self-hosted:** one Bun process, notes in local Git repos, sign-in off by default (everything shared), behind the owner's own network.
- **Mac app (experimental):** the same notes in a native window (Rust + Rune); it shares the editor engine and must match the web's note typography value for value (`docs/typography.md`).
- **Agents:** a workspace's URL is a bash shell over its live notes; MCP covers all of someone's workspaces. Agent commits are kept apart from people's.
- **Sharing ritual:** a note's URL *is* the share link. Workspaces are organized into folders; `Ctrl/Cmd+P` searches files.

## Capabilities and Constraints

- Live multiplayer editing with per-person cursors and presence; edits commit to Git after 3 s of quiet; History restores any version.
- Live-preview Markdown editor: markers (`**`, `> `, pipes) stay collapsed unless the caret is on that line; headings, tables, code blocks, images, checkboxes, tags, highlights all render in place. The engine is Rust compiled to WebAssembly, shared with the Mac app; if it fails, the note falls back to read-only text.
- Stack: Bun + TypeScript, no frontend framework (DOM + Yjs CRDT), client in `src/client`, styles in `src/client/app.css` (app shell) and `src/client/editor-rs/editor.css` (note editor). This is a **fork** of `anomalyco/grim` on branch `features/ui-modes`; production runs from a separate checkout, which fork work must never touch.
- **Hard UI rule from the product owner: no explainer or hint text in the UI, ever.** Controls are minimal and self-explanatory; if a feature needs a caption to be understood, the design is wrong. (Inferred boundary, labeled: invisible accessibility labels — `aria-label`, `title` tooltips — are not UI text and remain required.)
- Performance constraints from `docs/08-first-load.md`: the first view must paint in one frame within a 3 s boot cap; no feature may add blocking work to first load.
- Theme parity: the note's type and colours are mirrored value-for-value in the Mac app's `theme.rs`; web-only visual changes to the note must either be mirrored there or explicitly accepted as divergence (an open decision for dark mode; see Upcoming Features).
- Explicitly undecided product facts: none beyond the per-feature open questions listed under Upcoming Features.

## Brand Commitments

- **Name:** Grim. **Logo:** the slab — a square-edged, ink-inverted block of Inter 800, the one deliberately un-rounded element in the UI.
- **Voice:** plain, warm, short sentences. Sentence case everywhere; no uppercase labels.
- **Look:** paper and ink with neutral tints; blue reserved for links and focus; soft warm yellow for warnings; red only for deleting an account. Icons are drawn (CSS borders, inline SVG), never icon-font glyphs with text labels beside them.
- **Feel:** native-app quality in a browser — whole-pixel layout, platform fonts (San Francisco on Apple devices, Inter elsewhere), no font-smoothing override.

## Evidence on Hand

- `README.md` and `docs/` (architecture, typography, self-hosting, agent API) — real, maintained documentation.
- The live implementation itself: `src/client/app.css` (~2,700 lines, heavily commented), `src/client/editor-rs/editor.css`, `docs/typography.md` (the note's shared type/colour table with contrast ratios).
- The landing page with hand-drawn pencil bots (`src/client/landing/`), in production at grimnotes.app.
- Absence to respect: no marketing copy, testimonials, or benchmarks exist and none may be invented; there is no dark mode, view-mode toggle, or comment feature in the incumbent code yet.

## Product Principles

1. **The file is the feature.** Everything on screen maps to real Markdown and real Git history; no representation may drift from the file.
2. **Quiet by default.** The interface recedes: ink on paper, hairlines, no chrome that doesn't act. Expression lives in precise details, not decoration.
3. **Nothing to learn.** Opening a link is onboarding. Any control that needs a hint violates the no-explainer rule; make it obvious or cut it.
4. **Multiplayer is ambient.** Other people's cursors, presence and commits are always visible and never interrupt.
5. **Native-quality discipline.** Whole pixels, platform fonts, keyboard paths, touch behaviour thought through — browser app, desktop craft.

## Accessibility & Inclusion

- Visible `:focus-visible` treatment on every interactive element (2px blue outline); icon-only buttons must carry `aria-label` (and `aria-expanded` where they open menus).
- Text contrast is maintained by token: small grey text ≥ 4.5:1, control borders ≥ 3:1 against their surfaces — any new palette must hold the same ratios (verified for the proposed dark palette; see DESIGN.md).
- Touch is a primary target: hover-revealed controls must also be reachable without hover; mobile must never force a software keyboard on someone who only wanted to read or scroll.

## Upcoming Features (this fork)

Design direction lives in DESIGN.md (§ Upcoming Features); the product truth and constraints for each:

1. **Dark mode toggle (persisted).** A user choice, remembered per device; the app must not flash the wrong theme on load, and the note editor's tokens must flip with the shell. Open decision: whether dark tokens are mirrored into the Mac app's `theme.rs` (preserving documented parity) or accepted as a web-fork divergence.
2. **View mode toggle.** A read-only rendered note with no text cursor: mobile users can scroll and read without the keyboard popping up; editing requires an intentional action. The read-only editor state already exists (`.mde.readonly`, used for GitHub copies) and is the foundation. Open decision (decided here, confirmable): default mode is read on small/touch screens and edit on desktop pointers; the toggle itself is one icon button in the note header.
3. **Inline comments.** On desktop, hovering a line shows a subtle icon button; clicking inserts an ordinary Markdown edit that renders visually set apart (blockquote style). It must be plain Markdown in the file (principle 1), readable by agents and other Markdown tools with no new syntax. Mobile gets an intentional, hover-free path that never opens the keyboard by accident.
4. **Icon-only buttons.** New controls are icon-only, integrated into the existing header/row-action patterns, each with an invisible `aria-label`. This is a standing constraint on all four features above, not a separate screen.
