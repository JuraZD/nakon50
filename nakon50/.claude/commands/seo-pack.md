# Komanda: /seo-pack

Doradi SEO elemente postojećeg drafta.
Možeš koristiti samostalno ili se automatski poziva unutar /article-orchestrator.

## Ulazni parametri

| Parametar     | Obavezno | Opis |
|---------------|----------|------|
| `target_path` | DA       | Putanja do postojećeg index.md |
| `focus_kw`    | ne       | Primarna ključna riječ (ako već znaš) |
| `competitors` | ne       | URL-ovi konkurentskih članaka za analizu strukture |

## Primjer poziva

```
/seo-pack
target_path="content/posts/2026/02/ai-email-workflow/index.md"
focus_kw="AI email workflow"
```

## Što radi

### 1. Analiza trenutnog stanja
- Čita `target_path` i izvlači: naslov, H2/H3 strukturu, meta opis, slug, duljinu
- Identificira nedostatke prema Nakon50 quality baru

### 2. Dorađuje u fajlu
- **Title tag**: primarni KW u prvoj trećini, max 60 znakova
- **Meta description**: 120–155 znakova, sadrži KW, ima CTA glagol
- **Slug**: kebab-case, bez dijakritika, bez stop-wordova, max 60 znakova  
- **H2 struktura**: min. 1 H2 sadrži varijaciju KW prirodno
- **FAQ sekcija**: 3–5 pitanja iz "People also ask" za temu (dodaje na kraj ako nedostaje)
- **Alt tekst prijedlozi**: za svaku sliku unutar posta

### 3. Generira SEO report
Sprema u `workflows/article-orchestration/seo.md`:

```
=== SEO PACK REPORT ===
Datum: {datum}
Fajl: {target_path}

Primarna KW:       "{focus_kw}"
Sekundarne KW:     [lista]
LSI pojmovi:       [lista]

Title (final):     "{naslov}" ({X} znakova)
Meta desc (final): "{opis}" ({X} znakova)
Slug (final):      /{slug}/

H struktura:
H1: {naslov}
  H2: {naslov sekcije}
    H3: {naslov podsekcije}
  H2: ...

Interni link prijedlozi:
- Iz ovog posta → "{naslov drugog posta}" (/{slug}/) — sidro: "{tekst linka}"
- ...

Procijenjeni SEO score: XX/100
Razlog gubitka bodova: [lista]
```

## Napomena
Skill koji se poziva: `skills/seo-pack.md`
