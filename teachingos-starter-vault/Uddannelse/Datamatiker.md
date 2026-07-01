---
type: uddannelse
titel: "Datamatiker"
ansvarlig: "Tue Hellstern"
aar: 2026
ects: 150
beskrivelse: "Erhvervsakademiuddannelse i systemudvikling og programmering."
tags: [uddannelse]
---

# Datamatiker

Denne vault dækker Datamatiker-uddannelsen (én vault pr. uddannelse, jf. beslutning B4).

## Moduler

```dataview
TABLE nr AS "Nr", status AS "Status"
FROM #modul
WHERE uddannelse = this.titel
SORT nr ASC
```

## Genveje

- [[Semesteroversigt]]
- [[Kursus - Mangler]]
