# Updating the app you already installed

Nothing here can break your reading data — the app files and your data are
stored separately on the phone. But do step 1 anyway.

You do **not** need to delete the Home Screen icon, and you do **not** need to
re-install. You're replacing the files on the website the icon points at.

---

## Step 1 — Back up first (2 taps)

1. Open Marginalia from your Home Screen.
2. Scroll to the bottom of the shelf screen. Tap **Back up**.
3. The share sheet opens → **Save to Files** → *On My iPhone* or *iCloud Drive*
   → **Save**.

If anything goes sideways later, *Restore* on that file puts you back.

---

## Step 2 — Get the new files

1. Click the download card in chat labelled **"Marginalia v3"**.
2. Unzip `app.zip` (Mac: double-click. Windows: right-click → Extract All).
3. Open the `app` folder. You want these five files — ignore the `.md` files:

   ```
   index.html
   manifest.webmanifest
   sw.js
   icon-192.png
   icon-512.png
   ```

Do not hand-edit anything. The `sw.js` in this folder is already bumped to
`marginalia-v3`, which is what makes the phone pick up the change.

---

## Step 3 — Replace the files on your host

### If you used GitHub Pages (Route A)

Upload all five again — same filenames, so GitHub overwrites them. This is
safer than editing files by hand in the browser.

1. Go to **github.com** → your repositories → click **marginalia**.
2. Just above the file list, click the **Add file** dropdown → **Upload files**.
3. Drag all five files from your unzipped `app` folder onto the drop area.
   (Or click **choose your files** and multi-select them.)
4. Wait for all five to list. GitHub will note it's replacing existing files —
   that's what you want.
5. Scroll to *Commit changes*, type `v3` in the message box, click the green
   **Commit changes**.
6. Wait ~60 seconds for the deploy. To check: repo → **Actions** tab → the top
   run should show a green tick. (Or just wait a minute.)

### If you used Netlify Drop (Route B)

1. Go to **app.netlify.com** and sign in.
2. Click your site (e.g. `marginalia-yourname`).
3. Click the **Deploys** tab.
4. At the bottom of that page is a drop area: *"Need to update your site? Drag
   and drop your site output folder here."* Drag your unzipped **`app` folder**
   onto it.
5. Wait for the deploy line to turn from *Building* to **Published**.

---

## Step 4 — Make the phone take the update

The service worker serves the cached copy first, so the new version lands on
the *second* launch. This is normal and not a fault.

1. Open Marginalia from the Home Screen.
2. Force-quit it: swipe up from the bottom edge and hold, then flick the
   Marginalia card up off the screen. (On a Home-button phone: double-click the
   Home button, flick the card up.)
3. Open it again from the Home Screen.
4. If it still looks old, repeat 2–3 once more. Being on Wi-Fi helps — the
   worker needs one online fetch to pick up the new files.

---

## Step 5 — Confirm you're on v2

Scroll to the bottom of the shelf screen. You should see:

```
ON THIS DEVICE · v3        Back up · Restore · Start fresh
```

Things that are new, all of them proof the update landed:

- **v3** in that footer line
- a **Start fresh** link next to Back up / Restore
- **Remove this book from the shelf** at the bottom of any book's page
- past sessions on a book page are **collapsed to one line** — date and page
  range — and expand when you tap them, with an *expand all* / *collapse all*
  link beside the "Sessions" heading

If you see full-length sessions or no version stamp, you're on an older build — repeat step 4,
then check that the commit in step 3 actually went through.

---

## Step 6 — Now clear the demo books

1. Bottom of the shelf → **Start fresh** → **OK** in the confirm box.
2. The shelf is empty and stays empty. (In v1 it would have re-seeded the demo
   books on the next launch — that was the bug.)
3. Tap **Add a book**:
   - Title: `Atomic Habits`
   - Author: `James Clear`
   - Pages: `320`
   - Type: **Nonfiction**
4. **Put it on the shelf.**

To drop a single book later instead of everything: open it → bottom of the page
→ **Remove this book from the shelf**.

---

## Step 7 — Your first session

There's nothing to recall yet, so this first one is one-way: you log, you aren't
quizzed. The retrieval test starts on visit two.

1. Read. When you put the book down: open the app → **Atomic Habits** →
   **Log a session**.
2. **Pages read** — from and to, whatever you actually covered.
3. **Core idea** — book closed. The main idea, plainly, in your own words.
4. **Personal connection** — one real situation in your own life.
5. **Pushback** — optional. *Skip this one* is a legitimate answer.
6. **For future you** — one question you'll answer cold next time, plus the
   answer. Specific enough that guessing fails.
7. **Fact check** — tap *Copy my answers + the check request*, paste it to
   Claude in chat, paste the reply into *Claude's notes*, tap a verdict tag.
   Or skip and use the *add verdict* link on that session later.
8. **Save this session.**

Next time you tap Atomic Habits, that question is the first thing on screen,
before the page count or anything else. Answer it in your head, tap *I've
answered — show what I wrote*, grade yourself nailed / partly / blank. That's
the loop, and it's the whole point of the app.

---

## If it goes wrong

**App won't open at all after the update.** The upload was incomplete —
`index.html` is missing or misnamed. Re-do step 3 with all five files.

**Data gone.** Restore your step-1 backup: shelf → *Restore* → pick the JSON.

**Stuck on v1 after four launches.** Delete the Home Screen icon, open the site
URL in Safari, re-add it (Share → Add to Home Screen). Your data survives this
because it's tied to the site's origin, not the icon — but you did back up in
step 1, so either way you're covered.
