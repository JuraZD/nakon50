# Komanda: /newsletter-weekly

Generira tjedni newsletter za Nakon50 — plain text verziju i HTML verziju za email.

## Ulazni parametri

| Parametar        | Obavezno | Opis |
|------------------|----------|------|
| `week_start`     | DA       | Datum početka tjedna (YYYY-MM-DD) |
| `include_posts`  | DA       | Lista slug-ova novih postova (comma-separated) |
| `tone`           | ne       | `summary` / `curated` / `opinionated` (default: curated) |
| `max_items`      | ne       | Max broj eksternih resursa (default: 3) |
| `teaser`         | ne       | Kratka najava za sljedeći tjedan (1 rečenica) |

## Primjer poziva

```
/newsletter-weekly
week_start="2026-02-24"
include_posts="ai-email-workflow,obsidian-pocetak"
tone="curated"
teaser="Sljedeći tjedan: kako automatizirati tjedni izvještaj u Pythonu za 20 minuta."
```

## Tijek izvršavanja

```
[1] Čitaj frontmatter i sadržaj svakog posta iz include_posts
[2] Izvuci: naslov, description, slug, kategoriju, ključni takeaway
[3] Pozovi skill: newsletter-digest.md
[4] Generiraj 3 varijante subject linea (A/B/C test)
[5] Sastavi newsletter u dva formata:
    → workflows/newsletter/weekly-{week_start}.md       (plain text)
    → workflows/newsletter/weekly-{week_start}-html.md  (HTML email)
```

## Format newslettera

### Subject line (3 varijante)
```
A: [direktan] "{konkretna korist ovog tjedna}"
B: [pitanje]  "{Pitanje koje rezonira s publikom?}"
C: [novost]   "Novo na Nakon50: {naslov najvažnijeg posta}"
```

### Struktura sadržaja

```
---
Bok [ime],

[Uvodni paragraf — 3–4 rečenice, osoban ton, vezan uz temu tjedna]

──────────────────────────────────────
📌 OVAJ TJEDAN NA NAKON50
──────────────────────────────────────

1. {Naslov posta 1}
   {1–2 rečenice — problem koji rješava + što ćeš naučiti}
   → {puni URL}

2. {Naslov posta 2}
   {1–2 rečenice}
   → {puni URL}

──────────────────────────────────────
🔗 ŠTO SAM JOŠ ČITAO / GLEDAO
──────────────────────────────────────

- {Naziv resursa} — {1 rečenica zašto vrijedi}
  → {URL}

- {Naziv resursa} — {1 rečenica}
  → {URL}

──────────────────────────────────────

[Zaključni paragraf — 2–3 rečenice, refleksija ili poticaj]

Do sljedećeg tjedna,
[Potpis]

P.S. {Kratka opservacija, pitanje publici ili najava sljedećeg tjedna}

───
Odjavnica: {link}   |   Arhiva: {link}
Nakon50.hr
```

## Napomena o HTML verziji
HTML verzija koristi isti sadržaj ali s:
- `<h2>` za sekcijske naslove
- `<ul>` za liste resursa
- Gumbom (link styled as button) za svaki post
- Inline CSS (kompatibilan s Gmail, Outlook, Apple Mail)

Agent: `agents/newsletter.md`
