---
title: "ChatGPT za službene dopise: kako zvučati profesionalno bez birokratskog žargona"
date: 2026-03-10
tags: ["AI", "ChatGPT", "pisanje", "dopisi", "uredski posao", "prompti"]
categories: ["AI alati u praksi"]
summary: "Službeni dopisi ne moraju biti pisani jezikom iz 1987. ChatGPT može pomoći — ali samo uz pravi prompt. Vodič s 5 tipova dopisa, konkretnim promptovima i anti-promptovima."
---

# ChatGPT za službene dopise: kako zvučati profesionalno bez birokratskog žargona

Svaki tko je ikad pisao službeni dopis u hrvatskoj javnoj upravi, proračunskoj instituciji ili većoj korporaciji zna ovaj osjećaj: trebaš reći jednu jednostavnu stvar, ali tekst mora zvučati "službeno". Na kraju imaš četiri rečenice, tri pasiva i nulo jasnoće.

A.I. može pomoći — ali samo ako znaš kako ga usmjeriti.

Ako samo napišeš "napiši mi službeni dopis", dobit ćeš generički engleski stil prijeveden na hrvatski. Neće biti loš. Ali neće biti ni tvoj, ni prikladan za lokalni kontekst, ni usklađen s internim standardima tvoje organizacije.

Ključ je u promptu.

---

## Što dobar prompt za dopis mora sadržavati

Dobra uputa A.I.-ju za pisanje dopisa sadrži četiri elementa:

1. **Kome pišeš** — institucija, odjel, konkretna uloga osobe (ne nužno ime)
2. **Što tražiš ili javljaš** — jedna rečenica, bez okolišanja
3. **Koji je ton prikladan** — formalan, poluformalan, konkretan, ali kolegijalan
4. **Koji je željeni format** — zahtjev, obavijest, odgovor, molba, prigovor

Primjer lošeg prompta:
> "Napiši dopis o produljenju roka."

Primjer dobrog prompta:
> "Napiši kratki službeni dopis kojim se obraćam voditelju projekta u javnoj ustanovi i tražim produljenje roka za dostavu izvještaja za 7 dana zbog tehničkih poteškoća s informacijskim sustavom. Ton: formalan, ali konkretan. Bez uvoda koji traje dva odlomka. Na hrvatskom jeziku."

Razlika u rezultatu je značajna. U prvom slučaju dobiješ predložak. U drugom dobiješ radnu verziju.

---

{{< d3chart id="dopisi-tipovi" type="donut" datafile="/data/dopisi-tipovi.json" title="Koji tip dopisa se najčešće piše u organizacijama" label="ANALIZA KOMUNIKACIJE" subtitle="Udio prema frekvenciji u uredskom okruženju (%)" source="Procjena Nakon50" height="320" >}}

## 5 tipova dopisa s konkretnim promptovima

### Tip 1: Zahtjev za produljenje roka

Jedan od najčešćih dopisa u svakoj organizaciji. Mora biti konkretan, bez opravdavanja, s jasnim novim rokom.

**Prompt:**
```
Napiši službeni dopis kojim tražim produljenje roka za dostavu [naziv dokumenta/izvještaja] 
za [broj] dana. Razlog: [navedi razlog — tehnički problem, bolest, nedostupnost podataka]. 
Primatelj: [voditelj, nadređeni, naručitelj — bez imena]. 
Ton: formalan i direktan. Bez dugog uvoda. Na hrvatskom.
```

**Što prilagodiš:** Naziv dokumenta, broj dana, konkretan razlog, interni broj predmeta ako postoji.

**Anti-prompt (što ne pisati):**
> "Napiši dopis u kojem objašnjavam zašto kasnim i tražim da razumiju situaciju."

Ovakav prompt daje tekst koji se previše opravdava. U formalnoj komunikaciji nije potrebno — dovoljno je navesti razlog i tražiti novo rješenje.

---

### Tip 2: Obavijest o promjeni

Koristiš kad trebaš obavijestiti suradnike, klijente ili nadređene o promjeni koja utječe na njih — novi rok, nova procedura, novi kontakt.

**Prompt:**
```
Napiši kratku internu obavijest kojom informiram [odjel/tim/suradnike] da se od [datum] 
mijenja [što se mijenja — procedura, kontakt osoba, rok, format dokumenta]. 
Navedi što točno znači za primatelja i što trebaju poduzeti. 
Ton: informativno, jasno, bez nepotrebnih pojedinosti.
```

