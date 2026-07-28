<!--
  Mobile Language Learning Design Environment (MLLDE) — Curriculum Design Blueprint
  Copyright © 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved.
  Proprietary and confidential. See LICENSE and NOTICE. "Language Passport"™ is one
  lesson of this Curriculum. No patent filed or granted.
-->

# Curriculum Design Blueprint
## Mobile Language Learning Design Environment (MLLDE) — a replicable framework for gamified, 5-minute mobile language lessons

> © 2026 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved. · Proprietary — see [LICENSE](../LICENSE)
>
> *This blueprint is the framework for the whole Curriculum. **“Language Passport”** — the Barcelona *De Tapas Por La Rambla* travel-quest — is **one lesson** built from it, used throughout as the worked example.*

**Status:** v1.0 (design contract) · **Level:** A1–A2, millennial learners · **First build:** Barcelona — *De Tapas Por La Rambla*

This blueprint is the **replicable design contract** behind the Language Passport
game. It is deliberately **destination- and language-agnostic**: the game is an
*engine + data* system, and a new city or language is authored by filling the
[Destination Schema](#7-the-replicable-destination-schema) — not by rewriting
code. Everything here is grounded in the attached source matrix
(*Educational Resources and Research on Digital Learning*); citations use `[S#]`
keyed to [Sources](#12-sources).

---

## 1. Design goal

Deliver **standalone 5-minute mobile missions** that take an A1–A2 learner from
passive exposure to **authentic communicative output**, wrapped in a travel
narrative and a persistent gamified economy — replicable across destinations and
languages, and shippable in two tiers (free/offline and Pro/AI).

Mobile learning demands its *own* design logic, distinct from e-learning:
brevity, relevance, and usability for fragmented attention `[S3]`. 25% of users
abandon an app after a single use `[S9]`, so every second of the 5-minute loop
must earn the next.

---

## 2. Theoretical foundations (synthesised from the source matrix)

| Framework | Contribution to the design | Source |
|---|---|---|
| **SAM** (Successive Approximation Model) | Agile build method: Preparation → Iterative Design (Savvy Start) → Iterative Development (Alpha/Beta/Gold). Rapid prototyping over linear planning. | `[S-SAM]` |
| **G-CLIL** (Gamified CLIL) | Four-ring concentric model: game mechanics *are* language tasks; disciplinary genre is the structural engine; narrative beats = identity formation. | `[S-GCLIL]` |
| **CLIL 4Cs** (Coyle) | Content · Communication · Cognition · Culture — every mission must touch all four. | `[S-GCLIL]` |
| **IPO** (Casañ-Pitarch) | Input → Processing → Output cycle: encounter, manipulate, deploy language. | `[S-IPO]` |
| **ESA** (Harmer) | Session-level sequencing: Engage → Study → Activate; variants Straight Arrow / Boomerang / Patchwork. | `[S-ESA]` |
| **CTL** (Johnson) | Brain-compatible learning via 8 components + authentic assessment. | `[S-CTL8]` |
| **REACT** | Relating · Experiencing · Applying · Cooperating · Transferring — CTL made actionable. | `[S-REACT]` |
| **Mobile Learning Design** | Context-driven design, microlearning, empathy-based design, Bloom's adaptation, "Using AI" prompts. | `[S3]` |
| **GenAI competency (e-learning principles)** | Multimedia, pre-training, learn-by-doing, scaffolding; equitable gains. | `[S4]` |
| **Responsible Human–AI Collaboration** | AI mentor scaffolds, never replaces, the learner; AI is a tutor, not an answer key. | `[S-AWJ]` |
| **UI/UX best practices + HIG / Material** | Progressive disclosure, low cognitive load, touch targets, meaningful motion. | `[S9]` |
| **AWJ precedent** | Narrative identity arc (Novice→Professor Prodigy) + AI mentor as a proven pattern. | `[S-AWJ]` |

---

## 3. The integrated design model

The frameworks are not alternatives — they nest:

```
SAM  ── how we BUILD it (agile, iterative)
 └─ G-CLIL 4 Rings ── how the GAME is STRUCTURED
     └─ Ring 1  Disciplinary genre & content   (the "why": real scenario)
        Ring 2  Pedagogical purpose            (CTL objectives, ESA phase)
        Ring 3  Game genre                      (role-play travel sim)
        Ring 4  Mechanics/dynamics/emotions     (coins, souvenirs, energy…)
         └─ IPO × ESA ── how each 5-min SESSION FLOWS
             └─ CTL + REACT ── how learning stays MEANINGFUL & AUTHENTIC
                 └─ Mobile UX + GenAI principles ── how it FEELS on a phone
```

**Session sequencing — IPO mapped to ESA:**

| Loop phase | IPO | ESA | CTL / REACT |
|---|---|---|---|
| Arrive (narrative hook) | — | **Engage** | Relating |
| Vocabulary (animated images) | **Input** | Study | Experiencing |
| Drills (gap-fill, drag-match) | **Processing** | Study | Applying |
| NPC ordering mission | **Output** | **Activate** | Applying · Cooperating |
| Reflection (podcast/postcard) | **Output** | Activate | Transferring |

---

## 4. Narrative & identity (G-CLIL Ring 3 + AWJ pattern)

- **Arc:** the learner rises **from Hitchhiker → Travel Ambassador**, echoing the
  proven AWJ identity transformation (Novice Writer → Professor Prodigy) `[S-AWJ]`.
- **AI mentor:** a friendly travel-guide mentor scaffolds the learner (the
  Language Passport analogue of PhD Chema), giving **hints, never answers** —
  Responsible Human–AI Collaboration `[S-AWJ]`.
- **Narrative transportation:** learner **choices advance the plot and carry
  consequences** (ordering wrong drains energy) — they are a participant, not a
  spectator.
- Each destination is a **stamped page** in a growing story; the passport is the
  spine of the narrative.

---

## 5. Vocabulary as animated dual-coded images (new core principle)

Grounded in the **multimedia principle** — people learn better from words + images
than words alone — and consistent-cue retrieval `[S4]`, reinforced by mobile
brevity/relevance `[S3]`:

1. **Every vocabulary item carries an image** (offline: an **inline SVG
   illustration**, e.g. *patatas bravas*, *tortilla*, *cervecilla*, *pinchos*).
2. On **Input**, each image plays a **defined entrance animation** (e.g. a themed
   "pop-in": scale + fade + slight rotate). The animation is a **named property of
   the vocab item**, not incidental styling.
3. When the term is later needed and the learner taps **"pista / hint"** during
   Processing or the NPC mission, the **same image replays the exact same
   animation** in a hint popover.
4. **Why:** identical encoding and retrieval cues strengthen the memory trace and
   give the learner a stable, recognisable anchor — the picture *is* the mnemonic.

**Spec:** `vocab[i] = { term, translation, svg, anim }` where `anim` is one of a
small named set (`popIn`, `slideUp`, `flip`…). The Input renderer and the hint
renderer call the **same** animation routine, guaranteeing they match.

---

## 6. Objectives & authentic assessment (CTL)

**Action-oriented objectives** — state the knowledge with active verbs, and state
the **benefit** so the learner sees personal meaning `[S-CTL8]`:

> *"By the end of this mission you will **order** food and drinks at a Spanish bar
> like a local — so you'll never freeze at a counter in Barcelona again."*

**Authentic assessment**, not multiple-choice `[S-CTL8]`: the learner is judged on
**real in-game performance** — successfully getting the *camarero* to serve a full
order **before the energy/hambre meter empties**. "Excellent achievement" =
complete order + correct register (`nos pone…`) + no energy lost.

Each mission touches all **CLIL 4Cs**: Content (tapas domain), Communication
(ordering), Cognition (choosing register/quantities), Culture (La Rambla facts).

---

## 7. The replicable Destination Schema

**This is the replicability engine.** New destination/language = new data object;
the engine is untouched.

```js
Destination = {
  id, city, country, language, flag,          // "barcelona","Spain","es-ES","🇪🇸"
  level,                                       // "A1-A2"
  genre,                                       // disciplinary genre / scenario
  objective: { verbStatement, benefit, excellentAchievement },   // CTL
  fourCs: { content, communication, cognition, culture },        // CLIL

  narrative: { arrivalHook, identityFrom, identityTo, mentorName, mentorAvatar },

  vocab: [ { term, translation, svg, anim } ],                   // §5 animated images

  model: [ { speaker, text } ],               // Input dialogue (TTS)

  processing: {
    gapFill:   [ { sentence, answer } ],
    dragMatch: [ { term, target } ]
  },

  mission: {                                  // Output — authentic assessment
    npc, goal, energyStart,
    freeScript,                               // branching dialogue tree (offline)
    proPrompt,                                // LLM system prompt (Pro tier)
    successCriteria, hints
  },

  reflection: {                              // Output — choose your skill
    oral:    { prompts:[ "travel podcast", "call your mom" ], sttLang },
    written: { prompt: "postcard to a friend" },
    rubric                                    // targets: vocab used, min length…
  },

  culture: [ { icon, title, fact } ],         // "¿Sabías que…?"

  rewards: {
    stampSvg,
    souvenir: { name, svg, cost },            // e.g. Miró-mosaic tile
    nextFlight: { destinationId, cost }       // "buy a ticket to the next country"
  }
}
```

**To add a new destination/language:** author one `Destination` object (new
vocab + SVGs, new scenario, new souvenir), set `nextFlight`, done. To add a new
**language**, also set `language`/`sttLang` for TTS/STT.

---

## 8. Gamified economy (G-CLIL Ring 4) — every mechanic traces to a learning aim

| Mechanic | Learner meaning | Ties back to |
|---|---|---|
| **Coins** 🪙 | Earned by completing Processing/Output correctly; **spent to buy a flight** to the next country. | Mastery, progression |
| **Energy / hambre** meter | Depletes on ordering errors in the NPC mission. | Authentic assessment `[S-CTL8]` |
| **Passport stamp** 🛂 | Awarded per completed destination — proof of the journey. | Significant work, narrative |
| **Souvenir** 🧳 | Bought with coins, stored in the **carry-on bag** (persistent inventory). | Collection, autonomy |
| **Flight ticket** ✈️ | Unlocks the next destination. | Progression, goal-setting |
| **Rank** | Hitchhiker → … → Travel Ambassador. | Identity transformation `[S-AWJ]` |

**Persistence:** passport, coins, and carry-on bag are saved in `localStorage`
(per-browser, no login) so the meta-game carries across visits.

---

## 9. Mobile UI/UX requirements `[S9]`

- **Progressive disclosure / onboarding:** teach controls *in* the first level,
  don't front-load instructions.
- **Low cognitive load:** one task on screen at a time; brevity and scanability.
- **Touch targets:** min ~44×44pt, ample spacing (iOS 375pt / Android 360dp
  reference widths).
- **Immediate feedback:** micro-interactions (color, motion) confirm every action
  instantly — meaningful motion, not decoration.
- **Empathy-based design:** built for 5-minute windows in distracting environments.

---

## 10. Delivery tiers (Conflict-1 resolution — Hybrid)

| | **Free trial (offline)** | **Pro (real AI)** |
|---|---|---|
| Hosting | Self-contained HTML, GitHub-Pages-ready, no network | Same shell + network + API key |
| NPC mission | Scripted **branching** *camarero* (`freeScript`) | **LLM** conversation (`proPrompt`) |
| Reflection feedback | Rule-based rubric check | LLM feedback on podcast/postcard |
| Speech | Web Speech **TTS**; **STT** where supported | Same + AI transcription/feedback |

The mock-up ships the **free** experience in full and exposes an **"Upgrade to
Pro ✨"** path so the portfolio demonstrates both tiers.

---

## 11. Build methodology (SAM)

1. **Preparation** — this blueprint + learner/mobile constraints (done).
2. **Iterative Design (Savvy Start)** — Barcelona vertical slice as the low-fi→hi-fi
   prototype.
3. **Iterative Development** — Alpha (engine + Barcelona data, offline), Beta (Pro
   AI hooks + polish), Gold (portfolio Before↔After index).

Deliverables: **BEFORE** (`examples/de-tapas-por-la-rambla.original.html`, already
saved) ↔ **AFTER** (`Language Passport`), plus this blueprint.

---

## 12. Sources

Keyed to the attached matrix *Educational Resources and Research on Digital
Learning* and its "Referencias de fuentes" index.

| Key | Resource (matrix) | Underlying reference |
|---|---|---|
| `[S-AWJ]` | The Academic Writing Journey (AWJ) | Final Tarea 3 Simulation.pdf `[1,2]` |
| `[S3]` | Clothier, P. (2026). *Mastering Mobile Learning Design: A Practical Guide* (1st ed.). Routledge. | BOOK REVIEW 1.docx `[3]` |
| `[S4]` | Asynchronous modules for genAI knowledge/self-efficacy | 1-s2.0-S0360131526000783-main.pdf `[4,5]` |
| `[S-CTL8]` | Contextual Teaching and Learning — 8 components (Johnson) | Elaine Johnson, CTL `[6,7]` |
| `[S-REACT]` | CTL: Preparing students for the new economy (REACT) | `[6]` |
| `[S-GCLIL]` | G-CLIL (Casañ-Pitarch four rings + Coyle 4Cs) | Final Tarea 3 Simulation.pdf `[1,2]` |
| `[S-SAM]` | Successive Approximation Model (SAM) | `[1,2]` |
| `[S-IPO]` | Casañ-Pitarch's IPO Framework | `[1,2]` |
| `[S-ESA]` | Harmer's ESA Model | `[2]` |
| `[S9]` | UI/UX Best Practices + Apple HIG / Material Design | UI/UX guides `[9]` |
| `[S-DT]` | De Tapas Por La Rambla (v1.2) | Storyboard `[11]`, CLT Info-Gap `[12]` |

*Full bibliographic details live in the source workbook.*
