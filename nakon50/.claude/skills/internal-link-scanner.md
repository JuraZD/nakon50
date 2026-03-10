# Skill: Internal Link Scanner

## Zadatak
Skeniraj sve Markdown postove, izgradi mapu internih linkova i identificiraj
prilike za poboljšanje međusobnog linkanja.

## Input
- `scope` — `all` / `{rubrika}` (default: all)
- `min_links` — upozori na postove s manje od X dolaznih linkova (default: 1)

## Proces

### 1. Skeniranje fajlova
Prolazi kroz sve `content/posts/**/*.md` fajlove.

Za svaki fajl izvuci:
```
{
  slug:       string,    // iz frontmattera ili putanje
  title:      string,    // iz frontmattera
  category:   string,    // iz categories[0]
  tags:       string[],
  h2_topics:  string[],  // naslovi svih H2 sekcija
  outbound:   string[],  // sve interne veze koje post šalje (linkovi na druge slugove)
  inbound:    string[],  // popunjava se u koraku 2
  word_count: number,
  date:       string
}
```

### 2. Izgradnja grafa
```
Za svaki post A:
  Za svaki outbound link u A:
    Pronađi post B s tim slug-om
    Dodaj A u B.inbound[]
```

### 3. Identifikacija siročadi
Siročad = post s `inbound.length < min_links`.

Prioritizacija:
1. Siročad s visokim word_count-om (investicija bez povrata)
2. Siročad u dobro zastupljenim rubrikama
3. Siročad s puno tagova koji se preklapaju s drugim postovima

### 4. Generiranje prijedloga za linkove

Za svaki par postova A i B koji nisu linkani:
Izračunaj score srodnosti:
```
score = 0
if A.category == B.category: score += 3
for tag in A.tags:
  if tag in B.tags: score += 2
for topic in A.h2_topics:
  if tematska_sličnost(topic, B.title): score += 1  // ključne riječi
```

Prijedlog se generira ako `score >= 4`.
Za svaki prijedlog generiraj i prikladni sidro tekst:
- Izvuci 2–4 ključne riječi iz naslova B
- Formuliraj kao frazu koja prirodno uklapa u tekst A
- Nije "kliknite ovdje" ili URL

### 5. ASCII mreža po rubrikama

Za svaku rubriku prikaži:
```
[slug-a] ──→ [slug-b]
[slug-b] ──→ [slug-c]
[slug-d]    ← (siročad — nema dolaznih linkova)
```

## Output integrira se u agents/site-analyst.md → site-report.md

Format prijedloga:
```
PRIJEDLOG {n}:
  IZ:    /{slug-posta-koji-šalje}/
         "{naslov posta koji šalje}"
  U:     /{slug-posta-koji-prima}/
         "{naslov posta koji prima}"
  SIDRO: "{prijedlog sidro teksta}"
  GDJE:  Sekcija "{H2 naslov}" u postu koji šalje
  SCORE: {X}/10
```

## Napomene o implementaciji

Ovo je analitički skill koji ne mijenja fajlove.
Sve izmjene (dodavanje linkova) rade se ručno ili kroz zasebnu komandu.

Regex za detekciju internih linkova u Markdownu:
```
\[([^\]]+)\]\((/posts/[^)]+)\)
```

Ignorirati:
- Linkovi na eksterne domene
- Linkovi na /static/ resurse
- Linkovi unutar code blokova
