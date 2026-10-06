# Internship Tracker

Built by Amelia Koth. Free to use and share with friends.

**Using a copy?** Your applications are saved privately in your own browser by
default, so nobody else sees your data. If you want cloud sync, create your
own JSONBin bin (Part A) — don't share a bin or key with anyone.

A single-page, no-build internship application tracker. Everything lives in one
file — `index.html` — with data cached in your browser's `localStorage` and
optionally synced to a free [JSONBin.io](https://jsonbin.io) bin so it shows
the same data across your phone, laptop, etc.

There's no login and no server — anyone with the deployed URL can read/write
the data, so treat the link like a shared notebook, not a private account.

---

## Part A — Set up cloud sync with JSONBin.io

This step is optional but recommended — without it, your data only lives in
the browser you're currently using (still works fine, it just won't follow
you to another device).

1. Go to **https://jsonbin.io** and click **Sign Up** (free tier is plenty).
2. Verify your email and log in to the JSONBin dashboard.
3. Click **Create Bin** (or the **+** button).
   - Paste in `{}` as the initial content (just an empty JSON object).
   - Give it a name like `internship-tracker` if asked.
   - Click **Create**.
4. After creating the bin, open it and copy the **Bin ID** — it's the string
   of letters/numbers in the URL or shown at the top of the bin view (looks
   like `65f1a2b3c4d5e6f7a8b9c0d1`).
5. Go to your account/profile area and find **API Keys** (sometimes under
   "Secret Key" or "X-Master-Key"). Copy your **X-Master-Key** — it's a long
   string starting with something like `$2a$10$...`.
6. Open `index.html` in a text editor and find these two lines near the top
   of the `<script>` section (search for `JSONBIN_KEY`):

   ```js
   const JSONBIN_KEY = '';
   const JSONBIN_ID  = '';
   ```

   Paste your values in between the quotes:

   ```js
   const JSONBIN_KEY = '$2a$10$your-actual-key-here';
   const JSONBIN_ID  = '65f1a2b3c4d5e6f7a8b9c0d1';
   ```

7. Save the file and reload `index.html` in your browser. The status pill in
   the top-right (and the footer) should change from "Local only" to
   "Loaded ✓" — that confirms it's talking to your bin. Add an application
   and you should see "Synced ✓" appear.

That's it — this bin is brand-new and only used by this app, completely
separate from any other project's bin.

---

## Part B — Deploy for free with GitHub Pages

Run these from inside this folder:

1. **Initialize git and make the first commit**

   ```bash
   git init
   git add index.html README.md
   git commit -m "Initial commit: Internship Tracker"
   ```

2. **Create a GitHub repo.** Easiest with the GitHub CLI (`gh`), if you have
   it installed and logged in (`gh auth login`):

   ```bash
   gh repo create internship-tracker --public --source=. --remote=origin --push
   ```

   This creates the repo on GitHub, adds it as your `origin` remote, and
   pushes your commit in one step.

   *No `gh` CLI?* Instead:
   - Go to **https://github.com/new**, name the repo `internship-tracker`,
     leave it empty (no README/gitignore), and click **Create repository**.
   - Then run:
     ```bash
     git remote add origin https://github.com/YOUR-USERNAME/internship-tracker.git
     git branch -M main
     git push -u origin main
     ```

3. **Turn on GitHub Pages.**
   - On GitHub, open your new repo → **Settings** → **Pages** (left sidebar).
   - Under **Build and deployment** → **Source**, choose **Deploy from a
     branch**.
   - Under **Branch**, pick `main` and folder `/ (root)`, then **Save**.
   - Wait about a minute, then refresh the Pages settings screen — it will
     show your live URL, something like:
     `https://YOUR-USERNAME.github.io/internship-tracker/`

4. **Pushing future changes** — any time you edit `index.html` and want the
   live site updated:

   ```bash
   git add index.html
   git commit -m "Update tracker"
   git push
   ```

   GitHub Pages redeploys automatically within a minute or two of the push.

---

## Part C — Add it to your iPhone home screen

Once you have the GitHub Pages URL from Part B:

1. Open the URL in **Safari** on your iPhone (must be Safari, not Chrome —
   only Safari can add home-screen apps on iOS).
2. Tap the **Share** icon (the square with an arrow pointing up) in the
   bottom toolbar.
3. Scroll down the share sheet and tap **Add to Home Screen**.
4. Confirm the name (defaults to "Internship Tracker") and tap **Add** in
   the top-right corner.
5. The icon now appears on your home screen. Opening it launches the tracker
   full-screen, without Safari's address bar — it behaves like a lightweight
   app.

Because data syncs through JSONBin.io (Part A), the home-screen app on your
phone and the tab on your laptop will show the same applications.
