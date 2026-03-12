---
title: "Python za ured: automatsko spajanje CSV izvještaja bez znanja programiranja"
date: 2026-03-10
tags: ["Python", "CSV", "automatizacija", "Excel", "podaci"]
categories: ["Vještine koje se odmah koriste"]
summary: "Svaki mjesec isti ritual: izvoz CSV-a iz tri sustava, ručno spajanje u Excelu, sat vremena izgubljen. Python to rješava za 8 sekundi. Vodič s gotovom skriptom i uputama za početnike."
---

# Python za ured: automatsko spajanje CSV izvještaja bez znanja programiranja

Svaki mjesec isti ritual: izvoz iz jednog sustava daje ti jedan CSV, drugi sustav drugi CSV, treći treći. Otvoriš Excel, kopiraš, paziš na stupce, provjeriš duplikate, potrošiš sat vremena. Sljedeći mjesec — isto.

Python može to napraviti za tebe za manje od 10 sekundi.

I ne, ne trebaš znati programirati da bi to koristio/la.

---

## Što trebaš (i što ne trebaš)

**Što trebaš:**
- Python instaliran na računalu (besplatno, instalacija traje 5 minuta)
- Skriptu koju ćeš preuzeti uz ovaj vodič (ne trebaš je pisati)
- Razumijevanje što skripta radi — ne *kako*, nego *što*

**Što ne trebaš:**
- Programersko iskustvo
- Razumijevanje svakog reda koda
- Poseban softver osim Pythona

Ovo je važna distinkcija za početnike: **ne trebaš razumjeti svaki red koda**. Trebaš razumjeti ulaz (tvoji CSV-ovi), izlaz (spojeni CSV) i što prilagoditi (nazive stupaca, naziv datoteke, putanju do mape).

---

## Instalacija Pythona: 5 minuta, jednom zauvijek

