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

**Privacy and usage are per-app on purpose, not just for tidiness.** Each policy has to speak
for exactly one app — it names that app, describes that app's storage and permissions, and is
the URL given on that app's Play listing. A merged policy could not do that without hedging
every sentence about which app it meant, and any later divergence would silently make it wrong
for one of them. Never merge them.

What differs today: the two one-time purchases unlock different things — HomeHealth's
unlocks backup &amp; restore. Both apps now require **Android 8.0+** (`minSdk 26`) and both
declare `INTERNET` for the same two reasons (the calendar-picker Intent, and Google Play for
purchase validation), so neither is a point of difference any more — both used to be, and this
README said so for longer than it was true in each case.

The policies stay separate regardless. They are kept apart because each is the URL on one app's
Play listing and must describe that app's storage without hedging, not because the two happen to
differ on any particular line today.

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
