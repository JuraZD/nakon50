# Komanda: /internal-link-audit

Skenira sve postove i generira mapu internih linkova s konkretnim prijedlozima
za nove veze između tematski srodnih članaka.

## Ulazni parametri

| Parametar    | Obavezno | Opis |
|--------------|----------|------|
| `scope`      | ne       | `all` / `{rubrika}` (default: all) |
| `min_links`  | ne       | Upozori na postove s manje od X dolaznih linkova (default: 1) |
| `output`     | ne       | `full` / `summary` (default: full) |

## Primjer poziva

```
/internal-link-audit
scope="all"
min_links="2"
```

## Tijek izvršavanja

```
[1] internal-link-scanner — čita sve .md fajlove
[2] Gradi mapu: slug → meta + sadržaj
[3] Analizira linkove: dolazni, odlazni, siročad
[4] Identificira nepovezane tematske srodnosti
[5] Generira prijedloge s konkretnim sidro tekstom
[6] Sprema: workflows/link-audit/audit-{datum}.md
```

## Output — audit-{datum}.md

```
=== INTERNAL LINK AUDIT ===
Datum:          {datum}
Skenirani fajlovi: X

──────────────────────────────────────
📊 STATISTIKE
──────────────────────────────────────

Ukupno postova:       X
Prosj. dolazni:       X linkova/post
Prosj. odlazni:       X linkova/post

Distribucija po rubrikama:
- AI alati u praksi:          X postova
- Vještine koje se odmah...:  X postova
- Karijera 50+:               X postova
- Projekti i dodatan prihod:  X postova
- Sustavi i navike:           X postova

──────────────────────────────────────
🚨 SIROČAD (0 dolaznih linkova)
──────────────────────────────────────

Ovi postovi nisu nigdje linkani — nitko ih ne može organski otkriti:

1. /posts/2026/01/obsidian-pocetak/
   Naslov: "Obsidian za početnike: kako početi za 30 minuta"
   Kategorija: Sustavi i navike
   → Prijedlog: dodaj link u "{naslov srodnog posta}" (/{slug}/)
      Sidro tekst: "Obsidian za organizaciju bilješki"

2. ...

──────────────────────────────────────
🔗 TOP PRIJEDLOZI ZA NOVE LINKOVE
──────────────────────────────────────

Format: IZ → U (sidro tekst)

1. /posts/2026/02/ai-email-workflow/
   → /posts/2026/01/prompt-library/
   Sidro: "kako izgraditi vlastitu prompt biblioteku"
   Gdje u tekstu: sekcija "Korak 3 — Pripremi prompte"

2. /posts/2026/01/excel-ai-izvjestaj/
   → /posts/2026/02/python-csv-automatizacija/
   Sidro: "automatizirati obradu podataka u Pythonu"
   Gdje u tekstu: zaključni paragraf

[... max 15 prijedloga, poredani po prioritetu ...]

──────────────────────────────────────
🗺 MREŽA PO RUBRIKAMA (ASCII)
──────────────────────────────────────

AI ALATI U PRAKSI
  [ai-email-workflow] ──→ [prompt-library]
  [chatgpt-za-excel]  ──→ [ai-email-workflow]
  [chatgpt-za-excel]  ──→ [prompt-library]

VJEŠTINE KOJE SE ODMAH KORISTE
  [excel-pivot]       ──→ [chatgpt-za-excel]
  [python-csv]        ──→ [excel-pivot] (NEDOSTAJE →)

... (jedna rubrika po sekciji)

──────────────────────────────────────
✅ NEXT ACTIONS
──────────────────────────────────────

[ ] Dodaj linkove za X siročadi (visoki prioritet)
[ ] Implementiraj X prijedloga iz "Top prijedlozi"
[ ] Pokreni /internal-link-audit za 5 novih postova
```

## Agent koji se poziva
`agents/site-analyst.md`
