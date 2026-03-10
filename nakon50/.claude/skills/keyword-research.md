# Skill: Keyword Research

## Zadatak
Identificiraj ključne riječi za jedan Nakon50 članak.
Fokus: hrvatska publika, pretrage na hrvatskom i engleskom, uredski kontekst.

## Input
- `topic` — tema članka
- `pillar` — rubrika
- `intent` — što čitatelj može napraviti
- `audience_note` — opcionalna napomena

## Proces

### 1. Primarna KW analiza
Iz `topic` i `intent` izvuci **jednu primarnu ključnu riječ**:
- Specifična (ne generička) — "AI email workflow" > "AI"
- Prirodno se uklapa u H1 naslov
- Pretraživa u HR tržištu (HR ili EN verzija)
- Duljina: 2–4 riječi (long-tail preferirati)

### 2. Sekundarne KW (3–5)
Varijacije primarne KW:
- Sinonimne fraze
- Fraze s namjerom ("kako", "vodič", "primjer", "za početnike")
- Fraze s kontekstom (50+, uredski posao, bez iskustva)

### 3. LSI pojmovi (5–8)
Semantički srodni pojmovi koji se prirodno pojavljuju u kvalitetnom tekstu na ovu temu.
Primjer za temu "AI email workflow":
`prompti, produktivnost, automatizacija, predlošci emailova, ChatGPT, radno vrijeme, uredska komunikacija`

### 4. Procjena volumena i konkurencije
Za svaki KW daj aproksimativnu procjenu:
- **Volumen**: visok / srednji / nizak (HR tržište)
- **Konkurencija**: visoka / srednja / niska
- **Prikladnost za Nakon50**: ✅ / ⚠️ / ❌

### 5. "People also ask" — simulacija
5 pitanja koja čitatelji vjerojatno postavljaju vezano uz ovu temu.
Koristit će se za FAQ sekciju u postu.

## Output: workflows/article-orchestration/keywords.md

```markdown
# Keyword Research: {topic}
Datum: {datum}
Pillar: {pillar}

## Primarna KW
**{primarna_kw}**
- Volumen: {visok/srednji/nizak}
- Konkurencija: {visoka/srednja/niska}
- Preporučeni oblik u H1: "{prijedlog H1 naslova}"

## Sekundarne KW
| KW | Volumen | Konkurencija |
|----|---------|--------------|
| {kw_1} | {vol} | {konk} |
| {kw_2} | {vol} | {konk} |
| {kw_3} | {vol} | {konk} |

## LSI pojmovi
{pojam_1}, {pojam_2}, {pojam_3}, {pojam_4}, {pojam_5}, {pojam_6}, {pojam_7}

## People Also Ask (FAQ prijedlozi)
1. {pitanje}?
2. {pitanje}?
3. {pitanje}?
4. {pitanje}?
5. {pitanje}?

## Preporučena primarna KW za meta opis
"{primarna_kw}" + "{intent kao kratka fraza}"
```
