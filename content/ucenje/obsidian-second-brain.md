---
title: "Obsidian: Second Brain koji zaista koristiš"
date: 2026-02-24
tags: ["Obsidian", "PKM", "second brain", "produktivnost"]
categories: ["Sustavi i Navike"]
summary: "Obsidian može biti previše kompliciran ili savršeno jednostavan — ovisno o tome kako ga postaviš. Evo minimalna verzija koja funkcionira od prvog dana."
showTableOfContents: true
---

![Bilješke i organizacija](/img/notes.jpg)

Previše Obsidian vodiča počinje s \"mapom misli\", \"backlinkovima\" i \"Zettelkasten metodom\".

Ako te ovo nije privuklo — ne čudi me. Mene nije na početku.

Ono što me privuklo jest jedna jednostavna stvar: **mogućnost da nešto što naučim ne izgubim**.

---

## Što je Obsidian i zašto nije Notion

**Obsidian** je aplikacija za bilješke u plain text formatu (Markdown). Datoteke žive na tvojem računalu — nije cloud, nema pretplate za osnovnu funkciju.

| | Obsidian | Notion |
|---|---|---|
| Format | Plain text (.md) | Proprietary |
| Lokacija | Tvoje računalo | Cloud |
| Brzina | Trenutna | Ovisi o internetu |
| Kompleksnost | Umjerena | Visoka |
| Offline | Da, uvijek | Ograničeno |

Za ljude koji žele **kontrolu nad podacima** i **offline dostupnost** — Obsidian pobjeđuje.

---

## Instalacija i minimalna konfiguracija

1. Preuzmi na [obsidian.md](https://obsidian.md) — besplatno
2. Kreiraj novi Vault (= folder gdje žive bilješke)
3. Isključi sve napredne opcije koje vidiš
4. Instaliraj samo ove pluginove (ugrađeni, ne trzih strana):
   - **Daily notes** — automatski otvara novu bilješku za danas
   - **Templates** — predlošci za ponavljajuće bilješke
   - **Backlinks** — veza između bilješki (aktiviraj tek kad shvatiš zašto)

---

## Minimalni sustav koji funkcionira

Tri foldera. Ništa više za početak:

```
/Inbox          ← Sve što dobiješ/naučiš odmah ide ovdje
/Aktivno        ← Projekti na kojima trenutno radiš
/Reference      ← Znanje koje čuvaš za budućnost
```

Jednom tjedno: prođeš kroz Inbox i prebacuješ bilješke na pravo mjesto.

---

## Daily Note: srce sustava

Daily Note je automatska bilješka za svaki dan. Predložak:

```markdown
# {{date:DD.MM.YYYY}}

## Prioriteti danas
- [ ]
- [ ]
- [ ]

## Naučio/la sam
-

## Ideje za zapis
-

## Otvorena pitanja
-
```

Svakog jutra: otvori, popuni prioritete. Svake večeri: 5 minuta za \"Naučio/la sam\".

Ovo je navika koja gradi second brain — ne kompleksna arhitektura.

---

## Veza između bilješki: kad i zašto

Obsidian je poznat po backlinkovima — vezama između bilješki. Ali ne počinjaš s njima.

Počinjaš kad primijetiš: „Ovo što čitam povezano je s onim što sam zabilježio/la prošli tjedan."

Tada napišeš `[[naziv bilješke]]` i Obsidian automatski kreira vezu.

Primjer:
```markdown
U vodiču o LinkedIn-u naučio/la sam važnost [[Headline formule]].
To se veže s onim što smo radili u [[Excel AI izvještaj]] vodiču —
jasna komunikacija vrijednosti.
```

---

## Obsidian + AI: kombinacija koja funkcionira

```python
# Python skripta za eksport Obsidian bilješki u CSV
# za analizu s AI-em

import os
import csv

VAULT = "/putanja/do/vault"  # promijeni ovo
OUTPUT = "biljeske.csv"

with open(OUTPUT, "w", encoding="utf-8", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["Datoteka", "Naslov", "Sadržaj"])

    for root, _, files in os.walk(VAULT):
        for file in files:
            if file.endswith(".md"):
                path = os.path.join(root, file)
                with open(path, encoding="utf-8") as md:
                    content = md.read()
                    naslov = file.replace(".md", "")
                    writer.writerow([path, naslov, content[:500]])

print(f"Eksportirano {sum(1 for _ in open(OUTPUT))-1} bilješki.")
```

Eksportiraš bilješke → zalijepite u Claude ili ChatGPT → „Što su moji glavni interesi iz ovih bilješki?" ili „Koje teme se ponavljaju?"

---

## Koliko vremena trebaš uložiti

```
Dan 1:    Instalacija + Daily Note template (30 min)
Tjedan 1: Pisanje Daily Notes svaki dan (5 min/dan)
Tjedan 2: Počni dodavati bilješke iz Inboxa
Tjedan 4: Počni koristiti linkove između bilješki
Tjedan 8: Evaluiraj — što koristiš, što ne koristiš
```

**Ključno:** Obsidian koji koristiš 10 minuta dnevno bolji je od savršeno dizajniranog sustava koji ne otvaraš.

---

**Actionable output:** Preuzmi Obsidian i postavi Daily Note template koji ti je dan u ovom vodiču. Koristi ga 7 dana. Ništa više — samo daily note. Nakon 7 dana odluči hoće li sustav ostati jednostavan ili ćeš dodavati slojeve.

---

*Pogledaj i: [Gdje krenuti s AI-em →](/ucenje/gdje-krenuti/) · [Digitalne vještine 50+ →](/vjestine/digitalne-vjestine-trendovi/)*
