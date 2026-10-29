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
- Your data belongs to the **web address** the app is hosted at. If you ever
  move the app to a different address (a new GitHub Pages or Netlify URL),
  the app at the new address starts empty. A backup (below) carries your data
  across.
- Uninstalling the "app" (which is really this bookmark/shortcut) removes
  the icon but may or may not clear the underlying data depending on your
  phone; if you want a clean wipe, use the in-app "Reset all data" link too.

Because of this, **make a backup regularly** — see the next section.

## 4. Back up your data

The app has a **Backup** tab (the last tab, next to "Body weight").

### Make a backup
1. Open the app and tap **Backup**.
2. Tap **Download backup**. A file named like
   `fitness-tracker-backup-2026-10-28.json` is saved to your phone's
   **Downloads** folder.
3. Optional: tap **Share backup** (shown if your phone supports it) to send the
   file straight to Google Drive, email, WhatsApp, etc.
4. Keep a copy somewhere other than the phone — Google Drive, email it to
   yourself, or a computer. A backup that only sits on the phone is lost if the
   phone is lost.

The Backup tab shows the date of your last backup and turns red when it is
more than 30 days old. A good habit: back up once a week, or after a big
change such as a new template.

The backup contains your workouts, templates and body weight entries. It does
not contain the unfinished workout you're currently filling in on the Log tab.

### Restore from a backup
Use this if your data got erased, or you want to go back to an earlier state.
1. Make sure the backup file is on the phone (download it from Drive or
   email first if needed).
2. Open the app → **Backup** → **Choose backup file**, and pick the `.json`
   file. Files in the Downloads folder are easiest to find.
3. The app shows what the file contains next to what is currently stored.
   Check that it looks right.
4. Tap **Yes, replace my data**. Everything currently in the app is replaced by
   the backup, so if you have newer entries you want to keep, download a
   fresh backup first.

If the file isn't a Fitness Tracker backup, the app says so and changes
nothing. Entries in a backup that are damaged are skipped, and the app tells you
how many.

## 5. Moving to a new phone

Your data does not move by itself, so transfer it with a backup file:

**On the old phone** (while you still have it):
1. Open the app → **Backup** → **Download backup**.
2. Get the file off the phone: tap **Share backup** to Google Drive, or email
   it to yourself.

**On the new phone:**
1. Open the **same web address** in Chrome as you used before, then
   **⋮ → Add to Home screen** to install the app (step 2 above).
2. Get the backup file onto the new phone (open your Drive/email and
   download it).
3. Open the app → **Backup** → **Choose backup file** → pick the file →
   **Yes, replace my data**.

Your history, templates and body weight graph are back.

**If the old phone is lost or broken**, you can only restore if you made a
backup earlier and kept a copy somewhere else, which is why step 4 of "Make a
backup" matters. Only the data since your last backup is lost.

## Want an actual installable .apk instead?

Once it's hosted at a URL, you can feed that URL into
**[PWABuilder](https://www.pwabuilder.com/)** (a free Microsoft tool) —
it packages a hosted PWA into a real Android `.apk`/`.aab` you can sideload
or even submit to the Play Store. It needs your app to already be hosted
first, which is why step 1 above comes first.
