# Data Confidence Evaluation — Deploy Guide

This repository contains a single static page `index.html` that runs the Joshua Project Data Confidence evaluation tool.
It works on phones and laptops, supports branching logic, scoring, copy/print, and **submits results to Google Sheets**.

## 0) Prerequisites
- A Google Sheet + Apps Script Web App deployed with **Anyone** access. Keep the Web App URL handy.
- The HTML stores the endpoint **per-browser** using localStorage.

## 1) Deploy to GitHub Pages (no build)
1. Create a new GitHub repo (public or private).
2. Upload/commit these files:
   - `index.html`
   - (optional) `README.md`
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, choose:
   - **Source**: *Deploy from a branch*
   - **Branch**: `main` (or `master`) and **/ (root)**
5. Click **Save**. Wait for the green check.
6. Your site will be at:
   - `https://<USERNAME>.github.io/<REPO>/`

### Using a custom path (if you keep the filename `data-confidence-evaluation.html`)
If you don't rename, the final URL will be: `https://<USERNAME>.github.io/<REPO>/data-confidence-evaluation.html`

## 2) Deploy to Netlify
### A) Drag-and-drop (fastest)
1. Go to https://app.netlify.com → **Add new site → Deploy manually**.
2. Drag **index.html** into the drop zone.
3. Netlify gives you a temporary URL like `https://<random-name>.netlify.app/`.
4. Click **Site settings → Change site name** to something memorable.

### B) From GitHub (auto-deploy on push)
1. **Add new site → Import an existing project** → choose your GitHub repo.
2. Build command: **(leave empty)**
3. Publish directory: **/** (root)
4. Deploy → future pushes auto-deploy.

## 3) First-run setup (in the browser)
1. Open the site URL.
2. Expand **Admin → Google Sheets Web App URL**.
3. Paste your Apps Script **Web App URL** and click **Save Endpoint**.
4. Fill the required respondent fields; buttons will enable.
5. Test **Send Results** and confirm a new row in your Sheet.

## 4) Tips
- **HTTPS:** Both GitHub Pages and Netlify serve HTTPS by default. Apps Script URLs are HTTPS too.
- **Caching:** If you update `index.html`, hard-refresh or append `?v=2` to the URL to bust caches.
- **Mobile:** The page is responsive; test the **Print / Save PDF** on iOS/Android as behavior varies by browser.
- **Baking the endpoint:** If you prefer not to paste the endpoint each time, ask the developer to embed your URL by default in the script.

## 5) Troubleshooting
- **Buttons disabled:** The endpoint must be saved and all four respondent fields must be valid (email format).
- **No rows in Sheet:** Re-deploy the Apps Script **Web App** and ensure access is “Anyone”. Check script logs for errors.
- **CORS warnings:** The page tries a standard POST; if blocked, it retries with `no-cors` (fire-and-forget). The Sheet should still receive rows.