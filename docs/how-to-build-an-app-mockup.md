<!--
  Copyright © 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved.
  Proprietary — see ../LICENSE and ../NOTICE. "Language Passport"™.
-->

# How to create an app mockup — a step-by-step lesson

> **What you’ll learn:** how to turn a lesson idea into a **working, installable app
> mockup** using the Language Passport toolkit — no app-store account or coding
> bootcamp required. By the end you’ll have a playable lesson you can open on a
> phone, install, and (optionally) publish to Google Play.

**Who it’s for:** educators and designers. **Time:** ~60–90 minutes for your first
one; ~20 minutes once you know the flow. **You need:** a computer, the Chrome or
Edge browser, and the project folder. That’s it.

---

## The big idea (read this first)

A good mockup keeps **three things separate** — the same separation used in the
GPT Design Blueprint:

| Layer | Question it answers | In this project |
|---|---|---|
| **1. Engine** | *How does the app behave?* | `language-passport/app/index.html` (already built — you reuse it) |
| **2. Design** | *How does the game work?* | your **content**: a destination data object (`DESTS` entry) |
| **3. Knowledge** | *What does it teach?* | your curriculum (vocab, chunks, mission, culture) |

**You do not rebuild the engine.** You only write **Layer 2 + 3** — one data object —
and the engine turns it into a playable app. That’s the whole trick.

The pipeline:

```
Idea → Blueprint → Worksheet → Data object → Preview → Brand → Install (PWA) → Package (Android)
```

---

## Step 1 — Frame the idea (5 min)

Open `docs/curriculum-design-blueprint.md`. Decide, in one sentence each:

- **Scenario / real-world genre** — e.g. *“ordering breakfast in a Roman café.”*
- **Level** — e.g. A1–A2.
- **Objective (active verb) + benefit** — *“Order a coffee and a cornetto in Italian
  — so you can start your day like a local.”*

> 💡 Grounded in **CTL** (Johnson): a real context + a personal benefit = motivation.

---

## Step 2 — Author it in the Worksheet (20 min)

Open `mllde/curriculum-design-worksheet.html` in your browser (the generic worksheet — for a **new** language / app). For a **Language Passport** lesson, use `language-passport/language-passport-level-creator.html` instead (it opens blank and can load the Barcelona/Sevilla examples).

1. Set the **lesson length** (5 / 10 / 15 min) — the guide tells you how much content
   to add.
2. Fill the sections top-to-bottom: basics, objective, CLIL 4Cs, narrative,
   **vocabulary** (with an emoji + animation each), **chunks**, dialogue, drills,
   the **NPC mission**, reflection, **culture & pragmatics cards**, rewards.
3. Click **💾 Save (JSON)**. You now have `worksheet-<yourcity>.json` — your design,
   captured.

> 💡 The worksheet mirrors the **Destination Schema** (blueprint §7). Every field you
> fill maps to one field in the data object you’ll create next.

---

## Step 3 — Turn it into a data object (15 min)

Open `language-passport/app/index.html` in a text editor. Find the
`DESTS.barcelona = { … }` block and **copy it** as a template. Paste a new block and
rename it to your city, then swap in your worksheet content. Example (a new Roma
lesson):

```js
DESTS.roma = {
  id:"roma", city:"Roma", country:"Italy", flag:"🇮🇹",
  language:"Italian", langCode:"it-IT", level:"A1–A2",
  title:"Colazione al Bar",
  scenario:"Ordering breakfast at a Roman café",
  objective:"Order a coffee and a cornetto like a local",
  benefit:"…so you can start your Roman day the right way.",
  identityFrom:"Hitchhiker", identityTo:"Travel Ambassador",
  mentor:{ name:"Grace", emoji:"🌊", bio:"…", aiPrompt:"…" },

  vocab:[
    {es:"un cappuccino", en:"a cappuccino", emoji:"☕", anim:"popIn"},
    {es:"un cornetto",   en:"a croissant",  emoji:"🥐", anim:"slideUp"}
    // …add as many as your lesson length allows
  ],
  chunks:[ {es:"vorrei…", en:"I’d like…", fn:"requesting", emoji:"🙏", anim:"popIn"} ],
  dialogue:[ {who:"Barista", side:"a", es:"Buongiorno! Cosa desidera?"} ],
  gapfill:[ {before:"Vorrei un ", answer:"cappuccino", after:", per favore."} ],
  mission:{ npc:"Barista", energy:3, coinsGoal:80,
            proSystem:"You are Grace… (Rome café, order 1 coffee + 1 pastry politely)…",
            steps:[ /* say + 3 choices, one ok:true */ ] },
  reflection:{ oral:["Record a vlog…"], written:"Write a postcard…",
               targets:["cappuccino","cornetto","roma"] },
  culture:[ {cat:"Art", icon:"🏛️", title:"Il Colosseo", body:"…"} ],
  rewards:{ stamp:"Roma 🇮🇹", rankUp:"Buongustaio",
            souvenirs:[ {name:"Colosseo", emoji:"🏛️", cost:40} ],
            levelEndVideo:"…", levelEndLink:"…" }
};
```

