# ZopDev Website · Handover Repo

> **Tracker:** [zopdev/website#713](https://github.com/zopdev/website/issues/713) (umbrella) · [zopdev/projects/9](https://github.com/orgs/zopdev/projects/9/views/1) (tech-support board) · 12 sub-tickets [#714](https://github.com/zopdev/website/issues/714)–[#725](https://github.com/zopdev/website/issues/725).

This repo is the **static prototype + design system + acceptance criteria** for the ZopDev marketing site (production lives at `zopdev/website`, a Next.js app). Frontend devs (Naveen + team) should treat this as the **source-of-truth reference** when porting fixes to the production Next.js codebase.

---

## What's here

### Docs (read first)

| File | Purpose |
|---|---|
| [`DESIGN.md`](DESIGN.md) | Canonical design system — tokens, spacing, type scale, components, voice. 1,085 lines. |
| [`ACCEPTANCE-CRITERIA-VISUAL-BUGS.md`](ACCEPTANCE-CRITERIA-VISUAL-BUGS.md) | 12 visual-bug ACs with testable checklists and `How to verify` recipes. Each one is also a GitHub sub-issue (#714–#725). |
| [`HANDOVER-WEBSITE-DEVS.md`](HANDOVER-WEBSITE-DEVS.md) | Handover overview — state at handover, files created/modified, suggested ship order, known limitations. |

### Static prototype (the actual site)

| Path | Purpose |
|---|---|
| `index.html` | Homepage (1.27 MB / 26,919 lines — note TICKET-12, trim is a backlog item) |
| `zopnight.html`, `zopday.html`, `zopcloud.html` | The 3 product pages |
| `cdcr-whitepaper.html` | CDCR research brief with in-browser ebook reader overlay |
| `k8s-view.html` | Kubernetes View page (ZopDay bridge) |
| `cur-calculator.html` | AWS CUR waste estimator (form-driven) |
| `walkthrough.html` | 7-surface video walkthrough hub |
| `site-map.html` | Auto-generated site map (46 public URLs) |
| ~40 other `*.html` files | Marketing pages (about, careers, customers, blog, case studies), content (ebooks, guides), legal (trust, accessibility), error pages |

### Chrome (shared CSS + JS)

| File | Purpose |
|---|---|
| `tokens.css` | All design tokens (colors, spacing, type). Single source of truth. |
| `chrome.css` | Base chrome + nav + footer + buttons (~34 KB) |
| `homepage-chrome.css` | Page-specific chrome + components (~183 KB) |
| `chrome-footer.css` | Footer-specific responsive rules (~16 KB) |
| `chrome-navmenu.js` | Desktop nav-overlay open/close, focus + keyboard |
| `chrome-mobilenav.js` | Mobile drawer behavior |
| `chrome-footer.js` | Footer year, regions globe, status pill |
| `chrome-pagetransition.js` | View Transitions API + fallback fade |
| `chrome-darkfold.js` | Theme toggle persistence (reads `localStorage('zop-theme')`) |

### Assets

| Type | Files |
|---|---|
| Videos | 20 `.mp4` files (product walkthroughs · the largest is 28 MB) |
| Images | Founders, brand covers, ebook covers, hex tile mocks |
| Config | `robots.txt`, `manifest.json` (PWA), `sitemap.xml`, `vercel.json` (cache rules) |

---

## How to run locally

```bash
git clone https://github.com/Ravdesigns/zopdev-website-handover.git
cd zopdev-website-handover
python3 -m http.server 8765
# Open http://localhost:8765/
```

No build step — every page is plain HTML referencing the shared CSS/JS files. View source on any page to see the markup pattern.

---

## How to read the ACs

The 12 acceptance criteria are in [`ACCEPTANCE-CRITERIA-VISUAL-BUGS.md`](ACCEPTANCE-CRITERIA-VISUAL-BUGS.md) and mirrored as GitHub sub-issues:

| # | Title | Priority | Issue |
|---|---|---|---|
| 01 | Footer drift | HIGH (✅ done in prototype) | [#714](https://github.com/zopdev/website/issues/714) |
| 02 | Empty SVG brand marks (17 pages) | HIGH | [#715](https://github.com/zopdev/website/issues/715) |
| 03 | Keyboard focus invisible (a11y) | HIGH | [#716](https://github.com/zopdev/website/issues/716) |
| 04 | Z-index stacking conflicts | MEDIUM | [#717](https://github.com/zopdev/website/issues/717) |
| 05 | Border-radius drift | MEDIUM | [#718](https://github.com/zopdev/website/issues/718) |
| 06 | Reduced-motion gate (a11y) | MEDIUM | [#719](https://github.com/zopdev/website/issues/719) |
| 07 | `!important` refactor | LOW | [#720](https://github.com/zopdev/website/issues/720) |
| 08 | Mobile table scroll | MEDIUM | [#721](https://github.com/zopdev/website/issues/721) |
| 09 | Fixed pixel widths > 600px | MEDIUM | [#722](https://github.com/zopdev/website/issues/722) |
| 10 | Non-brand hex colors | LOW | [#723](https://github.com/zopdev/website/issues/723) |
| 11 | Skip-link extraction | LOW | [#724](https://github.com/zopdev/website/issues/724) |
| 12 | `index.html` DOM weight (1.27 MB) | MEDIUM | [#725](https://github.com/zopdev/website/issues/725) |

---

## ⚠️ Prototype-vs-Production gap

This repo is **static HTML**. The deployed site `zopdev/website` is a **Next.js app**.

When implementing a ticket, devs should:

1. Read the AC + `How to verify` block in the corresponding sub-issue
2. Open the affected page(s) in this prototype to see the target markup/CSS
3. Port the fix to the equivalent Next.js component(s) in `zopdev/website`
4. Verify against the AC checklist before closing the issue

The 3 new pages (`cdcr-whitepaper.html`, `k8s-view.html`, `cur-calculator.html`) were built in this prototype and **need to be ported to Next.js routes** before they ship to `zop.dev`.

---

## License

Internal — © ZopDev. Not for redistribution.
