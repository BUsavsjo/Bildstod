# Bildstöd – Dagsplanerare

Ett litet, fristående (frontend‑only) verktyg för att göra en överskådlig dagsplan med bildstöd för barn (t.ex. med NPF). Fokus ligger på: få val, stabil layout, stora klickytor, och tydlig progression ("NU" och "KLAR"). All data sparas lokalt i webbläsaren – inget skickas till någon server.

## Syfte
- Hjälpa barn att se dagens struktur visuellt.
- Minska stress genom igenkänning och korta texter.
- Ge vuxna ett enkelt sätt att snabbt lägga till/ändra aktiviteter.

## Funktioner
- Fördefinierade tidsblock: Morgon, Förmiddag, Lunch, Eftermiddag, Kväll.
- Aktivitetskort med emoji, kort text och (valfri) tid.
- Markering av nästa ej klara aktivitet (badge "NU").
- Enkel toggling barnläge / vuxenläge (låst / upplåst redigering).
- Lägg till, ändra, ta bort aktiviteter via modal.
- Dra och släpp (i vuxenläge) för att flytta eller omordna aktiviteter.
- Export / import av dagsplan som JSON-fil.
- Nollställning av alla "KLAR" statusar.
- Bibliotek av vanliga aktiviteter + nya tillagda (Häst, Dator, Kompisar, Syskon tjej, Syskon kille, Mamma, Pappa, Mormor).
- Ljust tema (vit bakgrund, enhetligt gränssnitt).

## Teknisk översikt
Projektet består av en enda fil: `index.html` som innehåller:
- Inbyggd CSS med variabler för färgtema.
- DOM-baserad rendering (ingen ramverksberoende kod).
- State-hantering i ett objekt `state` som lagras i `localStorage` med nyckeln `bildstod_plan_v1`.
- Generering av kort och slots sker dynamiskt vid varje `render()`.
- Modalhantering och drag‑och‑släpp implementerat med native events.

## Datastruktur
```jsonc
state = {
  id: "YYYY-MM-DD",        // datumstämpel
  title: "Dagsplan",        // reservfält
  slots: [                  // ordnade tidsblock
    { key, label, hint, items: [itemId, ...] }, ...
  ],
  items: {                  // uppslag av aktiviteter
    itemId: { id, text, time, emoji, done }
  },
  version: 1
}
```

## Användning
1. Öppna `index.html` direkt i en webbläsare (Chrome, Edge, Firefox, Safari).
2. I barnläge kan barnet klicka på ett kort för att markera det som "KLAR".
3. Vuxenläge: klicka på knappen "Lås upp (vuxenläge)" för att kunna:
   - Lägga till aktiviteter ("＋ Lägg till").
   - Klicka kort för att redigera eller ta bort.
   - Dra kort mellan tidsblock.
4. "Visa tider" / "Dölj tider" växlar visning av tidsfält.
5. "Nollställ Klar" tar bort alla klarmarkeringar.
6. "Exportera" sparar nuvarande plan som JSON-fil.
7. "Importera" läser tidigare sparad plan och ersätter den aktuella.

## Tillgänglighet / UX
- Stora klickytor (64–72px ikon, kort > 86px höjd).
- Kort text + emoji underlättar igenkänning.
- Färgkodning: Grön kant + badge "KLAR"; blå markering för "NU".
- Vuxen-/barnläge förhindrar oavsiktlig omstrukturering.
- Badge "NU" hjälper fokus på nästa steg.

## Anpassning
- Lägg till fler pictos genom att utöka arrayen `LIBRARY` i `index.html`.
- Ändra färgtema genom CSS-variabler i `:root`.
- För att börja varje dag på nytt kan du rensa `localStorage` för nyckeln eller bygga logik som roterar datum.

## Säkerhet & Integritet
- Ingen nätverkskommunikation. Allt stannar i browsern.
- Export är manuell – användaren väljer själv att spara fil.
- Inga personliga uppgifter lagras (endast aktivitetsnamn).

## Begränsningar / MVP
- Ingen server / synk mellan enheter.
- Ingen avancerad schema- eller kalenderintegration.
- Ingen automatisk tidslogik eller påminnelser.

## Förslag på vidareutveckling
- Mörkt/ljust temaväxling (toggle) med `prefers-color-scheme` stöd.
- Möjlighet till kopiering av gårdagens plan med snabb rensning.
- Kategorier / filter för biblioteket.
- Sortering med mer exakt dragposition (nu flyttas till slutet vid samma slot).
- Enkla statistikmoduler (hur många aktiviteter klara, tid kvar, etc.).
- Lokal backup-rotation (flera sparpunkter).
- Förenklad mobilvisning med större typsnitt.

## Felsökning
- Om sidan verkar "fast": Öppna webbläsarens utvecklingsverktyg och rensa `localStorage` för nyckeln `bildstod_plan_v1`.
- Om importerad fil inte laddas: kontrollera att JSON inkluderar fälten `slots` och `items`.

## Snabbstart (Windows PowerShell)
```powershell
# Gå till mappen
cd "c:\Users\petwen\OneDrive - Höglandsförbundet\Projekt\Bildstod"
# Öppna filen i standardwebbläsare
start index.html
```

## Licens
Ingen explicit licens angiven. Lägg till vid behov (t.ex. MIT) innan publicering om andra ska återanvända koden.

---
### English (brief)
A single‑file visual day planner with emoji activity cards for children. Local storage only, editable parent mode, drag & drop, JSON export/import, and focus on next incomplete task.

---
Har du önskemål om fler aktiviteter, funktioner eller språkstöd? Skicka gärna en uppföljning.
