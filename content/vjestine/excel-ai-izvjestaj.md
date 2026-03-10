---
title: "Excel + A.I.: kako za 15 minuta napraviti izvještaj koji bi inače trajao sat"
date: 2026-03-10
tags: ["Excel", "AI", "izvještaji", "produktivnost", "ChatGPT", "Copilot"]
categories: ["Vještine koje se odmah koriste"]
summary: "Excel je i dalje najkorišteniji alat za analizu podataka. Kombiniran s A.I.-jem, najsporije faze — formule, struktura, komentar za upravu — skraćuju se na minute. Vodič korak po korak."
---

# Excel + A.I.: kako za 15 minuta napraviti izvještaj koji bi inače trajao sat

Excel je i dalje najkorišteniji alat za analizu podataka u većini organizacija. I dalje je moćan. I dalje može biti spor, zamoran i sklon greškama kad radiš ručno.

Kombinacija Excela i A.I. mijenja taj omjer u tvoju korist — ne tako što zamjenjuje Excel, nego tako što eliminira najmukotrpnije dijelove rada s njim.

---

## Scenarij koji se ponavlja svaki tjedan

Imaš tablicu s podacima: prodaja po regijama, troškovi po odjelima, prisutnost zaposlenika, evidencija predmeta, bilo što. Trebaš napraviti pregled s ključnim pokazateljima, grafikon i kratki komentar za upravu ili nadređene.

**Uobičajeni put:**
1. Čišćenje podataka ručno (duplikati, prazna polja, pogrešni formati)
2. Pisanje formula (VLOOKUP, SUMIF, COUNTIF, pivot)
3. Formatiranje tablice sažetka
4. Izrada grafikona
5. Pisanje komentara ili popratnog teksta

Ukupno: sat do sat i pol, ovisno o kompleksnosti i broju grešaka usput.

**Alternativni put s A.I.:**
1. Čišćenje podataka — A.I. piše formulu ili Python skriptu za tebe
2. Formule — ChatGPT objašnjava i generira formulu prema opisu
3. Struktura sažetka — A.I. predlaže koji pokazatelji idu gdje
4. Komentar za upravu — A.I. ga generira na temelju tvojih podataka

Ukupno: 15-20 minuta, plus tvoja provjera.

---

## Dio 1: Formule bez muke

Najčešći razlog gubitka vremena u Excelu nije unos podataka — nego pisanje i ispravljanje formula. VLOOKUP s pogrešnom referencom, SUMIF koji ne uzima u obzir prazna polja, pivot koji ne prepoznaje format datuma.

A.I. može generirati formulu prema opisu na hrvatskom.

### Primjer 1: SUMIF prema kriteriju

**Tvoj opis ChatGPT-u:**
```
Imam Excel tablicu. Stupac A su nazivi odjela (tekst), stupac B su iznosi troškova (broj). 
Trebam formulu koja zbroji sve troškove samo za odjel "Računovodstvo". 
Napiši mi formulu i objasni svaki dio.
```

**Što dobiješ:**
```
=SUMIF(A:A,"Računovodstvo",B:B)
```
S objašnjenjem: A:A je raspon u kojemu tražimo kriterij, "Računovodstvo" je uvjet, B:B je raspon koji zbrajamo.

### Primjer 2: VLOOKUP koji spaja dvije tablice

**Tvoj opis:**
```
Imam dvije tablice u Excelu. Tablica 1 ima ID zaposlenika (stupac A) i broj sati rada (stupac B). 
Tablica 2 ima ID zaposlenika (stupac D) i ime zaposlenika (stupac E). 
Trebam u Tablici 1, stupac C, prikazati ime zaposlenika na temelju ID-a.
```

**Što dobiješ:**
```
=VLOOKUP(A2,$D:$E,2,FALSE)
```
S objašnjenjem svakog parametra i napomenom kako kopirati formulu za sve redove.

### Primjer 3: COUNTIF za brzo prebrojavanje

**Tvoj opis:**
```
Stupac C ima statuse predmeta: "Otvoreno", "Zatvoreno", "U tijeku". 
Trebam formulu koja broji koliko predmeta ima status "Otvoreno".
```

**Što dobiješ:**
```
=COUNTIF(C:C,"Otvoreno")
```

**Važno:** Uvijek kopiraj formulu u Excel i provjeri rezultat na poznatom skupu podataka. A.I. griješi u referencama na stupce ako mu ne daš dovoljno konteksta — testiranje je obavezno.

---

## Dio 2: Pivot tablica bez frustracije

Pivot tablice su jedan od najmoćnijih alata u Excelu — i jedan od najnepristupačnijih za početnike. Greška u postavljanju vrti se u krug: krivo polje, krivi format, nečitljiv rezultat.

A.I. pomaže na dva načina:

