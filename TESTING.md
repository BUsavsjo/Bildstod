# Testplan – Bildstöd Dagsplanerare

## Förberedelse
1. Öppna `index.html` i en modern webbläsare (Chrome, Firefox, Edge, Safari)
2. Öppna webbläsarens Developer Tools (F12) → Console för att se eventuella fel
3. Testa i både desktop och mobil-läge (Chrome DevTools)

---

## STEG 1: Barnläge – Grundläggande funktionalitet

### 1.1 Startsida & Layout
- ✓ Sidan laddar utan fel
- ✓ Header visar: "🧩 Bildstöd – Dagsplanerare" + "Barnläge" pill
- ✓ Fem tidsblock synliga: Morgon, Förmiddag, Lunch, Eftermiddag, Kväll
- ✓ Default-aktiviteter finns i varje block
- ✓ Stor text, stora ikoner, god kontrast

### 1.2 Aktivitetskort – Barnläge
- ✓ Kort visar: emoji + text (t.ex. "🌅 Vakna")
- ✓ Kort har tydliga gränser och stor klickyta (min 86px höjd)
- ✓ Kort är snygga och barnvänliga

### 1.3 Klicka på kort för att markera "KLAR"
- ✓ Klicka "🍞 Frukost" → kortet blir grönt med "KLAR" badge
- ✓ Kortet förblir grönt efter omladdning (data sparas)
- ✓ Klicka igen → kortet blir vitt och "KLAR" försvinner
- ✓ Endast ett kort per tidsblock kan markeras som "NU" (nästa ej klara)

### 1.4 Badge "NU" – Nästa aktivitet
- ✓ Första ej klara aktiviteten får blå badge "NU"
- ✓ Efter att markera det som "KLAR" → nästa aktivitet får "NU"
- ✓ Badge försvinner när alla är "KLAR"

---

## STEG 2: Vuxenläge – Barnläge (redigering)

### 2.1 Växla läge
- ✓ Klicka "🔒 Lås upp (vuxenläge)" → läge byter till vuxenläge
- ✓ Pill ändras från "Barnläge" till "Vuxenläge"
- ✓ Knapptext ändras till "🔓 Lås (barnläge)"
- ✓ Klicka igen → tillbaka till barnläge

### 2.2 Vuxenläge – UI
- ✓ "＋ Lägg till"-knappar dyker upp på alla tidsblock
- ✓ Delete-ikoner (🗑️) dyker upp på varje kort
- ✓ Drag-handle (↕ dra) visas i nedre högra hörnet av kort
- ✓ Personsektionen visar redigerings-kontroller

---

## STEG 3: Tider – Digital & Analog

### 3.1 Visa/Dölj tider – Grundläggande
- ✓ Klicka "🕒 Visa tider" → tider visas under aktivitetstext
- ✓ T.ex. "🌅 Vakna" visar tid "08:00" under
- ✓ "🕐 Analog klocka"-knapp dyker upp när tider visas
- ✓ Klicka "🕒 Dölj tider" → tider försvinner, analog-knapp döljs
- ✓ Inställningen sparas (reload → samma läge)

### 3.2 Analog Klocka – Visning
- ✓ Klicka "🕐 Analog klocka" → aktivitetskort visar SVG-klocka
- ✓ Klockan är ca 48×48px och väl placerad
- ✓ Timvisare (kort) och minutvisare (lång) synliga
- ✓ Digital tid "08:00" visas fortfarande under som stöd
- ✓ Analog klocka visar rätt tid:
  - 08:00 → timvisare pekar på 8, minutvisare på 12
  - 14:30 → timvisare mellan 2 och 3, minutvisare på 6
  - 09:15 → timvisare mellan 9 och 10, minutvisare på 3

### 3.3 Digital Klocka – Växla tillbaka
- ✓ Klicka "🕐 Digital klocka" → analog försvinner, endast tid visas
- ✓ Knapptext ändras till "🕐 Analog klocka"
- ✓ Inställningen sparas över reload

### 3.4 Tidsformat
- ✓ Enkel tid "09:30" → analog visar rätt
- ✓ Tidsintervall "10:00–11:00" → analog visar första tiden (10:00)
- ✓ Felaktig tid "25:99" → fallback till digital text (ingen SVG)

---

## STEG 4: Deltagare – Vem är med?

### 4.1 Personsektionen – Barnets perspektiv
- ✓ Rubrik är "Dagens människor"
- ✓ Default-personer: Mamma (här), Pappa (senare, kommer 18:00), Syskon (borta)
- ✓ Varje person visar: Namn, Status (✅ här/🚗 borta/⏳ senare), Aktivitet, Tider
- ✓ T.ex. "👩 Mamma ✅ här, 💼 Jobbar hemma, mellan 08:00 - 16:00"

