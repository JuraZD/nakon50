# Komanda: /hugo-validate

Pokreće Hugo build i provjerava ima li errora, warningsa i broken linkova.
Možeš koristiti u bilo kojem trenutku ili se automatski poziva u /article-orchestrator.

## Ulazni parametri

| Parametar  | Obavezno | Opis |
|------------|----------|------|
| `scope`    | ne       | `single` (samo zadnji post) / `full` (cijeli site) — default: full |
| `verbose`  | ne       | `true` za detaljni output (default: false) |

## Primjer poziva

```
/hugo-validate
scope="full"
verbose="true"
```

## Što radi

```bash
# Korak 1 — čist build
hugo --minify 2>&1

# Korak 2 — provjera broken internih linkova
hugo --templateMetrics --buildDrafts 2>&1 | grep -i "error\|warn"

# Korak 3 — provjera frontmattera
# Prolazi kroz sve .md i traži obavezne fieldsove iz CLAUDE.md
```

## Output — build-report.md

Sprema u `workflows/article-orchestration/build-report.md`:

```
=== HUGO VALIDATE REPORT ===
Datum:     {datum i vrijeme}
Hugo ver:  {verzija}
Scope:     {full / single}

BUILD STATUS: ✅ PASS / ❌ FAIL

--- Errori (blokiraju deploy) ---
[lista errora ili "Nema errora"]

--- Upozorenja (ne blokiraju, ali doradi) ---
[lista warningsa ili "Nema upozorenja"]

--- Frontmatter audit ---
Postovi s nedostajućim fieldovima:
- {putanja}: nedostaje {field}
...

--- Statistike ---
Ukupno postova:  X
Draftova:        X (nisu uključeni u build)
Kategorije:      {rubrika: X postova, ...}

--- Preporuka ---
[PASS] Spreman za: git commit && git push
[FAIL] Ispravi greške prije commita.
```

## Što znači FAIL
Ako build vrati FAIL:
1. Prikaži errore i točne linije koda
2. Predloži ispravke
3. NE nastavljaj s deployom
4. Nakon ispravke: automatski ponovi `/hugo-validate`
