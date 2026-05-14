# PHI Construction — Weekly Dashboard
**Live construction operations dashboard hosted on GitHub Pages**

---

## 🗂 Files in this repo

| File | Purpose |
|---|---|
| `index.html` | Public live dashboard (auto-fetches `data.json`) |
| `admin.html` | Password-protected weekly data entry form |
| `data.json` | Single source of truth — all dashboard data |
| `README.md` | This setup guide |

---

## 🚀 One-Time Setup (do this once)

### Step 1 — Create the GitHub repo

1. Go to [github.com](https://github.com) and sign in
2. Click **+** → **New repository**
3. Name it: `phi-construction-dashboard` (or any name you like)
4. Set to **Public** (required for free GitHub Pages)
5. Click **Create repository**

---

### Step 2 — Upload files

1. In your new repo, click **Add file** → **Upload files**
2. Upload all 4 files: `index.html`, `admin.html`, `data.json`, `README.md`
3. Click **Commit changes**

---

### Step 3 — Enable GitHub Pages

1. Go to your repo → **Settings** → **Pages** (left sidebar)
2. Under **Source**, select: **Deploy from a branch**
3. Branch: `main` | Folder: `/ (root)`
4. Click **Save**
5. Wait 1–2 minutes, then your dashboard is live at:
   ```
   https://YOUR_GITHUB_USERNAME.github.io/YOUR_REPO_NAME/
   ```

---

### Step 4 — Create a GitHub Personal Access Token (PAT)

The admin page uses this to push data updates directly to GitHub.

1. Go to GitHub → **Settings** → **Developer settings** → **Personal access tokens** → **Tokens (classic)**
2. Click **Generate new token (classic)**
3. Note: `PHI Dashboard Admin`
4. Expiration: set to **1 year** (or no expiration)
5. Check the box: ✅ **repo** (full control of private repositories)
6. Click **Generate token**
7. **Copy and save the token** — you'll need it every time you log into admin

---

### Step 5 — Configure your usernames in the files

Open `index.html` and find these two lines near the bottom (in the `<script>` section):

```javascript
const GITHUB_USER = 'YOUR_GITHUB_USERNAME';
const GITHUB_REPO = 'YOUR_REPO_NAME';
```

Replace with your actual values, e.g.:
```javascript
const GITHUB_USER = 'phi-construction';
const GITHUB_REPO = 'phi-construction-dashboard';
```

Do the same in `admin.html` (same two lines, plus you can change the admin password):
```javascript
const GITHUB_USER = 'phi-construction';
const GITHUB_REPO = 'phi-construction-dashboard';
const ADMIN_PASSWORD = 'phi2026admin'; // ← change this!
```

Then re-upload both files to the repo.

---

## 📅 Every Week — How to Update the Dashboard

### Option A: Admin Page (recommended)

1. Go to: `https://YOUR_USERNAME.github.io/YOUR_REPO/admin.html`
2. Enter your **GitHub PAT** and **admin password**
3. Update data across the panels (Meta, Projects, Cost, Safety, etc.)
4. Click **💾 Save & Publish**
5. Dashboard at `index.html` updates within seconds

### Option B: Edit `data.json` directly in GitHub

1. Open your repo on GitHub
2. Click `data.json` → pencil icon (Edit)
3. Update the values
4. Click **Commit changes**
5. Dashboard refreshes automatically on next page load

---

## 🔒 Security Notes

- The **dashboard** (`index.html`) is public — anyone with the link can view it
- The **admin page** (`admin.html`) requires both a PAT and a password
- Your GitHub PAT is stored in browser session memory only (not saved to disk or the repo)
- To revoke access: delete the PAT from GitHub Settings → Developer settings
- Rotate the `ADMIN_PASSWORD` in `admin.html` periodically

---

## ➕ Adding a New Project

1. Go to `admin.html` → Sign in
2. Update the `data.json` project array via the Projects panel
   - OR edit `data.json` directly in GitHub and add a new project object following the existing structure
3. Save & Publish

---

## 📌 Dashboard URL Format

| Page | URL |
|---|---|
| Live Dashboard | `https://USERNAME.github.io/REPO/` |
| Admin Panel | `https://USERNAME.github.io/REPO/admin.html` |
| Raw Data | `https://raw.githubusercontent.com/USERNAME/REPO/main/data.json` |

---

*PHI Construction Operations | Weekly Dashboard | Confidential — Internal Use*