**Što prilagodiš:** Datum, sadržaj promjene, akcija koja se od primatelja očekuje.

**Anti-prompt:**
> "Napiši obavijest koja objašnjava razlog promjene i opravdava odluku."

Interni dokumenti ne trebaju opravdavati svaku odluku. Dovoljno je jasno reći što, kada i što je potrebno napraviti.

---

### Tip 3: Odgovor na prigovor ili upit

Najosjetljiviji tip dopisa — mora biti korektan, ali ne i obrambeni. Mora dati odgovor, ali ne nuditi ustupke koje nisi ovlašten/a davati.

**Prompt:**
```
Napiši odgovor na prigovor stranke/klijenta koji se odnosi na [sažetak prigovora u jednoj rečenici]. 
U odgovoru: potvrdi primitak prigovora, objasni što smo provjerili ili poduzeli, 
navedi zaključak ili sljedeći korak. 
Ton: formalan, empatičan, ali ne obranjen. Bez obećanja koja ne možemo ispuniti.
```

**Što prilagodiš:** Sažetak prigovora, ono što je stvarno poduzeto, konkretan zaključak.

**Anti-prompt:**
> "Napiši odgovor kojim se ispričavamo i nudimo rješenje."

Isprika bez konteksta i ponuda bez ovlaštenja mogu stvoriti pravne i komunikacijske komplikacije. Bolje je biti konkretan nego velikodušan bez pokrića.

---

### Tip 4: Molba za informaciju ili dokumentaciju

Koristiš kad trebaš dobiti nešto od druge institucije, odjela ili osobe — bez pritiska, ali s jasnim očekivanjima.

**Prompt:**
```
Napiši formalnu molbu kojom od [naziv institucije/odjela] tražim dostavu [što točno tražiš]. 
Navedi svrhu zahtjeva u jednoj rečenici i predloži rok do kojeg bi nam podaci bili potrebni. 
Ton: profesionalan i konkretan, bez previše uvoda.
```

**Što prilagodiš:** Naziv institucije, što točno tražiš, rok, pravna ili proceduralna osnova ako postoji.

**Anti-prompt:**
> "Napiši molbu u kojoj objašnjavam sve razloge zašto trebamo ove podatke."

Dugačka objašnjenja u molbama obično smanjuju vjerojatnost brzog odgovora. Kraće, jasnije molbe su efikasnije.

---

### Tip 5: Zahvala ili potvrda suradnje

Kratki, ali važan tip dopisa — potvrda primitka, zahvala na suradnji, završetak projekta. Mora biti topao, ali ne pretjerano neformalan.

**Prompt:**
```
Napiši kratki dopis kojim zahvaljujem [instituciji/osobi] na suradnji u [naziv projekta ili teme]. 
Istakni jednu konkretnu stvar koja je bila vrijedna. 
Ton: topao, profesionalan, kratak — maksimalno jedan odlomak.
```

**Što prilagodiš:** Konkretna stvar koju hvališ, naziv suradnje, eventualni nastavak suradnje ako postoji.

---

## Nakon što dobiješ tekst od A.I.-ja: 3 koraka provjere

Bez obzira koliko je prompt bio dobar, svaki tekst koji A.I. generira prolazi kroz tvoju provjeru. Evo što konkretno gledaš:

**Korak 1: Pročitaj naglas**
Ako zvuči čudno kad se čita glasno — A.I. je pretjerao s formalnostima ili koristio neprirodan red riječi. To su mjesta gdje ručno interveniraš.

**Korak 2: Provjeri terminologiju**
A.I. koristi opće termine. Tvoja institucija ili industrija možda ima specifičan žargon, interne nazive projekata ili zakonske pojmove koji moraju biti točni. Provjeri svaki stručni termin.

**Korak 3: Provjeri što nedostaje**
A.I. ne zna što je interni broj predmeta, referentni datum, ime primatelja, tvoj potpis ili prilog koji treba biti u dokumentu. Sve to dodaješ ručno.

---

## Sljedeći korak

Uzmi jedan dopis koji imaš na redu danas ili sutra. Formuliraj prompt prema gornjoj strukturi: kome, što, ton, format. Pogledaj rezultat — i prilagodi.

Za početnike: besplatna verzija ChatGPT-a (GPT-4o) potpuno je dovoljna za ovaj tip zadataka.

Za one koji žele ići korak dalje: Kako izgraditi vlastitu prompt biblioteku za posao — vodič u kojemu pokazujemo kako organizirati promptove koje koristiš svaki tjedan.
