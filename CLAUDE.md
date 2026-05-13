# CLAUDE.md — Daily Magazine Workflow Rules

## 🗞️ Project Identity
This is a **daily magazine folder**. I am the reporter. I will create magazine websites daily using the `recall-magazine` skill or custom HTML/CSS builds.

---

## 📁 Folder Structure

```
project-root/
├── CLAUDE.md                  # This rules file
├── index.html                 # Today's live magazine page (always the latest)
├── credentials/               # GitHub credentials folder (DO NOT expose contents)
│   └── github.json            # Contains: username, repo, token, branch
└── previous_news/             # Archive of past magazine pages
    └── {maincontent}{date}.html   # e.g., breaking_news2026-05-13.html
```

---

## 🚀 GitHub Upload Workflow

When I say **"upload to GitHub"**, follow these steps **in order**:

### Step 1 — Archive the existing `index.html`
1. Read the current `index.html` file.
2. Extract the **main content topic/title** from the page (use the `<title>` tag or main headline — strip special characters, replace spaces with underscores, lowercase).
3. Get **today's date** in `YYYY-MM-DD` format.
4. Move (copy + delete original) `index.html` → `previous_news/{maincontent}{date}.html`
   - Example: `previous_news/tech_roundup2026-05-13.html`

### Step 2 — Set the new page as `index.html`
- The newly created magazine page becomes `index.html` in the root.

### Step 3 — Read GitHub credentials
- Open `credentials/github.json` (or the credentials folder).
- Extract: `username`, `repo`, `token`, `branch` (default: `main`).
- **Never print or expose the token in chat.**

### Step 4 — Push to GitHub
Use the GitHub API or `git` CLI to:
1. Commit and push the archived file to `previous_news/`.
2. Commit and push the new `index.html` to the repo root.
3. Confirm the live URL: `https://{username}.github.io/{repo}/`

---

## ✏️ Daily Magazine Creation Rules
- Each day's magazine is a **single self-contained HTML file** (CSS + JS inline).
- Always use today's date visibly in the magazine layout.
- Maintain consistent editorial branding across issues.
- The page must look polished and publication-ready before upload.

---

## ⚠️ Safety Rules
- Never expose GitHub tokens or credentials in chat or in any file other than the credentials folder.
- Always archive before overwriting `index.html` — no issue is ever lost.
- If `previous_news/` folder doesn't exist, create it before archiving.
- If no `index.html` exists yet (first run), skip the archive step and go straight to upload.
