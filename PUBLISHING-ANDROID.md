<!--
  Copyright © 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved.
  Proprietary — see ../LICENSE and ../NOTICE.
-->

# Publishing “Language Passport — Barcelona” to Google Play (Android)

**What you have:** `app/` is a self‑contained **Progressive Web App (PWA)** — an
installable, offline‑capable web app (HTML/CSS/JS + `manifest.webmanifest` +
`service-worker.js` + icons). The recommended way to get a *web* lesson onto
**Google Play** is to wrap it in a **Trusted Web Activity (TWA)** — a thin Android
container that runs your PWA full‑screen with no browser UI. You upload the
resulting **`.aab`** (Android App Bundle) to the Play Console.

You do **not** rewrite the lesson — the same files ship on the web *and* inside
the Android app.

```
app/ (PWA)  ──►  wrap as TWA  ──►  app-release-bundle.aab  ──►  Google Play
```

---

## 0. Prerequisites (one‑time)

| Need | Notes |
|---|---|
| **The PWA hosted over HTTPS** | e.g. GitHub Pages — see §1. A TWA loads your live URL. |
| **Google Play Developer account** | One‑time **US$25** at <https://play.google.com/console>. |
| **Node.js 18+** | Only for Method B (Bubblewrap). Method A needs no local tools. |
| **A signing key** | Generated for you by PWABuilder/Bubblewrap; **back it up** — you cannot update the app later without it. |

---

## 1. Host the PWA over HTTPS (GitHub Pages — free)

1. Push this repo to GitHub (branch `main`).
2. Repo **Settings → Pages → Build and deployment → Source: Deploy from a branch**,
   pick `main` / root, **Save**.
3. Your PWA will be live at:
   `https://<user>.github.io/portofolio/language-passport/app/`
4. Open it on an Android phone in Chrome → menu **⋮ → Install app** to confirm it
   installs and runs offline. (This install prompt is what makes it TWA‑ready.)

> Any HTTPS host works (Netlify, Cloudflare Pages, your own domain). Note the
> final URL — you’ll need it below.

---

## 2A. Method A — PWABuilder (easiest, no local tools) ✅ recommended

1. Go to **<https://www.pwabuilder.com>** and paste your hosted URL from §1.
2. It audits the manifest/service‑worker (both are already included here).
3. Click **Package for stores → Android**. Choose **“Google Play”** (signed
   TWA/AAB). Options to set:
   - **Package ID**: e.g. `com.profeanaeslava.langpassport` (must be unique, lowercase).
   - **App name**: `Language Passport — Barcelona`.
   - **Signing key**: let PWABuilder **generate** one, then **download and back up
     the key + the `assetlinks.json`** it gives you.
4. Download the ZIP → it contains **`app-release-bundle.aab`** and a
   **`assetlinks.json`**.
5. **Digital Asset Links (removes the browser address bar):** put the provided
   `assetlinks.json` at
   `language-passport/app/.well-known/assetlinks.json` **and/or** at your
   site root `/.well-known/assetlinks.json`, commit, and redeploy. This proves you
   own both the site and the app so the TWA runs full‑screen.
6. Go to **§3** to upload the `.aab`.

## 2B. Method B — Bubblewrap CLI (local, more control)

```bash
npm install -g @bubblewrap/cli

# point it at your hosted manifest
bubblewrap init --manifest https://<user>.github.io/portofolio/language-passport/app/manifest.webmanifest

# answer the prompts (package id, app name, key). Then:
bubblewrap build
# → produces app-release-bundle.aab  and a signing key (.keystore)  — BACK BOTH UP
```

Bubblewrap prints the SHA‑256 fingerprint and an `assetlinks.json`; host it as in
Method A step 5. Then continue to §3.

## 2C. Method C — Capacitor (fully offline, no server needed)

If you’d rather bundle the files **inside** the APK (no live URL required):

```bash
npm init -y && npm install @capacitor/core @capacitor/cli @capacitor/android
npx cap init "Language Passport" com.profeanaeslava.langpassport --web-dir=app
npx cap add android
npx cap copy
npx cap open android      # opens Android Studio → Build → Generate Signed Bundle (.aab)
```

Use this if the lesson must work with no internet at all (the service worker
already caches everything, but Capacitor guarantees a 100% offline package).

---

## 3. Upload to Google Play Console

1. <https://play.google.com/console> → **Create app** (name, language, “App”, free).
2. **Release → Testing → Internal testing → Create release** (start here, not
   Production). **Upload** your `app-release-bundle.aab`.
3. Complete the required declarations (Play won’t publish without them):
   - **Store listing** — title, short & full description, screenshots (use the
     ones from this project), the 512×512 icon (`app/icons/icon-512.png`),
     and a feature graphic (1024×500).
   - **Content rating** questionnaire → this app is *Everyone* (educational).
   - **Data safety** — declare the **microphone** use (the *Speak* reflection uses
     speech‑to‑text) and that data is processed on‑device / not collected.
   - **Target audience**, **Privacy policy URL** (a simple page is fine),
     **App access** (no login required).
4. Add testers (emails) to the internal track, **Save → Review release → Roll out**.
5. When you’re happy, promote the same build to **Production**. First reviews for a
   new developer account can take a few days.

---

## 4. After publishing — updating the app

- Change the **lesson content** → edit `app/index.html` (or its `DEST` data),
  push, redeploy. TWA users get the update **instantly** (it’s the live site) — no
  Play re‑submission needed.
- Change the **package** (icon, name, Android version) → rebuild the `.aab` **with
  the same signing key**, bump `versionCode`, upload a new release.

---

## 5. Checklist

- [ ] PWA live over HTTPS and installs on a phone (§1)
- [ ] `.aab` generated and **signing key backed up** (§2)
- [ ] `assetlinks.json` hosted under `/.well-known/` (removes the URL bar)
- [ ] Store listing, content rating, **data‑safety (microphone)** completed (§3)
- [ ] Internal test passed → promoted to Production

---

### Files in this package
| File | Purpose |
|---|---|
| `app/index.html` | The playable lesson (self‑contained). |
| `app/manifest.webmanifest` | PWA metadata — name, icons, colors, `standalone`. |
| `app/service-worker.js` | Offline caching of the app shell. |
| `app/icons/icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | App/launcher icons. |

> This lesson is one part of the **Mobile Language Learning Design Environment (MLLDE)**.
> © 2026 Ana Eslava‑Graterol (ProfeAnaEslavaEdTech). All Rights Reserved.
> “Language Passport”™. Referenced pedagogical frameworks © their respective authors.