**Način 1: Opis koraka**

```
Imam Excel tablicu s ovim stupcima: Datum, Odjel, Vrsta troška, Iznos. 
Objasni mi korak po korak kako napraviti pivot tablicu koja pokazuje 
ukupne troškove po odjelu za svaki mjesec.
```

Dobiješ točne korake za tvoju verziju Excela (navedi verziju u promptu: Microsoft 365, Excel 2019, Excel 2016).

**Način 2: Provjera zašto ne radi**

```
Napravio/la sam pivot tablicu u Excelu. Kad pokušam zbrojiti stupac "Iznos", 
prikazuje "Broj stavki" umjesto "Suma". Zašto se to događa i kako popraviti?
```

Najčešći odgovor: stupac sadrži tekst ili prazna polja koja Excel čita kao ne-numeričke vrijednosti. A.I. objašnjava i kako provjeriti i kako popraviti.

---

## Dio 3: Grafikon koji prenosi pravu poruku

Grafikon nije dekoracija. Grafikon je argument. I loš odabir tipa grafikona može prikazati iste podatke na način koji zbunjuje umjesto da pojašnjava.

**Prompt za odabir pravog tipa:**

```
Imam podatke o troškovima po odjelima za 12 mjeseci. 
Hoću prikazati: ukupni trend kroz godinu i usporedbu između odjela u isto vrijeme. 
Koji tip grafikona preporučuješ u Excelu i zašto?
```

**Tipičan odgovor:** Kombinirani grafikon (grouped column za usporedbu po odjelima + line chart za trend), ili zasebni grafovi za svaku svrhu s objašnjenjem kompromisa.

**Prompt za formatiranje:**

```
Moj Excel grafikon ima previše boja i legenda je nejasna. 
Kako ga pojednostaviti da bude čitljiviji za prezentaciju upravi?
```

---

## Dio 4: Komentar za upravu koji A.I. generira

Ovo je najčešće zanemareni dio — i onaj koji oduzima najviše energije. Imaš brojeve. Znaš što znače. Ali formulirati zaključak koji zvuči jasno i uvjerljivo za upravu zahtijeva još energije.

**Prompt:**

```
Imam sljedeće podatke iz tromjesečnog izvještaja:
- Ukupni troškovi: 124.500 EUR (porast 8% u odnosu na prethodni kvartal)
- Odjel s najvećim rastom troškova: IT (+22%)
- Odjel koji je smanjio troškove: Administracija (-5%)
- Broj predmeta u obradi: 412 (porast 12%)

Napiši kratki komentar za upravu (max 150 riječi) koji objašnjava ključne trendove 
i predlaže jedno pitanje za raspravu. Ton: profesionalan, konkretan.
```

**Što prilagođuješ:** Stvarni zaključak koji imaš o uzroku trenda — A.I. ne zna je li porast IT troškova planiran ili iznenađenje. Tu dodaješ svoju interpretaciju.

---

## Što ostaje na tebi (i zašto je to važno)

Sve ove uštede vremena vrijede samo ako tebi ostaju slobodni za ono što zahtijeva tvoj sud:

- **Razumijevanje što podaci stvarno znače** u kontekstu tvoje organizacije
- **Prepoznavanje anomalija** koje A.I. nije istaknuo (iznenađujući pad u jednoj liniji, duplikat koji skripta nije uhvatila)
- **Odluka što ide u završni izvještaj** — što izostaviš jednako je važno kao što uključiš
- **Odgovornost za zaključak** koji potpisuješ

To je ureditorska uloga — i to je viša razina kompetencije, ne niža.

---

## Provjera kompatibilnosti s tvojom verzijom Excela

Funkcije i načini rada razlikuju se između verzija:

| Funkcija | Microsoft 365 | Excel 2019 | Excel 2016 |
|---|---|---|---|
| XLOOKUP (zamjena za VLOOKUP) | ✅ | ❌ | ❌ |
| Dinamičke formule (FILTER, SORT) | ✅ | ❌ | ❌ |
| Copilot integracija | ✅ (plaćeni plan) | ❌ | ❌ |
| Pivot tablice | ✅ | ✅ | ✅ |
| Power Query | ✅ | ✅ | ✅ |

Ako koristiš Excel 2016 ili 2019 — sve iz ovog vodiča funkcionira, samo koristi VLOOKUP umjesto XLOOKUP.

---

## Sljedeći korak

Uzmi jedan izvještaj koji radiš ručno svaki tjedan ili svaki mjesec. Identificiraj koji dio oduzima najviše vremena. Formuliraj pitanje za ChatGPT prema gornjim primjerima.

Za napredak: [Python za ured: automatsko spajanje CSV izvještaja](#) — kad Excel više nije dovoljan za količinu podataka koju imaš.
