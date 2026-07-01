---
titel: Konkurrentanalyse — TeachingOS for Obsidian
dato: 2026-07-01
status: udkast
---

# Konkurrentanalyse: TeachingOS for Obsidian

## Formål

At kortlægge eksisterende systemer der helt eller delvist løser samme opgave som **TeachingOS** — et komplet undervisningsoperativsystem bygget på Obsidian, hvor undervisere kan **planlægge → udvikle → gennemføre → evaluere → genbruge** undervisning, understøttet af AI og baseret på åbne standarder.

## Konklusion først

Der findes stærke systemer for *dele* af visionen, men **intet produkt kombinerer alle fire kernekarakteristika samtidig**:

1. Lokalt, ejet fundament (Obsidian / markdown-filer)
2. Åbne standarder og formater
3. *Hele* undervisningscyklussen (ikke kun planlægning eller kun indhold)
4. AI som integreret lag

De nærmeste konkurrenter er enten lukkede LMS/AI-platforme (stærke på cyklus, svage på åbenhed/ejerskab) eller åbne publiceringsværktøjer (stærke på åbenhed, svage på cyklus). **Din niche er ikke besat.**

---

## Kategori 1 — Danske læringsplatforme

Tættest på "hele cyklussen" i en dansk kontekst, men lukkede, kommunale SaaS-løsninger.

### Meebook
Danmarks mest udbredte læringsplatform. Lærerens digitale arbejdsrum: planlægning af forløb, materialesamling, deling med elever. **ShareIT** giver adgang til 40.000+ forløb lavet af andre lærere til genbrug og tilpasning. Har integreret AI der genererer forløbsudkast ud fra minimalt input.
- Dækker: planlæg, udvikl, gennemfør, (del/genbrug internt), AI
- Mangler: åbne standarder, lokal fillagring, ejerskab, genbrug uden for platformen
- Link: https://meebook.com/

### MinUddannelse
Konkurrerende kommunal læringsplatform (bruges i andre kommuner end Meebook). Samme grundmodel: forløbsplanlægning, mål, elevdeling.
- Link: https://www.minuddannelse.net/

### Aula
Den nationale kommunikationsplatform for folkeskoler og dagtilbud. Ikke en planlægnings-/forløbsplatform, men det lag Meebook/MinUddannelse ofte kobles til. Relevant som kontekst, ikke som direkte konkurrent.
- Link: https://aulainfo.dk/

**Vurdering:** Adskiller sig fra TeachingOS på ejerskab, åbenhed og genbrug. Lukket data, ingen markdown, ingen lokal kontrol.

---

## Kategori 2 — AI-undervisningsplatforme (internationale)

Stærke på *udvikling* (generering af materialer). Cloud-baserede sort-boks-værktøjer uden ejet, persistent vidensbase.

### MagicSchool
80+ værktøjer til forløb, opgaver, differentiering, rubrikker, feedback og forældrekommunikation. Integrerer med Google Docs, Classroom og Canvas. Gratis basis; Plus ~$12,99/md. SOC 2, FERPA/COPPA.
- Dækker: udvikl, differentiér, (evaluér via rubrikker), AI
- Mangler: cyklus-sammenhæng, åbenhed, ejerskab
- Link: https://www.magicschool.ai/

### SchoolAI
AI-guidede læringsmiljøer ("Spaces") — 200.000+ til genbrug/remix. "Mission Control"-dashboard viser hvem der er i gang og hvor der er huller. Gratis for lærere. FERPA/COPPA, 1EdTech-certificeret, SOC 2.
- Dækker: gennemfør, evaluér (live-monitorering), genbrug (remix), AI
- Mangler: planlægning/forberedelse, åbne filformater, ejerskab
- Link: https://schoolai.com/

### TeachBetter.ai
Genererer forløb, quizzer, worksheets, præsentationer og rapporter. "Smart Content Studio" til at berige output med visuals, differentiering og lokalisering.
- Link: https://teachbetter.ai/

### TeacherMatic
Genererer forløb, quizzer, feedback og ressourcer. Udviklet med input fra 300+ lærere.
- Link: https://teachermatic.com/

**Vurdering:** Bedst til hurtig materialeproduktion, men ingen ejet vidensbase, ingen åbne formater, og cyklussen hænger ikke sammen på tværs af værktøjer.

---

## Kategori 3 — Obsidian-baserede tilgange

Her findes **intet færdigt produkt** — kun community-DIY-setups. Det bekræfter både behovet og at nichen er åben.

### Community-setups (templates + Dataview)
Lærere bygger egne systemer i Obsidian: templates til forløb/lektioner, der linker elever, hold, emner og evaluering; Dataview til dynamiske oversigter (fx elevers fremmøde og opgaver).
- Fordele: lokalt, ejet, markdown, fuldt fleksibelt, gratis
- Ulemper: kræver teknisk opsætning, ingen samlet pakke, ingen AI ud af boksen, ingen delt standard
- Referencer:
  - https://forum.obsidian.md/t/bulding-a-system-for-teaching-tracking-students-lessons-and-plans/82356
  - https://forum.obsidian.md/t/teachers-lesson-notes-where-to-start/37481

**Vurdering:** Det er præcis fundamentet TeachingOS vil pakke som et sammenhængende produkt. Ingen har gjort det endnu.

---

## Kategori 4 — Åbne standarder / markdown-baseret OER

Stærke på åbenhed og genbrug, men det er publiceringsværktøjer for *indhold* — ikke arbejdsflow for hele undervisningsprocessen.

### Pressbooks
Nem ebog-/OER-forfatterplatform til at lave og udgive åbne læremidler.
- Link: https://pressbooks.com/

