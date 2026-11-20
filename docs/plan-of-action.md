# Shop+ CMS UI Revamp: Plan of Action

Exported Nov 17, 2026. Live version: https://claude.ai/artifact/6caiwybkPskHAHKrpQQAkp

## Context and goal

We are revamping the UI of the RCTI+ Shop+ CMS so one person can put Shopee products on a TV program in one guided flow, in one tool.

- **Source:** recorded Zoom call "Shop+ Walkthrough & UI/UX discussion" (39 min). The client’s product owner demoed the CMS; a tracking specialist explained tracking.
- **Client ask:** a UI revamp of the CMS. The call was a walkthrough only; no page-by-page change list was given.
- **Next client touchpoint:** UI/UX session at 10:00 Jakarta time, scheduled by the client’s project lead.

## Current state

Today, putting products on one show takes nine stages across two separate CMSes, with a URL copied by hand between them.

| Module | Where | Pages shown |
| --- | --- | --- |
| Catalogue CMS | cms-interactive.mncplus.com | 21 |
| Interactive CMS | cms.mncplus.com → Master Activity Interactive | 8 |
| Viewer app | rctiplus.com, m.rctiplus.com | 4 |

1. Create brand and category (master data).
2. Create the catalog (Add Event: title, six color fields, brand, options).
3. Add products from Shopee, or manually / by Excel.
4. Assign the catalog to a channel and program, with limit, random order and Tags 1–5.
5. Copy the Embed URL from View Event.
6. In the second CMS, create an activity and paste the URL.
7. Turn it on in Interactive Action.
8. Check the live player (DevTools, incognito when the cache misleads).
9. Read sales by tag in Shopee's affiliate portal, outside the CMS.

Main problems: two tools for one task; unlabeled tracking tags; no preview or live status; unclear concepts (brands, Type, Embed); inconsistent UI (two styles, mixed languages, icon-only actions, long modals); no results in the CMS.

## Target experience

1. **Catalog:** name, brand and a theme preset with live preview.
2. **Products:** pick from Shopee with a selection tray, then reorder and pin.
3. **Placement:** channel, program from an EPG picker, start/end time, product limit, labeled tracking (Platform, Program, Campaign).
4. **Review and go live:** phone preview of the Shop panel, then one Go live button.

Go live creates and switches on the interactive activity behind the scenes. If the CMSes cannot merge, the new UI calls the Interactive CMS's API instead.

Design principles: speak the admin's language; show, don't describe; one status vocabulary (Draft, Scheduled, Live, Ended); full pages for work, modals for confirmations; one design system and one language setting.

## Scope

| Area | Pages | Scope |
| --- | --- | --- |
| Catalog list | Event list | In scope |
| Catalog create and edit | Add event, event edit, view event | In scope |
| Product picker | Add Shopee product | In scope |
| Placement | Assign catalogue, assignments table | In scope |
| Master data | Brands, product category | In scope |
| Activation | List / add / edit activity, interactive action | In scope; may be absorbed into Go live |
| Manual products | Add product, Upload Excel | Confirm |
| Viewer Shop panel | Live player, Shop panel | Confirm |
| Not demonstrated | Dashboard, Homepage Shop+, Master Partnership, Partner, Type, Embed, Affiliate, Polling | Confirm |

## Feature backlog

| Feature | Problem it solves | Phase |
| --- | --- | --- |
| Single guided flow with Go live | Two tools, URL pasted by hand | Phase 1 |
| Live phone preview (iOS, Android, Web, MWEB) | Verifying needs DevTools | Phase 1 |
| Labeled tracking fields with presets | Tags 1–5 are unreadable | Phase 1 |
| Drafts and one status vocabulary | Only active / inactive today | Phase 1 |
| Drag to reorder and pin products | Only random order today | Phase 1 |
| Shopee sync health per product | Price, stock changes go unnoticed | Phase 1 |
| Filters, saved views, bulk actions | About 1,587 catalogs, search only | Phase 1 |
| Duplicate catalog and conflict warning | Rebuilding recurring shows | Phase 1 |
| Scheduling linked to the EPG | Catalogs switched by hand | Phase 2 |
| Performance dashboard (Shopee affiliate data) | Results live outside the CMS | Phase 2 |
| Live control panel (push / pin on air) | No way to match the moment | Phase 2 |
| Product suggestions | Curation is fully manual | Phase 2 |
| Catalog templates | Repeated setup | Phase 2 |
| Roles, approvals, activity log | No record of who changed what | Phase 2 |

## Plan of action

Phases: Discovery (done) → Foundations → **Core flow** → Supporting pages → Hand off.
Gates: UI/UX session (after Discovery), client sign-off (after Core flow).

**Discovery**
- [x] Analyse the recording and write the summary
- [x] Capture all 33 screens by module
- [x] Map the current flow and admin journey
- [x] Write this plan

**Foundations**
- [ ] Run the UI/UX session and answer the open questions
- [ ] New sitemap
- [ ] Design system: colors, type, spacing, table, form, picker, status chips, toasts
- [ ] Status vocabulary

**Core flow**
- [x] First pass: catalog list + 4 steps (see design/)
- [ ] Client review of the core flow

**Supporting pages**
- [ ] Brands and categories, with inline creation
- [ ] Activation screens, only if the CMSes cannot merge
- [ ] Empty, loading and error states
- [ ] Tablet and small-laptop layouts

**Hand off**
- [ ] Clickable prototype
- [ ] Usability check with the client's team
- [ ] Component specs and developer handoff

## Open questions for the UI/UX session

- [ ] Can the two CMSes merge, or must the new UI call the Interactive CMS's API?
- [ ] Is the viewer-side Shop panel in scope?
- [ ] What do Dashboard, Homepage Shop+, Type and Embed do?
- [ ] Is manual product creation / Excel upload still needed?
- [ ] English, Bahasa Indonesia, or a toggle?
- [ ] Does Shopee's affiliate API expose clicks, orders and revenue by tag?
- [ ] Is there an EPG / program schedule API?
- [ ] Brand guidelines or an existing design system?
- [ ] Admin roles and approvals before going live?
