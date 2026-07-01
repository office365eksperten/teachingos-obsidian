---
titel: TeachingOS for Obsidian — PRD
version: 0.1
dato: 2026-07-01
status: udkast
ejer: office365eksperten
repo: https://github.com/office365eksperten/teachingos-obsidian
licens: GPL-3.0
---

# TeachingOS for Obsidian — Produktkravsspecifikation (PRD) v0.1

## 1. Formål med dette dokument

Denne PRD oversætter visionen i `TeachingOS_for_Obsidian_Projektbeskrivelse.md`
til konkrete, testbare krav. Den definerer hvad der bygges i MVP'en, hvad
der bevidst udskydes, og hvordan succes måles. Projektbeskrivelsen ejer
"hvorfor"; denne PRD ejer "hvad" og "hvornår".

## 2. Problem

Undervisere arbejder på tværs af adskilte værktøjer (LMS, kontorpakke,
evalueringsværktøj, filmapper). Sammenhængen mellem planlægning,
gennemførelse og forbedring går tabt, og undervisning kan sjældent
genbruges uden manuelt arbejde. Eksisterende systemer er enten lukkede
(vendor lock-in) eller dækker kun én del af cyklussen.

## 3. Mål og ikke-mål

### Mål

-   Én vault dækker hele cyklussen: planlæg → udvikl → gennemfør →
    evaluér → genbrug.
-   Fuldt ejerskab: lokale Markdown-filer, ingen backend, ingen lock-in.
-   Didaktisk struktur (læringsmål, aktiviteter) frem for løse noter.
-   AI som valgfrit, understøttende lag — ikke en forudsætning.

### Ikke-mål (v0.x–v1.0)

-   Intet fuldt LMS (ingen elevadministration/tilmelding).
-   Intet karakter-/eksamenssystem.
-   Ingen elevvendt adgang.
-   Ingen central hosting eller brugerkonti.
-   Ingen binding til én AI-udbyder.

## 4. Personas

**P1 — Kasper, underviser på erhvervsakademi (primær).**
Underviser i Python og SQL. Vil forberede hurtigere og genbruge forløb
fra semester til semester. Tekniknær, bruger allerede Markdown og GitHub.
Jobs-to-be-done: "Byg et modul én gang, kør det igen næste hold med
minimal tilpasning."

**P2 — Marie, gymnasielærer (primær).**
Mindre teknisk. Vil have struktur og overblik, ikke et udviklerværktøj.
Jobs-to-be-done: "Se hvad der mangler i mit kursus, og saml alt ét sted."

**P3 — Jens, selvstændig kursusudvikler (sekundær).**
Sælger kurser til virksomheder. Vil pakke og eksportere materialer i
flere formater. Jobs-to-be-done: "Genbrug indhold på tværs af kunder og
eksportér til deres LMS."

## 5. User stories (MVP-relevante)

-   Som underviser vil jeg oprette en ny lektion fra en skabelon, så alle
    felter (læringsmål, aktiviteter, evaluering) er på plads fra start.
-   Som underviser vil jeg se et dashboard over et kursus, så jeg med det
    samme kan se hvilke lektioner der mangler slides, quiz eller
    evaluering.
-   Som underviser vil jeg knytte genbrugelige aktiviteter til en lektion,
    så jeg ikke genopfinder Think-Pair-Share hver gang.
-   Som underviser vil jeg registrere en kort evaluering efter en lektion,
    så jeg husker hvad der skal ændres næste gang.
-   Som underviser vil jeg genbruge en hel lektion i et nyt hold uden at
    kopiere filer manuelt.
-   Som underviser vil jeg (valgfrit) bede AI om et udkast til quiz ud fra
    lektionens indhold, så jeg sparer forberedelsestid.

## 6. Funktionelle krav

Prioritering: **M** = Must (v0.x), **S** = Should (v1.0), **C** = Could
(efter v1.0).

