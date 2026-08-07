# casahealth

The public website for **Casa Health**, the publisher of the **HomeBase** Android app.

Casa Health is the publisher; HomeBase is the app. The nav brand and the page footers say Casa
Health, while the page titles and copy describe HomeBase. That split is deliberate — keep it.

## What's here

The site is plain, self-contained HTML and CSS. No build step, no CDNs, no JavaScript
dependencies: system fonts only, and every link between pages is relative, so the whole thing
works when opened from disk as well as when served.

| File | Page |
| --- | --- |
| `index.html` | Landing page — what HomeBase is, and the offline-first model |
| `usage.html` | How to use the app, including the child-safety section |
| `privacy.html` | Privacy policy (the URL the Play Console listing points at) |
| `support.html` | Support contact and common questions |
| `styles.css` | Shared styles for all four pages |

## Publishing

Served by GitHub Pages from the **`main` branch, `/` (root)**. Edit the HTML, commit, push — Pages
redeploys on its own.

## Editing

This repo is the canonical copy of these pages. A copy also exists at `docs/` in the private
`homebase` app repo, which is where they were originally written; if you change a page in one
place, mirror it to the other or the two will drift apart.
