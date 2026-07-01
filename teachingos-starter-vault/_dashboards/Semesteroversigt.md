---
type: dashboard
titel: Semesteroversigt
tags: [dashboard]
---

# Semesteroversigt

Kræver **Dataview**-pluginnet (se README).

## Alle lektioner

```dataview
TABLE
  modul AS "Modul",
  nr AS "Nr",
  status AS "Status",
  varighed_min AS "Min",
  choice(sidst_evalueret, "✅", "—") AS "Evalueret"
FROM #lektion
SORT modul ASC, nr ASC
```

## Fremdrift pr. status

```dataview
TABLE length(rows) AS "Antal lektioner"
FROM #lektion
GROUP BY status
```

## Samlet undervisningstid

```dataview
TABLE sum(rows.varighed_min) AS "Minutter i alt"
FROM #lektion
GROUP BY modul AS "Modul"
```