### 4.2 Lägg till person (vuxenläge)
- ✓ Klicka "＋ Lägg till" i personsektionen
- ✓ Ny person "Person" dyker upp med redigeringskontroller
- ✓ Länka känner till nya personer omedelbar

### 4.3 Redigera personnamn
- ✓ Namnfält fyller med "Person"
- ✓ Skriv nytt namn (t.ex. "Elsa") → sparas direkt
- ✓ Reload → namn är kvar

### 4.4 Redigera person-status
- ✓ Dropdown: "✅ här", "🚗 borta", "⏳ senare"
- ✓ Ändra status → sparas direkt
- ✓ Status uppdateras i barnläges-vyn

### 4.5 Redigera personens aktivitet
- ✓ Dropdown "Gör:" med: —, 💼 Jobbar, 🎨 Rita, osv.
- ✓ Välj aktivitet → sparas direkt
- ✓ Visas i personsektionen (t.ex. "💼 Jobbar hemma")

### 4.6 Redigera personens tider (ETA)
- ✓ Start- och slut-tid dropdowns
- ✓ Välj "08:00" start och "16:00" slut
- ✓ Sparas → visar "mellan 08:00 - 16:00" i barnläge

### 4.7 Ta bort person
- ✓ Klicka "🗑️ Ta bort" på person
- ✓ Bekräftelsedialg: "Ta bort Mamma?"
- ✓ Efter bekräftelse → person försvinner
- ✓ Reload → person är borta

---

## STEG 5: Deltagare på Aktiviteter

### 5.1 Lägg till deltagare på aktivitet (vuxenläge)
- ✓ Klicka "＋ Lägg till" på aktivitet
- ✓ Modal öppnas: "Lägg till aktivitet"
- ✓ Ny sektion: "Vem är med?" med checkboxar för varje person
- ✓ T.ex. checkboxar: ☐ Mamma, ☐ Pappa, ☐ Syskon

### 5.2 Välja deltagare
- ✓ Bocka "Mamma" och "Syskon"
- ✓ Skriv text "Frukost", tid "08:00", välj emoji 🍞
- ✓ Klicka "Spara"
- ✓ Kort visas med deltagare: "🍞 Frukost, 08:00, Mamma, Syskon"

### 5.3 Redigera deltagare på befintlig aktivitet
- ✓ Klicka på aktivitetskort i vuxenläge
- ✓ Modal öppnas: "Ändra aktivitet"
- ✓ Deltagare-checkboxar visar redan valda (☑ Mamma, ☑ Syskon)
- ✓ Avbocka Syskon, bocka Pappa
- ✓ Klicka "Spara" → uppdaterar kort

### 5.4 Visa deltagare på kort (barnläge)
- ✓ Barnläge: kort visar deltagare under tid
- ✓ "🍞 Frukost, 08:00, Mamma, Pappa"
- ✓ Namn på en rad eller radbrytning om många

### 5.5 Ta bort alla deltagare
- ✓ Redigera aktivitet, avbocka alla
- ✓ Spara → deltagare försvinner från kort

---

## STEG 6: Aktivitetshantering

### 6.1 Lägg till aktivitet
- ✓ Vuxenläge: Klicka "＋ Lägg till"
- ✓ Modal: skriv "Test", tid "13:00", välj emoji
- ✓ Välj deltagare: t.ex. Mamma
- ✓ Klicka "Spara"
- ✓ Kort visas med allt: text, tid, emoji, deltagare

### 6.2 Redigera aktivitet
- ✓ Klicka befintligt kort
- ✓ Modal: ändra text/tid/emoji/deltagare
- ✓ Klicka "Spara" → kort uppdateras

### 6.3 Ta bort aktivitet
- ✓ Klicka kort i vuxenläge
- ✓ Klicka "🗑️ Ta bort" i modal
- ✓ Bekräftelse
- ✓ Kort försvinner

### 6.4 Dra och släpp kort
- ✓ Vuxenläge: dra ett kort från Morgon till Förmiddag
- ✓ Kort flyttas mellan tidsblock
- ✓ Reload → kort är i rätt block

---

## STEG 7: Data & Lagring

### 7.1 localStorage sparar allt
- ✓ Gör ändringar (aktiviteter, status, deltagare)
- ✓ Reload sidan → allt är kvar
- ✓ Barnläge: markera kort som "KLAR" → reload → fortfarande "KLAR"

