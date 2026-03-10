# Skill: Article Outline

## Zadatak
Kreiraj detaljan outline za Nakon50 članak koji agent može odmah pretvoriti u draft.
Outline je ugovor — draft se drži ga striktno.

## Input
- `keywords_path` — putanja do keywords.md
- `topic`
- `intent`
- `pillar`

## Proces

### 1. Pročitaj keywords.md
Izvuci primarni KW, sekundarne KW, LSI pojmove i FAQ pitanja.

### 2. Definiraj H1 naslov
- Primarni KW u prvoj trećini naslova
- 45–65 znakova
- Konkretan glagol ili broj ako odgovara
- Bez clickbaita, bez "ultimativnog vodiča"

Loše: "Sve što trebaš znati o AI emailovima"
Dobro: "AI workflow za email: 5 koraka za uredske poslove"

### 3. Strukturiraj sekcije

Svaka sekcija (H2) mora imati:
- Naslov (H2)
- Opis što će sadržavati (2–3 rečenice)
- Je li potreban H3 niz? Ako da, koji?
- Koji KW/LSI uključuje prirodno?

**Obavezne sekcije (u ovom redoslijedu):**

```
[UVOD — bez H2]
Problem ili situacija čitatelja
Što će naučiti / moći napraviti
Zašto je relevantno za 50+ kontekst

[H2: Zašto {tema} vrijedi naučiti]
Motivacija — konkretan benefit, ne generička pohvala
Kratka, max 200 riječi

[H2: Korak 1 — ...] × 3–7 koraka
Svaki korak ima jasan naslov i konkretan sadržaj
Ako je kompleksan → H3 unutra

[H2: Primjer iz prakse — OBAVEZNO]
Format: Situacija → Problem → Rješenje → Rezultat
Konkretan, izmišljeni ali realistični primjer iz HR uredskog konteksta

[H2: Najčešće greške — opcionalno, ali preporučeno]
3–5 grešaka s kratkim objašnjenjem i ispravkom

[H2: Checklist]
Shortcode checklist — sažetak koraka

[H2: Sljedeći korak — CTA]
Shortcode CTA — konkretan poziv na akciju
```

### 4. Provjeri balans
- Postoji li logičan tijek od problema do rješenja?
- Je li "Primjer iz prakse" dovoljan za identifikaciju (publika 50+, uredski kontekst)?
- Je li checklist stvarno actionen (ne teorijski)?

## Output: workflows/article-orchestration/outline.md

```markdown
# Outline: {topic}
Datum: {datum}
Primarna KW: {primarna_kw}

---

## H1: {naslov}
*({X} znakova)*

---

## [UVOD — bez H2]
**Problem:** {opis situacije čitatelja}
**Što će naučiti:** {konkretno, 1 rečenica}
**Zašto 50+ relevantno:** {specifičan kontekst}
*Duljina: ~80–120 riječi*

---

## H2: {naslov sekcije}
**Sadržaj:** {opis}
**KW koji uključuje:** {kw}
**Duljina:** ~{X} riječi

  ### H3: {podnaslov} — *ako je potreban*
  **Sadržaj:** {opis}

---

## H2: Primjer iz prakse ⭐ OBAVEZAN
**Profil junaka:** {tko je, koliko godina, koji posao}
**Situacija:** {kontekst}
**Problem:** {konkretan izazov}
**Rješenje:** {koraci koje je poduzeo}
**Rezultat:** {mjerljiv/opipljiv ishod}

---

## H2: Checklist
*Shortcode {{< checklist >}}*
Stavke: {lista svih koraka iz članka kao kratke bullet points}

---

## H2: Sljedeći korak
*Shortcode {{< cta >}}*
**Akcija:** {konkretna akcija}
**Link:** {newsletter / download / srodni post}
**Tekst gumba:** {tekst}

---

## Statistike outlinea
Ukupno H2: {X}
Ukupno H3: {X}
Procjenjena duljina drafta: {X}–{Y} riječi
```
