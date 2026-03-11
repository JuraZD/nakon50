# Nakon50

Edukativna platforma za ljude koji ulaze u novu fazu rada — AI alati, digitalne vještine i karijera 50+.

**Live:** https://JuraZD.github.io/nakon50/

---

## Tehnički stack

- **Generator:** [Hugo](https://gohugo.io/) (statičan site)
- **Tema:** [Congo](https://jpanther.github.io/congo/)
- **Hosting:** GitHub Pages (automatski deploy via GitHub Actions)
- **Jezik:** Hrvatski

## Struktura projekta

```
nakon50/
├── archetypes/          # Hugo predlošci za nove stranice
├── assets/css/          # custom.css — svi prilagođeni stilovi
├── config/_default/     # Konfiguracija (params, menus, languages)
├── content/             # Markdown članci
│   ├── ai-alati/        # Vodiči za AI alate
│   ├── karijera/        # Karijera 50+
│   ├── projekti/        # Digitalni projekti
│   ├── ucenje/          # Učenje i razvoj
│   ├── vjestine/        # Digitalne vještine
│   ├── clanci/          # Unified lista svih članaka
│   ├── o-projektu/        # "Što je Nakon50?", privatnost.md, uvjeti.md
│   └── usluge/          # Usluge (konzultacije, radionice)
├── layouts/             # Hugo template overrideovi
│   ├── _default/        # single.html — layout za članak, list.html
│   ├── clanci/          # list.html — unified prikaz svih članaka
│   ├── o-projektu/      # list.html — full-width layout za sekciju
│   ├── usluge/          # list.html — stranica usluga
│   ├── partials/        # footer.html, logo.html, extend_head.html, cookie-banner.html
│   └── shortcodes/      # d3chart.html — D3.js grafovi
├── static/
│   ├── data/            # JSON podaci za D3 grafove
│   └── img/             # Slike (favicon, OG)
├── templates/           # Predlošci za pisanje novih članaka
├── themes/congo/        # Congo tema (ne mijenjati direktno)
└── hugo.toml            # Glavni konfig
```

## Lokalni razvoj

```bash
# Pokretanje dev servera
hugo server

# Build za produkciju
hugo --minify
```

## Dodavanje novog članka

Predlošci se nalaze u `templates/` folderu. Primjer:

```bash
hugo new ai-alati/naziv-clanka.md
```

Frontmatter koji svaki članak treba:

```yaml
---
title: "Naslov članka"
date: 2026-01-01
description: "Kratki opis za SEO i prikaz u listama"
summary: "Jedna rečenica za karticu u listi"
categories: ["AI Alati"]
tags: ["chatgpt", "produktivnost"]
---
```

## D3.js grafovi

Shortcode za ugradnju interaktivnog grafa u članak:

```
{{< d3chart id="jedinstveni-id" type="bar" datafile="/data/naziv.json" title="Naslov grafa" >}}
```

Podržani tipovi: `bar`, `hbar`, `line`, `multiline`, `pie`, `donut`, `scatter`

JSON format podataka i primjeri nalaze se u `static/data/`.

## GDPR i pravne stranice

Sve pravne stranice su u `content/o-projektu/` s `_build: { list: never, render: always }` — vidljive su na URL-u ali ne pojavljuju se u listama i gredu članaka.

| Stranica | URL | Fajl |
|---|---|---|
| Politika privatnosti i kolačića | `/o-projektu/privatnost/` | `content/o-projektu/privatnost.md` |
| Uvjeti korištenja | `/o-projektu/uvjeti/` | `content/o-projektu/uvjeti.md` |

Cookie banner (`layouts/partials/cookie-banner.html`) prikazuje se pri prvoj posjeti, koristi `localStorage` za pamćenje pristanka.

**Placeholderi koje treba popuniti:**
- `[UPIŠI IME I PREZIME]` i `[UPIŠI EMAIL]` u `privatnost.md`
- `[IME I PREZIME]`, `[kratki opis]`, `[EMAIL]` u `o-projektu/_index.md` i `uvjeti.md`

---

## Deploy

Push na `main` granu automatski pokreće GitHub Actions workflow koji builda i deploya site na GitHub Pages.

```bash
git push origin main
```

## Design sustav

| Token | Vrijednost | Uporaba |
|---|---|---|
| `--n50-ivory` | `#F5F0E8` | Pozadina |
| `--n50-amber` | `#B84E16` | Primarni akcent, CTA gumbi |
| `--n50-navy` | `#163458` | Sekundarni akcent |
| `--n50-charcoal` | `#1A1816` | Tekst |
| `--n50-f-display` | Big Shoulders Display | Naslovi |
| `--n50-f-body` | Instrument Sans | Tijelo teksta |
| `--n50-f-mono` | Geist Mono | Labele, meta podatci |

Svi stilovi nalaze se u `assets/css/custom.css`. Congo tema se ne mijenja direktno — sve prilagodbe idu kroz override layoute u `layouts/`.