### 7.2 Exportera dagsplan
- ✓ Klicka "⬇️ Exportera"
- ✓ JSON-fil laddas ned: `bildstod-YYYY-MM-DD.json`
- ✓ Öppna i texteditor → JSON är korrekt formaterad
- ✓ JSON innehåller: `slots`, `items` (med `participants`), `people`

### 7.3 Importera dagsplan
- ✓ Klicka "⬆️ Importera"
- ✓ Välj tidigare exporterad JSON-fil
- ✓ Sidan laddar → all data från filen visas
- ✓ Gamla data är borta, nya är aktiv

### 7.4 Nollställ allt
- ✓ Klicka "↺ Nollställ & Rensa"
- ✓ Bekräftelsedialog: "Nollställa KLAR och rensa alla kort?"
- ✓ Efter OK → alla kort är borta, alla "KLAR"-märken borta
- ✓ Personsektionen finns fortfarande

---

## STEG 8: Gränssnitts-stabilitet

### 8.1 Header-knappar
- ✓ Alla knappar är klickbara och responsiva
- ✓ Inget flimrar eller glitchar vid knapptryck
- ✓ Text uppdateras korrekt

### 8.2 Modal-hantering
- ✓ Öppna modal → fokus på text-fält
- ✓ Klicka "Avbryt" → modal stängs
- ✓ Klicka utanför modal → modal stängs
- ✓ Ingen data försvinner

### 8.3 Responsivitet (mobil)
- ✓ Öppna i mobil-läge (DevTools)
- ✓ Kort är stora nog att trycka på
- ✓ Text är läsbar
- ✓ Rutnät anpassas till skärmbredd

### 8.4 Tema & Tillgänglighet
- ✓ Ljust tema är konsistent
- ✓ Ikoner och text har god kontrast
- ✓ Inga färgberoende indikationer (använd also form, inte bara färg)

---

## STEG 9: Edge Cases & Felhantering

### 9.1 Tomt namnfält
- ✓ Spara aktivitet utan text → inget sparas, fokus på text-fält

### 9.2 Felaktig tid
- ✓ Skriv "25:99" → analog visas inte, fallback till digital text

### 9.3 Många deltagare
- ✓ Lägg till alla 3 personer på en aktivitet
- ✓ Kort visar alla namn utan att bli för stort

### 9.4 Många aktiviteter
- ✓ Lägg till 10+ aktiviteter i ett tidsblock
- ✓ Scroll fungerar korrekt
- ✓ Ingen prestandaminskning

### 9.5 localStorage full
- ✓ (Sällsynt) Men om detta händer, browser-varning bör visas

---

## STEG 10: Licens & Dokumentation

### 10.1 LICENSE-fil
- ✓ Fil `LICENSE` existerar
- ✓ Innehåller MIT-licens
- ✓ År är korrekt (2026)

### 10.2 README uppdaterad
- ✓ README nämner "Deltagare på aktiviteter"
- ✓ README nämner "Analog/digital klocka"
- ✓ Uppdaterad användarbeskrivning
- ✓ Licens är MIT

### 10.3 Kod kommenterad
- ✓ Viktiga funktioner har kommentarer
- ✓ SVG-rendering-kod är förklarad
- ✓ Deltagare-logik är tydlig

---

## Test-resultat-mall

```
Resultat från test: [DATUM]
Testare: [NAMN]

Miljö: 
- Webbläsare: [Chrome/Firefox/Safari/Edge]
- Version: [XX]
- OS: [Windows/Mac/Linux]
- Enhet: [Desktop/Mobile]

Genomförda steg: 1-10 ✓
Misslyckade steg: [Om någon]
Buggar/problem: [Om någon]
Observationer: [Annat som noterats]

Status: ☐ KLAR ☐ PÅ VÄGEN ☐ BLOCKERAD
```

---

## Sammanfattning

**Nya funktioner att testa:**
- ✓ Deltagare på aktiviteter (vem är med)
- ✓ Analog klocka visning
- ✓ Toggle för analog/digital
- ✓ Personnamn kan redigeras
- ✓ MIT-licens
- ✓ Uppdaterad dokumentation

**Gamla funktioner (regression-test):**
- ✓ Barnläge / Vuxenläge
- ✓ Aktiviteter: lägg till, ändra, ta bort
- ✓ Dra och släpp
- ✓ Export / Import
- ✓ Nollställ
- ✓ Tider: visa/dölj
- ✓ localStorage-sparning

**Esperant OK-resultat:**
- ✓ Noll JavaScript-fel i console
- ✓ Alla knappar funktionella
- ✓ Data sparas och laddas korrekt
- ✓ Analog klocka visar rätt tid
- ✓ Barnläge är enkelt och tydligt för barn