Then add your city to the journey (one line):

```js
const JOURNEY = ["barcelona","seville","roma"];
```

> ✅ **That’s the entire build.** No new screens, no engine changes — the mission,
> wallet, souvenirs, map, TTS and dark mode all work automatically from your data.

**Field cheat-sheet** (worksheet → data):

| Worksheet section | Data field |
|---|---|
| Lesson basics | `id, city, country, flag, language, langCode, level, title, scenario` |
| Objective | `objective, benefit` |
| Vocabulary | `vocab: [{es,en,emoji,anim}]` |
| Chunks | `chunks: [{es,en,fn,emoji,anim}]` |
| Dialogue | `dialogue: [{who,side,es}]` |
| Drills | `gapfill: [{before,answer,after}]` |
| NPC mission | `mission: {npc,energy,coinsGoal,proSystem,steps}` |
| Reflection | `reflection: {oral,written,targets}` |
| Culture cards | `culture: [{cat,icon,title,body}]` |
| Rewards | `rewards: {stamp,rankUp,souvenirs,levelEndVideo}` |

---

## Step 4 — Preview the mockup (2 min)

Double-click `language-passport/app/index.html` to open it in Chrome/Edge. On the
**journey map**, tap your new city and play through it. Check: does the vocab speak
(🔊)? does the mission work? does the reward screen show your stamp/souvenirs?

> 🎤 **Speech** (text-to-speech + the mic) works best in **Chrome/Edge**.
> 🖥️ Tip: press **F12 → Console** to catch typos in your data object (a missing comma
> is the #1 first-timer bug).

---

## Step 5 — Brand it (optional, 10 min)

The look already matches the **Data Book** design (indigo + gold, light/dark). To
recolor, edit the CSS variables at the top of `index.html`:

```css
:root{ --indigo:#5B4FE5; --gold:#E8A33D; /* change these */ }
```

Keep the light **and** dark values in sync (`:root[data-theme="dark"]{…}`).

---

## Step 6 — Make it installable (PWA) (5 min)

Your mockup is already a **Progressive Web App** — an installable, offline app. The
three pieces are in `language-passport/app/`:

- `manifest.webmanifest` — the app’s name, colors, and icons.
- `service-worker.js` — caches the app so it works offline.
- `icons/` — the launcher icons.

Edit the **name/description** in `manifest.webmanifest` if you like. To test the
install: host the folder (Step 8) and, on a phone, open it in Chrome → **⋮ → Install
app**. It now lives on the home screen like a real app.

---

## Step 7 — Package for Android / Google Play (optional)

When you want it in the Play Store, follow **`language-passport/PUBLISHING-ANDROID.md`**:
host the app over HTTPS, run it through **PWABuilder** to get a signed `.aab`, and
upload to the Play Console. (No native coding — the PWA *is* the app.)

---

## Step 8 — Share the mockup (2 min)

Pick one:

- **Fastest:** send the single `index.html` file — anyone can open it in a browser.
- **Best link:** enable **GitHub Pages** on the repo → your app is live at
  `https://<user>.github.io/portofolio/language-passport/app/`.
- **On a phone:** open that link in Chrome and **Install app**.

---

## Quick checklist

- [ ] Scenario + objective + benefit written (Step 1)
- [ ] Worksheet filled and **saved as JSON** (Step 2)
- [ ] New `DESTS.<city>` object added + city in `JOURNEY` (Step 3)
- [ ] Played through with no Console errors (Step 4)
- [ ] (Optional) rebranded, PWA name set (Steps 5–6)
- [ ] (Optional) `.aab` built + uploaded (Step 7)
- [ ] Shared as a file or a GitHub Pages link (Step 8)

---

## Common first-timer fixes

| Symptom | Fix |
|---|---|
| Blank screen | A syntax error in your data object — open **F12 → Console**, look for the red line (usually a missing comma or quote). |
| City not on the map | You forgot to add it to `const JOURNEY = [...]`. |
| No sound | Use Chrome/Edge; the browser needs one tap before it will speak. |
| Grace (Pro AI) errors | Check the API key/model in the ✨ sheet, or turn Pro off to use the scripted mission. |
| Emoji looks like a box | That device lacks that emoji font — pick a more common emoji. |

---

*This lesson is part of the **Mobile Language Learning Design Environment (MLLDE)**.
© 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved. ·
“Language Passport”™. Referenced pedagogical frameworks © their respective authors.*
