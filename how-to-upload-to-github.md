# How to publish your two projects on GitHub — step by step (for beginners)

**Author:** Ana Eslava-Graterol (ProfeAnaEslavaEdTech) · Universitat Politècnica de València
**What this guide does:** takes you from *two ZIP files* to *two live websites*, with no coding and no command line — everything is done by **drag-and-drop in the browser**.

You will publish **two separate repositories** (a repository = one project folder on GitHub):

| # | ZIP you were given | GitHub repository to create | What it becomes |
|---|---|---|---|
| 1 | `repo-MLLDE.zip` | `mobilelanguagelearningdesingenviroment` | The **MLLDE** methodology site: PhD proposal + the 3 authoring tools |
| 2 | `repo-LanguagePassport.zip` | `edtech-mobile-json-lessons` | The **Language Passport** app + the world map (father → continents → countries) |

> 💡 **Tip:** do repository 1 completely, then repository 2. They are independent.

---

## Part 0 · One-time setup (only the first time ever)

1. Go to **https://github.com** and click **Sign up** (or **Sign in** if you already have an account).
   - Your username is **ProfeAnaEslavaEdTech** (that is what appears in your web addresses).
2. Verify your email when GitHub asks.
3. On your computer, **unzip** both ZIP files:
   - Windows: right-click the ZIP → **Extract All**.
   - Mac: double-click the ZIP.
   - You now have two normal folders you can open.

---

## Part 1 · Publish repository 1 — MLLDE

### 1.1 Create the repository
1. Sign in to GitHub. Top-right, click the **➕** → **New repository**.
2. **Repository name:** type exactly
   ```
   mobilelanguagelearningdesingenviroment
   ```
3. Set it to **Public** (required for the free website).
4. Leave every checkbox **unticked** (do **not** add a README — your ZIP already has one).
5. Click **Create repository**.

### 1.2 Upload the files (drag and drop)
1. On the new empty repository page, click the link **“uploading an existing file”**
   (or **Add file → Upload files**).
2. Open the **unzipped `repo-MLLDE` folder** on your computer.
3. Select **everything inside it** (Ctrl+A on Windows / Cmd+A on Mac) and **drag it onto the GitHub page**.
   - ✅ Drag the *contents* (the `index.html`, the `docs` folder, etc.), **not** the outer folder.
   - Wait until every file shows as uploaded (this can take a minute — there are PDFs).
4. Scroll down to **Commit changes** and click the green **Commit changes** button.

### 1.3 Turn on the website (GitHub Pages)
1. In the repository, click **Settings** (top menu).
2. Left menu → **Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. **Branch:** choose **main**, folder **/ (root)**, then click **Save**.
5. Wait 1–2 minutes, then refresh. GitHub shows a green box with your address:
   ```
   https://profeanaeslavaedtech.github.io/mobilelanguagelearningdesingenviroment/
   ```
   That is your live **MLLDE** site. 🎉

---

## Part 2 · Publish repository 2 — Language Passport

Repeat the same three moves with the second ZIP.

### 2.1 Create the repository
1. **➕ → New repository**.
2. **Repository name:** type exactly
   ```
   edtech-mobile-json-lessons
   ```
3. **Public**, no checkboxes ticked, **Create repository**.

### 2.2 Upload the files
1. **Add file → Upload files**.
2. Open the unzipped **`repo-LanguagePassport` folder**.
3. Select **everything inside it** and drag it onto the page.
   - This one has folders (`app`, `world`) — GitHub keeps the folders automatically. Just wait for all files.
4. **Commit changes**.

### 2.3 Turn on the website
1. **Settings → Pages → Deploy from a branch → main → / (root) → Save**.
2. After 1–2 minutes you get:
   ```
   https://profeanaeslavaedtech.github.io/edtech-mobile-json-lessons/
   ```
   - The **app** opens automatically.
   - The **world map** (father → continents → countries) is at:
     ```
     https://profeanaeslavaedtech.github.io/edtech-mobile-json-lessons/world/
     ```

---

## Part 3 · How to change something later

You never need to re-do everything. To update one file:

1. Open your repository on GitHub.
2. Click the file you want to change → the **✏️ pencil** icon → edit → **Commit changes**.

To add or replace many files: **Add file → Upload files** again and drag the new ones (same name = it replaces the old one).

The website refreshes itself 1–2 minutes after each commit.

---

## Part 4 · What is inside each repository

**Repository 1 — `mobilelanguagelearningdesingenviroment` (MLLDE):**
- `index.html` — the MLLDE home page (links to everything below)
- `docs/MLLDE-PhD-Research-Proposal.pdf` — the **PhD proposal**
- `curriculum-design-worksheet.html` — **(a)** the JSON curriculum maker
- `gpt-design-worksheet.html` — **(b)** the GPT maker
- `language-passport-level-creator.html` — **(c)** the Language Passport level maker
- `gpt-design.html` + `docs/gpt-records/` — the GPT designs & authorship records
- `docs/` — the Curriculum Master Document, theoretical framework and blueprints

**Repository 2 — `edtech-mobile-json-lessons` (Language Passport):**
- `index.html` — opens the app
- `app/` — the Language Passport app (works offline; installable)
- `world/` — the **father** (world) → **sons** (5 continents) → **grandsons** (countries) map

---

## Quick reference card

| I want to… | Do this |
|---|---|
| Make a new project | ➕ → New repository → name it → Public → Create |
| Add my files | Add file → Upload files → drag everything → Commit changes |
| Turn on the website | Settings → Pages → main → / (root) → Save |
| See my website | `https://profeanaeslavaedtech.github.io/<repository-name>/` |
| Change a file | Click the file → ✏️ → edit → Commit changes |

---

© 2024–2027 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved. · “Language Passport”™ · MLLDE