### OER Commons (Open Author)
Fri editor til at lave, remixe og tilpasse åbne læremidler for grupper og kurser.
- Link: https://www.oercommons.org/

### GitBook
GitHub-baseret værktøj til at skrive "lærebøger" i markdown i et repository, med rich/multimedie-indhold.
- Link: https://www.gitbook.com/

### Quarto / bookdown
Markdown- og Pandoc-baseret publicering til HTML, PDF og EPUB — teknisk stærkt til reproducerbart, åbent indhold.
- Links: https://quarto.org/ · https://bookdown.org/

**Vurdering:** Deler TeachingOS' åbenheds-DNA, men stopper ved indhold/publicering. Ingen planlægning, gennemførelse, evaluering eller AI-lag.

---

## Feature-matrix

Skala: ✅ dækket · 🟡 delvist · ❌ ikke dækket

| System | Planlæg | Udvikl | Gennemfør | Evaluér | Genbrug | Åbne standarder | Lokalt/ejet | AI | Dansk kontekst |
|---|---|---|---|---|---|---|---|---|---|
| **TeachingOS (mål)** | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |
| Meebook | ✅ | ✅ | ✅ | 🟡 | 🟡 | ❌ | ❌ | ✅ | ✅ |
| MinUddannelse | ✅ | ✅ | ✅ | 🟡 | 🟡 | ❌ | ❌ | 🟡 | ✅ |
| MagicSchool | 🟡 | ✅ | 🟡 | 🟡 | 🟡 | ❌ | ❌ | ✅ | ❌ |
| SchoolAI | ❌ | 🟡 | ✅ | ✅ | ✅ | 🟡 | ❌ | ✅ | ❌ |
| TeachBetter | 🟡 | ✅ | 🟡 | 🟡 | 🟡 | ❌ | ❌ | ✅ | ❌ |
| TeacherMatic | 🟡 | ✅ | ❌ | 🟡 | 🟡 | ❌ | ❌ | ✅ | ❌ |
| Obsidian DIY | ✅ | 🟡 | 🟡 | 🟡 | 🟡 | ✅ | ✅ | ❌ | 🟡 |
| Pressbooks / OER | ❌ | 🟡 | ❌ | ❌ | ✅ | ✅ | 🟡 | ❌ | ❌ |
| Quarto / GitBook | ❌ | 🟡 | ❌ | ❌ | ✅ | ✅ | ✅ | ❌ | ❌ |

---

## Positionering: TeachingOS' hvide plet

Ingen konkurrent scorer højt på både **cyklus-fuldstændighed** og **åbenhed/ejerskab** samtidig:

- LMS/AI-platforme (Meebook, MagicSchool, SchoolAI) → stærke på cyklus, lukkede og ikke-ejede.
- Åbne OER-værktøjer (Pressbooks, Quarto) → åbne, men kun indhold.
- Obsidian-DIY → åbent og ejet, men ikke pakket og uden AI.

**TeachingOS' unikke løfte:** det eneste system der giver underviseren *ejerskab* (lokale markdown-filer, ingen lock-in), *hele cyklussen* i ét sammenhængende flow, *åbne standarder* til deling/genbrug, og *AI* som understøttende lag — bygget på et fundament (Obsidian) som lærere allerede DIY-bruger, men som ingen har produktgjort.

### Anbefalede næste skridt
- Vælg 2-3 skarpe differentiatorer at kommunikere (fx "dine data, dine filer", "hele forløbet ét sted", "genbrug på tværs af standarder").
- Overvej hvilke åbne standarder der konkret understøttes (fx 1EdTech LTI/QTI, Common Cartridge) — det er både en teknisk og en positioneringsbeslutning.
- Definér hvad AI-laget gør *mere* end MagicSchool/Meebook allerede gør, så det ikke bare bliver "endnu en forløbsgenerator".

---

## Kilder

- Meebook — https://meebook.com/
- Meebook, bedre undervisningsplanlægning — https://meebook.com/blog/hvordan-kan-laerere-spare-tid-i-planlaegningen-af-undervisningen
- MeeBook bygger ansvarlig AI (DI) — https://www.danskindustri.dk/vi-radgiver-dig/virksomhedsregler-og-varktojer/ai/cases-og-eksempler/casearkiv-ai-for-alle/MeeBook/
- MinUddannelse — https://www.minuddannelse.net/
- Aula — https://aulainfo.dk/
- Læringsplatforme og portaler (Folkeskolen) — https://www.folkeskolen.dk/debat/laeringsplatforme-og-portaler/
- MagicSchool — https://www.magicschool.ai/
- MagicSchool pricing — https://www.magicschool.ai/pricing
- SchoolAI — https://schoolai.com/
- SchoolAI Spaces — https://schoolai.com/products/spaces
- TeachBetter.ai — https://teachbetter.ai/
- TeacherMatic — https://teachermatic.com/
- Top AI-platforme for lærere 2026 — https://teachbetter.ai/best-ai-platforms-for-teachers-in-2026/
- 50 AI tools for teachers (Ditch That Textbook) — https://ditchthattextbook.com/ai-tools/
- Obsidian Forum — system til undervisning — https://forum.obsidian.md/t/bulding-a-system-for-teaching-tracking-students-lessons-and-plans/82356
- Obsidian Forum — teacher's lesson notes — https://forum.obsidian.md/t/teachers-lesson-notes-where-to-start/37481
- Pressbooks — https://pressbooks.com/
- OER Commons — https://www.oercommons.org/
- GitBook — https://www.gitbook.com/
- Quarto — https://quarto.org/
- bookdown — https://bookdown.org/
