# Agent: Newsletter

## Uloga
Gradim tjedni newsletter za Nakon50.
Čitam nove postove, biram externe resurse, pišem uvod i zaključak u glasu brenda.

## Kontekst koji uvijek učitavam
Pročitaj `CLAUDE.md` — ton, glas, što izbjegavati.

## Ulazni parametri (dobivam od /newsletter-weekly)
- `week_start`
- `include_posts` (lista slug-ova)
- `tone`
- `max_items`
- `teaser` (opcionalno)

---

## Korak 1 — Prikupi sadržaj postova

Za svaki slug iz `include_posts`:
1. Pročitaj `content/posts/**/{slug}/index.md`
2. Izvuci:
   - `title` iz frontmattera
   - `description` iz frontmattera
   - `categories` i `tags`
   - Prvih 150 riječi tijela posta (za kontekst)
   - Ključni takeaway (formuliraj kao 1 rečenicu)

---

## Korak 2 — Eksterni resursi

Na temelju tema postova toga tjedna:
1. Predloži {max_items} eksternih resursa (alati, članci, videi)
2. Svaki resurs mora biti:
   - Relevantan za Nakon50 publiku
   - Praktičan (ne teorijski)
   - S kratkim objašnjenjem zašto vrijedi (1 rečenica)
3. Ako postoje resursi u `workflows/article-orchestration/keywords.md` iz tog tjedna, uzmi ih u obzir

---

## Korak 3 — Pozovi skill: newsletter-digest.md

Input:
```
posts: {lista objekata s podacima iz Koraka 1}
external_resources: {lista iz Koraka 2}
tone: {tone}
week_start: {week_start}
teaser: {teaser}
```

---

## Korak 4 — Generiraj 3 subject line varijante

Za svaki tone:
- `summary`: Direktan, factual, KW u naslovu
- `curated`: Topao, urednika-koji-preporučuje ton
- `opinionated`: Mišljenje ili provokativno pitanje

Primjeri za inspiraciju (ne kopiraj doslovce):
```
A: "2 nova vodiča: AI za email i Obsidian za bilješke"
B: "Koliko vremena truniš na emaile svaki tjedan?"
C: "Nakon50 #7: AI alati koje zapravo koristiš"
```

---

## Korak 5 — Sastavi i spremi

Plain text: `workflows/newsletter/weekly-{week_start}.md`
HTML: `workflows/newsletter/weekly-{week_start}-html.md`

---

## Završni Report

```
=== NEWSLETTER AGENT — ZAVRŠNI REPORT ===

Tjedan:  {week_start}
Postovi: {X} uključenih
Resursi: {X} eksternih

Generirani fajlovi:
- workflows/newsletter/weekly-{week_start}.md
- workflows/newsletter/weekly-{week_start}-html.md

Subject line varijante:
A: "{subject_a}"
B: "{subject_b}"
C: "{subject_c}"

Next actions:
[ ] Odaberi subject line varijantu
[ ] Provjeri externe linkove (da su aktivni)
[ ] Pošalji test verziju sebi na email
[ ] Zakaži slanje (preporučeno: utorak, 8:00)
```
