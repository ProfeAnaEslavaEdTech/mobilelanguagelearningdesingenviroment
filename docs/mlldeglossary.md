<!--
  © 2026 Ana Eslava-Graterol. All Rights Reserved.
  Brand & website: profeanaeslava · GitHub: profeanaeslavaedtech · Universitat Politècnica de València.
  All information in this document forms part of a PhD proposal. MLLDE methodology;
  "Language Passport"™; "Grace". CEFR (Council of Europe), PCIC (Instituto Cervantes),
  xAPI (ADL/IEEE), ESCO (European Union) and IPA (International Phonetic Association)
  are cited standards, not redistributed.
-->

# Glossary of Technical Terms — MLLDE Measurement Module

*Written for a jury of linguists and language-education specialists. Every technical
term from AI engineering and learning-data standards used in the MLLDE Measurement
Module, explained in plain language, with the reason it matters to this research.
Companion to the MLLDE xAPI IRI Registry and the Measurement Module concept.*

**Measurement model:** v0.8.3 · **Content inventory:** v0.7.1 (15/08/2026) · **Updated:** 2026-10-23 · **Author:** Ana Eslava-Graterol (profeanaeslava)

*Canonical IRI registry (live): https://profeanaeslavaedtech.github.io/mllde-xapi/ — content inventory and measurement model version on two separate axes.*

---

## 1. Standards bodies and frameworks

**ADL (Advanced Distributed Learning Initiative).** The United States government
programme that created and maintains both SCORM and xAPI — the two learning-data
standards this project exports to. ADL also runs the official public registry of
xAPI profiles (see *profile*), the library this research searched to establish that
no language-learning vocabulary yet exists — and the venue where the MLLDE
vocabulary can be published and become citable worldwide.

**CEFR / MCER — Companion Volume (2020).** The Common European Framework of
Reference for Languages in its updated edition, the evaluation standard of this
project. It reorganises communication into four modes — reception, production,
interaction and **mediation** — each with *can-do* descriptor scales from Pre-A1 to
C2. In MLLDE every metric must trace back to one named descriptor scale.

**ESCO (European Skills, Competences, Qualifications and Occupations).** The
European Commission's official multilingual classification of skills and jobs,
published as linked data: every skill has a stable web address of the form
`data.europa.eu/esco/skill/<code>`. Its language entries describe whole competences
per language (e.g. "communicate in English in a competent way"). Because EU human
resources and recruitment systems classify job requirements using ESCO, attaching
the ESCO address to a learner's CEFR result makes the administrator's report to HR
machine-readable by the employment systems already in use across the EU.

**Europass.** The EU platform hosting the CEFR self-assessment grid used as this
project's canonical evaluation reference.

**IEEE 9274.1.1-2023.** The formal international standard that codifies xAPI —
evidence that xAPI is a stable, citable standard, not a passing technology.

**PCIC (Plan curricular del Instituto Cervantes).** The Instituto Cervantes
curriculum that specifies the linguistic content of Spanish per CEFR level; the
data layer for Spanish instances of MLLDE.

**IPA (International Phonetic Alphabet).** The standard notation for the sounds of
human languages, maintained by the International Phonetic Association. In this
project IPA supplies the *linguistic half* of pronunciation assessment: the target
sound inventory each level aims at, written so that any assessment engine — or any
linguist — can read it.

## 2. Learning-data standards (the "logbook" family)

**LMS (Learning Management System).** The platform that hosts courses and users —
Moodle, Chamilo, Canvas. The administrator persona of this project works here.

**SCORM (Sharable Content Object Reference Model).** The older packaging standard
(ADL, 2001–2004) that lets a course run inside any LMS and report a small fixed set
of results: completion, pass/fail, a score. In MLLDE, SCORM is the *compatibility
layer*: it carries the task-gate result only, never the turn-level voice detail.

