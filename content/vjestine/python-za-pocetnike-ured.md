---
title: "Python za početnike: Prva skripta u 20 minuta"
date: 2026-01-30
tags: ["Python", "automatizacija", "CSV", "početak"]
categories: ["Vještine koje se odmah koriste"]
summary: "Python ne mora biti programerska disciplina. Jedna skripta koja čita CSV, filtrira podatke i sprema rezultat — to je dovoljno za početak. Evo točno toga."
showTableOfContents: true
---

![Apstraktni kod](/img/abstract.jpg)

Netko ti kaže „nauči Python" i odmah misliš: tečajevi, algoritmi, objektno orijentirano programiranje. Zaboravi to.

Evo što trebaš: jednu skriptu koja radi nešto korisno na tvojim stvarnim podacima. Danas. Za 20 minuta.

---

## Što ćemo napraviti

Skripta koja:
1. Čita CSV datoteku (izvoz iz Excela)
2. Filtrira redake prema kriteriju
3. Sprema rezultat u novu CSV datoteku

Konkretno: imaš listu kupaca, filtriraš samo one koji su kupili više od X eura.

---

## Instalacija (jednom, 5 minuta)

Idi na [python.org](https://python.org) → Download → Instaliraj.

**Važno:** Na Windows-u, označi ✓ **"Add Python to PATH"** prije instalacije.

Provjera u terminalu:
```
python --version
```
Treba pisati `Python 3.x.x`. Ako piše, sve je u redu.

---

## Skripta korak po korak

### Korak 1 — Pripremi CSV

U Excelu: `Datoteka → Spremi kao → CSV`.

Primjer datoteke `kupci.csv`:
```csv
Ime,Email,Ukupno EUR,Datum
Ana Horvat,ana@email.com,1250,2026-01-15
Marko Kovač,marko@email.com,340,2026-01-18
Ivana Perić,ivana@email.com,2100,2026-01-20
Stjepan Blažić,stjepan@email.com,890,2026-01-22
Maja Tomić,maja@email.com,3400,2026-01-25
```

### Korak 2 — Napiši skriptu

Otvori Notepad ili bilo koji tekstualni editor. Snimi datoteku kao `filter_kupci.py`:

```python
import csv

# Konfiguriraj ovdje
ULAZNA_DATOTEKA = "kupci.csv"
IZLAZNA_DATOTEKA = "kupci_vip.csv"
MINIMALNI_IZNOS = 1000  # EUR

# Učitaj i filtriraj
vip_kupci = []

with open(ULAZNA_DATOTEKA, encoding="utf-8") as f:
    reader = csv.DictReader(f)
    for red in reader:
        iznos = float(red["Ukupno EUR"])
        if iznos >= MINIMALNI_IZNOS:
            vip_kupci.append(red)

# Spremi rezultat
with open(IZLAZNA_DATOTEKA, "w", encoding="utf-8", newline="") as f:
    writer = csv.DictWriter(f, fieldnames=vip_kupci[0].keys())
    writer.writeheader()
    writer.writerows(vip_kupci)

print(f"Pronađeno {len(vip_kupci)} VIP kupaca.")
print(f"Rezultat spremen u: {IZLAZNA_DATOTEKA}")
```

### Korak 3 — Pokreni

Otvori terminal u folderu gdje su datoteke:
```
python filter_kupci.py
```

Rezultat:
```
Pronađeno 3 VIP kupaca.
Rezultat spremen u: kupci_vip.csv
```

---

## Prilagodbe koje odmah možeš napraviti

**Promijeni kriterij filtriranja:**
```python
# Filtriraj po datumu (samo siječanj 2026)
if "2026-01" in red["Datum"]:
    vip_kupci.append(red)
```

**Dodaj zbrajanje:**
```python
ukupno = sum(float(r["Ukupno EUR"]) for r in vip_kupci)
print(f"Ukupna vrijednost VIP kupaca: {ukupno:.2f} EUR")
```

**Sortiraj po iznosu:**
```python
vip_kupci.sort(key=lambda x: float(x["Ukupno EUR"]), reverse=True)
```

---

## Gdje dalje?

Ova skripta je temelj. Sljedeći koraci po redu važnosti:

1. Nauči `pandas` biblioteku — Excel operacije u Pythonu
2. Automatizacija emailova s `smtplib`
3. Obrada Word dokumenata s `python-docx`

Svaki od ovih je jedan vodič na ovom portalu.

---

**Actionable output:** Instaliraj Python i pokreni ovu skriptu na nekim tvojim CSV podacima. Mjeri koliko minuta traje — slijedeći tjedan ćeš ga pokrenuti za 2 minute.

---

*Pogledaj i: [Excel Pivot tablice →](/vjestine/excel-pivot-tablice/) · [ChatGPT prompti za ured →](/ai-alati/chatgpt-prompti-za-ured/)*
