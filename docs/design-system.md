# Shop+ CMS design system (v4, locked 18 Nov 2026)

The reference build is `design/html/v4/`. New screens copy its tokens and components. If this file and v4 disagree, v4 wins and this file gets updated.

## Colour tokens

Every colour is a CSS variable. Light is the default; dark comes from the theme switch or the OS setting, and `?theme=dark` forces it.

| Token | Light | Dark | Use |
| --- | --- | --- | --- |
| `--bg` | `#E9ECF1` | `#050608` | Backdrop behind the sidebar and canvas |
| `--canvas` | `#FFFFFF` | `#0D0F14` | Main content sheet, cards, dialogs |
| `--panel` | `#F6F7F9` | `#12151B` | Section headers, inputs, quiet fills |
| `--hover` | `#F0F2F5` | `#171B22` | Hover fill |
| `--line` / `--line-2` | `#E2E5EB` / `#D2D7DF` | `#1E222A` / `#2A2F39` | Dividers / control outlines |
| `--ink` / `--ink-2` | `#0C1016` / `#2C3440` | `#F1F3F6` / `#C8CED8` | Main text / secondary text |
| `--muted` / `--faint` | `#5D6877` / `#8A94A3` | `#8B95A4` / `#646E7C` | Helper text / labels and axis text |
| `--brand` | `#0E74B5` | `#0E74B5` | RCTI+ blue (the logo's blue, darkened so white text passes 4.5:1). Primary buttons, avatar, brand moments |
| `--brand-red` | `#D71E55` | `#D71E55` | The red of the logo's "+". Also the Live status colour |
| `--primary` | `#0C1016` | `#F1F3F6` | Neutral selected states only (active pills, current step, toast). Not for buttons |
| `--accent` | `#0E74B5` | `#5CB8EE` | Links, focus ring, info |

Status colours, each with a `-soft` background:

| Status | Token | Light | Dark |
| --- | --- | --- | --- |
| Live | `--live` | `#D71E55` | `#FF5C82` |
| Scheduled | `--sched` | `#0B6F8C` | `#4FCBEE` |
| Waiting for approval | `--warn` | `#955700` | `#F4BB52` |
| Draft | `--draft` | `#4A5361` | `#B0B7C2` |
| Done / OK | `--ok` | `#137A3E` | `#4FD493` |
| Ended | outline chip, `--muted` text | | |

Status vocabulary stays **Draft, Scheduled, Live, Ended**. "Waiting for approval" is a label on a Draft or on pending changes, not a fifth status.

## No decorative gradients

Colour comes from the RCTI+ identity: blue for actions, the "+" red for Live, neutrals for everything else. No gradient buttons, gradient text, glow blobs or gradient borders. Gradients are allowed only as stand-ins for real images (product photos, video frames) and for hatching patterns.

## Type

- **Schibsted Grotesk** 400–800 for everything. Page title 34px/700, tracking −0.035em. Section title 16px/700. Body 14px/1.5.
- **JetBrains Mono** 400–500 for times, counts, IDs and keyboard hints.
- Numbers in stat cards: 34px/700, tracking −0.04em.

## Shape and spacing

- Radii: canvas 20px, cards and sections 16px, buttons and inputs 10–12px, chips fully round.
- Canvas padding 32px (16px on phones). Gap between sections 24px.
- Depth: `--shadow-sm` on resting cards, `--shadow` on hover and on dialogs. No heavy drop shadows elsewhere.

## Layout

- **Sidebar** (236px, folds to 68px icons; the choice is remembered). Powder matte blue panel (`--side` #E3ECF6 light, #0F1824 dark) so navigation reads apart from the white content; the current page is a white chip with blue text. RCTI+ wordmark and a product switcher at the top, then Dashboard · Catalogs · Homepage Shop+ · Partners ▾ · Library ▾ · Settings ▾. User, language, theme and fold at the bottom. Folded shows the R+ icon and hover labels.
- **Search** lives in the page header: a wide field on the dashboard, a search icon button (⌘K) on other pages. Not in the sidebar.
- **Page header status**: live status and "saved" sit with the title (status chip next to the name, saved note on the line above), never as loose items in the middle of the header.
- **Canvas**: one rounded sheet on the backdrop. Page header (eyebrow, title, actions on the right), then sections.
- **Builder**: three panes inside the canvas: products 340px, live preview on a dotted "studio floor", settings 360px with tabs.
- Hidden below 760px for the sidebar; the canvas goes edge to edge.

## Components (see v4 for markup)

| Component | Rules |
| --- | --- |
| Button | Primary (solid RCTI+ blue), default (outlined), quiet (no outline), red (destructive). 40px; 32px small. |
| Chip | Status chips use the tokens above, with a dot for Live. |
| Stat card | Icon tile, label, big number, one-line caption. "Live now" gets a Live-coloured edge. |
| Section | Rounded card with a `--panel` header row: title, optional caption, actions right. |
| Schedule | One lane per channel, hour grid, NOW line, past hours hatched. Live blocks show the product on screen. |
| Catalog card | Product mosaic, status chip top-left, title, show · channel, owner and product count. |
| Hover actions | Appear on hover and keyboard focus, always visible on touch screens. Never the only way to reach an action. |
| Tabs | Underlined text tabs, with a green (done) or amber (needs attention) dot. |
| Stepper | One step per screen, numbered circles joined by a line that turns green. Continue / Back. |
| Dropdown | Never the browser's own list. Field matches inputs, chevron with 14px right padding; themed list with a tick on the current value and an optional tag on the right. Long lists get search; lists users add to (brands) get "+ Create … “name”" at the bottom. Opens upward when there's no room below. Keys: ↑/↓, Enter, Esc, type-to-jump. |
| Live preview | Phone frame in the RCTI+ Night theme; updates as the user types or picks. |
| Drawer | Slides in from the right for multi-step side tasks (Add products). |
| Confirmation | Shared `ask()` dialog: icon, title, what happens, optional warning and note. Red for destructive (focus on Cancel), dark for go-ahead. |
| Toast | Bottom centre, 4 seconds, plain sentence. |
| Command bar | ⌘K. Searches catalogs, programs, actions and other CMS menus. |

## Behaviour rules

- **Content types**: "Where it airs" follows the content type. Live TV = channel + program (schedule lanes). Live event = pick an event with its own start/end (its own "Live events" row in the schedule). Stories / Short+ = pick one video or a whole series from vertical thumbnails, then "Until I take it off" or "Between dates" (listed under **On demand**, never on the schedule). The preview phone switches to a full-screen vertical video with a Shop pill for Stories and Short+.
- **Quick tour**: each page has 4–7 steps (welcome card, then a highlight + card per area, with step dots, Back/Next/Skip, ← → Esc). Opens once per page on first visit, replayable from the sidebar **?** button or `#tour`. Steps whose area isn't visible are skipped. Keep step text to two sentences.
- **Help text**: no instruction boxes. A field may have one short grey line under it; anything longer goes in an ⓘ next to the label (shows on hover, keyboard focus or tap). Warnings that prevent mistakes (manual products, conflicts) stay visible but kept to one sentence.
- **Inline edit**: titles that can change (the catalog name in the builder) are editable in place: hover shows a pencil, click to type, Enter saves, Esc undoes, empty isn't allowed.
- **Autosave** everything; show "Saved just now". Unfinished work appears in Continue where you left off. There is no autosave toggle and no separate Save button.
- **Leaving a flow**: one button, top right. While nothing is entered it reads **✕ Cancel**, leaves at once and creates no draft (the Draft chip and "Saved" status stay hidden too). Once anything is entered it becomes **🕒 Finish later** and asks "Leave this catalog?" with **Keep draft and exit** (primary, focused), Cancel, and **Delete draft** (red, set apart on the left).
- **Confirm** anything destructive, irreversible or viewer-facing: delete, take off air, submit, publish, restore, discard unsaved picks, imports. Don't confirm autosaved or easily undone edits.
- **Roles**: Editors submit, Publishers approve and publish. Anyone on duty can take a catalog off air.
- **Sample data**: screens show realistic sample names, prices (`Rp 649.000`), times and counts, labelled "Sample data" in the sidebar. A product keeps the same name, price and rating everywhere; summary counts match the lists they summarise.
- **Header tint**: page headers sit on a faint brand-blue band (`--head-tint`) with a line below, so each page opens with a hint of RCTI+ colour.
- **Motion**: 150–300ms, ease-out; every animation is switched off for `prefers-reduced-motion`.

## Language

EN / ID switch on every page, remembered per browser. UI strings sit in a per-page `ID` dictionary; English is the markup. Allow about 25% extra length for Bahasa. The Bahasa copy is a first draft and needs a native-speaker review.

## Accessibility

Visible focus ring (`--accent`), labelled icon buttons, 4.5:1 text contrast in both themes, keyboard paths for drag-and-drop (arrow keys on the handle) and for hover actions (focus).

## Assets

- `design/html/assets/rcti-plus-logo.png`: RCTI+ wordmark, open sidebar.
- `design/html/assets/products/`: free Unsplash photos standing in for Shopee product images (sources in `CREDITS.md`; no photos with visible third-party brands). Mapped to the thumbnail classes `t1`–`t7` and `tx-*`, and `v1`–`v6` for vertical video stand-ins.
- `design/html/assets/RCTI+_Icon.svg`: R+ icon, folded sidebar and browser-tab icon. Link as `RCTI%2B_Icon.svg`.