| ID | Krav | Prioritet |
|----|------|-----------|
| F1 | Standardiseret vault-mappestruktur (uddannelse → modul → lektion) | M |
| F2 | Frontmatter-skabeloner for uddannelse, modul, lektion, aktivitet, ressource, evaluering | M |
| F3 | Dataview-dashboards: semesteroversigt, kursus-"mangler", statistik | M |
| F4 | Kalender-/oversigtsvisning over undervisningsaktiviteter | S |
| F5 | Plugin-kommando: "Ny lektion" opretter note fra skabelon med udfyldt frontmatter | S |
| F6 | Plugin-kommando: "Ny aktivitet" fra aktivitetsbibliotek | S |
| F7 | Aktivitetsbibliotek med genbrugelige, linkbare aktiviteter | S |
| F8 | Ressourcebibliotek (billeder, video, kode, PDF, links) med genbrug via links | S |
| F9 | Evalueringsflow pr. lektion (hvad virkede, tid brugt, feedback) | S |
| F10 | Læringsmål med taksonomi-tag (Bloom/SOLO/ECTS) | S |
| F11 | Eksport til PDF og Marp | S |
| F12 | AI: generér udkast til lektionsplan, quiz, øvelser, slides | C |
| F13 | AI: RAG over vaulten (lokal model som standard) | C |
| F14 | Eksport til Moodle/Canvas via **Common Cartridge** (kursuspakke; QTI-quiz kan indlejres) | C |
| F15 | Eksport til Word/HTML/PowerPoint | C |

## 7. Datamodel (frontmatter)

Enhver note er en Markdown-fil med YAML-frontmatter. Foreløbige skemaer
(kan justeres i implementeringen):

### Lektion

```yaml
---
type: lektion
titel: "Løkker i Python"
uddannelse: "Datamatiker"
modul: "Python"
nr: 3
laeringsmaal:
  - id: LM1
    tekst: "Anvende for- og while-løkker"
    taksonomi: bloom-anvende
forudsaetninger: ["Variabler"]
varighed_min: 90
aktiviteter: ["[[Live Coding]]", "[[Think-Pair-Share]]"]
materialer: ["[[loops-slides]]"]
quiz: "[[loops-quiz]]"
status: planlagt        # planlagt | klar | gennemført
sidst_evalueret: null
tags: [python, loops]
---
```

### Aktivitet

```yaml
---
type: aktivitet
titel: "Think-Pair-Share"
kategori: samarbejde
varighed_min: 15
beskrivelse: "..."
egnet_til: [online, tilstede]
---
```

### Evaluering

```yaml
---
type: evaluering
lektion: "[[Løkker i Python]]"
dato: 2026-09-12
virkede: "..."
virkede_ikke: "..."
aendringer: "..."
tid_brugt_min: 95
feedback_score: 4.2      # aggregeret/anonymiseret
---
```

Principper: relationer udtrykkes med Obsidian-links (`[[...]]`);
dashboards bygges med Dataview-forespørgsler mod `type`-feltet.

## 8. MVP-afgrænsning

MVP (Fase 1–3 i roadmap) er **ren Obsidian + Dataview uden custom-plugin**:
vault-struktur, skabeloner og dashboards. Det er et brugbart produkt i sig
selv og validerer datamodellen før plugin- og AI-arbejde påbegyndes.

## 9. Ikke-funktionelle krav

-   **Offline-first:** al kernefunktion virker uden internet.
-   **Privatliv/GDPR:** persondata bliver lokalt; ingen elevdata til
    cloud-AI uden eksplicit samtykke; feedback anonymiseres/aggregeres.
-   **Ingen lock-in:** alt er ren Markdown, læsbart uden pluginnet.
-   **Ydelse:** dashboards skal være brugbare på en vault med 200+
    lektioner.
-   **Kompatibilitet:** fungerer på gængse Obsidian-versioner (desktop
    først).
-   **Licens:** GPL-3.0 — afklar tidligt konsekvenser for distribution som
    Obsidian community-plugin.

