# Stack Tracker — v2.1.0

A personal fitness and lifestyle journal. Single static page, no backend,
no account — everything is stored in the browser's IndexedDB on whatever
device it's opened on.

## Files in this package

Every file goes at the **root** of the repo — no folders, no subfolders.

| File | What it is |
|---|---|
| `index.js` | The whole app, baked into one Worker script |
| `wrangler.toml` | Cloudflare config — tells it to run `index.js` |
| `package.json` | Lets Cloudflare's build step install Wrangler |
| `.gitignore` | Keeps build junk out of the repo |
| `README.md` | This file |
| `CHANGELOG.md` | What's new in this version |

That's six files, zero folders. `index.js` contains the entire app —
HTML, CSS, and JavaScript — embedded directly inside it as one big string,
so there's nothing else to upload or organize.

## Step 1 — Create the GitHub repo

1. Go to **github.com → New repository**. Name it `stack-tracker` (or
   whatever you like), set it to Public or Private, and create it —
   don't add a README from GitHub's side, you already have one here.
2. On the new repo's page, tap **Add file → Create new file**.
3. Type the filename exactly as shown in the table above (e.g.
   `index.js`), then paste in that file's contents below it.
4. Scroll down and tap **Commit changes**.
5. Repeat for all six files: `index.js`, `wrangler.toml`, `package.json`,
   `.gitignore`, `README.md`, `CHANGELOG.md`.

When you're done, your repo's file list should show exactly those six
files sitting at the top level — no folders.

## Step 2 — Connect Cloudflare to the repo

1. Log into the **Cloudflare dashboard**.
2. Go to **Workers & Pages → Create → Connect to Git**.
3. Authorize Cloudflare's GitHub app if it asks, then select your
   `stack-tracker` repository.
4. Cloudflare will detect `wrangler.toml` automatically. When it asks you
   to confirm the Worker name, make sure it's exactly `stack-tracker`
   (matching the `name` field in `wrangler.toml`) — a mismatch here is
   the most common cause of a failed build.
5. Build command: leave **blank** — there's nothing to build.
6. Deploy command: leave it as the default, `npx wrangler deploy`.
7. Tap **Save and Deploy**.

Cloudflare will install dependencies, run `wrangler deploy`, and give you
a live URL that looks like:

```
https://stack-tracker.<your-subdomain>.workers.dev
```

## Step 3 — Verify it worked

Open that URL. You should see the **Loading Stack Tracker…** splash for a
moment, then the app itself. Tap the **i** button in the header — if the
About panel shows **Version 2.1.0**, you're running the right build.

## Updating later

Any time you have a new version of the app:
1. Edit `index.js` in GitHub (or replace its contents entirely) and
   commit.
2. Cloudflare picks up the push automatically and redeploys — no need to
   touch the Cloudflare dashboard again.

## A note on your data

Everything lives in IndexedDB in your browser, scoped to this exact URL.
- It does **not** sync between devices or browsers automatically.
- Use **Setup → Export** inside the app any time to download a full
  backup, and **Setup → Import** to restore it (on this device or
  another one).
- If you ever change the deployed URL (e.g. a custom domain), your old
  data won't follow automatically — export first, then import on the new
  URL.
