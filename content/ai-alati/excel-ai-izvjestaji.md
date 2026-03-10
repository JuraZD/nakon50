---
title: "Excel + AI: Tjedni izvještaj za 15 minuta"
date: 2026-02-13
tags: ["Excel", "AI", "automatizacija", "izvještaj"]
categories: ["AI Alati u Praksi"]
summary: "Spojiti Excel i ChatGPT nije komplicirana magija — to je workflow koji se uči za jedan popodne. Evo točnog redoslijeda."
showTableOfContents: true
---

![Podaci i grafikoni](/img/tech-data.jpg)

Tjedni izvještaj. Svaki petak, ista priča — kopiraš tablicu, formatiraš, pišeš komentar, šalješ. 45 minuta posla koji se ponavlja.

S ovim workflowom: **15 minuta**.

---

## Što ćeš naučiti

Tri koraka:
1. Eksportiraš Excel podatke u format koji AI može pročitati
2. AI generira komentar i uvide
3. Ti samo provjeriš i šalješ

Nikakvo programiranje. Samo Excel, ChatGPT/Claude i tvoj uredovni email.

---

## Korak 1 — Pripremi podatke za AI

Excel → CSV format je najlakši put. Uđi u: `Datoteka → Spremi kao → CSV (odvojen zarezima)`.

Alternativno, selektiraj raspon u Excelu i kopiraj (`Ctrl+C`). ChatGPT razumije tablice zalijepljene kao tekst.

### Što treba biti u tablici?

Minimalno:
- Datumska kolona
- Numeričke vrijednosti koje pratite
- Eventualno kolona s kategorijama

Primjer koji koristimo u ovom vodiču:

```
Tjedan,Prodaja EUR,Broj narudžbi,Prosjek/narudžba
T01,12400,87,142.53
T02,13100,91,143.96
T03,11800,78,151.28
T04,14200,104,136.54
T05,15600,112,139.29
T06,14800,98,151.02
T07,16200,119,136.13
T08,17100,128,133.59
```

---

## Korak 2 — Prompt za analizu

Ovaj prompt radi konzistentno:

```
Analiziraj ove prodajne podatke i napiši kratki tjedni izvještaj za menadžment.

Podaci:
[zalijepi CSV tablicu]

Izvještaj treba sadržavati:
1. Ključni trend (1-2 rečenice)
2. Tjedan s najboljim i najlošijim rezultatom — i mogući razlog
3. Upozorenje ako postoji anomalija (naglo raste ili pada)
4. Preporuka za sljedeći tjedan (konkretna, ne generička)

Format: kratke rečenice, bez bulshit-a. Max 200 riječi.
```

### Što AI vraća?

```
Prodaja bilježi stabilan rast od 38% u analiziranom razdoblju
(T01–T08), s jednim izuzetkom: T03 je pokazao pad od 10% u
usporedbi s prethodnim tjednom.

Najslabiji tjedan T03 (11.800 EUR, 78 narudžbi) vjerojatno
odražava sezonski pad ili privremeni problem s opskrbom.
Prosječna vrijednost narudžbe T03 bila je najviša u periodu
(151,28 EUR) — manji broj kupaca, ali veće narudžbe.

Anomalija: prosječna vrijednost narudžbe konstantno pada od
T06 nadalje, dok volumen raste. Moguće: rast manjih narudžbi,
akcija ili segment s nižim cijenama preuzima udio.

Preporuka: analiziraj strukturu narudžbi T06–T08 po kategoriji
proizvoda — identificiraj koji segment snižava prosjek.
```

---

## Korak 3 — Vizualizacija unutar Excela

Dok AI piše komentar, ti u Excelu napraviš jedan grafikon.

Kombinirani grafikon (linija + stupci) za prodaju i broj narudžbi:

1. Selektaj kolone `Tjedan`, `Prodaja EUR`, `Broj narudžbi`
2. `Umetni → Preporučeni grafikoni → Kombinirani`
3. Postavi `Broj narudžbi` na sekundarnu os

Excel automatski generira — ne moraš podešavati svaki put ako spasiš predložak.

---

## Ušteda vremena kroz 8 tjedana

{{< d3chart
  id="chart-usteda"
  datafile="/data/ai-alati.json"
  type="multiline"
  title="Minuti po tjednom izvještaju — s AI i bez AI"
  subtitle="Trend pada vremena kako se workflow usavršava"
  label="ANALIZA UŠTEDE"
  source="Nakon50 interno praćenje"
  height="300"
>}}

Prva dva tjedna su sporija — učiš što funkcionira. Od trećeg tjedna ubrzanje je vidljivo.

---

## Predložak koji možeš preuzeti

Cijeli workflow u 3 koraka (Excel predložak + prompt set):

```
TJEDNI IZVJEŠTAJ WORKFLOW
──────────────────────────
1. Kopiraj tablicu iz Excela
2. Zalijepi u ChatGPT s promptom:
   "Analiziraj i napiši izvještaj za menadžment.
    Podaci: [tablica]. Format: trend + anomalija + preporuka."
3. Provjeri, kopiraj u email, pošalji.
──────────────────────────
Ukupno: 15 minuta.
```

Spremi ovo kao `.txt` datoteku — to je tvoj starter template.

---

**Actionable output:** Sljedeći petak, umjesto da pišeš izvještaj od nule, probaj ovaj workflow na stvarnim podacima. Ako ne radi u prvom pokušaju, prilagodi prompt — to je normalan dio procesa.

---

*Prethodni: [7 ChatGPT prompta za ured →](/ai-alati/chatgpt-prompti-za-ured/)*
