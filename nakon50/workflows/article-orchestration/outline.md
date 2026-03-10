# Outline: Python za ured: automatiziraj spajanje CSV tablica
Datum: 2026-03-02
Primarna KW: spajanje CSV fajlova Python

---

## H1: Spoji više CSV tablica u Pythonu — bez prethodnog programerskog znanja
*(63 znakova)*

---

## [UVOD — bez H2]
**Problem:** Svaki mjesec dobijaš izvješća od pet odjela u CSV formatu i ručno ih kopiraš jedan po jedan u Excel — a to traje 20 minuta, uvijek se nešto pogrešno zalijepi.
**Što će naučiti:** Kako napisati kratku Python skriptu koja automatski spoji sve CSV fajlove iz jedne mape u jednu tablicu — spreman za pokretanje bez razumijevanja koda.
**Zašto 50+ relevantno:** Uredski radnici svakodnevno rade s izvozima iz ERP-a, baza podataka i alata koji ne "razgovaraju" međusobno — Python tu radi prljavi posao umjesto tebe.
*Duljina: ~100 riječi*

---

## H2: Zašto Python, a ne Excel makroi ili Power Query?
**Sadržaj:** Kratka usporedba: Excel makroi zahtijevaju VBA znanje, Power Query je moćan ali kompleksan za nestandardne structure. Python s pandas bibliotekom radi jednako uz manje klikanja — i besplatan je. Naglasak nije na tome da Python "pobijedi" Excel, nego da je za ovaj konkretni zadatak najizravniji put.
**KW koji uključuje:** Python za početnike, automatizacija tablice, pandas CSV
**Duljina:** ~150 riječi

---

## H2: Što trebaš instalirati (jednom, zauvijek)
**Sadržaj:** Instalacija Pythona i pandas biblioteke. Korak po korak — download s python.org, pokretanje instalera, potvrda u terminalu (`python --version`), instalacija pandas (`pip install pandas`). Naglasak: ovo se radi samo jednom.
**KW koji uključuje:** instalacija Python Windows, pip install pandas
**Duljina:** ~180 riječi

  ### H3: Provjera instalacije
  **Sadržaj:** Kratka provjera u terminalu — dvije linije koje potvrđuju da sve radi. Screenshot-friendly uputa.

---

## H2: Pripremi CSV fajlove — što mora biti isto
**Sadržaj:** Pretuvjet koji mnogi preskoče: svi CSV fajlovi moraju imati iste nazive stupaca (header red). Objašnjenje zašto — pandas spaja po stupcima. Savjet: provjeri u Excelu, poravnaj naslove ako se razlikuju (npr. "Naziv" vs "naziv" vs "NAZIV"). Kratko o encodingu (UTF-8 vs windows-1250 — čest problem u HR uredima).
**KW koji uključuje:** CSV format, header redak, encoding problem
**Duljina:** ~180 riječi

---

## H2: Skripta — kopiraj, zalijepi, pokreni
**Sadržaj:** Kompletan kod u copy-paste bloku. Skripta koja:
1. Čita sve .csv fajlove iz zadane mape
2. Spaja ih u jedan DataFrame
3. Sprema kao output.csv

Objašnjenje svake linije u plain Croatian — ne tehnički, nego "ova linija kaže Pythonu neka prođe kroz sve fajlove u mapi".
**KW koji uključuje:** pandas concat, glob CSV, Python skript spajanje
**Duljina:** ~250 riječi

  ### H3: Kako pokrenuti skriptu
  **Sadržaj:** Terminal/Command Prompt, navigacija do mape, `python spoji_csv.py` — i što se dogodi ako prođe, i što ako ne.

---

## H2: Česte greške i kako ih riješiti
**Sadržaj:** 4 greške koje se najčešće dogode:
1. "ModuleNotFoundError: No module named 'pandas'" — pandas nije instaliran
2. "UnicodeDecodeError" — problem s encodingom, dodaj `encoding='utf-8-sig'`
3. Output je prazan — provjeri jesu li naslovi stupaca identični
4. Skripta ne vidi fajlove — provjeri jesu li CSV-ovi u istoj mapi kao skripta
**KW koji uključuje:** Python error rješavanje, pandas greška
**Duljina:** ~200 riječi

---

## H2: Prilagodbe — kad standardna skripta nije dovoljna *(opcionalno, kratko)*
**Sadržaj:** Tri brze prilagodbe za naprednije situacije: dodaj stupac "Izvor" koji pokazuje iz kojeg fajla dolazi red, filtriraj samo određene stupce, automatiziraj pokretanje svaki ponedjeljak (Windows Task Scheduler). Svaka prilagodba = +3–5 linija koda, objašnjeno.
**KW koji uključuje:** pandas filter stupci, automatsko pokretanje Python skripte
**Duljina:** ~200 riječi

---

## H2: Primjer iz prakse ⭐ OBAVEZAN
**Profil junaka:** Vesna (54), administratorica u logističkoj tvrtki, Zagreb
**Situacija:** Svaki ponedjeljak prima 6 CSV izvoza iz TMS sustava (po jedan po regionalnom uredu). Treba objedinjeni pregled za tjedni izvještaj direktoru.
**Problem:** Ručno kopiranje u Excel traje 25 minuta. Jednom je zalijepila pogrešan list — greška je otkrivena tek u petak.
**Rješenje:**
1. Instalirala Python za vikend (YouTube vodič, 15 minuta)
2. Kopirala skriptu iz ovog članka, promijenila putanju mape
3. Testirala na 3 stara CSV-a — output.csv bio ispravan za 8 sekundi
4. Svaki ponedjeljak: spremi CSV-ove u mapu → dvostruki klik na skriptu → gotovo
**Rezultat:** Objedinjavanje s 25 minuta svela na 2 minute (pokretanje + provjera). Greška zalijepljenog lista — nemoguća.
*Duljina: ~180 riječi*

---

## H2: Checklist
*Shortcode {{< checklist >}}*
Stavke:
- Instaliran Python (python.org)
- Instaliran pandas (`pip install pandas`)
- Svi CSV-ovi u istoj mapi, identični naslovi stupaca
- Skripta kopirana i putanja do mape ispravljena
- Testno pokretanje na manjem skupu fajlova
- output.csv provjeren u Excelu — ispravni podaci
- (Opcionalno) Dodan stupac "Izvor" za praćenje podrijetla redaka

---

## H2: Sljedeći korak
*Shortcode {{< cta >}}*
**Akcija:** Prijava na newsletter
**Link:** https://nakon50.hr/newsletter/
**Tekst gumba:** Prijava na newsletter →

---

## Statistike outlinea
Ukupno H2: 8
Ukupno H3: 2
Procjenjena duljina drafta: 900–1200 riječi
