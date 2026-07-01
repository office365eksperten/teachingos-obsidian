# TeachingOS — Starter-vault (Fase 1)

Dette er fundamentet fra roadmap-Fase 1: en Obsidian-vault med struktur,
skabeloner og Dataview-dashboards. **Ingen custom-plugin og ingen AI kræves** —
det er ren Obsidian + Dataview, så datamodellen kan afprøves med det samme.

Én vault svarer til én uddannelse (beslutning B4). Denne demo er "Datamatiker".

## Kom i gang

1. Åbn denne mappe som en vault i Obsidian (*Open folder as vault*).
2. Installér community-pluginnet **Dataview**
   (*Settings → Community plugins → Browse → Dataview → Install → Enable*).
3. Åbn `_dashboards/Semesteroversigt.md` og `_dashboards/Kursus - Mangler.md`.
   Tabellerne udfyldes automatisk.
4. (Valgfrit) Aktivér kerne-pluginnet **Templates** og peg det på mappen
   `_skabeloner`, så du kan indsætte skabeloner med ét klik.

> Uden Dataview vises dashboard-forespørgslerne bare som kodeblokke — så
> pluginnet er nødvendigt for at se tabellerne.

## Struktur

```text
teachingos-starter-vault/
├── README.md
├── _skabeloner/          # Frontmatter-skabeloner (kopiér ved ny note)
├── _dashboards/          # Dataview-oversigter
├── Uddannelse/           # Uddannelses-noten (Datamatiker)
├── Moduler/              # Et modul pr. mappe → Lektioner/
│   └── Python/
│       └── Lektioner/
├── Aktivitetsbibliotek/  # Genbrugelige aktiviteter
├── Ressourcebibliotek/   # Links, PDF, kode, video ...
└── Evalueringer/         # Én note pr. gennemført lektion
```

## Datamodel

Hver note har `type` i frontmatter: `uddannelse`, `modul`, `lektion`,
`aktivitet`, `ressource`, `evaluering`. Relationer laves med `[[links]]`.
Dashboards forespørger på `type` via tags (`#lektion` osv.). Fuld
specifikation: se `PRD_v0.1.md` §7 i beskrivelses-mappen.

## Sådan tilføjer du indhold

- **Nyt modul:** kopiér `_skabeloner/Skabelon - Modul.md` ind i `Moduler/<navn>/`.
- **Ny lektion:** kopiér `_skabeloner/Skabelon - Lektion.md` ind i
  modulets `Lektioner/`-mappe, og udfyld frontmatter.
- **Ny evaluering:** kopiér `_skabeloner/Skabelon - Evaluering.md` ind i
  `Evalueringer/` og link til lektionen.

## Genbrug på tværs af uddannelser

Da hver uddannelse er sin egen vault, ligger `Aktivitetsbibliotek` og
`Ressourcebibliotek` her lokalt. Vil du dele dem på tværs, kan de senere
flyttes til et delt bibliotek-vault eller en delt mappe (jf. B4-noten i PRD).

## Demo-detalje

Lektionen `03 - Funktioner` er bevidst kun *planlagt* (mangler læringsmål,
slides og quiz), så den dukker op i `Kursus - Mangler` — det viser hvordan
dashboardet fanger huller.