1. Idi na [python.org/downloads](https://www.python.org/downloads/)
2. Klikni na veliku zelenu tipku "Download Python" (preuzmi najnoviju verziju)
3. Pokreni instalaciju — **važno:** na prvom ekranu označi kvačicu "Add Python to PATH"
4. Klikni "Install Now" i pričekaj 2-3 minute
5. Provjeri instalaciju: otvori Command Prompt (Windows) ili Terminal (Mac), upiši `python --version`, pritisni Enter. Ako vidiš broj verzije — Python je instaliran.

---

## Skripta za spajanje CSV datoteka

Evo kompletne skripte. Svaki red ima komentar koji objašnjava što radi.

```python
import pandas as pd   # biblioteka za rad s tabličnim podacima
import os             # biblioteka za rad s mapama i datotekama
from datetime import date  # za dodavanje datuma u naziv izlazne datoteke

# --- POSTAVI OVE VRIJEDNOSTI ---
MAPA_S_CSV = "C:/Korisnici/TvojeIme/Dokumenti/csv-izvjestaji"  # mapa gdje su tvoji CSV-ovi
NAZIV_IZLAZA = f"spojeni_izvjestaj_{date.today()}.csv"          # naziv izlazne datoteke (automatski s datumom)
SEPARATOR = ";"   # najčešće ";" u hrvatskim CSV-ovima, ponekad ","

# --- KOD KOJI NE TREBA MIJENJATI ---

# Pronađi sve CSV datoteke u mapi
sve_datoteke = [f for f in os.listdir(MAPA_S_CSV) if f.endswith('.csv')]
print(f"Pronađeno datoteka: {len(sve_datoteke)}")

# Učitaj svaku datoteku u listu
lista_tablica = []
for datoteka in sve_datoteke:
    putanja = os.path.join(MAPA_S_CSV, datoteka)
    tablica = pd.read_csv(putanja, sep=SEPARATOR, encoding='utf-8-sig')
    lista_tablica.append(tablica)
    print(f"Učitano: {datoteka} ({len(tablica)} redova)")

# Spoji sve tablice u jednu
spojena = pd.concat(lista_tablica, ignore_index=True)

# Ukloni potpune duplikate (redovi koji su identični u svim stupcima)
prije = len(spojena)
spojena = spojena.drop_duplicates()
poslije = len(spojena)
print(f"Uklonjeno duplikata: {prije - poslije}")

# Spremi rezultat
izlaz = os.path.join(MAPA_S_CSV, NAZIV_IZLAZA)
spojena.to_csv(izlaz, sep=SEPARATOR, index=False, encoding='utf-8-sig')
print(f"Gotovo! Datoteka spremljena: {izlaz}")
print(f"Ukupno redova u izlaznoj datoteci: {len(spojena)}")
```

---

## Kako pokrenuti skriptu: korak po korak

### Korak 1: Pripremi datoteke

Stavi sve CSV-ove koje hoćeš spojiti u jednu mapu. Npr: `C:\Dokumenti\csv-izvjestaji\`

**Važno:** Svi CSV-ovi moraju imati iste stupce (isti nazivi, isti redoslijed). Ako se stupci razlikuju, skripta će ih svejedno spojiti, ali rezultat može biti neuređen — u tom slučaju javi se u komentarima i pokazat ćemo proširenu verziju.

### Korak 2: Spremi skriptu

Kopiraj kod iznad u Notepad (ili bilo koji editor teksta). Spremi datoteku kao `spoji_csv.py` — pazi da ekstenzija bude `.py`, a ne `.txt`.

### Korak 3: Prilagodi putanju

U liniji `MAPA_S_CSV` zamijeni primjer putanjom do tvoje mape. Primjer za Windows:
```
MAPA_S_CSV = "C:/Users/TvojeIme/Documents/csv-izvjestaji"
```

### Korak 4: Instaliraj pandas biblioteku

Otvori Command Prompt i upiši:
```
pip install pandas
```
Pritisni Enter i pričekaj preuzimanje (jednom zauvijek).

### Korak 5: Pokreni skriptu

U Command Promptu navedi putanju do skripte:
```
python C:/Users/TvojeIme/Desktop/spoji_csv.py
```

Ili, lakša opcija: otvori mapu s Python skriptom, u adresnoj traci File Explorera upiši `cmd` i pritisni Enter — Command Prompt se otvori direktno u toj mapi. Tada samo upiši:
```
python spoji_csv.py
```

---

## Što vidite kad skripta radi

```
Pronađeno datoteka: 3
Učitano: sijecanj.csv (412 redova)
Učitano: veljaca.csv (398 redova)
Učitano: ozujak.csv (445 redova)
Uklonjeno duplikata: 7
Gotovo! Datoteka spremljena: C:/Dokumenti/csv-izvjestaji/spojeni_izvjestaj_2026-03-10.csv
Ukupno redova u izlaznoj datoteci: 1248
```

Izlazna datoteka automatski ima datum u nazivu, pa ne možeš slučajno prepisati prošli izvještaj.

---

## Česte greške i rješenja

**Greška: `ModuleNotFoundError: No module named 'pandas'`**
Rješenje: nisi instalirao/la pandas. Pokreni `pip install pandas` u Command Promptu.

**Greška: `FileNotFoundError`**
Rješenje: putanja u `MAPA_S_CSV` nije ispravna. Provjeri da nema tipfelera i da mapa stvarno postoji na toj lokaciji. Koristi kose crte `/` ili duple `\\`.

**Greška: Čudni znakovi u izlaznoj datoteci (npr. umjesto č, ž, š)**
Rješenje: promijeni `encoding='utf-8-sig'` u `encoding='cp1250'` — to je standardno Windows kodiranje za HR jezik.

**Greška: Stupci u izlazu su razdvojeni, ali podaci izgledaju pomaknuto**
Rješenje: tvoji CSV-ovi vjerojatno koriste drugačiji separator. Promijeni `SEPARATOR = ";"` u `SEPARATOR = ","` ili obrnuto.

---

## Koliko vremena ušteđuješ

{{< d3chart id="python-csv-usteda" type="hbar" datafile="/data/python-csv-usteda.json" title="Utrošeno vrijeme godišnje: ručno vs. Python" label="UŠTEDA VREMENA" subtitle="Ukupno minuta za 12 izvršavanja zadatka (jednom månadsvis)" source="Izračun: 12 × 45 min ručno / 12 × 8 sek Python" height="180" >}}

Ako ovaj zadatak radiš jednom tjedno i traje ti 45 minuta ručno, skripta to rješava za 8-10 sekundi.

Za godinu dana: **36+ sati vraćenih sebi**.

To nije metafora. To je sat i trideset tjedno koji možeš utrošiti na nešto što zahtijeva tvoje rasuđivanje — ne ručno kopiranje.

---

## Sljedeći korak

Ako ova skripta radi za tvoj slučaj — sjajno. Ako imaš CSV-ove s drugačijim stupcima, ako trebaš filtrirati podatke ili ako hoćeš rezultat direktno u Excel formatu (`.xlsx`) — to su nadogradnje koje pokrivamo u sljedećem vodiču:

Python za ured: automatsko generiranje izvještaja iz CSV-a s grafovima

---

*Uz ovaj članak dostupna je gotova skripta za preuzimanje: [spoji_csv.py](#download) — s komentarima na hrvatskom i uputama za prilagodbu.*
