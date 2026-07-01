---
type: modul
titel: "Python"
uddannelse: "Datamatiker"
nr: 1
status: i gang
beskrivelse: "Grundlæggende programmering i Python."
tags: [modul]
---

# Python

Grundlæggende programmering: variabler, løkker, funktioner, lister og filer.

## Lektioner

```dataview
TABLE nr AS "Nr", status AS "Status", varighed_min AS "Min", choice(sidst_evalueret, "✅", "—") AS "Evalueret"
FROM #lektion
WHERE modul = this.titel
SORT nr ASC
```
