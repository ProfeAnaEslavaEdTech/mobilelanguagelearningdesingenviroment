<!--
  Copyright © 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved.
  Proprietary — see ../LICENSE and ../NOTICE.
-->

# Project status & handoff — Mobile Language Learning Design Environment (MLLDE)

**Owner:** Ana Eslava-Graterol (ProfeAnaEslavaEdTech) · **Updated:** 2026-07-21 ·
**Branch:** `claude/new-project-0mpfp7` · **Local commits pending push:** 22

> Read this first to resume. It captures the whole project, every decision, what’s
> built, what’s pending, and the next steps. The Barcelona lesson is a working,
> **Android/Play-ready PWA** (see `PUBLISHING-ANDROID.md`).

---

## 1. What this project is

A **Mobile Language Learning Design Environment (MLLDE)** — a replicable, gamified method
for 5-minute mobile language lessons. It is the protected umbrella work.

```
Mobile Language Learning Design Environment (MLLDE)   ← the copyrighted umbrella
   (theory · blueprint · worksheet · methodology · GPT design)
      └── "Language Passport"                 ← the game (engine + data)
              ├── Barcelona — De Tapas Por La Rambla   ✅ playable
              ├── Sevilla — De Bares por Santa Cruz    ✅ playable
              └── Africa · Asia · America · Oceania   🔒 próximamente
```

**Game master:** **Grace** 🌊 — an empathic, free-spirited, ocean-loving foodie
travel agent. She is the **Pro-tier AI** (a Custom GPT / LLM); her full design and
system prompt are in `docs/grace-gpt-design.md`.

**Grounding frameworks** (each credited to its author): SAM (Allen) · G-CLIL / IPO
(Casañ-Pitarch) · CLIL 4Cs (Coyle) · ESA (Harmer) · CTL (Johnson) · REACT
(CORD/Crawford) · dual-coding (Mayer) · lexical chunks (Lewis) · pragmatics
(Kasper & Rose) · Mobile Learning Design (**Clothier, 2026, Routledge**) · UI/UX
(Apple HIG, Google Material).

---

## 2. Decisions locked in

- **Two portfolio versions** — *Before* = original Canva export (reference);
  *After* = the game.
- **Hybrid tiers** — **Free** = offline, scripted branching camarero (built);
  **Pro** = **Grace live** as a **Custom GPT** — the app’s **🤖 button** opens her
  ChatGPT link (no API key), behind a one-time-per-tap **third-party/cost warning**.
  GPT link + design in `docs/grace-gpt-design.md`.
- **Scope** — vertical slice: Barcelona fully playable; other continents teased.
- **Lesson lengths** — 5 / 10 / 15 min (worksheet scales content).
- **Narrative / economy** — Hitchhiker → Travel Ambassador; **global wallet**
  (coins persist across lessons); passport stamps; **pick one souvenir** (place
  emoji) into the carry-on bag; **world map** of 5 continents (Europe ✓, others
  “coming soon”); level-complete Canva video on the passport screen.
- **Vocabulary** — emoji images with a named animation the **hint replays**;
  plus **lexical chunks** and categorized **culture & pragmatics** cards.
- **Design** — matches the metadiscourse **Data Book**: indigo `#5B4FE5` + gold
  `#E8A33D`, Inter, **light/dark toggle**. Self-contained / offline PWA.
- **Navigation & UX model (see [`APP-MODEL.md`](APP-MODEL.md))** — the **“📖 El Tour”
  map is the only landing** (root redirects into the app); **Continent → Country →
  City → lesson** drill-down (Europe → España/Italia as clickable countries);
  **inline-SVG flags** (emoji flags show as “ES” on Windows); per-city icons
  (Barcelona 🏛️ / Sevilla 🍊); **clean learner UI** (no theory citations; output
  step titled **“Don’t give up!”**); **↺ Restart** reset-to-0. Full rationale +
  change log in `APP-MODEL.md`.
- **IP** — proprietary “All Rights Reserved”; “Language Passport”™ & “Grace”;
  **no patent filed** (nothing marked patent-pending).

---

## 3. What’s built (files)

| File | What it is | Status |
|---|---|---|
| `docs/theoretical-framework.md` | The mind-map framework, transcribed | ✅ |
| `docs/curriculum-design-blueprint.md` | Design contract + Destination Schema | ✅ |
| `docs/Language-Passport-Curriculum-Blueprint.pdf` | Styled PDF of the blueprint | ✅ |
| `docs/gpt-design-blueprint.md` | Blank 21-section GPT design template | ✅ |
| `docs/grace-gpt-design.md` | **Grace** populated instance + paste-ready system prompt (§22) | ✅ |
| `docs/sources/…xlsx` | Source literature matrix | ✅ |
| `language-passport/language-passport-level-creator.html` | Language Passport level creator — opens blank; loads Barcelona/Sevilla examples (5/10/15-min, chunks, culture cats, attributions, dark mode) | ✅ |
| `mllde/curriculum-design-worksheet.html` | Generic MLLDE worksheet — author lessons for a **new language / app** | ✅ |
| `language-passport/app/index.html` | **Multi-destination app** (engine + data): **Barcelona + Sevilla** lessons, **“El Tour” map** with **Continent → Country → City** drill-down, full IPO flow, global wallet, souvenir shop, level video, TTS/STT, **Grace (🤖) via her Custom GPT link** (with cost warning), **↺ Restart**, **fixed light/dark** (root themed), offline. Add a city = one `DESTS` entry. | ✅ |
| `language-passport/APP-MODEL.md` | **App model & design rationale** — navigation model, flags, learner-UI rules, replicable rule, change log | ✅ |
| `language-passport/app/manifest.webmanifest` · `service-worker.js` · `icons/*` | PWA packaging (Play-ready) | ✅ |
| `language-passport/PUBLISHING-ANDROID.md` | Google Play guide (TWA / PWABuilder / Bubblewrap / Capacitor) | ✅ |
| `examples/de-tapas-por-la-rambla.original.html` | Original Canva lesson (the “Before”) | ✅ |
| `LICENSE` · `NOTICE` | Proprietary license + ownership/patent notice | ✅ |

