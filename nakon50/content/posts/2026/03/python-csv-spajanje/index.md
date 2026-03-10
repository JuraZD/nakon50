---
title: "Spoji više CSV tablica u Pythonu — bez prethodnog programerskog znanja"
date: 2026-03-02
lastmod: 2026-03-02
draft: false
description: "Nauči spojiti više CSV fajlova u jedan Python skriptom — kopiraj, zalijepi, pokreni. Prikladno za uredske radnike bez Python iskustva."
slug: "python-csv-spajanje-ured"
categories: ["Vještine koje se odmah koriste"]
tags: ["python", "csv", "automatizacija", "pandas", "uredski-alati"]
author: "Nakon50"
readingTime: true
series: ""
featuredImage: "cover.webp"
---

Svaki mjesec primaš izvješća od nekoliko odjela u CSV formatu i ručno ih spajate u Excel — red po red, list po list. Traje 20 minuta, a jednom se nešto pogrešno zalijepi i grešku otkriješ tek tjedan kasnije. U ovom vodiču naučit ćeš napisati Python skriptu koja taj posao napravi za 8 sekundi. Ne trebaš razumjeti programiranje — trebaš samo kopirati kod, promijeniti jednu putanju i pokrenuti.

## Zašto Python, a ne Excel makroi ili Power Query?

Excel makroi zahtijevaju VBA — poseban programski jezik koji nije intuitivan. Power Query je moćan, ali kompleksan za nestandardne strukture fajlova.

Python s **pandas** bibliotekom radi isti posao uz manje klikanja. Besplatan je, radi na svakom računalu i skripta koju ćeš dobiti u ovom članku ne traži nikakvo predznanje. Jednom je napišeš, zauvijek koristiš.

{{< tip >}}
Ovo nije uvod u Python kao programski jezik. Ovo je jedan konkretan alat za jedan konkretan problem — kao što koristiš VLOOKUP bez da razumiješ kako Excel interno radi.
{{< /tip >}}

## Što trebaš instalirati (jednom, zauvijek)

**Korak 1: Instaliraj Python**

