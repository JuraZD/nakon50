# Komanda: /draft-only

Brza verzija za pisanje — samo outline i draft, bez SEO, builda i distribucije.
Korisno kad imaš jasnu ideju i hoćeš brzo doći do teksta.

## Ulazni parametri

| Parametar       | Obavezno | Opis |
|-----------------|----------|------|
| `topic`         | DA       | Tema članka |
| `pillar`        | DA       | Jedna od 5 rubrika |
| `intent`        | DA       | Što čitatelj može napraviti nakon čitanja |
| `target_path`   | DA       | Putanja do index.md |
| `style`         | ne       | `how-to` / `case-study` / `listicle` (default: how-to) |
| `length`        | ne       | `short` (400–600r) / `standard` (800–1200r) / `long` (1200–1800r) (default: standard) |

## Primjer poziva

```
/draft-only
topic="Obsidian za početnike: kako početi za 30 minuta"
pillar="Sustavi i navike za učenje"
intent="Čitatelj postavlja osnovnu Obsidian strukturu za bilješke s posla"
target_path="content/posts/2026/02/obsidian-pocetak/index.md"
style="how-to"
length="standard"
```

## Tijek izvršavanja

```
[1] article-outline  → workflows/article-orchestration/outline.md
    ↓ PAUZA — pregled outlinea (možeš korigirati prije drafta)
[2] article-draft    → {target_path}
```

## Output

```
=== DRAFT-ONLY — ZAVRŠNI REPORT ===

Post:     {target_path}
Stil:     {style}
Duljina:  ~X riječi (~Y minuta čitanja)

Sljedeći korak:
Pokreni /seo-pack target_path="{target_path}" za doradu SEO elemenata.
Ili /article-orchestrator za potpuni workflow.
```
