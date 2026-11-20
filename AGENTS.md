# Project context for Codex

- Goal: redesign the RCTI+ Shop+ CMS (Shopee product catalogs shown in the live TV player).
- Read `docs/plan-of-action.md` first; `research/` describes the current system.
- The design direction is locked: build new screens in `design/html/v4/`, following `docs/design-system.md`. `design/html/` (first pass), `v2/` and `v3/` are archive for reference only.
- Screens are static HTML, one self-contained file per page: tokens and styles in a `<style>` block, behaviour in an inline `<script>`. No frameworks or build step unless asked. Google Fonts and files in `design/html/assets/` are the only external resources.
- Keep the status vocabulary: Draft, Scheduled, Live, Ended.
- UI copy ships in English and Bahasa Indonesia via the EN / ID switch; write English in the markup and add the Bahasa string to the page's `ID` dictionary.
- Do not invent prices, dates or counts; use `[placeholder]` text.
- Destructive or viewer-facing actions go through the shared confirmation dialog.
