# Shop+ CMS UI Revamp

UI revamp of the RCTI+ Shop+ CMS: one guided flow to put Shopee products on a TV show.

## Folders

| Path | What |
| --- | --- |
| `docs/plan-of-action.md` | Plan, scope, backlog, open questions (snapshot of the live doc) |
| `docs/design-system.md` | Locked v4 theme: colours, type, layout, components, behaviour rules |
| `research/` | Client screenshots and meeting notes. Kept private, not in this public repository |
| `design/html/v4/` | **Current design.** Static HTML screens |
| `design/html/assets/` | RCTI+ logo and R+ icon |
| `design/html/` (root), `v2/`, `v3/` | Earlier directions, kept as archive |
| `design/canvas-source/` | Original Claude design canvas files (`.dc.html`), for reference |

## Preview the current design (v4)

Live link (GitHub Pages): https://shravank-uiux.github.io/rcti-_shop-_cms_revamp/


Serve `design/html/` (for example VS Code → **Open with Live Server**, or `python3 -m http.server 5500` in that folder) and open `v4/index.html`.

| Page | What it shows |
| --- | --- |
| `v4/index.html` | Dashboard: stats, schedule by channel (live blocks show the product on screen), drafts with delete, needs attention, catalogs with hover actions |
| `v4/catalogs.html` | All catalogs: status tabs with counts, search, filters (content type, channel, brand, owner), sort, table with row actions, bulk Duplicate / Take off air / Delete with confirmations. `#live`, `#draft` etc. open a status tab |
| `v4/new.html` | New catalog, one step per screen: Basics (name, brand) → Starting point → Products (Shopee search, paste links, manual, Excel; selected count; viewer limit) → Where it airs → Review. Live preview: summary card and a mini phone |
| `v4/builder.html` | Builder: drag-and-drop product order, live phone preview, settings tabs, Add products drawer (Shopee, paste links, manual, Excel). "Demo role" switches Editor / Publisher. `#golive` plays the publish check, `#add-manual` opens the drawer, `#review` opens Review changes as a publisher |
| `v4/shop-panel.html` | Viewer preview: Live TV & events, Stories & Short+ and Web, each as watching → browsing → deciding; theme switch (RCTI+ Night, Paper, Festive, Newsroom). `#vod`, `#web` open a tab |

- Sidebar: product switcher at the top (Home, Video, Interactive, Shop+, Ads, Settings), then Dashboard, Catalogs (was Event), Homepage Shop+, and folded groups Partners, Library and Settings. The fold button shrinks it to icons and the choice is remembered.
- Every v4 page has a quick tour: it opens once on first visit, and the **?** button at the bottom of the sidebar (or `#tour` on the URL) replays it. To see the first-visit prompt again, clear the site's local storage.
- Theme and language are remembered per browser. Add `?theme=dark` or `?theme=light` to any link.
- Sample data uses names from the walkthrough; `[price]`, `[date]` and similar are placeholders.

## Archive

| Folder | Direction |
| --- | --- |
| `design/html/index.html` + `step1–4` | First pass: classic sidebar and 4-step wizard |
| `design/html/v2/` | Editorial light / control-room dark, top bar, EN/ID, roles |
| `design/html/v3/` | "Studio": app frame, channel monitor wall, ⌘K, go-live check |

## Live links

- Plan doc: https://claude.ai/artifact/6caiwybkPskHAHKrpQQAkp
- Design canvas: https://claude.ai/artifact/5EAGDcGrCTvRVNQBvghnNM
