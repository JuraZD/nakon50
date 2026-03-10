# Skill: Hugo Validate

## Zadatak
Pokreni Hugo build i analiziraj rezultate. Generiraj strukturirani report.

## Input
- `scope` — `full` / `single` (default: full)
- `verbose` — `true` / `false`

## Proces

### 1. Čisti build
```bash
hugo --minify 2>&1
```

Parsaj output i kategoriziraj:
- `ERROR` → blokiraju build → FAIL
- `WARN` → ne blokiraju → bilježi
- Trajanje builda (performansni indikator)
- Broj generiranih stranica

### 2. Template metrike (ako verbose: true)
```bash
hugo --templateMetrics 2>&1
```

### 3. Frontmatter provjera
Pokreni `skills/frontmatter-linter.md` s `scope: all`.
Integriraj rezultate u report.

### 4. Draft provjera
```bash
hugo list drafts 2>&1
```

## Interpretacija errora

| Error tip | Značenje | Preporučena akcija |
|-----------|----------|-------------------|
| `failed to render` | Template greška | Provjeri shortcode sintaksu |
| `ref "..." not found` | Broken interni link | Ispravi putanju linka |
| `YAML error` | Nevalidan frontmatter | Provjeri YAML sintaksu (navodnici, uvlake) |
| `no bundle found` | Post bez bundle foldera | Kreiraj folder i premjesti .md |
| `shortcode not found` | Nepostoji shortcode | Provjeri layouts/shortcodes/ |

## Output: workflows/article-orchestration/build-report.md

```markdown
# Hugo Validate Report
Datum: {datum i vrijeme}
Hugo verzija: {verzija iz `hugo version`}
Scope: {full / single}

---

## BUILD STATUS: ✅ PASS / ❌ FAIL

Trajanje builda: {X}s
Generirane stranice: {X}
Draftovi (isključeni): {X}

---

## Errori (blokiraju deploy)

{Nema errora. ✅}

/ ako postoje:

### 1. {tip errora}
Fajl: {putanja}
Redak: {X}
Poruka: `{originalna poruka}`
Prijedlog ispravka: {konkretna akcija}

---

## Upozorenja (doradi kad imaš vremena)

{Nema upozorenja. ✅}

/ ako postoje:

- {upozorenje 1}
- {upozorenje 2}

---

## Draftovi koji čekaju objavu

| Putanja | Datum kreiranja | Dana čeka |
|---------|-----------------|-----------|
| {path}  | {datum}         | {X} dana  |

---

## Statistike sadržaja

| Rubrika | Postova |
|---------|---------|
| AI alati u praksi | X |
| Vještine koje se odmah koriste | X |
| Karijera 50+ i tržište rada | X |
| Projekti i dodatni prihodi | X |
| Sustavi i navike za učenje | X |
| **UKUPNO** | **X** |

---

## Preporuka

### ✅ PASS
```
Spreman za deploy:
git add .
git commit -m "post: {naslov posta}"
git push origin main

GitHub Actions će automatski buildati i deployati na GitHub Pages.
```

### ❌ FAIL
Ispravi greške navedene gore.
**Ne commiti** dok build ne prođe.
Nakon ispravke pokreni /hugo-validate ponovo.
```
