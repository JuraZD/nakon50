# Skill: Distribution Snippets

## Zadatak
Generiraj gotove snippete za sve distribucijske kanale Nakon50.
Copy-paste ready — nikakva dorada ne smije biti potrebna.

## Input
- `target_path` — putanja do objavljenog posta
- `seo_path` — putanja do seo.md (za KW i meta desc)

## Proces
1. Pročitaj post: naslov, uvod, H2 naslovi, checklist stavke, CTA
2. Pročitaj seo.md: primarna KW, meta description
3. Generiraj snippete za sve kanale

---

## Kanal 1: LinkedIn Post

### Pravila
- Duljina: 150–300 riječi (optimal za reach)
- Hook: prva rečenica mora zaustaviti scrollanje — pitanje, kontrast ili neuobičajena tvrdnja
- Struktura: Hook → Kontekst (1-2 retka) → Bullet lista ključnih koraka → CTA
- Bullet lista: max 5 stavki, svaka počinje emojiem ili →
- Hashtagi: na kraju, 3–5, uvijek #Nakon50
- Bez "U ovom postu" — kreni direktno
- Pozivi: "Što ti iskušavaš s AI emailovima?" (potiče engagement)

### Format
```
{Hook — 1 rečenica koja zaustavlja}

{Kontekst — 1-2 rečenice}

{prazna linija — LinkedIn je voli}

{Emoji/→} {Korak/insight 1}
{Emoji/→} {Korak/insight 2}
{Emoji/→} {Korak/insight 3}
{Emoji/→} {Korak/insight 4}
{Emoji/→} {Korak/insight 5}

{prazna linija}

{CTA rečenica — link u komentarima ili direktan}

{prazna linija}

#{tag1} #{tag2} #{tag3} #Nakon50
```

### Primjer
```
Svaki tjedan pišeš isti email 15 puta. A mogao bi ga napisati za 30 sekundi.

Nije tajna — samo navika. Evo kako sam postavio AI email workflow koji koristi i moja kolegica Marija iz računovodstva:

→ Sistemski prompt s kontekstom tvog posla (jednom, zauvijek)
→ Biblioteka od 5–8 situacijskih promptova
→ Draft u 30 sekundi + 2 minute dorade
→ Više vremena za posao koji zapravo treba tvoj mozak
→ Bez plaćenih alata — ChatGPT free je dovoljan

Cijeli vodič, korak po korak, na linku u prvom komentaru.

Pitanje za tebe: na koji tip emailova gubiš najviše vremena?

#produktivnost #AIalati #uredskiposao #digitalizacija #Nakon50
```

---

## Kanal 2: Newsletter Blurb

### Verzija s linkom (za HTML newsletter)
```
**{Naslov posta}**
{2–3 rečenice: koji problem rješava + konkretni rezultat koji čitatelj može očekivati}
[Čitaj vodič →]({puni URL})
```

### Verzija bez linka (za plain text)
```
{Naslov posta}: {1 rečenica sažetka, max 80 znakova}
```

---

## Kanal 3: Open Graph / Social Meta

Za slučaj da Tailwind/Hugo ne generira automatski — fallback tekst:
```
{meta description iz seo.md}
```
Provjeri da je ≤ 155 znakova.

---

## Kanal 4: Kratki video script (30–60 sekundi)

Za Instagram Reels / TikTok / LinkedIn video.
Format: hook → problem → rješenje (3 koraka) → CTA

```
HOOK (0–3s):
"{Provokativno pitanje ili tvrdnja — govori se, ne čita}
 Primjer: 'Koliko vremena tjedno gubiš na pisanje emailova?'"

PROBLEM (3–8s):
"{Opis situacije koja rezonira}
 Primjer: 'Ako pišeš iste emailove iznova — postoji bolji način.'"

RJEŠENJE (8–50s):
"Korak 1: {akcija — max 10 riječi}
 Korak 2: {akcija — max 10 riječi}
 Korak 3: {akcija — max 10 riječi}
 Rezultat: {konkretan benefit}."

CTA (50–60s):
"Cijeli vodič je na Nakon50.hr — link u bio."
```

---

## Output: workflows/article-orchestration/distribution.md

Spremi sve gornje snippete u jedan fajl.
Na vrhu dodaj:

```markdown
# Distribution Pack: {naslov posta}
Datum: {datum}
URL: https://nakon50.hr/{slug}/

---
Koristi snippete direktno — copy-paste ready.
Provjeri URL prije dijeljenja (GitHub Actions mora završiti deploy).
```
