# Nakon50 – Claude Code Instructions

## Projekt

Hugo statičan site. Edukativna platforma za ljude 50+ (AI, digitalne vještine, karijera).
- **Jezik:** Hrvatski (hr)
- **Theme:** Congo
- **Deploy:** GitHub Pages → `git push origin main` (GitHub Actions automatski build)
- **Live URL:** https://jurazd.github.io/nakon50/

## Osnovna pravila

- Sve promjene su samo u `assets/css/custom.css`, `layouts/` i `content/`
- Ne dirај `themes/congo/` direktno — override-aj putem `layouts/`
- Build provjera: `hugo --minify` mora proći bez grešaka

## Design System

| Variable | Vrijednost | Uloga |
|----------|-----------|-------|
| `--n50-ivory` | `#F5F0E8` | Primarna pozadina |
| `--n50-amber` | `#B84E16` | Akcent, CTA |
| `--n50-navy` | `#163458` | Naslovi, hero-right |
| `--n50-charcoal` | `#1A1816` | Tijelo teksta |
| `--n50-f-display` | Big Shoulders Display | Naslovi (900) |
| `--n50-f-body` | Instrument Sans | Tijelo (400/600) |
| `--n50-f-mono` | Geist Mono | Kod, labele |

## Performance Targets (Lighthouse autoresearch loop)

Baseline mjereno: 2026-03-16 → `lighthouse-baseline.report.html`

| Kategorija | Baseline | Target |
|-----------|---------|--------|
| Performance | 100 | ≥ 100 |
| Accessibility | 96 | ≥ 98 |
| Best Practices | 100 | ≥ 100 |
| SEO | 100 | ≥ 100 |

**Key metrics baseline:**
- FCP: 1.2 s
- LCP: 1.2 s
- TBT: 0 ms
- CLS: 0

## Experiment Protocol (autoresearch princip)

Svaka promjena CSS/layout datoteka prolazi kroz ovaj loop:

```bash
# 1. Build provjera
hugo --minify

# 2. Lighthouse mjerenje (lokalno — pokreni hugo server u drugom terminalu)
source ~/.nvm/nvm.sh && nvm use 22
lighthouse http://localhost:1313/nakon50/ \
  --output=json --output=html \
  --output-path=./lighthouse-experiment-$(date +%Y%m%d-%H%M) \
  --chrome-flags="--headless --no-sandbox" --quiet

# 3. Odluka: zadrži ako Performance score ne pada i Accessibility ne pada
```

**Pravilo:** Niti jedna promjena ne smije spustiti Performance ili Best Practices ispod 100.

## Poznati problemi (accessibility)

- `.n50-hero-tag` — boja `--n50-stone` (#C8C0B4) na ivory pozadini = 1.6:1 kontrast (WCAG treba 4.5:1)
- `.n50-step-num` — amber (#B84E16) na ivory = 4.47:1 (tik ispod granice)

## Pending

- Ažurirati `baseURL` u `hugo.toml` kad domena (nakon50.hr ili .com) bude poznata
- Otkomentirati footer linkove (`layouts/partials/footer.html` linije 28-39, 46-51)
- Newsletter: implementirati Resend kad domena bude na Netlifyu