Idi na [python.org/downloads](https://python.org/downloads) i preuzmi najnoviju verziju (dugme "Download Python 3.x.x"). Pokreni instalacijski program.

Važno: **označi kvačicu "Add Python to PATH"** na prvom ekranu. Bez toga terminal ne može pronaći Python.

**Korak 2: Instaliraj pandas**

Otvori Command Prompt (tipkovnički prečac: `Win + R`, upiši `cmd`, Enter). Upiši ovu liniju i pritisni Enter:

```
pip install pandas
```

Pričekaj dok se instalacija završi — može trajati minutu-dvije.

### Provjera instalacije

U istom terminalu upiši:

```
python --version
python -c "import pandas; print(pandas.__version__)"
```

Ako vidiš dvije verzije (npr. `Python 3.13.1` i `2.2.3`) — sve je ispravno postavljeno. Više se ne vraćaš na ovaj korak.

## Pripremi CSV fajlove — što mora biti isto

Prije pokretanja skripte provjeri jedan uvjet: **svi CSV fajlovi moraju imati identične naslove stupaca u prvom retku.**

Ako jedan fajl ima stupac `Naziv`, a drugi `naziv` ili `NAZIV` — pandas ih tretira kao različite stupce i spajanje neće biti ispravno.

Otvori svaki fajl u Excelu (ili Notepad-u) i provjeri prvi red. Poravnaj naslove ako se razlikuju.

{{< tip >}}
Čest problem u hrvatskim uredima: fajlovi izvezeni iz starijih sustava koriste windows-1250 encoding umjesto UTF-8. Ako vidiš iskrivljene znakove (š → š±, č → Ä), rješenje je u sekciji "Česte greške" ispod.
{{< /tip >}}

## Skripta — kopiraj, zalijepi, pokreni

Otvori Notepad, kopiraj cijeli blok ispod i spremi fajl kao `spoji_csv.py` u **istu mapu** gdje se nalaze tvoji CSV fajlovi.

```python
import pandas as pd
import glob
import os

# JEDINO ŠTO MIJENJAĆ: putanja do tvoje mape s CSV fajlovima
mapa = "C:/Users/tvoje_ime/Documents/csv_fajlovi"

# Pronađi sve CSV fajlove u mapi
csv_fajlovi = glob.glob(os.path.join(mapa, "*.csv"))

# Pročitaj svaki fajl i dodaj ga na listu
lista_tablica = []
for fajl in csv_fajlovi:
    df = pd.read_csv(fajl, encoding='utf-8-sig')
    lista_tablica.append(df)

# Spoji sve tablice u jednu
spojena_tablica = pd.concat(lista_tablica, ignore_index=True)

# Spremi rezultat u istu mapu
spojena_tablica.to_csv(os.path.join(mapa, "output.csv"), index=False, encoding='utf-8-sig')

print(f"Gotovo! Spojeno {len(csv_fajlovi)} fajlova, ukupno {len(spojena_tablica)} redaka.")
```

Što radi svaki dio:
- **`glob.glob`** — traži sve `.csv` fajlove u mapi, kao Windows pretraživanje s `*.csv`
- **`for` petlja** — prolazi kroz svaki fajl i čita ga kao tablicu
- **`pd.concat`** — slaže sve tablice jednu ispod druge
- **`to_csv`** — sprema rezultat kao novi CSV fajl pod imenom `output.csv`

Mijenjaj samo liniju s `mapa = "..."` — unesi stvarnu putanju do tvoje mape.

### Kako pokrenuti skriptu

Otvori Command Prompt i navigiraj do mape gdje si spremi/la `spoji_csv.py`:

```
cd C:/Users/tvoje_ime/Documents/csv_fajlovi
python spoji_csv.py
```

Ako sve prođe, vidjet ćeš poruku poput: `Gotovo! Spojeno 6 fajlova, ukupno 1847 redaka.`

Rezultat je `output.csv` u istoj mapi — otvori ga u Excelu i provjeri.

## Česte greške i kako ih riješiti

**1. "ModuleNotFoundError: No module named 'pandas'"**
Pandas nije instaliran ili Python ne vidi instalaciju. Vrati se na korak s `pip install pandas` i ponovi.

**2. "UnicodeDecodeError" (iskrivljeni znakovi ili greška pri čitanju)**
Problem s encodingom. U skripti promijeni liniju s `read_csv` u:
```python
df = pd.read_csv(fajl, encoding='windows-1250')
```

**3. Output je prazan ili ima samo naslove**
Provjeri jesu li naslovi stupaca identični u svim fajlovima. Jedno extra razmak ili razlika u velikim/malim slovima uzrokuje problem.

**4. "FileNotFoundError" ili skripta ne pronalazi CSV-ove**
Putanja u varijabli `mapa` nije ispravna. Provjeri je li putanja točna i koristi kose crte `/` umjesto obrnutih `\` (ili koristi dvostruke: `\\`).

## Prilagodbe — kad standardna skripta nije dovoljna

**Dodaj stupac koji pokazuje iz kojeg fajla dolazi svaki red:**

```python
for fajl in csv_fajlovi:
    df = pd.read_csv(fajl, encoding='utf-8-sig')
    df['Izvor'] = os.path.basename(fajl)  # dodaje naziv fajla kao stupac
    lista_tablica.append(df)
```

**Zadrži samo određene stupce:**

```python
stupci = ['Datum', 'Naziv', 'Iznos']  # navedi stupce koje hoćeš
df = pd.read_csv(fajl, encoding='utf-8-sig', usecols=stupci)
```

**Automatiziraj pokretanje svaki ponedjeljak** — Windows Task Scheduler može pokrenuti skriptu automatski. Pretraži "Task Scheduler" u Start izborniku, kreiraj novi zadatak i kao akciju navedi: `python C:/putanja/do/spoji_csv.py`.

## Primjer iz prakse: Vesna iz logistike

**Situacija:** Vesna (54) radi kao administratorica u logističkoj tvrtki. Svaki ponedjeljak ujutro prima 6 CSV izvoza iz TMS sustava — po jedan od svakog regionalnog ureda. Direktor treba objedinjeni pregled do 10 sati.

**Problem:** Ručno kopiranje u Excel trajalo je 25 minuta. Jednom je zalijepila pogrešan list — greška je otkrivena u petak, na sastanku s klijentom.

**Rješenje:**
1. Za vikend je instalirala Python (YouTube vodič, 15 minuta)
2. Kopirala skriptu iz ovog članka, promijenila putanju do svoje mape
3. Testirala na tri stara CSV-a — `output.csv` bio spreman za 8 sekundi
4. Sada svaki ponedjeljak: spremi CSV-ove u mapu → dvostruki klik na skriptu → gotovo

**Rezultat:** Objedinjavanje s 25 minuta svela na 2 minute — pokretanje i kratka provjera. Greška zalijepljenog lista više nije moguća jer skripta čita podatke direktno, bez kopiranja.

---

<!-- INTERNI LINK TODO: Dodaj link na srodni post o Python alatima za ured kad bude objavljen -->

## Checklist: spajanje CSV-ova korak po korak

{{< checklist >}}
- [ ] Instaliran Python s python.org (kvačica "Add to PATH" označena)
- [ ] Instaliran pandas (`pip install pandas` u terminalu)
- [ ] Provjera instalacije — obje verzije se prikazuju
- [ ] Svi CSV-ovi u istoj mapi, identični naslovi stupaca
- [ ] Skripta kopirana u Notepad i spremljena kao `spoji_csv.py`
- [ ] Putanja do mape ispravljena u varijabli `mapa`
- [ ] Testno pokretanje — poruka "Gotovo!" se prikazuje
- [ ] `output.csv` otvoren u Excelu — podaci ispravni
{{< /checklist >}}

## Sljedeći korak

{{< cta >}}
Svaki tjedan jedan praktičan vodič za uredske alate — direktno u inbox, bez spama.
Prijavi se i dobij i mini-vodič za automatizaciju Excel izvještaja kao bonus.

[Prijava na newsletter →](https://nakon50.hr/newsletter/)
{{< /cta >}}
