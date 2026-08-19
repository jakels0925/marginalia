# Marginalia — install it on your iPhone

Every tap, in order. Two routes: **A** if you have a computer (easier to update
later), **B** if you only have the phone. Both end with a real app icon on your
Home Screen that opens with no address bar and works with no signal.

---

## Part 1 — Get the files out of this chat

1. Scroll up to the download card in the chat that says
   **"Marginalia — installable app"**. Click it.
2. A file called **`app.zip`** downloads.
3. Unzip it.
   - **Mac:** double-click `app.zip` in your Downloads folder. You get a folder
     called `app`.
   - **Windows:** right-click `app.zip` → *Extract All…* → *Extract*.
   - **iPhone:** open the **Files** app → *Downloads* → tap `app.zip` once. It
     becomes a folder called `app` sitting next to it.
4. Open the `app` folder and confirm you see exactly these five items:

   ```
   index.html
   manifest.webmanifest
   sw.js
   icon-192.png
   icon-512.png
   README.md          ← this file; you don't need to upload it
   ```

   **Important:** you will upload the five files *from inside* this folder, not
   the folder itself. `index.html` has to end up at the top level of your site
   or the URL won't load.

---

## Route A — GitHub Pages (computer, ~10 minutes, free forever)

### A1. Make the repository

1. Go to **github.com** and sign in (create a free account if you don't have
   one — email, password, username, verify the email).
2. Top-right, click the **`+`** icon → **New repository**.
3. **Repository name:** type `marginalia`
4. Leave *Description* blank. Under visibility choose **Public**.
   (Pages needs Public on a free account.)
5. Do **not** tick "Add a README file."
6. Click the green **Create repository** button.

### A2. Upload the app

You land on a page headed *"Quick setup — if you've done this kind of thing
before."*

7. In the grey box, find the sentence *"…or **upload an existing file**"* and
   click the **upload an existing file** link.
8. A drag-and-drop area appears: *"Drag files here to add them to your
   repository."* Open your `app` folder in another window, select the five files
   — `index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`,
   `icon-512.png` — and drag them onto that area.
   (If dragging is fiddly, click **choose your files** and multi-select them.)
9. Wait until all five appear in the list below the drop zone.
10. Scroll down to *Commit changes*. In the first box type `add app`.
11. Click the green **Commit changes** button.
12. You should now be looking at a file list containing all five files. If you
    see a folder called `app` instead, you uploaded the folder — click it,
    that's wrong; delete the repo and redo step 8 selecting the files inside.

### A3. Switch on hosting

13. Click **Settings** (top row of the repo, right-hand end, gear icon).
14. In the left sidebar, under *Code and automation*, click **Pages**.
15. Under **Build and deployment → Source**, the dropdown says
    *GitHub Actions*. Change it to **Deploy from a branch**.
16. Two dropdowns appear underneath. Set **Branch** = `main` and the folder
    dropdown = **`/ (root)`**.
17. Click **Save**.
18. Wait about 60 seconds, then reload the page. A box appears at the top:
    *"Your site is live at …"* with a URL like

    ```
    https://YOUR-USERNAME.github.io/marginalia/
    ```

19. Click **Visit site** to check it loads. You should see the dark shelf screen
    with Atomic Habits on it. If you get a 404, wait another minute and reload —
    the first deploy is slow.

### A4. Get the URL onto the phone

Pick whichever is least annoying:

- **AirDrop / Messages:** copy the URL and text it to yourself.
- **Handoff:** if you're signed into the same iCloud account, the tab appears
  in Safari on the phone under the tab-switcher's *From your Mac* section.
- **Type it:** it's short — `yourusername.github.io/marginalia`

### A5. Add to Home Screen

20. Open the URL **in Safari on the iPhone**. This must be Safari — Chrome,
    Firefox and in-app browsers on iOS cannot install to the Home Screen.
21. Tap the **Share** button: the square with an arrow pointing up out of it.
    It's in the bottom toolbar, centre. (If your toolbar is hidden, tap once
    near the bottom of the screen to bring it back. If Safari is in
    landscape/tab-bar mode the Share button sits in the top-right instead.)
22. The share sheet slides up. Scroll the **lower** list — the one with grey
    icons, below the row of app icons — until you see **Add to Home Screen**.
    (It's usually beneath *Add to Reading List*, *Add Bookmark*, *Find on
    Page*. If you can't see it, scroll that list to the very bottom and tap
    **Edit Actions…**, then tap the green `+` next to *Add to Home Screen*.)
23. Tap **Add to Home Screen**. A preview shows the icon and the name
    *Marginalia* — you can edit the name here if you want.
24. Tap **Add**, top-right.
25. The icon lands on your Home Screen (or in your App Library on the last
    Home Screen page). Tap it.

### A6. Confirm it installed properly

- **No address bar, no tabs, no Safari toolbar** at the bottom → correct, iOS
  is running it standalone with its own storage.
- If you *do* see the address bar, you opened the bookmark, not the app.
  Delete the icon and redo A5, making sure you tapped *Add to Home Screen* and
  not *Add Bookmark*.
- Turn on Airplane Mode and reopen it. It should still work. That confirms the
  offline cache took.

### A7. Updating it later

1. Go to the repo → click `index.html` → click the **pencil** icon (top-right
   of the file view) → make your edit.
2. Click `sw.js` → pencil → change the line `const CACHE = 'marginalia-v1';`
   to `'marginalia-v2'` (then `v3` next time, and so on). **This step matters
   — without it the phone keeps serving the cached old version.**
3. Commit both.
4. On the phone, open the app, close it fully (swipe up from the bottom and
   flick the card away), then open it again. Second launch shows the new build.

