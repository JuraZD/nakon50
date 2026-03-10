# Skill: Newsletter Digest

## Zadatak
Sastavi kompletan newsletter u plain text i HTML formatu.
Piše u glasu Nakon50 — osoban, direkt, bez marketinške napuhanosti.

## Input (dobivam od agents/newsletter.md)
- `posts` — lista objekata s podacima o postovima
- `external_resources` — lista eksternih resursa
- `tone` — summary / curated / opinionated
- `week_start` — datum
- `teaser` — najava sljedećeg tjedna (opcionalno)

## Glas pisanja po tonovima

### `summary` — tjedni pregled
Faktualni, bez osobnih komentara. Čitatelj odmah vidi što je novo i može kliknuti.
Uvod: 2 rečenice max. Fokus na sadržaj.

### `curated` — urednička selekcija (default)
Topao, kao da urednik preporučuje prijatelju.
Uvod: 3–4 rečenice s osobnom opservacijom o temi tjedna.
Svaki resurs ima kratki komentar zašto ga preporučuje.

### `opinionated` — stav + sadržaj
Urednik iznosi mišljenje o nečemu vezanom uz temu tjedna, pa linkova sadržaj.
Uvod: 4–6 rečenica s jasnim stavom (ali bez politike i kontroverznih tema).
Ton: siguran, ali ne aroganta.

## Pravila pisanja

**Uvijek:**
- Kratke rečenice (< 18 riječi)
- Konkretan benefit u naslovu svakog posta
- Nema "klik ovdje" — link ide na URL ili prirodni sidro tekst
- P.S. na kraju — jedina sekcija gdje se može biti malo više opušten/duhovit

**Nikad:**
- "Imamo sjajne vijesti za vas!"
- "Ne propustite..."
- "Ekskluzivno samo za naše pretplatnike"
- 3+ uzastopna uskličnika
- Health/fitness tematika

## Strukturni predložak

### Plain text verzija

```
Predmet: {subject line — odabrani}

---

Bok,

{Uvodni paragraf — ton po odabiru}

──────────────────────────────────────
📌 OVAJ TJEDAN NA NAKON50
──────────────────────────────────────

{Za svaki post:}
{broj}. {Naslov posta}
   {1–2 rečenice: koji problem rješava, što ćeš moći napraviti}
   → {puni URL}

──────────────────────────────────────
🔗 ŠTO SAM JOŠ PRONAŠAO
──────────────────────────────────────

{Za svaki externi resurs:}
- {Naziv} — {1 rečenica zašto vrijedi}
  → {URL}

──────────────────────────────────────

{Zaključni paragraf — 2–3 rečenice}

Do sljedećeg tjedna,
[Ime urednika]
Nakon50.hr

P.S. {Kratka opservacija, pitanje ili najava (teaser)}

───
Odjavnica: {URL}   |   Arhiva: {URL}
```

### HTML verzija

Koristi inline CSS kompatibilan s Gmail, Outlook 2016+, Apple Mail.
Max širina kontejnera: 600px.

```html
<!DOCTYPE html>
<html lang="hr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{subject line}</title>
</head>
<body style="margin:0;padding:0;background:#f7f5f0;font-family:Georgia,serif;">
  <div style="max-width:600px;margin:0 auto;background:#ffffff;padding:32px 24px;">

    <!-- HEADER -->
    <div style="border-bottom:3px solid #2C5F8A;padding-bottom:16px;margin-bottom:24px;">
      <span style="font-size:22px;font-weight:bold;color:#2C5F8A;">Nakon50</span>
      <span style="font-size:14px;color:#6B7280;margin-left:8px;">Novi dan. Nove vještine.</span>
    </div>

    <!-- UVOD -->
    <p style="font-size:16px;line-height:1.7;color:#1F2937;">{uvodni paragraf}</p>

    <!-- SEKCIJA: POSTOVI -->
    <div style="background:#f0f4f8;border-left:4px solid #2C5F8A;padding:16px;margin:24px 0;">
      <h2 style="font-size:14px;text-transform:uppercase;letter-spacing:1px;color:#2C5F8A;margin:0 0 16px;">
        📌 Ovaj tjedan na Nakon50
      </h2>
      {Za svaki post:}
      <div style="margin-bottom:16px;">
        <strong style="color:#1F2937;font-size:16px;">{naslov}</strong>
        <p style="margin:4px 0 8px;color:#4B5563;font-size:15px;">{opis}</p>
        <a href="{URL}" style="display:inline-block;background:#E8913A;color:#ffffff;
           padding:8px 16px;text-decoration:none;border-radius:4px;font-size:14px;">
          Čitaj vodič →
        </a>
      </div>
    </div>

    <!-- SEKCIJA: RESURSI -->
    <h2 style="font-size:14px;text-transform:uppercase;letter-spacing:1px;color:#2C5F8A;">
      🔗 Što sam još pronašao
    </h2>
    <ul style="padding-left:16px;color:#4B5563;font-size:15px;line-height:1.8;">
      {Za svaki resurs:}
      <li><a href="{URL}" style="color:#2C5F8A;">{naziv}</a> — {opis}</li>
    </ul>

    <!-- ZAKLJUČAK -->
    <p style="font-size:16px;line-height:1.7;color:#1F2937;margin-top:24px;">{zaključak}</p>

    <p style="font-size:15px;color:#1F2937;">Do sljedećeg tjedna,<br>
    <strong>[Ime]</strong><br>
    <a href="https://nakon50.hr" style="color:#2C5F8A;">Nakon50.hr</a></p>

    <!-- PS -->
    <p style="font-size:14px;color:#6B7280;border-top:1px solid #E5E7EB;padding-top:16px;">
      P.S. {teaser ili opservacija}
    </p>

    <!-- FOOTER -->
    <div style="border-top:1px solid #E5E7EB;margin-top:24px;padding-top:16px;
         font-size:12px;color:#9CA3AF;text-align:center;">
      <a href="{odjavnica_url}" style="color:#9CA3AF;">Odjava</a> &nbsp;|&nbsp;
      <a href="https://nakon50.hr/newsletter/arhiva/" style="color:#9CA3AF;">Arhiva newslettera</a>
    </div>

  </div>
</body>
</html>
```

## Output
Dva fajla — plain text i HTML — prema putanjama definiranim u agents/newsletter.md.
