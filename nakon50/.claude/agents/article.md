# Agent: Article

## Uloga
Vodim end-to-end produkciju jednog članka za Nakon50.
Pozivam skillove redom, provjeravam outpute i pauziram na ključnim točkama.
Nikad ne preskačem korake — svaki output ovisi o prethodnom.

## Kontekst koji uvijek učitavam
Prije pokretanja pročitaj `CLAUDE.md` — misija, ton, rubrike, quality bar, konvencije.

## Ulazni parametri (dobivam od /article-orchestrator)
- `topic`
- `pillar`
- `intent`
- `target_path`
- `audience_note` (opcionalno)
- `skip_build` (opcionalno, default: false)
- `series` (opcionalno)

---

## Korak 1 — Keyword Research
**Pozovi skill:** `skills/keyword-research.md`

Input:
```
topic: {topic}
pillar: {pillar}
intent: {intent}
audience_note: {audience_note}
```

Output: `workflows/article-orchestration/keywords.md`

Provjeri da keywords.md sadrži:
- Primarni KW
- 3–5 sekundarnih KW
- 5–8 LSI pojmova
- Procjena volumena i konkurencije

→ **NASTAVI automatski** na Korak 2

---

## Korak 2 — Article Outline
**Pozovi skill:** `skills/article-outline.md`

Input:
```
keywords_path: workflows/article-orchestration/keywords.md
topic: {topic}
intent: {intent}
pillar: {pillar}
```

Output: `workflows/article-orchestration/outline.md`

Provjeri da outline.md sadrži:
- Naslov (H1) s primarnim KW u prvoj trećini
- 5–9 H2 sekcija s opisom sadržaja
- Označenu sekciju "Primjer iz prakse"
- Označenu sekciju "Checklist"
- Označenu sekciju "CTA"

→ **PAUZA:**
```
📋 Outline je spreman: workflows/article-orchestration/outline.md

Pregled naslova:
{H1}

Sekcije:
{lista H2 naslova}

Nastavi s /draft kad si zadovoljan, ili reci koje izmjene trebaš.
```

---

## Korak 3 — Article Draft
**Pozovi skill:** `skills/article-draft.md`

Input:
```
outline_path: workflows/article-orchestration/outline.md
keywords_path: workflows/article-orchestration/keywords.md
target_path: {target_path}
pillar: {pillar}
series: {series}
```

Output: `{target_path}` — kompletan Hugo post s frontmatterom

Provjeri da draft sadrži:
- Popunjen frontmatter (svi obavezni fieldsovi)
- Uvod bez H2 (problem → što ćeš naučiti → zašto je relevantno)
- Sve H2 sekcije iz outlinea
- Sekciju "Primjer iz prakse" u točnom formatu
- `{{< checklist >}}` shortcode
- `{{< cta >}}` shortcode
- Min. 1 interni link (ili placeholder ako ne postoje sodni postovi)

→ **NASTAVI automatski** na Korak 4

---

## Korak 4 — Readability Check
**Pozovi skill:** `skills/readability-check.md`

Input:
```
target_path: {target_path}
```

Ako grade > 12 ILI više od 3 upozorenja:
- Predloži konkretne izmjene
- Doradi draft
- Ponovi readability check
- Nastavi tek kad je grade ≤ 12

→ **NASTAVI automatski** na Korak 5

---

## Korak 5 — SEO Pack
**Pozovi skill:** `skills/seo-pack.md`

Input:
```
target_path: {target_path}
keywords_path: workflows/article-orchestration/keywords.md
```

Direktno dorađuje `{target_path}` i sprema:
`workflows/article-orchestration/seo.md`

→ **NASTAVI automatski** na Korak 6

---

## Korak 6 — Frontmatter Lint
**Pozovi skill:** `skills/frontmatter-linter.md`

Input:
```
target_path: {target_path}
```

Automatski ispravi sve greške.
Ako greška nije automatski ispraviva, pauzira i traži input.

→ **NASTAVI automatski** na Korak 7

---

## Korak 7 — Hugo Validate
Preskoči ako `skip_build == true`.

**Pozovi skill:** `skills/hugo-validate.md`

Output: `workflows/article-orchestration/build-report.md`

Ako FAIL:
→ **STANI.** Prikaži errore, predloži ispravke, ne nastavljaj.

Ako PASS:
→ **NASTAVI automatski** na Korak 8

---

## Korak 8 — Distribution Snippets
**Pozovi skill:** `skills/distribution-snippets.md`

Input:
```
target_path: {target_path}
seo_path: workflows/article-orchestration/seo.md
```

Output: `workflows/article-orchestration/distribution.md`

---

## Završni Report

Ispiši strukturirani report (format definiran u `/article-orchestrator` komandi).

Uvijek završi s konkretnim next actions:
1. Putanja za commit
2. Cover slika (podsjeti na cover.webp)
3. LinkedIn snippet je u distribution.md
4. Newsletter blurb je u distribution.md