Your reading data survives updates — it's stored separately from the app files.

---

## Route B — iPhone only (no computer, ~5 minutes)

GitHub's mobile site is painful for uploads, so use Netlify Drop.

1. In **Files**, unzip `app.zip` as described in Part 1.
2. Open Safari and go to **`app.netlify.com/drop`**.
3. Tap **Browse to upload**.
4. The file picker opens. Navigate to *Downloads* → tap the **`app`** folder
   name once to open it, then tap **Select** (top-right), tap the five files,
   and tap **Open**.
   - If it insists on a folder rather than files, selecting the `app` folder
     itself also works — Netlify flattens single-folder uploads.
5. It uploads and shows a URL like `https://random-words-123456.netlify.app`.
   Tap it.
6. **Create the free account it prompts you for.** If you skip this, the site
   is deleted after an hour and your Home Screen icon breaks. Email + password,
   or sign in with GitHub.
7. Optional: in the Netlify dashboard → *Site configuration* → *Change site
   name* → set it to something you'll recognise, e.g. `marginalia-yourname`.
   The URL becomes `marginalia-yourname.netlify.app`.
8. Open that URL in **Safari**, then follow **A5** above (Share → Add to Home
   Screen → Add).

To update later: drag a changed folder onto `app.netlify.com/drop` again while
signed in, choosing the same site — remembering to bump `CACHE` in `sw.js`
first.

---

## Clearing the demo books and starting fresh

The app ships with three example books so the screens aren't empty on first
open. To wipe them:

1. Open the app and scroll to the **bottom of the shelf screen**.
2. Under the fading rule you'll see three links: *Back up* · *Restore* ·
   **Start fresh**.
3. Tap **Start fresh** → **OK**. Everything goes; the shelf is empty.
4. Tap **Add a book** → Title `Atomic Habits`, Author `James Clear`, Pages
   `320`, Type **Nonfiction** → *Put it on the shelf*.

To drop just one book and keep the rest: open that book → scroll to the very
bottom → **Remove this book from the shelf**.

### Your first reading check

There's nothing to recall yet, so the first pass is one-way — you log, you
don't get quizzed. The quiz starts on visit two.

1. Read as usual. When you put the book down, open the app → tap **Atomic
   Habits** → **Log a session**.
2. **Pages read** — from and to. Whatever you actually covered.
3. **Core idea** — book closed. Say the main idea plainly in your own words.
4. **Personal connection** — one real situation from your own life.
5. **Pushback** — optional; *Skip this one* is fine.
6. **For future you** — write one question you'll answer cold next time, and
   the answer. Make it specific enough that guessing fails.
7. **Fact check** — tap *Copy my answers + the check request*, paste it to
   Claude in chat, then paste the reply into *Claude's notes* and tap a verdict
   tag. Or skip it and add it later via the *add verdict* link on that session.
8. **Save this session.**

Next time you tap Atomic Habits, your question appears **first**, before
anything else. Answer it in your head, tap *I've answered — show what I wrote*,
then grade yourself. That's the loop.

---

## Backing up your reading log

Everything lives on the phone under one storage key. There is no cloud copy, by
design — that's what kept failing before.

**To back up:** open the app → scroll to the bottom of the shelf screen → tap
**Back up**. A file named `marginalia-2026-08-18.json` is saved via the iOS
share sheet; choose *Save to Files* → *On My iPhone* or *iCloud Drive*.

**To restore:** shelf screen → **Restore** → pick a `.json` file. It replaces
everything currently stored, so only restore a backup you trust.

**Back up before you:** delete the Home Screen icon, reset the phone, hand the
phone on, or clear Safari website data. Deleting the icon can take the data
with it.

---

## If something goes wrong

**Blank white screen.** The URL is wrong or `index.html` isn't at the root.
Visit the URL with `/index.html` on the end — if that works, the file is one
folder too deep. Re-upload the files, not the folder.

**"Add to Home Screen" is missing from the share sheet.** You're not in Safari,
or you're in a Private tab (Private tabs hide it). Switch to a normal Safari
tab.

**It opens with an address bar.** You made a bookmark, not an app. Delete and
redo A5.

**Won't open offline.** Service workers only register over HTTPS. Confirm the
URL starts `https://`, then open it online once more and reopen — the cache
fills on first successful load.

**Nothing saves / a save error.** You're probably in Private Browsing, which
blocks storage. Open the installed Home Screen app instead of the Safari tab.

**Data vanished after an update.** It shouldn't — but this is exactly why
*Back up* exists. Restore your latest JSON.

---

## What's in the app

- **Shelf** — books, reading streak, recall accuracy with a sparkline of your
  last eight self-grades, and a count of retrieval checks waiting.
- **Cold retrieval quiz** — opening a book with a pending question shows that
  question *first*, before anything else. Answer from memory, reveal what past
  you wrote, grade yourself nailed / partly / blank. Older questions return on
  a day 3 / 7 / 21 schedule.
- **Session wizard** — six screens, one question each: page range; three
  reflection prompts (nonfiction: core idea, personal connection, pushback /
  fiction: what happened, character want & obstacle, emerging theme); the quiz
  question and answer you seal for future you; the fact-check handoff.
- **Fact check** — one button copies a ready prompt with the book, page range
  and your unaided answers, instructing Claude to check against public sources
  rather than a copyrighted text. Paste the verdict back into the notes field
  and tag it held up / partly off / missed it; it saves permanently beside your
  original answer. Older sessions have an *add verdict* link for attaching one
  later.
- **Finish this book** — three takeaways from memory plus one concrete
  application, kept as a closing note.
