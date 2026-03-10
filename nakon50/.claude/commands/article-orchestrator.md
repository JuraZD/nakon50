# Komanda: /article-orchestrator

Pokreće end-to-end produkciju jednog članka za Nakon50.
Vodi te kroz sve faze uz pauziranje na ključnim točkama za ljudski review.

## Ulazni parametri

| Parametar       | Obavezno | Opis |
|-----------------|----------|------|
| `topic`         | DA       | Tema članka u jednoj rečenici |
| `pillar`        | DA       | Jedna od 5 rubrika (vidi CLAUDE.md) |
| `intent`        | DA       | Što čitatelj može **napraviti** nakon čitanja |
| `target_path`   | DA       | Npr. `content/posts/2026/02/ai-email-workflow/index.md` |
| `audience_note` | ne       | Specifična napomena o publici za ovaj post |
| `skip_build`    | ne       | `true` ako ne želiš pokrenuti hugo validate (default: false) |
| `series`        | ne       | Naziv serije ako je post dio niza |

## Primjer poziva

```
/article-orchestrator
topic="Kako koristiti AI za pisanje e-mailova na poslu bez gubljenja vremena"
pillar="AI alati u praksi"
intent="Čitatelj može postaviti vlastiti AI email workflow u 10 minuta"
target_path="content/posts/2026/02/ai-email-workflow/index.md"
```

## Tijek izvršavanja

```
[1] keyword-research     → workflows/article-orchestration/keywords.md
[2] article-outline      → workflows/article-orchestration/outline.md
    ↓ PAUZA — pregled outlinea
[3] article-draft        → {target_path}
[4] readability-check    → inline report, doradi ako grade > 12
[5] seo-pack             → dorađen {target_path} + seo.md
[6] frontmatter-linter   → automatski ispravlja greške
[7] hugo-validate        → workflows/article-orchestration/build-report.md
    ↓ STANI ako FAIL
[8] distribution-snippets → workflows/article-orchestration/distribution.md
```

## Output

Na kraju ispiši strukturirani summary:

```
=== ARTICLE ORCHESTRATOR — ZAVRŠNI REPORT ===

Post:        {target_path}
Naslov:      {title iz frontmattera}
Kategorija:  {pillar}
Čitanje:     ~X minuta

Workflow fajlovi:
- workflows/article-orchestration/keywords.md
- workflows/article-orchestration/outline.md
- workflows/article-orchestration/seo.md
- workflows/article-orchestration/build-report.md
- workflows/article-orchestration/distribution.md

Quality bar:
- Readability grade: X [OK / UPOZORENJE]
- Hugo build: PASS / FAIL
- Interni linkovi: X pronađenih
- SEO score (procjena): X/100

Next actions:
[ ] Provjeri predložene interne linkove ručno
[ ] Uploadaj cover.webp u bundle folder
[ ] Commit + push → GitHub Actions deploy
[ ] Podijeli LinkedIn snippet iz distribution.md
```

## Agent
Delegira izvršavanje na: `.claude/agents/article.md`
