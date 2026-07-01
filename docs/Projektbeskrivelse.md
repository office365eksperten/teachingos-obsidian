# TeachingOS for Obsidian

## Vision

> Et komplet undervisningsoperativsystem bygget på Obsidian, hvor
> undervisere kan planlægge, udvikle, gennemføre, evaluere og genbruge
> undervisning -- understøttet af AI og baseret på åbne standarder.

Projektet skal være mere end en note-plugin. Målet er at skabe et samlet
værktøj, der understøtter hele undervisningsprocessen -- fra idé til
evaluering.

------------------------------------------------------------------------

# GitHub

https://github.com/office365eksperten/teachingos-obsidian

**Licens:** GPL-3.0

------------------------------------------------------------------------

# Problem & baggrund

Undervisere jonglerer i dag mellem flere adskilte værktøjer: et LMS til
planlægning og deling, et kontorprogram til slides, et separat sted til
evaluering og endnu et til materialer. Sammenhængen mellem idé,
gennemførelse og forbedring går tabt, og undervisningen kan sjældent
genbruges uden manuelt klip-og-klister.

En markedskortlægning (se `Konkurrentanalyse.md`) viser tre typer
eksisterende løsninger -- men ingen der dækker behovet:

-   **Lukkede LMS/AI-platforme** (Meebook, MinUddannelse, MagicSchool,
    SchoolAI): stærke på cyklus, men lukket data, ingen lokal fillagring
    og reelt vendor lock-in.
-   **Åbne OER-/publiceringsværktøjer** (Pressbooks, Quarto, GitBook):
    åbne formater, men dækker kun indhold -- ikke planlægning,
    gennemførelse eller evaluering.
-   **Obsidian gør-det-selv-opsætninger:** lokalt og ejet, men ingen
    samlet pakke, ingen didaktisk struktur og ingen AI ud af boksen.

**TeachingOS' hvide plet:** det eneste system der samtidig giver
underviseren *ejerskab* (lokale Markdown-filer, ingen lock-in), *hele
cyklussen* i ét flow, *åbne standarder* til deling/genbrug, og *AI* som
understøttende lag.

------------------------------------------------------------------------

# Målgruppe

## Primær

-   Universitetsundervisere
-   Erhvervsakademier
-   Professionshøjskoler
-   Gymnasier
-   Kursusudbydere
-   Online undervisere

## Sekundær

-   Virksomheder med intern uddannelse
-   Konsulenter
-   Selvstændige kursusudviklere

------------------------------------------------------------------------

# Grundprincipper

-   Markdown-first
-   Offline-first
-   Ingen vendor lock-in
-   Open Source
-   AI er en assistent -- ikke centrum
-   Alt kan eksporteres
-   Git-versionering understøttes

------------------------------------------------------------------------

# Ikke-mål (afgrænsning)

For at holde fokus er følgende bevidst **uden for** scope -- i hvert fald
frem til version 1.0:

-   Ikke et fuldt LMS: ingen elevadministration, tilmelding eller
    brugerstyring.
-   Ikke et karakter-/eksamenssystem: ingen officiel bedømmelse eller
    beviser.
-   Ikke en elevvendt platform: TeachingOS er et underviserværktøj.
    Studenterfeedback importeres/registreres, men eleverne arbejder ikke
    inde i vaulten.
-   Ikke en cloud-tjeneste med central hosting: der er ingen backend og
    ingen brugerkonti.
-   Ikke afhængig af én bestemt AI-udbyder.

------------------------------------------------------------------------

# Åbne standarder

Konkret hvilke standarder projektet bygger på og sigter mod:

-   **Fundament (fra dag 1):** Markdown (CommonMark), YAML frontmatter,
    Git.
-   **Interoperabilitet (mål):** eksport/mapping mod
    -   **QTI** (quiz/assessment)
    -   **Common Cartridge** (kursuspakker til Moodle/Canvas)
    -   **xAPI / cmi5** (læringsaktivitets-data)
    -   **SCORM** (hvor ældre LMS kræver det)
-   **Læringsmål-taksonomier:** Bloom, SOLO, ECTS Learning Outcomes.

Interoperabilitets-standarderne er et mål, ikke et løfte for MVP -- de
prioriteres i takt med reelt behov (se roadmap og PRD).

------------------------------------------------------------------------

# Hovedmoduler

## 1. Uddannelser

Eksempler:

-   Datamatiker
-   MIL
-   Python
-   Power BI
-   Excel
-   SQL

## 2. Moduler

Eksempel:

``` text
Python
├── Variabler
├── Løkker
├── Funktioner
├── Lister
└── Filer
```

## 3. Lektioner

Hver lektion indeholder:

-   Læringsmål
-   Forudsætninger
-   Tidsplan
-   Aktiviteter
-   Øvelser
-   Materialer
-   Slides
-   Quiz
-   Refleksion
-   Evaluering

## 4. Aktivitetsbibliotek

Genbrugelige aktiviteter såsom:

-   Think-Pair-Share
-   Code Along
-   Live Coding
-   Kahoot
-   Peer Review
-   Casearbejde
-   Gruppearbejde
-   Refleksion
-   Quiz

## 5. Ressourcebibliotek

Genbrug af:

-   Billeder
-   Videoer
-   Links
-   Kode
-   PDF
-   PowerPoint
-   Marp
-   GitHub repositories

## 6. Læringsmål

Understøttelse af:

-   Bloom
-   SOLO
-   ECTS Learning Outcomes

AI kan foreslå læringsmål.

## 7. Evaluering

Efter hver lektion registreres:

