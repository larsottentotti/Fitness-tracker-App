# Fitness Tracker — Android app package

This is a **Progressive Web App (PWA)** version of Fitness Tracker. It's not a
compiled native Android app (I can't build/sign an actual .apk in this
environment), but once hosted, it installs on Android from Chrome as a real
app: its own icon on your home screen, opens full-screen with no browser
bar, works offline, and saves your data locally on your phone.

## What's in this folder

- `index.html`, `bundle.js` — the app itself (already built, nothing to compile)
- `manifest.json` — tells Android this is an installable app
- `sw.js` — service worker that caches the app so it works offline
- `icons/` — app icons

## 1. Host it somewhere (pick one, both are free)

**GitHub Pages** (if you have or don't mind making a GitHub account):
1. Create a new repository, upload everything in this folder to it.
2. In the repo's Settings → Pages, set the source to your main branch.
3. GitHub gives you a URL like `https://yourname.github.io/reponame/`.

**Netlify Drop** (no account needed):
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. Netlify gives you a URL immediately.

Either way, a PWA needs to be served over `https://` for install and offline
support to work — that's what these give you.

## 2. Install it on your Android phone

1. Open the hosted URL in **Chrome** on your phone.
2. Tap the **⋮** menu → **Add to Home screen** (or Chrome may prompt you
   with an "Install app" banner automatically).
3. Confirm — you'll get a "Fitness Tracker" icon on your home screen that
   opens like a normal app.

## 3. Your data

All your workouts, templates, and body weight entries are saved in the
phone's local browser storage for that site. They stay on your phone and
persist between opens, but note:
- Clearing Chrome's site data/storage for this app will erase it.
- It won't sync between devices — this is on-device storage only.
- Uninstalling the "app" (which is really this bookmark/shortcut) removes
  the icon but may or may not clear the underlying data depending on your
  phone; if you want a clean wipe, use the in-app "Reset all data" link too.

## Want an actual installable .apk instead?

Once it's hosted at a URL, you can feed that URL into
**[PWABuilder](https://www.pwabuilder.com/)** (a free Microsoft tool) —
it packages a hosted PWA into a real Android `.apk`/`.aab` you can sideload
or even submit to the Play Store. It needs your app to already be hosted
first, which is why step 1 above comes first.
