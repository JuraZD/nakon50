# Skill: Article Draft

## Zadatak
Napiši kompletan Hugo post za Nakon50 prema outline.md i keywords.md.
Output je odmah publishabilan Markdown fajl s frontmatterom.

## Input
- `outline_path` — putanja do outline.md
- `keywords_path` — putanja do keywords.md
- `target_path` — gdje se sprema (npr. `content/posts/2026/02/ai-email-workflow/index.md`)
- `pillar` — rubrika
- `series` — naziv serije (opcionalno)

## Proces

### 1. Pročitaj outline i keywords
Ne improviziraš strukturu — pišeš prema outlineu.
KW koristiš prirodno, ne forsirano (ne "keyword stuffing").

### 2. Generiraj frontmatter

```yaml
---
title: "{H1 iz outlinea}"
date: {danas, YYYY-MM-DD}
lastmod: {danas, YYYY-MM-DD}
draft: false
description: "{max 155 znakova, sadrži primarni KW, ima CTA glagol, ne počinje s 'U ovom članku'}"
slug: "{kebab-case, bez dijakritika, max 60 znakova}"
categories: ["{pillar}"]
tags: [{3–5 tagova, malim slovima, bez dijakritika}]
author: "Nakon50"
readingTime: true
series: "{series ako postoji}"
featuredImage: "cover.webp"
---
```

**Pravila za description:**
- ✅ "Naučite kako postaviti AI email workflow u 5 koraka — prikladno i za početnike."
- ❌ "U ovom članku ćemo vam pokazati..."
- ❌ "Sve o AI emailovima."

**Pravila za slug:**
- ✅ `ai-email-workflow-uredski-posao`
- ❌ `kako-koristiti-ai-za-pisanje-e-mailova-na-poslu-bez-gubljenja-vremena`

**Pravila za tags:**
- ✅ `["ai", "email", "produktivnost", "chatgpt", "workflow"]`
- ❌ `["AI alati", "E-mail pisanje", "Produktivnost za početnike"]`

### 3. Uvod (bez H2, odmah ispod frontmattera)

Format: 3–4 rečenice.

```
Rečenica 1: Problem ili situacija (realna, nije dramatizirana)
Rečenica 2: Što ćeš naučiti / moći napraviti (konkretno)
Rečenica 3: Zašto je to relevantno za tvoj kontekst
[Rečenica 4: opcionalno — hook za nastavak]
```

Primjer:
> Pišeš isti tip emaila 10 puta tjedno. Svaki put od nule, svaki put
> gubite 5–10 minuta. U ovom vodiču postavit ćeš AI workflow koji ti
> generira prvi draft u 30 sekundi — bez pretplate na skupe alate.

### 4. Tijelo članka

Prati outline sekciju po sekciju. Za svaku H2:
- Napiši H2 naslov točno iz outlinea
- Piši prema opisu sadržaja iz outlinea
- Uključi KW/LSI prirodno (min. 1× primarni KW u prvom H2)
- Dodaj `{{< tip >}}` shortcode za ključne savjete (max 1–2 po sekciji)
- Koraci trebaju biti numerirani kad opisuju slijed radnji

**Format koraka:**
```markdown
**1. Otvori ChatGPT ili Claude**
Idi na chat.openai.com ili claude.ai. Besplatna verzija je dovoljna za početak.

**2. Pripremi sistemski prompt**
U prvoj poruci napiši kontekst svog posla. Primjer:
> "Ti si moj asistent za pisanje poslovnih emailova. Radim u
> [industrija], pišem emailove [klijentima/kolegama/dobavljačima].
> Ton: profesionalan ali topao."
```

### 5. Sekcija "Primjer iz prakse" (obavezna)

```markdown
## Primjer iz prakse: Marija iz računovodstvenog odjela

**Situacija:** Marija (57) radi kao viša računovođa u srednje velikoj tvrtki.
Svaki tjedan šalje 20–30 emailova dobavljačima i internim timovima.

**Problem:** Svaki email piše od nule. Gubi 45 minuta dnevno na pisanje
emailova koje smatra "tehničkim ali rutinskim poslom".

**Rješenje:**
1. Postavila sistemski prompt u ChatGPT s kontekstom svog posla
2. Napravila biblioteku od 8 predložnih promptova za najčešće situacije
3. Integrirala workflow: prompt → draft → 2-minutna dorada → slanje

**Rezultat:** Pisanje emailova svela na 15 minuta dnevno. Uštedila
~2.5 sata tjedno koje sada koristi za analitičke zadatke.
```

### 6. Checklist shortcode

```markdown
## Checklist: AI email workflow korak po korak

{{< checklist >}}
- [ ] Otvorio/la sam ChatGPT ili Claude račun
- [ ] Napisao/la sistemski prompt s kontekstom svog posla
- [ ] Testirao/la prompt na 3 različita tipa emaila
- [ ] Napravio/la biblioteku od 5+ promptova za česte situacije
- [ ] Postavio/la workflow: prompt → draft → dorada → slanje
{{< /checklist >}}
```

### 7. CTA shortcode

```markdown
## Sljedeći korak

{{< cta >}}
Preuzmi besplatni **Prompt Pack za uredske emailove** —
10 gotovih promptova koje možeš koristiti odmah.

[Preuzmi PDF →](https://nakon50.hr/resursi/prompt-pack-emailovi/)
{{< /cta >}}
```

Alternativno (ako nema downloada):
```markdown
{{< cta >}}
Prijavi se na tjedni newsletter — svaki tjedan jedan praktičan AI
vodič direktno u inbox, bez spama.

[Prijava na newsletter →](https://nakon50.hr/newsletter/)
{{< /cta >}}
```

### 8. Interni linkovi

Pretraži `content/posts/` za srodne postove.
Umetni min. 1 interni link s prirodnim sidro tekstom — ne "kliknite ovdje".

Ako ne postoje sodni postovi:
```markdown
<!-- INTERNI LINK TODO: Dodaj link na srodni post kad bude objavljen -->
```

## Output

Spremi kompletan fajl na `{target_path}`.
Fajl mora biti UTF-8, bez BOM, LF line endings.