## 10. Succesmål

-   Et helt modul (fx Python) kan planlægges, gennemføres og evalueres i
    vaulten.
-   En lektion genbruges i et nyt hold uden manuel filkopiering.
-   Fase 1–3 fungerer uden custom-plugin.
-   Målbar tidsbesparelse i forberedelsen (baseline måles på ét reelt
    forløb).
-   v1.0 udgivet som community-plugin med tilhørende eksempel-vault.

## 11. Risici og antagelser

| Risiko | Håndtering |
|--------|-----------|
| Scope creep (alt bliver MVP) | Streng MoSCoW; Fase 1–3 uden plugin |
| Offline-first vs. cloud-AI modsiger hinanden | Lokal AI som standard, cloud opt-in |
| GDPR ved studenterfeedback | Anonymisering + lokal lagring som default |
| GPL-3.0 spænder med community-plugin-distribution | Licensafklaring i Fase 1 |
| Dataview-ydelse ved store vaults | Test tidligt på realistisk datamængde |
| Åbne eksportstandarder (QTI/CC) er tunge | Udskudt til "Could"; kun ved reelt behov |

## 12. Afklarede beslutninger

| # | Spørgsmål | Beslutning | Konsekvens |
|---|-----------|-----------|-----------|
| B1 | LMS-eksportformat | **Common Cartridge** (kursuspakke). QTI kun som indlejret quiz. | F14 sigter mod CC; ét format frem for to |
| B2 | Studenterfeedback | **Manuel indtastning** i første version. Import udskudt. | Enklere datamodel; ingen ekstern integration i MVP |
| B3 | Lokal AI-model | **Qwen 3** til generering + **nomic-embed-text** til RAG-embeddings. **Llama 3.1 8B** som let fallback. | Stærk dansk/multilingual kvalitet; se note nedenfor |
| B4 | Vault-struktur | **Én vault pr. uddannelse.** | Bedre ydelse og renere genbrug; påvirker §9 og skabeloner |

### Note til B3 — AI-model

Undervisning foregår på dansk, så flersproget kvalitet vejer tungest.
**Qwen 3** leder på multilingual (dækker dansk godt) og er stærk til
generering af forløb, quizzer og kodeeksempler. Anbefaling afhænger af
hardware:

-   **14B** hvis maskinen har ~12 GB+ VRAM/RAM — bedste kvalitet.
-   **8B** som standard på mere beskeden hardware.
-   **Llama 3.1 8B** som let, robust fallback (kører fra ~6 GB VRAM).
-   **nomic-embed-text** til embeddings i RAG-laget uanset genereringsmodel.

Dette er en dokumentationsanbefaling, ikke en binding — brugeren kan
vælge enhver Ollama-model. (Kilder: Morph, LMSA, Local AI Master, 2026.)

### Konsekvens for B4 — én vault pr. uddannelse

-   Dashboards og Dataview kører pr. uddannelse (mindre datamængde,
    bedre ydelse — ydelseskravet i §9 bliver lettere at holde).
-   Genbrug *på tværs* af uddannelser sker ved at kopiere/linke fra
    delte biblioteker (aktiviteter, ressourcer) frem for én fælles vault.
-   Overvej et lille delt "bibliotek"-vault eller en delt mappe til
    aktivitets- og ressourcebiblioteket, så genbrug på tværs stadig er
    let.

## 13. Milepæle (afledt af roadmap)

1.  **M1 — Foundation:** vault-struktur, skabeloner, frontmatter-model.
2.  **M2 — Dashboards:** Dataview-oversigter (MVP færdig).
3.  **M3 — Teaching Framework:** læringsmål, aktivitets-/ressourcebibliotek,
    evaluering.
4.  **M4 — Plugin MVP:** kommandoer, kalender, note-oprettelse.
5.  **M5 — AI:** generering + RAG (lokal først).
6.  **M6 — v1.0:** dokumentation, community-plugin, eksempel-vault.
