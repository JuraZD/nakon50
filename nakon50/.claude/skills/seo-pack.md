# Skill: SEO Pack

## Zadatak
Doradi SEO elemente postojećeg drafta i generiraj SEO report.
Direktno modificiraš fajl — ne stvaraš novi.

## Input
- `target_path` — putanja do postojećeg index.md
- `keywords_path` — putanja do keywords.md

## Proces

### 1. Analiza trenutnog stanja
Pročitaj `target_path` i izvuci:
- Trenutni title, description, slug iz frontmattera
- H1, sve H2 i H3 naslove
- Duljinu u riječima
- Sve interne i eksterne linkove
- Postoji li FAQ sekcija?

### 2. Title tag optimizacija
**Kriteriji:**
- Primarni KW u prvoj trećini naslova
- Duljina: 45–60 znakova (ne kraće, ne dulje)
- Na kraju: " | Nakon50" (Hugo to dodaje automatski — ne dodavaj ručno)
- Glagol akcije ili broj gdje odgovara

**Primjeri:**
- ✅ "AI workflow za email: 5 koraka za uredske poslove"
- ✅ "Python za početnike 50+: automatiziraj CSV u 20 minuta"
- ❌ "Kako koristiti umjetnu inteligenciju za pisanje elektroničkih poruka"
- ❌ "AI email" (prekratko, nema konteksta)

### 3. Meta description
**Kriteriji:**
- 120–155 znakova (ne kraće — Google može odabrati vlastiti snippet)
- Sadrži primarni KW prirodno
- CTA glagol: "Nauči", "Preuzmi", "Vidi", "Počni"
- Ne počinje s "U ovom članku"
- Ne ponavlja doslovno H1 naslov

**Provjera duljine:**
Ako > 155: skrati, prioritet CTA + KW.
Ako < 120: proširi koristom ili kontekstom.

### 4. Slug optimizacija
**Kriteriji:**
- Samo primarni KW, bez stop-wordova (za, u, i, na, s, o...)
- Kebab-case, bez dijakritika
- Max 60 znakova
- Bez datuma (Hugo to rješava kroz putanju)

Konverter dijakritika:
```
č→c, ć→c, š→s, ž→z, đ→d
```

### 5. H struktura audit
- Postoji li točno jedan H1? (dolazi iz title frontmattera u Congo temi)
- Nema H2 koji preskače na H4?
- Postoji li min. 1 H2 s varijacijom primarnog KW?
- Naslovi su informativni (ne "Uvod", "Zaključak" bez konteksta)?

### 6. FAQ sekcija
Ako ne postoji: dodaj na kraju, prije Checklist sekcije.
Koristiti pitanja iz `keywords.md` → People Also Ask.

Format:
```markdown
## Česta pitanja

**Trebam li tehničko znanje za AI email workflow?**
Ne. Sve što trebaš je besplatni račun na ChatGPT-u ili Claudeu i
10 minuta za postavljanje. Nema kodiranja, nema instalacije.

**Koliko vremena treba za postavljanje?**
Oko 20–30 minuta za prvi setup. Nakon toga, svaki email pišeš
brže nego dosad.

**Je li AI workflow siguran za poslovne emailove?**
Da, uz jednu napomenu: ne stavljaj osjetljive podatke (šifre,
osobni ID, bankovni podaci) u AI prompt. Za standardne poslovne
emailove — potpuno sigurno.
```

### 7. Interni link plan
Na temelju sadržaja posta i dostupnih postova:
- Identificiraj 2–3 mjesta gdje prirodno ide interni link
- Predloži sidro tekst (ne "kliknite ovdje", ne URL)
- Predloži koji post linkati

### 8. External links provjera
- Svi vanjski linkovi imaju `target="_blank"` i `rel="noopener"`?
  U Markdownu: `[tekst](url){target="_blank" rel="noopener"}`
- Nema broken linkova?

## Output — dorađen fajl + seo.md

### Direktno u fajlu
Ažuriraj: `title`, `description`, `slug` u frontmatteru.
Dodaj: FAQ sekciju ako nedostaje.
Doradi: H2 naslove ako ne sadrže KW.

### workflows/article-orchestration/seo.md

```markdown
# SEO Pack Report
Datum: {datum}
Fajl: {target_path}

## Promjene

| Element | Prije | Poslije |
|---------|-------|---------|
| Title | "{stari}" ({X}z) | "{novi}" ({X}z) |
| Description | "{stara}" ({X}z) | "{nova}" ({X}z) |
| Slug | {stari} | {novi} |
| FAQ | Ne postoji | Dodana ({X} pitanja) |

## KW distribucija
Primarna KW "{kw}": pojavljuje se {X}× (preporučeno: 3–7×)
Sekundarne KW: {status po KW}

## Interni link prijedlozi
1. Sidro: "{tekst linka}"
   Link na: /{slug}/
   Gdje: {H2 sekcija, ~{X}. paragraf}

2. ...

## Procijenjeni SEO score: {XX}/100
Faktori:
+ {pozitivni faktori}
- {što je ostalo za poboljšanje}
```
