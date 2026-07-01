---
type: dashboard
titel: Kursus - Mangler
tags: [dashboard]
---

# Kursus — hvad mangler?

Kræver **Dataview**-pluginnet. Viser lektioner hvor noget endnu ikke er på plads.

## Mangler slides

```dataview
LIST
FROM #lektion
WHERE !slides
SORT modul ASC, nr ASC
```

## Mangler quiz

```dataview
LIST
FROM #lektion
WHERE !quiz
SORT modul ASC, nr ASC
```

## Mangler læringsmål

```dataview
LIST
FROM #lektion
WHERE length(laeringsmaal) = 0 OR !laeringsmaal
SORT modul ASC, nr ASC
```

## Ikke evalueret endnu

```dataview
LIST
FROM #lektion
WHERE !sidst_evalueret AND status = "gennemført"
SORT modul ASC, nr ASC
```

## Samlet mangel-overblik

```dataview
TABLE
  choice(slides, "✅", "❌") AS "Slides",
  choice(quiz, "✅", "❌") AS "Quiz",
  choice(length(laeringsmaal) > 0, "✅", "❌") AS "Læringsmål",
  choice(sidst_evalueret, "✅", "❌") AS "Evalueret"
FROM #lektion
SORT modul ASC, nr ASC
```
