# Komanda: /build-d3-chart

Generira kompletan D3.js grafikon s Hugo shortcodeom, podacima i stilovima —
spreman za umetanje u bilo koji post.

## Ulazni parametri

| Parametar          | Obavezno | Opis |
|--------------------|----------|------|
| `chart_type`       | DA       | `bar` / `line` / `scatter` / `timeline` / `donut` / `comparison` |
| `title`            | DA       | Naslov grafikona (prikazan iznad) |
| `context`          | DA       | Post ili tema za koji je grafikon (utječe na ton labela) |
| `target_post_path` | DA       | Bundle folder posta (npr. `content/posts/2026/02/ai-email-workflow/`) |
| `data_inline`      | ne       | JSON podaci direktno u parametru |
| `data_csv_path`    | ne       | Putanja do CSV u /static/data/ |
| `color_scheme`     | ne       | `nakon50` / `minimal` / `dark` (default: nakon50) |
| `caption`          | ne       | Tekst ispod grafikona (izvor, napomena) |
| `interactive`      | ne       | `true` za tooltip na hover (default: true) |
| `responsive`       | ne       | `true` za mobile-friendly (default: true) |

## Primjer poziva

```
/build-d3-chart
chart_type="bar"
title="Koje AI alate koriste uredski radnici 50+ (2025.)"
context="ai-alati-pocetnici"
target_post_path="content/posts/2026/02/ai-alati-za-ured/"
data_inline='[
  {"label": "ChatGPT", "value": 68},
  {"label": "Copilot", "value": 45},
  {"label": "Gemini", "value": 29},
  {"label": "Claude", "value": 22},
  {"label": "Ostali", "value": 11}
]'
caption="Izvor: Nakon50 anketa, veljača 2026. (N=143)"
```

## Color scheme: `nakon50`

```css
--n50-primary:    #2C5F8A;   /* plava — bar fill, linija */
--n50-secondary:  #E8913A;   /* narančasta — accent, hover */
--n50-neutral:    #6B7280;   /* siva — osi, tick labelovi */
--n50-bg:         #F7F5F0;   /* topla bijela — pozadina */
--n50-text:       #1F2937;   /* tamna — naslovi, labeli */
--n50-grid:       #E5E7EB;   /* svjetla siva — grid linije */
```

## Što generira

```
{target_post_path}
├── charts/
│   └── {auto-slug-od-title}/
│       ├── chart.js      ← D3 logika
│       ├── data.json     ← podaci
│       └── style.css     ← Nakon50 stilovi
```

```
layouts/shortcodes/
└── d3chart.html          ← kreira ako ne postoji
```

U terminal ispiše shortcode koji kopiraš u post:
```
{{< d3chart
  id="ai-alati-2025"
  src="/posts/2026/02/ai-alati-za-ured/charts/ai-alati-2025/"
  title="Koje AI alate koriste uredski radnici 50+"
  caption="Izvor: Nakon50 anketa, veljača 2026."
>}}
```

## Napomene o chart_type

| Tip          | Kada koristiti |
|--------------|----------------|
| `bar`        | Usporedba kategorija (horizontalni za duge labele) |
| `line`       | Trend kroz vrijeme |
| `scatter`    | Korelacija dviju varijabli |
| `timeline`   | Kronološki slijed koraka ili događaja |
| `donut`      | Udio dijelova u cjelini (max 5 segmenata) |
| `comparison` | Dva stupca: "Prije" vs "Poslije" ili A vs B |

## Skill koji se poziva
`skills/d3-chart-builder.md`