---

## 4. Uploading it as an app (Android / Google Play)

The Barcelona lesson is a complete **PWA**, ready to wrap as a **TWA** and publish.
Quick path (full detail in `PUBLISHING-ANDROID.md`):

1. **Host over HTTPS** (GitHub Pages): after write access is enabled and the branch
   is pushed → Settings → Pages → deploy `main` →
   `https://<user>.github.io/portofolio/language-passport/app/`.
2. **Package** with **PWABuilder** (paste the URL → download signed `.aab`) — or
   Bubblewrap / Capacitor. **Back up the signing key.**
3. **Google Play Console** (US$25 one-time): upload the `.aab`, complete store
   listing + content rating + **data safety (microphone)**, test, then release.
4. **Digital Asset Links** (`/.well-known/assetlinks.json`) to drop the URL bar.

> **Pro-AI note for release:** the in-app Grace key entry is demo-only. For a
> published app, proxy Grace’s API call through a backend so no key ships to the
> client (a TODO below).

---

## 5. ⚠️ Blocker to resolve first

**Cannot push to GitHub — 403 (read-only).** Both `git push` and the GitHub API
integration are denied for this session. All **15 commits exist locally only** and
are lost if the container is recycled. Files are also delivered in chat as backups.

**Fix:** grant the Claude GitHub App **write access** to
`ProfeAnaEslavaEdTech/portofolio`, then `git push -u origin claude/new-project-0mpfp7`.

### Pending (unpushed) commits — newest first (22, incl. this handoff update)
```
bfced29 Fix dark-mode contrast + stale-cache (theme now applies everywhere)
a636901 Update README to present Language Passport curriculum + data book
17384ac Call Grace via her Custom GPT link instead of an API key
52a387c Add step-by-step lesson: how to create an app mockup
3f04a8c Multi-destination app + add Sevilla; rename barcelona/ → app/
d50dbcc Update project handoff with today's work
6e3bd01 Populate GPT blueprint for Grace + wire her as the live Pro AI
1930189 Store GPT Design Blueprint (master template for Grace, the Pro AI)
63fdbed Global wallet, souvenir shop, world map, and game master Grace
ec7c8dd Add level-complete Canva video to the passport screen
70d7f6c Add project status & handoff doc for resuming tomorrow
9d6d958 Build Barcelona Language Passport lesson (PWA) + Android publishing guide
d4a324a Add dark-mode toggle; credit Paul Clothier; re-theme blueprint PDF
cd7f639 Expand worksheet + re-skin to Data Book design
fa80520 Rescope IP to the Curriculum; Language Passport is one lesson
013fed1 Add proprietary license, ownership notice, and copyright headers
2c9b3e3 Add curriculum design worksheet (interactive HTML authoring tool)
5841438 Add PDF render of the curriculum design blueprint
d2c400d Add curriculum design blueprint and source matrix
d29a5ec Add original Canva lesson export as reference
6ade68e Add theoretical framework for mobile learning design tool
```

---

## 6. Next steps (keep building)

1. **Push to GitHub** — enable write access, push the branch (do first).
2. **Backend proxy for Grace** — hide the API key for a production Pro tier.
3. **Store-listing kit** — screenshots + Play description + feature graphic.
4. **Second destination** (e.g. Roma) — author one `DEST` data object to prove the
   engine + data replicability; wire it into the world map.
5. **Sync the blueprint’s Destination Schema** to include duration + chunks +
   culture categories + wallet/souvenirs/continents (so doc matches the build).
6. Optional: portfolio **Before ↔ After** index page; XP/skill-tree; analytics.

---

## 7. How to resume

- Everything is on branch **`claude/new-project-0mpfp7`** under `language-passport/`
  and `docs/`.
- **Play the lesson:** open `language-passport/app/index.html` in Chrome/Edge
  (speech + Grace’s live chat work best there). Enable Grace via the **✨** button.
- **Author a Language Passport lesson:** open `language-passport/language-passport-level-creator.html` (blank; Barcelona/Sevilla examples loadable).
- **Author for a new language / app:** open `mllde/curriculum-design-worksheet.html`.
- **Grace’s brain:** `docs/grace-gpt-design.md` (system prompt in §22); it’s also in
  the app at `DEST.mission.proSystem`.
- **Design rules:** `docs/curriculum-design-blueprint.md` (§7 = Destination Schema).

*© 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved. ·
“Language Passport”™ is one lesson of this Curriculum.*
