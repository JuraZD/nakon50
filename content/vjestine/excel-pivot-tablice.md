---
title: "Excel Pivot tablice: od kaosa do izvještaja za 10 minuta"
date: 2026-02-06
tags: ["Excel", "pivot", "analiza", "tablice"]
categories: ["Vještine koje se odmah koriste"]
summary: "Pivot tablice su jedna od najmoćnijih Excel funkcija — i jedna od najlakše naučivih. Ako ih ne koristiš, gubite između 30 i 90 minuta tjedno na ručno sortiranje."
showTableOfContents: true
---

![Bilježnica s podacima](/img/notes.jpg)

Pivot tablica nije programiranje. Nije napredni Excel. To je alat koji Excel ima od devedesetih, a većina korisnika ga nikad ne dotakne.

Ovo je vodič koji ga mijenja — za 10 minuta rada.

---

## Što je pivot tablica?

Pivot tablica je automatski sažetak velikih skupova podataka. Umjesto da ručno sortiraš i zbrajаš, pivot to radi jednim klikom.

**Primjer:** Imaš tablicu od 500 redaka s prodajom po prodavaču, regiji i kategoriji. Pivot ti za 30 sekundi pokaže: koliko je svaki prodavač prodao, po regiji, u svakom kvartalu.

---

## Priprema podataka — kritični korak

Pivot funkcionira samo na "čistim" tablicama. Provjeri:

```
✓ Svaka kolona ima naslov (Ime, Datum, Iznos...)
✓ Nema praznih redaka unutar tablice
✓ Nema spojenih ćelija
✓ Datumi su u istom formatu (DD.MM.YYYY ili slično)
✓ Brojevi su zaista brojevi (ne tekst koji izgleda kao broj)
```

**Brza provjera:** Klikni na kolonu s brojevima — u donjem desnom kutu Excela vidiš `Zbroj`. Ako piše `0`, brojevi su zapravo tekst.

---

## Kreiranje prve pivot tablice

**Korak 1:** Klikni bilo gdje unutar tablice s podacima.

**Korak 2:** `Umetni → Zaokretna tablica (Pivot Table)`

**Korak 3:** Excel predlaže raspon — prihvati i klikni OK.

Otvara se novi radni list s praznim pivot panelom desno.

**Korak 4 — Rasporedi polja:**

```
REDCI → ovdje povuci kategoriju (npr. Prodavač)
KOLONE → vremenski period (npr. Kvartal)
VRIJEDNOSTI → što zbrajamo (npr. Prodaja)
FILTERI → opcionalno (npr. Regija)
```

**Korak 5:** Desni klik na vrijednosti → `Sažmi vrijednosti prema → Zbroj`.

Gotovo. Imaš pivot tablicu.

---

## Tri trika koja štede najviše vremena

### Trik 1 — Grupiranje datuma

Ako imaš kolonu s datumima, Excel može automatski grupirati po tjednima, mjesecima ili godinama:

Desni klik na datum u pivot tablici → `Grupiraj → odaberi Mjesec ili Kvartal`.

### Trik 2 — Udio u postotku

Desni klik na vrijednost → `Prikaži vrijednosti kao → % od ukupnog broja redaka`.

Umjesto apsolutnih iznosa dobiješ udio — korisno za prezentacije.

### Trik 3 — Slice (vizualni filtar)

`Analiza zaokretne tablice → Umetni rezač (Slicer)`.

Dobivаš gumb s kojim filtriraš pivot klikom — bez padajućih izbornika.

---

## Pivot + AI: sljedeći level

Kad naučiš pivot, kombinacija s AI postaje moćna:

```
Prompt za ChatGPT:
"Imam pivot tablicu s prodajom po kvartalima i regijama.
Evo podataka [zalijepi pivot rezultate].
Identificiraj top 2 regije i preporuči gdje povećati
resurse u sljedećem kvartalu."
```

AI analizira, ti odlučuješ.

---

## Actionable output

Otvori Excel koji imaš na računalu — bilo koji s podacima od više od 20 redaka. Kreiraj pivot tablicu prema gornjim koracima. Ako nemaš prikladne podatke, preuzmi besplatni [sample dataset](https://people.sc.fsu.edu/~jburkardt/data/csv/csv.html) i isprobaj na njemu.

---

*Pogledaj i: [Digitalne vještine 50+: Trendovi i alati →](/vjestine/digitalne-vjestine-trendovi/)*
