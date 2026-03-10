---
title: "ChatGPT u uredu: 7 prompta koji zaista rade"
date: 2026-02-20
tags: ["ChatGPT", "prompt", "ured", "produktivnost"]
categories: ["AI Alati u Praksi"]
summary: "Ne treba ti 500 prompta. Treba ti 7 koji pokrivaju 80% uredskih zadataka. Ovdje su."
showTableOfContents: true
---

![Radna površina s laptopom i podacima](/img/workspace.jpg)

Kad pitaš prosječnog radnika što radi s ChatGPT-om, čuješ: „Pa... pitam ga svašta." Kad pitaš koliko mu to štedi vremena, odgovor je nejasan.

Problem nije AI. Problem je nestrukturirani pristup.

Ovo je 7 prompta koji pokrivaju konkretne uredske zadatke — testiranih na stvarnim situacijama.

---

## Zašto samo 7?

Jer 80% onoga što uradiš u uredu spada u ove kategorije: pisanje, sažimanje, analiza, prijevod, formatiranje, brainstorming i izvještaji.

{{< d3chart
  id="chart-prompts"
  datafile="/data/ai-alati.json"
  type="hbar"
  title="Korisnost prompt kategorija u uredskom radu"
  subtitle="% korisnika koji su kategoriju ocijenili kao 'visoko korisnu' (n=148)"
  label="ANALIZA PROMPTA"
  source="Nakon50 istraživanje, veljača 2026"
  height="320"
>}}

Sažimanje i email su na vrhu — nije iznenađenje. Ono što iznenađuje je da su **izvještaji** na dnu popularnosti, ali **najviše štede vremena** (40 minuta po izvještaju).

---

## 7 prompta

### 01 — Sažimanje dugog emaila ili dokumenta

```
Sažmi ovaj tekst u 5 ključnih točaka, svaka max 2 rečenice.
Fokusiraj se na akcijske stavke i rokove.

[Zalijepi tekst]
```

**Kad koristiti:** Svaki put kad dobiješ email duži od 3 paragrafa ili dokument od više stranica.

---

### 02 — Pisanje profesionalnog emaila

```
Napiši profesionalni email kojim odgađam sastanak planiran za petak.
Razlog: neočekivani projekt s kratkim rokom.
Ton: pristojan, ne previše formalan.
Predloži alternativne termine: ponedjeljak ili utorak sljedeći tjedan.
```

**Rezultat:** Gotov email koji samo kopiraš. Ne pišeš od nule.

---

### 03 — Analiza tablice ili CSV podataka

```
Imam tablicu prodajnih rezultata za Q1. Evo podataka:
[Zalijepi tablicu]

Identificiraj:
1. Top 3 proizvoda po prihodu
2. Kategorije s padom u odnosu na Q4
3. Jednu neočekivanu anomaliju u podacima
```

---

### 04 — Prijevod s kontekstom

```
Prevedi sljedeći tekst na engleski.
Kontekst: poslovni email dobavljaču.
Ton: formalan, ali ne krut.
Zadrži sve specifične termine i nazive.

[Tekst za prijevod]
```

**Napomena:** Uvijek dodaj kontekst. "Prevedi ovo" daje lošije rezultate od prompta s kontekstom.

---

### 05 — Brainstorming rješenja

```
Imam problem: [opiši problem u 2-3 rečenice]

Generiraj 5 konkretnih rješenja.
Za svako: jedno rečenica opisa + jedna prednost + jedna mana.
Budi specifičan, bez generičkih savjeta.
```

---

### 06 — Formatiranje i struktura

```
Preformatirај ovaj popis zadataka u Markdown tablicu s kolonama:
Zadatak | Prioritet (Visok/Srednji/Nizak) | Rok | Odgovorna osoba

[Zalijepi popis]
```

Korisno kad radite u timovima koji koriste Notion, Confluence ili GitHub.

---

### 07 — Tjedni izvještaj u 10 minuta

```
Na temelju ovih bilješki s tjednih sastanaka, napiši kratki tjedni izvještaj za menadžment.
Format:
- Ključna postignuća (3-5 točaka)
- Otvoreni problemi (max 3)
- Sljedeći koraci (max 3)
- Metrike ako su navedene

Ton: koncizan, bez marketinškog jezika.

[Zalijepi bilješke]
```

---

## Actionable output

Uzmi jedan od ovih prompta i testiraj ga **danas** na stvarnom zadatku. Ne na testu — na pravom zadatku koji ionako moraš napraviti.

Spremi onaj koji ti da dobar rezultat. To je početak tvoje prompt biblioteke.

---

*Sljedeće: [Automatizacija Excel izvještaja pomoću AI →](/ai-alati/excel-ai-izvjestaji/)*