**xAPI (Experience API).** The modern successor: each learning event is recorded as
a short standardised sentence — *actor, verb, object* ("María — completed — Mission:
ordering in the café") — with optional result and context. Unlike SCORM it can
describe anything, anywhere, at any granularity, which is why the voice telemetry
of this project is expressed in xAPI.

**Statement.** One such xAPI sentence. The atomic unit of the project's logbook.

**LRS (Learning Record Store).** The gradebook-database that receives and stores
xAPI statements. Dashboards and reports are built by querying the LRS.

**cmi5.** A companion specification (ADL) that defines *how* an LMS launches xAPI
content and which minimum statements it must send — in effect, "SCORM's job done
with xAPI sentences." Relevant here as the bridge profile when a client's LMS needs
LMS-style course tracking alongside the rich MLLDE telemetry.

**Profile (xAPI profile).** A published, agreed vocabulary for one domain — the
verbs, activity types and extensions that community uses, each with its permanent
identifier. There are profiles for video, audio, serious games; this project
authors the first one for CEFR-based language learning.

**Verb / Activity type / Extension.** The three kinds of vocabulary a profile
defines. The *verb* is the action ("completed", "pronounced", "mediated"); the
*activity type* classifies what was acted on (a mission, a pronunciation drill, a
spoken turn); an *extension* is an extra labelled field for detail the standard
does not natively carry (a phoneme score, a rubric band, an incident type).

**IRI (Internationalized Resource Identifier).** A web-style address used as a
*name*, not a webpage — the unique label on each drawer of a shared filing cabinet.
Every verb, activity type and extension in a profile is identified by an IRI so
that all systems agree on its meaning. The MLLDE registry mints one distinct IRI
per concept: five skills, every Companion Volume subskill scale (mediation
included), levels, rubric categories, and more.

**UUID (Universally Unique Identifier).** A long random code (e.g.
`ff85b268-d74c-…`) used by systems like ESCO inside their addresses. Opaque by
design: it guarantees uniqueness but encodes no meaning — the reason ESCO
addresses cannot serve as skill/subskill identifiers inside statements.

**w3id.org.** A free, community-run service providing *permanent* web identifiers.
Modern xAPI profiles anchor their IRIs there so the identifiers outlive any
personal or corporate domain. MLLDE's canonical base is `https://w3id.org/mllde`
(registration filed from the profeanaeslavaedtech GitHub account); fallback:
`https://profeanaeslava.com/xapi`.

**JSON (JavaScript Object Notation).** The simple structured text format —
labelled fields and values in braces — in which xAPI statements, the IRI registry
and the machine-readable teacher reports are written. *JSON-LD* is JSON with
linked-data conventions, the format of formal xAPI profiles.

## 3. The voice pipeline (the "kitchen")

**ASR (Automatic Speech Recognition).** The app's ears: converts the learner's
speech to text. Every voice-derived score is mediated by ASR, so statements carry
its confidence value.

**ASR confidence.** The recogniser's own estimate (0–1) of how sure it is of the
transcript. Low confidence triggers an incident record rather than an unfair score.

**NLU (Natural Language Understanding).** The "what did they mean?" step: finds the
intent ("ordering food") and the details (item = tortilla), and flags language
errors for the pedagogy to handle.

**TTS (Text-to-Speech).** The app's voice: speaks the agent's reply, slowed or
warmed as the level requires.

**Phoneme.** A distinctive sound unit of a language (/r/ vs /ɾ/ in Spanish). *Broad
(phonemic) transcription* records only these units — the right depth for scoring,
because *narrow* transcription would punish legitimate accent variation.

**Forced alignment.** The engineering step that time-aligns the learner's audio
with the expected IPA phoneme sequence, locating each sound segment in the
recording. Prerequisite for any per-sound score.

**GOP (Goodness of Pronunciation).** The pronunciation meter: a likelihood-based
score (0–100) per phoneme, comparing the aligned audio against a reference model
of that sound (canonical method: Witt & Young, 2000). In MLLDE, GOP is solved in
two halves: the IPA-coded target inventory (linguistic half, owned by the
architect) and the acoustic scoring (engineering half, delegated — the engine
returns sound segments and the variant actually produced; *pedagogy decides
acceptability*). Product example of the engineering half available today: Azure AI
Speech Pronunciation Assessment (phoneme-level scores, IPA support, prosody).

**Endpointing.** Detecting when the learner has *finished* speaking rather than
merely paused — so the system does not cut them off. Failures are logged as
incidents.

**Prosody / suprasegmentals.** Stress, rhythm and intonation — assessed as their
own metric lines anchored to the Companion Volume *Prosodic features* scale, never
folded into phoneme scores.

**Turn-taking latency.** The silence between the agent's prompt and the learner's
first word, in milliseconds — a proxy for cognitive load (long pauses suggest the
learner is translating mentally).

## 4. Measurement concepts of the MLLDE module

**Telemetry.** The continuous stream of recorded events from the learning system —
this project's telemetry is expressed as xAPI statements sent to the LRS. MLLDE
records a **dual stream**: performance statements (what the learner did, CEFR-
anchored) and pedagogical-action statements (what the teaching side did about it —
e.g. an implicit recast — and its outcome).

**Recast.** The good-teacher move of correcting by remodelling ("¡Sí, *una*
tortilla!") without interrupting the flow. Logged, not just performed — so
adaptation decisions can be audited.

**Self-scaling rubric.** MLLDE's seven-category speaking rubric (Grammar/Accuracy ·
Vocabulary/Range · Pronunciation/Phonological control · Intelligibility ·
Interaction · Discourse management · Global achievement), banded **0–10** *read
against the level's descriptor*, so one instrument covers A1–C2 (a 6 at A2 ≠ a 6 at
C1). Pass = band ≥ 6; floors: intelligibility ≥ 4 AND interaction ≥ 4. (The
Cambridge 0–5 view = round(band/2), a reporting lens only. Corrected from the
earlier 1–3 draft wording.)

