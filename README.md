# MLLDE — Mobile Language Learning Design Environment

**Author:** Ana Eslava-Graterol (ProfeAnaEslavaEdTech) · Universitat Politècnica de València
**Repository:** `mobilelanguagelearningdesingenviroment`

MLLDE is a replicable, **language-agnostic** methodology for building short, gamified
mobile language lessons, anchored to the **CEFR** (Council of Europe). This repository
holds the **PhD research line** and the **three authoring tools**. Its first product,
**Language Passport** (Spanish), lives in a separate repository.

👉 Open **`index.html`** for the home page that links to everything below.

## What's in this repository

### 1 · Research
| File | What it is |
|---|---|
| `docs/MLLDE-PhD-Research-Proposal.pdf` | The **PhD research proposal** (also `docs/phd-proposal-mllde.md`). |
| `docs/MLLDE-Curriculum-Master-Document.pdf` / `.docx` | The Curriculum Master Document — method, CEFR competence core, blueprint. |
| `docs/theoretical-framework.md` | Frameworks + CEFR 4 modes · 3 communicative competences. |

### 2 · Authoring tools (self-contained, offline HTML)
| File | What it is |
|---|---|
| `curriculum-design-worksheet.html` | **(a) JSON curriculum maker** — author a lesson for any language / new app; **Save (JSON)**. |
| `gpt-design-worksheet.html` | **(b) GPT maker** — design your next Custom GPT; includes 4 worked examples (Grace TOP, PhD Chema, Cambridge B2 Examiner, Business Roleplay). |
| `language-passport-level-creator.html` | **(c) Language Passport level maker** — build a new city/lesson; opens blank + Barcelona/Sevilla examples. |

### 3 · GPT designs & authorship records
| File | What it is |
|---|---|
| `gpt-design.html` | Grace, the AI mentor — presentation + paste-ready system prompt. |
| `docs/gpt-records/` | Detailed **design & authorship records** (markdown + PDF) for the 4 GPTs — evidence for trademark/copyright filings — with a comparison index. |

### 4 · Publishing
| File | What it is |
|---|---|
| `docs/how-to-upload-to-github.md` | **Step-by-step GitHub guide for beginners** (also delivered as DOCX + PDF). |

## How this relates to Language Passport

```
mobilelanguagelearningdesingenviroment/   ← THIS repo — the methodology + tools
  ├── docs/MLLDE-PhD-Research-Proposal.pdf     (PhD proposal)
  ├── curriculum-design-worksheet.html         (a) JSON curriculum maker
  ├── gpt-design-worksheet.html                (b) GPT maker
  └── language-passport-level-creator.html     (c) level maker

edtech-mobile-json-lessons/               ← Product 1 (separate repo)
  ├── index.html + app/                        the Language Passport app
  └── world/                                   father → continents → countries → cities
```

- Use **`curriculum-design-worksheet.html`** to start a **brand-new language app** (French, German…).
- Use **`language-passport-level-creator.html`** to add lessons to **Language Passport**.
- Use **`gpt-design-worksheet.html`** to design a **mentor GPT** for any of them.

All tools mirror the same CEFR-anchored planning (4 modes of communication · 3 communicative
language competences). See [`docs/mllde-curriculum-master.md`](docs/mllde-curriculum-master.md).

---

© 2024–2027 Ana Eslava-Graterol (ProfeAnaEslavaEdTech). All Rights Reserved. Proprietary — see
[`LICENSE`](LICENSE) and [`NOTICE`](NOTICE). CEFR © Council of Europe; the *Plan curricular* ©
Instituto Cervantes (cited, not redistributed). Referenced frameworks © their respective authors.