-   Hvad fungerede?
-   Hvad fungerede ikke?
-   Hvad skal ændres?
-   Tid brugt
-   Studenterfeedback

------------------------------------------------------------------------

# AI-modul

AI skal kunne:

-   Generere lektionsplaner
-   Foreslå Bloom-læringsmål
-   Udarbejde øvelser
-   Generere quizzer
-   Oprette Marp-slides
-   Skrive kodeeksempler
-   Udarbejde eksamensspørgsmål
-   Foreslå hjemmeopgaver
-   Tilpasse til online undervisning
-   Understøtte flipped classroom
-   Differentiere undervisning

AI bør kunne anvende hele Obsidian-vaulten som RAG-vidensbase.

## Offline-first vs. cloud-AI

Der er en indbygget spænding mellem princippet om offline-first og brugen
af cloud-AI (ChatGPT, Claude, Gemini). Den håndteres bevidst:

-   **Standard = lokal:** Ollama / Open WebUI kører offline, så
    kerneprincippet holder uden data forlader maskinen.
-   **Cloud-AI er opt-in:** valgfri og tydeligt markeret. Underviseren
    accepterer aktivt at sende data til en ekstern udbyder.
-   **Ingen elevdata til cloud som default:** evaluerings- og
    feedbackdata behandles lokalt medmindre brugeren eksplicit vælger
    andet (se Privatliv).

------------------------------------------------------------------------

# Privatliv & GDPR

Evaluerings- og feedbackmodulet kan indeholde persondata (fx
studenterfeedback). Principper:

-   Data lever lokalt i vaulten -- ingen central indsamling.
-   Studenterfeedback bør som udgangspunkt være anonymiseret/aggregeret.
-   Ingen persondata sendes til cloud-AI uden eksplicit samtykke.
-   Eksport skal kunne ske uden personhenførbare oplysninger.

------------------------------------------------------------------------

# Dashboards

## Semester

-   Status på gennemførte lektioner
-   Fremdrift

## Kursus

Viser manglende:

-   Slides
-   Quiz
-   Evaluering
-   Læringsmål

## Kalender

Oversigt over undervisningsaktiviteter.

------------------------------------------------------------------------

# Teknisk arkitektur

## Backend

Ingen -- alt gemmes som Markdown.

## Datamodel

-   Markdown
-   YAML Frontmatter

## Plugin

-   TypeScript
-   Obsidian API

## AI

Valgfri integration:

-   Ollama
-   Open WebUI
-   ChatGPT
-   Claude
-   Gemini

## Eksport

-   PDF
-   Marp
-   PowerPoint
-   HTML
-   Moodle
-   Canvas
-   Word

------------------------------------------------------------------------

# Prioritering (MoSCoW)

For at undgå at "alt bliver MVP":

-   **Must (v0.x):** vault-struktur, frontmatter-model,
    standard-skabeloner (uddannelse/modul/lektion), Dataview-dashboards.
-   **Should (v1.0):** plugin-kommandoer (ny lektion/aktivitet),
    kalender, aktivitets- og ressourcebibliotek, evalueringsflow,
    eksport til PDF/Marp.
-   **Could (efter v1.0):** AI-generering, RAG over vault, eksport til
    Moodle/Canvas, QTI/Common Cartridge.
-   **Won't (nu):** elevvendt adgang, karaktersystem, cloud-hosting.

------------------------------------------------------------------------

# Roadmap

## Fase 1 -- Foundation (2--3 uger)

-   Vault-struktur
-   Mapper
-   Standard-skabeloner
-   Frontmatter-model
-   Dokumentation

## Fase 2 -- Dashboard (2 uger)

-   Dataview
-   Semesteroversigt
-   Status
-   Statistik

## Fase 3 -- Teaching Framework (3--4 uger)

-   Læringsmål
-   Aktivitetsbibliotek
-   Ressourcebibliotek
-   Evaluering

## Fase 4 -- Plugin MVP (4--6 uger)

-   Ny lektion
-   Ny aktivitet
-   Drag-and-drop
-   Semesteroversigt
-   Kalender
-   Automatisk oprettelse af noter

## Fase 5 -- AI (4--8 uger)

-   Lektionsplaner
-   Quizzer
-   Slides
-   Opgaver
-   Feedback
-   RAG over vaulten

## Fase 6 -- Version 1.0

-   Dokumentation
-   GitHub
-   Community-plugin
-   Eksempel-vault

------------------------------------------------------------------------

# Succeskriterier

Hvordan vi ved at projektet lykkes:

-   Et helt kursus (fx Python-modulet) kan planlægges, gennemføres og
    evalueres udelukkende i vaulten.
-   En lektion kan genbruges i et nyt hold uden manuel kopiering.
-   Underviseren oplever målbar tidsbesparelse i forberedelsen.
-   Fase 1-3 fungerer helt uden custom-plugin (ren Obsidian + Dataview).
-   Ved v1.0: publiceret som Obsidian community-plugin med en
    eksempel-vault andre kan tage i brug.

------------------------------------------------------------------------

# Langsigtet vision

TeachingOS skal udvikle sig til et komplet **Teaching Operating
System**, hvor undervisere kan styre hele undervisningsprocessen fra én
Obsidian-vault -- fra idé og planlægning til gennemførelse, evaluering
og løbende forbedring.

## Centrale differentieringspunkter

-   Didaktisk struktur frem for blot noter
-   Genbrugelige undervisningsaktiviteter
-   AI baseret på underviserens egne materialer (RAG)
-   Åbne standarder (Markdown, Git, lokale AI-modeller)
-   Offline-first og open source
