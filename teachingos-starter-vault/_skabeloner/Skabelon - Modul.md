---
type: modul
titel: "<Modulnavn>"
uddannelse: "<Uddannelsens navn>"
nr: 1
status: planlagt        # planlagt | i gang | afsluttet
beskrivelse: ""
tags: [modul]
---

# {{titel}}

Kort beskrivelse af modulet.

## Lektioner i dette modul

```dataview
TABLE nr AS "Nr", status AS "Status", varighed_min AS "Min", sidst_evalueret AS "Evalueret"
FROM #lektion
WHERE modul = this.titel
SORT nr ASC
```
