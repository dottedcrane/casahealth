# casahealth

The public website for **Casa Health**, publisher of the **HomeBase** and **HomeHealth** Android
apps.

Casa Health is the publisher; HomeBase and HomeHealth are the apps. The nav brand and the page
footers say Casa Health, while page titles and body copy name the specific app. That split is
deliberate, and a blanket find/replace over these files will get it wrong.

## Layout

Shared pages live at the root; anything that makes a claim about a *specific* app lives in that
app's folder.

```
index.html            Publisher landing page — lists every app
support.html          One support page covering all apps
styles.css            Shared stylesheet (all pages, both apps)
homebase/
  privacy.html        HomeBase privacy policy
  usage.html          HomeBase usage guide
homehealth/
  privacy.html        HomeHealth privacy policy
  usage.html          HomeHealth usage guide
```

**Privacy and usage are per-app on purpose, not just for tidiness.** The two policies differ on
points that matter: HomeBase has a one-time in-app purchase and declares `INTERNET` partly to
reach Google Play for purchase validation, whereas HomeHealth has no in-app purchases and
declares `INTERNET` solely so the calendar-picker Intent works. A single shared policy would be
factually wrong for one of the apps. Never merge them.

The apps also have different floors: **HomeBase requires Android 8.0+** (`minSdk 26`),
**HomeHealth requires Android 7.0+** (`minSdk 24`).

## Adding an app

1. Create `<app>/` with its own `privacy.html` and `usage.html`.
2. In those pages, link shared assets with `../` (`../styles.css`, `../index.html`,
   `../support.html`) and sibling pages flat (`usage.html`, `privacy.html`).
3. Add a card to the `#apps` grid in `index.html` and to the documentation grid in
   `support.html`.

## Publishing

Served by GitHub Pages from the **`main` branch, `/` (root)**. Edit, commit, push — Pages
redeploys on its own. The site is plain self-contained HTML and CSS: no build step, no CDNs, no
JavaScript, system fonts only, and all links relative, so it also works opened from disk.

## Where the source pages came from

The HomeBase pages were written in the private `homebase` app repo under `docs/`, which still
holds a copy; that repo is private, so Pages could never serve them from there. The HomeHealth
pages came from the `homehealth` repo, which serves its own site at
`dottedcrane.github.io/homehealth/` and is treated as read-only. Both origins still exist, so a
page edited here must be mirrored there by hand or the copies drift.
