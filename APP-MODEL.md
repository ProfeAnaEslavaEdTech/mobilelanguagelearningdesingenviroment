# Language Passport — App Model & Design Rationale

**Author:** Ana Eslava-Graterol (ProfeAnaEslavaEdTech) · MLLDE
**Repository:** `edtech-mobile-json-lessons` · **App:** `app/index.html` (service-worker `lang-passport-v24`)
**Status:** ✅ built & registered — this is the standard model for the whole app.

This document is the single source of truth for how the Language Passport app is
structured, why each decision was made, and how to extend it. Every destination
ever added plugs into this model — it is **data, not a redesign**.

![World-tour map model](design/world-map-model.png)

---

## 1. One landing for the whole app

- The **"📖 El Tour" map is the ONLY landing** the learner sees.
- The repo root `index.html` **redirects straight into `app/index.html`** — no "Play/Explore" cards page, no intro screen.
- Header line: kicker **LANGUAGE PASSPORT** · title **📖 El Tour** · tagline **"Advance one conversation at a time."** · lead **"Choose a destination…"**.
- The top bar carries the learner's state everywhere: 🪙 coins · 🛂 stamps · 🤖 Grace · 🌙 theme · rank.

**Rationale:** one clear front door reduces choice friction; the map *is* the product. The tagline sets the pedagogical promise (one conversation at a time = manageable, low-anxiety).

## 2. Navigation model — Continent → Country → City → Lesson

A three-level drill-down (adopted after testing; replaces the earlier flat one-screen):

```
📖 El Tour (map)
  └── 🌍 Europe            (continent card)
        ├── España 🇪🇸 ›    (country → clickable)
        │     ├── Barcelona 🏛️  ▶ start / ✓ play again
        │     └── Sevilla   🍊  ▶ start / ✓ play again
        └── Italia 🇮🇹       (country → "Próximamente")
  └── 🌐 More continents   (Africa · Asia · America · Oceania — locked)
```

- **Continents** are cards (🌍 Europe …). **Countries** are clickable rows *inside* a continent — **a country is never shown as a continent**.
- Tapping a **built country** (España) opens a **country screen** (`openCountry`) with a `← El Tour` back link and its cities.
- Tapping a **coming-soon country** (Italia) shows a **"Coming soon · Próximamente"** toast.
- Tapping a **city** starts its lesson.

**Rationale:** mirrors real geography (continent ▸ country ▸ city), scales cleanly as countries multiply, and keeps each screen short on a phone. Italy proved the model: it appears as a country inside Europe, not a separate section.

## 3. Flags — inline SVG, not emoji

Country flags are drawn as **inline SVG**, e.g. Spain (horizontal red-yellow-red) and Italy (vertical green-white-red), via `flagSvg(countryName)`.

**Rationale:** Windows browsers render flag emoji (`🇪🇸`) as the letters **"ES"** — SVG shows a real flag on every platform (Windows, Mac, phones). This is the reusable recipe for every future country (only colours / stripe direction change).

## 4. City icons

Each city has its own `icon` (Barcelona 🏛️, Sevilla 🍊); it falls back to the country flag if none is set.

**Rationale:** a memorable, place-specific mark reads faster than repeating the flag on every city.

## 5. Locked continents & coming-soon countries

- **Africa · Asia · America · Oceania** are locked (🔒, "Próximamente"); tapping shows a gentle "Coming soon" toast.
- Countries teased before they're built live in `COUNTRIES_SOON` and render as clickable "Próximamente" rows inside their continent (e.g. **Italia**).

**Rationale:** shows the roadmap and the ambition (a whole world) without dead ends or empty screens; "America" (singular) per request.

## 6. Restart

A **"↺ Restart my journey (reset to 0)"** link on the map clears the wallet and every `lp-prog-*` key back to 0.

**Rationale:** the app already defaults new users to 0 coins / 0 stamps / Hitchhiker; progress persists per browser. Restart lets a learner (or a tester on a shared device) start fresh — and confirms the "start at 0" expectation.

## 7. Grace (AI mentor) — icon & safety

- Grace's icon is **🤖** everywhere (header, panels, mentor blurb, the "Pregúntale a Grace" feedback button).
- Opening Grace always shows a **one-time-per-tap ChatGPT warning** *before* leaving the app: it opens **ChatGPT (OpenAI)**, may need an account or a paid OpenAI plan, messages go to OpenAI under its Terms & Privacy, don't share sensitive data, data charges may apply. Buttons: **🤖 I understand — open ChatGPT ↗** / **Cancel — I'll stay in Language Passport**.

**Rationale:** 🤖 signals "AI" unambiguously; the warning is informed-consent for a paid third-party service and appears every time so it's never missed.

## 8. Learner view is clean — theory stays in the docs

- Each lesson step shows only its **plain instruction**; the **Objective** card opens the lesson.
- **No pedagogical/theory citations in the UI** (removed "Dual-coding — Mayer", "REACT — CORD/Crawford", "ESA Study", etc.).
- The output/transfer step is labelled **"Don't give up!"** (encouraging, never "fail").

