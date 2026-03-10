---
title: "Naslov — kako učiti novu vještinu"
date: 2026-03-01
draft: false
categories: ["ucenje"]
tags: ["obsidian", "organizacija", "navike", "edukacija"]
summary: "Kratki opis pristupa ili alata za učenje. Prikazuje se u kartici na listingu."
cover:
  image: "/img/notes.jpg"   # abstract.jpg | notes.jpg | social.jpg | tech-data.jpg | workspace.jpg
  alt: "Opis slike"
---

<!-- UVOD: Zašto je učenje u 50+ drugačije nego u 25. I zašto je to prednost. -->

Mozak u 50+ ne uči sporije — uči drugačije. Sada se uči na temelju iskustva, a to znači da nova znanja odmah nalaze kontekst i primjenu.

---

## Zašto ovaj alat / pristup

<!-- 2-3 paragrafa. Što rješava. Zašto je primjeren za 50+. -->

Tekst...

---

## Postavljanje od nule

<!-- Korak po korak za apsolutne početnike. -->

### Korak 1: Instalacija

Tekst ili screenshot opis...

### Korak 2: Osnovna konfiguracija

Tekst...

### Korak 3: Prva upotreba

Tekst...

---

## Sistem koji funkcionira

<!-- Konkretna rutina ili framework koji korisnik može odmah primijeniti. -->

```
TJEDNA RUTINA UČENJA:

Ponedjeljak:  30 min — nova lekcija / video
Srijeda:      20 min — bilješke + veza s prethodnim
Petak:        15 min — primjena u stvarnom zadatku
Nedjelja:     10 min — pregled tjednih bilješki
```

---

## Grafikon: tempo napretka

{{< d3chart
  id="chart-ucenje-id"
  type="line"
  datafile="/data/primjer-line.json"
  title="Kumulativne sate učenja kroz godinu"
  subtitle="Prosječni korisnik Nakon50 platforme"
  label="NAPREDAK"
  source="Nakon50 interni podaci."
>}}

---

## Python skripta: automatski export bilješki

<!-- Samo ako je relevantno za temu. -->

```python
# export_biljezaka.py
# Izvozi sve .md datoteke u jedan PDF za printanje

import os
import glob

biljezke_dir = "/home/user/Obsidian/Biljezke"
datoteke = glob.glob(os.path.join(biljezke_dir, "**/*.md"), recursive=True)

for putanja in sorted(datoteke):
    naziv = os.path.basename(putanja)
    with open(putanja, 'r', encoding='utf-8') as f:
        sadrzaj = f.read()
    print(f"=== {naziv} ===")
    print(sadrzaj[:200])  # Preview prvih 200 znakova
    print()
```

---

## Savjeti za zadržavanje naučenog

<!-- Kratka, praktična lista. Bez teorije. -->

1. **Predajte** — objasnite netko iz obitelji što ste naučili
2. **Primijenite odmah** — ne čekajte "pravi trenutak"
3. **Povežite** s onim što već znate
4. **Ponovite** za 48 sati i za tjedan dana

---

## Zaključak

Učenje nije sprint. Jedna nova vještina po kvartalu — to je 4 vještine godišnje. Za 3 godine: 12 novih kompetencija.

**Pročitajte i:** [Obsidian Second Brain](/ucenje/obsidian-second-brain/) · [AI alati za učenje](/ai-alati/)
