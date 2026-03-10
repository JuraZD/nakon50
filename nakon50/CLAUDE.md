# Nakon50 — Project Memory

## Misija
Praktični vodič za ljude 50+ koji žele koristiti AI, digitalne alate i tehnologiju
u svakodnevnom radu — bez pretjerane tehničke terminologije i bez dramatiziranja.

## Publika
- Primarno: 50–65 godina, zaposleni ili u karijernoj tranziciji
- Pametni, iskusni, ali ne-tehničari
- Nemaju vremena za teoriju — trebaju konkretne korake
- HR kontekst: uredski poslovi, administracija, javni sektor, slobodne profesije

## Ton i glas
- Direktno i praktično ("evo što trebaš napraviti")
- Bez kondescendencije — zabranjeno: "ovo je lako", "samo klikni", "svak može"
- Bez health/fitness framinga (bez "ostani fit", "budi aktivan" metafora)
- Empatično prema strahu od promjena — normaliziraj, ali fokusiraj na akciju
- Hrvatski jezik; tech termini smiju ostati na engleskom (AI, workflow, prompt...)
- Rečenice kratke. Paragrafi max 3 retka. Bez pasiva gdje je moguće.

## 5 rubrika (content pillars)
1. AI alati u praksi
2. Vještine koje se odmah koriste
3. Karijera 50+ i tržište rada
4. Projekti i dodatni prihodi
5. Sustavi i navike za učenje

## Hugo konvencije
- Bundle postovi: `content/posts/{godina}/{mm}/{slug}/index.md`
- Slike: unutar bundle foldera (ne u /static), format WebP gdje god moguće
- Cover slika: `cover.webp` unutar bundle foldera
- Shortcodi: `{{< checklist >}}`, `{{< cta >}}`, `{{< tip >}}`, `{{< d3chart >}}`
- Tagovi: 3–5 po postu, sve malim slovima, bez dijakritika u slug-u

## Obavezni frontmatter
```yaml
title: ""
date: YYYY-MM-DD
lastmod: YYYY-MM-DD
draft: false
description: ""        # max 155 znakova, ne počinje s "U ovom članku..."
slug: ""               # kebab-case, bez dijakritika, max 60 znakova
categories: [""]       # TOČNO jedna od 5 rubrika
tags: []               # 3–5 tagova
author: "Nakon50"
readingTime: true
series: ""             # opcionalno — za serijalne članke
featuredImage: "cover.webp"
```

## Quality bar — checklist prije svakog commita
- [ ] Jedan H1 (title iz frontmattera), logičan H2/H3 niz bez preskakanja
- [ ] Primjer iz prakse postoji (situacija → problem → rješenje → rezultat)
- [ ] Checklist shortcode na kraju
- [ ] CTA shortcode — konkretan, ne generički
- [ ] Min. 1 interni link na postojeći post s prirodnim sidro tekstom
- [ ] Meta description ≤ 155 znakova
- [ ] `hugo server` bez errora i bez warnings-a
- [ ] Readability: prosječna rečenica < 18 riječi, paragrafi max 3 retka
- [ ] Frontmatter lint prošao (svi obavezni fieldsovi popunjeni)

## Što izbjegavati — uvijek
- "Lako je samo..." / "Svak može..." / "Nije strašno..."
- Clickbait naslovi s brojevima bez pokrića ("17 trikova...")
- Liste bez objašnjenja (svaka stavka mora imati kontekst)
- Generički CTA: "Pročitajte više", "Saznajte više", "Kliknite ovdje"
- Pasivne konstrukcije > 10% teksta
- Eksterni linkovi bez rel="noopener" atributa

## Monetizacijski elementi (tek od M3 nadalje)
- Affiliate linkovi: transparentno označeni, samo alati koje realno koristimo
- Digitalni proizvodi: predlošci, prompt pack, mini priručnici
- Newsletter kao primarni kanal — svaki post ima CTA prema newsletteru
