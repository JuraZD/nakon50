# Skill: Frontmatter Linter

## Zadatak
Provjeri i automatski ispravi frontmatter jednog ili više Hugo postova.
Uspoređuje s obaveznom strukturom iz CLAUDE.md.

## Input
- `target_path` — putanja do jednog fajla ILI `scope: all` za cijeli content/

## Obavezna struktura (iz CLAUDE.md)

```yaml
title: ""           # string, nije prazan
date: YYYY-MM-DD    # validan datum
lastmod: YYYY-MM-DD # validan datum, ≥ date
draft: false        # boolean
description: ""     # string, 1–155 znakova, nije prazan
slug: ""            # kebab-case, bez dijakritika, 1–60 znakova
categories: [""]    # točno jedna od 5 rubrika
tags: []            # array, 3–5 tagova
author: "Nakon50"   # točno "Nakon50"
readingTime: true   # boolean
featuredImage: "cover.webp"  # string
# series: ""        # opcionalno, ali ako postoji mora biti string
```

## Pravila validacije

| Field | Provjera | Automatska ispravka? |
|-------|----------|----------------------|
| `title` | nije prazan | NE — traži input |
| `date` | validan YYYY-MM-DD format | NE — traži input |
| `lastmod` | postoji i ≥ date | DA — postavi na date ako nedostaje |
| `draft` | je boolean (ne string "false") | DA — ispravi tip |
| `description` | 1–155 znakova | NE ako prazan, DA ako predug (skrati) |
| `slug` | kebab-case, bez dijakritika, ≤60z | DA — generiraj iz title |
| `categories` | točno 1, jedna od 5 rubrika | NE — traži input |
| `tags` | array, 3–5 stavki, malim slovima | DA — normaliziraj case |
| `author` | točno "Nakon50" | DA — ispravi |
| `readingTime` | boolean true | DA — dodaj ako nedostaje |
| `featuredImage` | "cover.webp" | DA — dodaj ako nedostaje |

## Slug generiranje (ako nedostaje ili je nevalidan)

1. Uzmi `title`
2. Pretvori dijakritike: č→c, ć→c, š→s, ž→z, đ→d
3. Malim slovima
4. Zamijeni razmake s `-`
5. Ukloni sve osim a-z, 0-9, -
6. Ukloni stop-wordove: za, u, i, na, s, o, je, su, se, te, da, od, do, po, iz
7. Skrati na 60 znakova (na granici cijele riječi)

Primjer:
`"Kako koristiti AI za pisanje e-mailova"` → `ai-pisanje-emailova`

## Provjera 5 rubrika (categories)
```
Dozvoljene vrijednosti:
- "AI alati u praksi"
- "Vještine koje se odmah koriste"
- "Karijera 50+ i tržište rada"
- "Projekti i dodatni prihodi"
- "Sustavi i navike za učenje"
```

## Output — inline report

### Za jedan fajl:
```
=== FRONTMATTER LINT: {filename} ===

✅ Ispravci primijenjeni automatski:
- lastmod: nije postajao → postavljeno na {date}
- author: "nakon50" → "Nakon50"
- readingTime: nedostajao → dodano: true
- tags: ["AI", "EMAIL"] → ["ai", "email"] (normaliziran case)

⚠️ Traži ručni unos:
- categories: prazno → Koja rubrika?
  Opcije: [1] AI alati u praksi  [2] Vještine koje se odmah koriste
          [3] Karijera 50+       [4] Projekti i prihodi
          [5] Sustavi i navike

❌ Kritična greška — ne možeš nastaviti bez ispravka:
- title: prazno → Upiši naslov članka.

STATUS: ⚠️ DJELOMIČNO ISPRAVLJENO — čeka ručni unos.
```

### Za scope: all (cijeli content/):
```
=== FRONTMATTER AUDIT — CIJELI SITE ===
Skenirano: {X} fajlova

✅ Bez grešaka: {X} fajlova
⚠️ Automatski ispravljeno: {X} fajlova
❌ Traži ručni unos: {X} fajlova

PROBLEMATIČNI FAJLOVI:
1. content/posts/2026/01/primjer/index.md
   - categories: prazno
   - description: 187 znakova (predugačko)

2. content/posts/2025/12/stari-post/index.md
   - slug: "stari post sa razmakom" (nevalidan)
   → Prijedlog: "stari-post-sa-razmakom"

Pokrenuto automatskih ispravaka: {X}
Ostaje za ručno: {X}
```
