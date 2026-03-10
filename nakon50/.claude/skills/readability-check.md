# Skill: Readability Check

## Zadatak
Procijeni čitljivost teksta za Nakon50 publiku i daj konkretne prijedloge za doradu.
Publika su pametni, iskusni čitatelji — ali nemaju vremena za kompleksne rečenice.

## Input
- `target_path` — putanja do index.md

## Proces

### 1. Pročitaj fajl
Ignoriraj: frontmatter (između ---), shortcode tagove ({{< >}}), kod blokove (``` ```).
Analiziraj: samo čisti tekst tijela članka.

### 2. Metrička analiza

**A) Prosječna duljina rečenice**
- Podijeli ukupne riječi s brojem rečenica
- Cilj: ≤ 18 riječi prosječno
- Upozorenje: > 22 riječi

**B) Dugi paragrafi**
- Paragraf = blok teksta između praznih redaka
- Upozorenje ako paragraf ima > 5 rečenica ili > 80 riječi
- Prikaži redni broj retka u fajlu

**C) Pasivne konstrukcije**
Traži obrasce: "je napravljen", "će biti", "treba biti", "može biti", "bio je napravljen"
- Cilj: < 10% rečenica
- Upozorenje: > 15%

**D) Višesložne riječi**
Riječi s > 3 sloga koje čine > 25% teksta signaliziraju kompleksnost.
(aproksimacija — brojaj slogove heuristički: 1 slog ≈ 1 samoglasnik)

**E) Rečenice počinju s istom riječju**
Ako 3+ uzastopnih rečenica počinje istom riječju → upozorenje.

**F) "Forbidden phrases" provjera**
Traži i označi:
- "Lako je samo"
- "Svak može"
- "Nije strašno"
- "Nije komplicirano"
- "Samo klikni"
- "Bez problema"
- "Uopće nije teško"

### 3. Procjena grade levela
Aproksimacija Flesch-Kincaid (prilagođeno za HR):
```
Grade = (0.39 × prosj_rij_po_rečenici) + (11.8 × prosj_slogovi_po_riječi) - 15.59
```

Cilj: ≤ 12
Crveno: > 14

## Output — inline report

```
=== READABILITY CHECK ===
Fajl: {target_path}
Analizirane riječi: {X}
Rečenice: {X}

METRIKE:
Prosj. rečenica:     {X} riječi  [✅ OK / ⚠️ UPOZORENJE / ❌ PREVISOKO]
Dugi paragrafi:      {X} pronađenih [✅ / ⚠️ / ❌]
Pasivne konstr.:     {X}% rečenica [✅ / ⚠️ / ❌]
Forbidden phrases:   {X} pronađenih [✅ / ❌]
Procij. grade level: {X} [✅ ≤12 / ⚠️ 13-14 / ❌ ≥15]

UKUPNA OCJENA: ✅ PASS / ⚠️ DORADI / ❌ FAIL

---
PRIJEDLOZI ZA DORADU:

⚠️ Dugački paragrafi (preporučena akcija: podijeli na 2-3):
- Redak {X}: "{prvih 40 znakova paragrafa}..."
  → Prijedlog: podijeli iza rečenice "{kraj rečenice za rezanje}"

⚠️ Duge rečenice (preporučena akcija: skrati ili podijeli):
- Redak {X}: "{cijela rečenica}"
  → Prijedlog: "{preformulirana verzija}"

❌ Forbidden phrase:
- Redak {X}: "...{kontekst}..."
  → Zamijeni s: "{alternativa bez kondescendencije}"

✅ PASS — nastavi na sljedeći korak.
/ 
❌ FAIL — doradi i ponovi provjeru.
```

## Što znači FAIL
Ako grade > 12 ILI pronađene forbidden phrases:
- Agent pauza i prikaže report
- Predloži konkretne izmjene
- Nakon dorade: ponovi skill automatski
- Nastavi tek kad grade ≤ 12 i nema forbidden phrases