**Evidence tiers.** The module's honesty rule for voice data. Tier 1: measurable
today (task gates, retries, rubric bands, help requests). Tier 2: measurable with
instrumentation (latency, confidence-weighted scores, vendor pronunciation APIs
over an IPA inventory). Tier 3: pending the bespoke GOP build. Every claim carries
its tier; reports never state more precision than the engine possesses.

**Input channel (voice | text).** A per-session marker of the modality that produced
the band. The band is read from the transcript in both cases; input-channel lets the
ASR-confidence gate (0.70) apply to *voice only* — a typed or OCR turn scores without
the gate. Added in measurement model v0.8.3.

**Measure-model.** Each scored session declares the model that produced its marks.
Kept for comparability (sessions scored by different models are not mixed in
aggregates) and governance: it is how a provider-routing deviation was detected and
the affected sessions excluded from the clean set. Added in v0.8.1.

**Persona pack / project pack.** MLLDE's replicability device: the engine (rules,
rubric, registry) is constant; each app or client fills one pack (language, levels,
task inventory, IPA sound inventory, LMS target). A new project is a filled pack,
not a redesign.

**Dual ledger.** The learner-facing report design: the game layer is visible
(stamps, coins, ranks — immersion preserved; the CEFR is never named in-app), the
CEFR layer runs underneath, with an explicit mapping between the two.

**Incident family & resolution ledger.** An independent metric family recording
system failures (ASR failure, endpointing cut-off, text fallback, unresolved help
request…) with rate and severity, plus the ledger: incident → change made → did
the rate drop. The system-improvement loop, and the honest part of the ROI story.

**KPI (Key Performance Indicator).** A headline management metric — progression
rate, time-to-band, completion — reported by the administrator persona.

**ROI (Return on Investment).** The Phillips methodology's Level 5 of programme
evaluation, beyond Kirkpatrick's four levels: ROI (%) = (net programme benefits −
programme costs) ÷ programme costs × 100. In MLLDE every claimed benefit in an ROI
report states its evidence tier.

---

## References (APA 7th)

Advanced Distributed Learning Initiative. (2017). *xAPI profiles specification* (Version 1.0). GitHub. https://adlnet.github.io/xapi-profiles/

Advanced Distributed Learning Initiative. (n.d.). *ADL xAPI profile server*. Retrieved August 4, 2026, from https://profiles.adlnet.gov/

Advanced Distributed Learning Initiative. (n.d.). *Companion specification for xAPI vocabularies*. GitBook. https://adl.gitbooks.io/companion-specification-for-xapi-vocabularies/

Advanced Distributed Learning Initiative. (n.d.). *xapi-authored-profiles* [Repository]. GitHub. Retrieved August 4, 2026, from https://github.com/adlnet/xapi-authored-profiles

Council of Europe. (2020). *Common European Framework of Reference for Languages: Learning, teaching, assessment — Companion volume*. Council of Europe Publishing. https://www.coe.int/lang-cefr

European Commission. (n.d.). *ESCO: European Skills, Competences, Qualifications and Occupations*. Retrieved August 4, 2026, from https://esco.ec.europa.eu/

Europass. (n.d.). *Common European Framework of Reference for language skills* [Self-assessment grid]. European Union. Retrieved August 4, 2026, from https://europass.europa.eu/en/common-european-framework-reference-language-skills

IEEE. (2023). *IEEE standard for learning technology — JSON data model format and RESTful web service for learner experience data tracking and access (xAPI)* (IEEE Std 9274.1.1-2023). IEEE Standards Association.

International Phonetic Association. (1999). *Handbook of the International Phonetic Association: A guide to the use of the International Phonetic Alphabet*. Cambridge University Press.

Kirkpatrick, J. D., & Kirkpatrick, W. K. (2016). *Kirkpatrick's four levels of training evaluation*. ATD Press.

Krashen, S. D. (1985). *The input hypothesis: Issues and implications*. Longman.

Microsoft. (n.d.). *Use pronunciation assessment* [Documentation]. Microsoft Learn. Retrieved August 4, 2026, from https://learn.microsoft.com/en-us/azure/ai-services/speech-service/how-to-pronunciation-assessment

Phillips, J. J., & Phillips, P. P. (2016). *Handbook of training evaluation and measurement methods* (4th ed.). Routledge.

Witt, S. M., & Young, S. J. (2000). Phone-level pronunciation scoring and assessment for interactive language learning. *Speech Communication, 30*(2–3), 95–108. https://doi.org/10.1016/S0167-6393(99)00044-8