**Rationale:** learners need clarity and encouragement, not academic apparatus. The frameworks remain fully credited in the methodology docs (`../docs/mllde-curriculum-master.md`, `../docs/theoretical-framework.md`, the GPT records) — the right audience, not the learner UI. The mandatory **Immediate Assessment** standard (non-punitive amber + 🤔, retry, Ask-Grace) is defined in the master doc §8.1.

## 9. The lesson cycle (unchanged, per city)

Arrival (hook + **Objective**) → Vocabulary → Chunks → Model dialogue → Gap-fill → **Mission** (authentic assessment) → **Immediate Assessment "Don't give up!"** (Speak/Write + instant feedback + Ask-Grace) → Culture → Rewards (coins, stamp, souvenirs, rank-up).

## 10. How to add a new destination (replicable rule)

Adding a city or country **never changes this model** — it is data:

1. **A whole country, playable:** add each city to `DESTS` (with `continent`, `countryName`, `flag`, city `icon`, and the full lesson data) and add its ids to `JOURNEY`. It auto-appears as a clickable country under its continent.
2. **A country teaser (not built yet):** add it to `COUNTRIES_SOON` with `continent`, `countryName`, and cities — it renders as a "Próximamente" row.
3. **Its flag:** add one entry to `flagSvg()` (colours + stripe direction).
4. **A new continent:** it appears automatically once a country references it; remove it from `CONTINENTS_SOON` when it has content.

This is the Language Passport realisation of the MLLDE **engine + data** principle (`../docs/mllde-curriculum-master.md` §6.1): the model is fixed; destinations are data.

## 10a. Brand mark (logo)

The **Language Passport** mark is an **L + P speech bubble**: a solid indigo P/D
bubble with a **chat tail** and the letter **L carved in negative space** — signalling
*language + conversation + the passport journey*. Master asset: `app/icons/logo-mark.svg`.

- **Favicon / tab:** `icons/logo-mark.svg` (crisp SVG, theme-independent).
- **App / home-screen icons:** `icons/icon-192.png`, `icon-512.png`, `icon-maskable-512.png`
  — indigo mark on a white tile (L reads white).
- **In-app:** the mark renders next to the "Language Passport" kicker on El Tour, in
  `currentColor` so it adapts to light/dark via `--brand-accent`.
- Colours: indigo `#5B4FE5` (light) / `#8B80F0` (dark); white counter for the L.

## 11. Design tokens (semantic system · WCAG AA)

The app uses a **centralized semantic-token layer** (light + dark), brand kept indigo:

| Token | Light | Dark | Use |
|---|---|---|---|
| `--bg-canvas` | `#F8F9FC` | `#0E1326` | app background |
| `--bg-surface` | `#FFFFFF` | `#1A1F36` | cards |
| `--text-primary` | `#111827` | `#FFFFFF` | headings, active |
| `--text-secondary` | `#4B5563` | `#9CA3AF` | descriptions (AA) |
| `--text-muted` | `#6B7280` | `#D1D5DB` | "Próximamente" / locked (AA) |
| `--border-subtle` | `#E5E7EB` | `#2D354E` | borders, dashed timeline |
| `--brand-accent` | `#5B4FE5` | `#8B80F0` | links, chevrons, primary |
| `--brand-warning` | `#E8A33D` | `#E8A33D` | locks 🔒, coins 🪙 |
| `--card-shadow` | soft | soft | card elevation |

- **WCAG AA**: text ≥ 4.5:1, interactive/borders ≥ 3:1. Legacy variable names (`--ink`, `--muted`, `--line`, `--bg`, `--card`) alias these tokens, so the whole app inherits the fixes.
- Country row = flag SVG in a transparent dot; city row = round chip with the city icon; **continuous dashed timeline** stretches the full route.
- Light/dark aware; offline-first PWA; installable.

---

## Change log & rationale (this iteration)

| # | Change | Why |
|---|---|---|
| 1 | Step 6 label **"Reflexión" → "Don't give up!"** | Encouraging, non-punitive framing |
| 2 | **Map is the only landing** (root redirects into the app) | One clear front door; the map is the product |
| 3 | **Continent → Country → City** drill-down; Europe holds España + Italia as clickable countries | Matches geography; scales; a country is not a continent |
| 4 | **City icons** Barcelona 🏛️ / Sevilla 🍊 | Faster, place-specific recognition |
| 5 | **Inline-SVG flags** (`flagSvg`) | Windows shows flag emoji as "ES"/"IT"; SVG shows a real flag everywhere |
| 6 | **Italy added** under Europe (front-page teaser, not built) | Show the roadmap without empty lessons |
| 7 | **El Tour** title + tagline; **America** (no s) | Product voice; requested wording |
| 8 | **Grace 🤖** everywhere + **every-time ChatGPT cost warning** | Clear AI signal; informed consent for a paid third-party service |
| 9 | **Removed theory citations** from the learner UI | Clarity for learners; theory stays in the docs |
| 10 | **↺ Restart my journey** reset-to-0 | Fresh start for learners/testers |

_Visual record: `design/world-map-model.png` · clickable mock: `design/world-map-model-mock.html`._

© 2024–2027 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved. · “Language Passport”™ · MLLDE
