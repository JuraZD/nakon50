---
title: "D3 grafovi — demo svih tipova"
date: 2026-03-01
draft: false
categories: ["ai-alati"]
tags: ["vizualizacija", "d3", "podaci"]
summary: "Demo stranica sa svim podržanim tipovima D3.js grafikona. Koristite kao referencu pri pisanju novih članaka."
---

Ova stranica prikazuje sve dostupne tipove grafikona koje možete ugraditi u članke pomoću shortcode-a `d3chart`. Kopirajte primjere i prilagodite `datafile` prema potrebi.

---

## 1. Stupčasti grafikon (bar)

Vertikalni stupci. Idealan za usporedbu kategorija.

```
{{</* d3chart
  id="demo-bar"
  type="bar"
  datafile="/data/primjer-bar.json"
  title="Popularnost AI alata u uredima"
  subtitle="% korisnika koji koriste alat barem jednom tjedno"
  label="ISTRAŽIVANJE"
  source="Nakon50 procjena, 2026."
*/>}}
```

{{< d3chart
  id="demo-bar"
  type="bar"
  datafile="/data/primjer-bar.json"
  title="Popularnost AI alata u uredima"
  subtitle="% korisnika koji koriste alat barem jednom tjedno"
  label="ISTRAŽIVANJE"
  source="Nakon50 procjena, 2026."
>}}

---

## 2. Horizontalni stupci (hbar)

Bolje čitljiv kad su labele dugačke (npr. fraze umjesto jedne riječi).

```
{{</* d3chart
  id="demo-hbar"
  type="hbar"
  datafile="/data/primjer-hbar.json"
  title="Primjena AI-a u svakodnevnom radu"
  subtitle="% ispitanika koji koriste AI za određenu aktivnost"
  label="ANKETA"
  source="Nakon50 procjena, 2026."
*/>}}
```

{{< d3chart
  id="demo-hbar"
  type="hbar"
  datafile="/data/primjer-hbar.json"
  title="Primjena AI-a u svakodnevnom radu"
  subtitle="% ispitanika koji koriste AI za određenu aktivnost"
  label="ANKETA"
  source="Nakon50 procjena, 2026."
>}}

---

## 3. Linijski grafikon (line)

Prikaz trenda kroz vrijeme. Jedan niz podataka.

```
{{</* d3chart
  id="demo-line"
  type="line"
  datafile="/data/primjer-line.json"
  title="Rast broja korisnika Nakon50"
  subtitle="Tisuće pretplatnika, 2025."
  label="RAST"
  source="Interni podaci."
*/>}}
```

{{< d3chart
  id="demo-line"
  type="line"
  datafile="/data/primjer-line.json"
  title="Rast broja korisnika Nakon50"
  subtitle="Tisuće pretplatnika, 2025."
  label="RAST"
  source="Interni podaci."
>}}

---

## 4. Višelinijski grafikon (multiline)

Usporedba više nizova podataka kroz vrijeme.

```
{{</* d3chart
  id="demo-multiline"
  type="multiline"
  datafile="/data/primjer-multiline.json"
  title="Minute admin posla tjedno"
  subtitle="Usporedba s AI alatima i bez"
  label="UČINKOVITOST"
  source="Nakon50 simulacija."
  height="360"
*/>}}
```

{{< d3chart
  id="demo-multiline"
  type="multiline"
  datafile="/data/primjer-multiline.json"
  title="Minute admin posla tjedno"
  subtitle="Usporedba s AI alatima i bez"
  label="UČINKOVITOST"
  source="Nakon50 simulacija."
  height="360"
>}}

---

## 5. Tortni grafikon (pie)

Udio kategorija u cjelini. Maksimalno 6 kategorija za čitljivost.

```
{{</* d3chart
  id="demo-pie"
  type="pie"
  datafile="/data/primjer-pie.json"
  title="Na što trošimo digitalno radno vrijeme?"
  subtitle="Udio po kategoriji aktivnosti"
  label="ANALIZA"
  source="Nakon50 procjena."
*/>}}
```

{{< d3chart
  id="demo-pie"
  type="pie"
  datafile="/data/primjer-pie.json"
  title="Na što trošimo digitalno radno vrijeme?"
  subtitle="Udio po kategoriji aktivnosti"
  label="ANALIZA"
  source="Nakon50 procjena."
>}}

---

## 6. Donut grafikon (donut)

Kao tortni, ali sredina prikazuje ukupan broj ili postotak.

```
{{</* d3chart
  id="demo-donut"
  type="donut"
  datafile="/data/primjer-donut.json"
  title="Status učenja — AI modul"
  subtitle="% korisnika po fazi"
  label="NAPREDAK"
  source="Nakon50 platforma."
*/>}}
```

{{< d3chart
  id="demo-donut"
  type="donut"
  datafile="/data/primjer-donut.json"
  title="Status učenja — AI modul"
  subtitle="% korisnika po fazi"
  label="NAPREDAK"
  source="Nakon50 platforma."
>}}

---

## 7. Raspršeni grafikon (scatter)

Korelacija dviju varijabli. X os = ulaganje, Y os = rezultat.

```
{{</* d3chart
  id="demo-scatter"
  type="scatter"
  datafile="/data/primjer-scatter.json"
  title="Sati ulaganja vs. poslovni rezultat"
  subtitle="Digitalni kanali — tjedna mjerenja"
  label="KORELACIJA"
  source="Nakon50 procjena."
  height="380"
*/>}}
```

{{< d3chart
  id="demo-scatter"
  type="scatter"
  datafile="/data/primjer-scatter.json"
  title="Sati ulaganja vs. poslovni rezultat"
  subtitle="Digitalni kanali — tjedna mjerenja"
  label="KORELACIJA"
  source="Nakon50 procjena."
  height="380"
>}}

---

## Format JSON podataka

Svaki grafikon čita vlastiti JSON iz mape `/static/data/`. Struktura po tipu:

```json
// bar / hbar
{ "data": [{"label":"A","value":42}, ...] }

// line
{ "data": [{"x":"Sij","y":100}, ...] }

// multiline
{ "series": [{"name":"Serija A","data":[{"x":"Sij","y":100},...]},...] }

// pie / donut
{ "data": [{"label":"Kategorija","value":35}, ...] }

// scatter
{ "data": [{"x":10,"y":20,"label":"opis"}, ...] }
```
