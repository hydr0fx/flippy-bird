# Sitzung 18.08.2026 – v3.0

## Änderungen

### Fix: Verkaufen & Bearbeiten funktioniert jetzt
- **Ursache:** Das "Als verkauft markieren"-Modal (`modal-mark-sold`) fehlte komplett im HTML – nur die JS-Funktionen existierten. Klick auf "Verkauft?" führte zu einem JS-Crash (null element), wodurch das Bearbeiten von Artikeln nicht mehr funktionierte.
- **Fix:** Modal mit Verkaufspreis, Plattform, Versandkosten, Gebühren wieder eingebaut.

### Preset-Daten entfernt
- Alle Demo-/Seed-Daten (5 Resell-Artikel, 6 Buchungen, 4 To-Dos, 3 Termine) entfernt.
- App startet jetzt leer: `resellItems: []`, `transactions: []`, `todos: []`, `events: []`.
- Storage-Key auf `flippy_bird_data_v3` gehoben → bestehende Demo-Daten werden nicht mehr geladen.
- "Demo-Daten neu laden" → "Alle Daten zurücksetzen".

### Kalender
- **Heutiger Tag immer leicht markiert** (Ring + dezenter Hintergrund), unabhängig von der Auswahl.

### Übersicht (Dashboard) klickbar
- Monatsgewinn-Karte → Statistik-Tab
- Restbudget-Karte + Budget-Bar → Finanzen-Tab
- Auf-Lager-Karte → Inventar
- To-Dos-Karte → Kalender (To-Do-Subtab)
- Termin-Liste → Kalender (springt zum Datum)
- To-Do-Liste → Kalender (To-Do-Subtab)
- Letzte-Verkäufe-Liste → Detailansicht des Artikels

### Monatsbudget verbessert
- Restbudget wird jetzt **inklusive Einnahmen** berechnet: `Budget + Einnahmen − Ausgaben`
- Budget-Bar berücksichtigt Einnahmen ebenfalls.

### Saubere Übergänge
- Modal-Sheets: Slide-Up-Animation (`modal-sheet`)
- Tab-Wechsel: Fade-In (`tab-fade`)
- Karten: Press-Effekt + Hover-Transition
- Budget-Bar: animierte Breite

### Kalender-Widget
- Neues "Flippy Bird Kalender"-Widget im Widget-Simulator (Settings) mit den nächsten 3 Terminen.

### Sonstiges
- `sw.js` Cache auf `flippy-bird-cache-v3` gehoben.
- Settings-Version auf v3.0.0.

## Status
- **Live:** https://hydr0fx.github.io/flippy-bird/ (GitHub Pages)
- **SW Cache:** v3
- **Kein Backend** – reine Client-PWA
- **Keine automatische Kleinanzeigen-Postings** – nur Export + Copy

---

# Sitzung 23.05.2026 – v3.1

## Änderungen seit v3.0

### Photo Viewer
- Vollbild-Overlay mit Zoom (rein/raus/reset), Rotation, Download
- Navigation mit Prev/Next-Pfeilen
- Indikator "X / Y"
- Bild aus Detailansicht, Inventarliste und Formular öffnbar

### PayPal Gebührenrechner
- Modal-Overlay mit Eingabe des Verkaufspreises
- Berechnung: 2,49% + 0,35€ Gebühr, Anzeige Netto-Betrag
- "Gebühr übernehmen"-Button: übernimmt berechnete Gebühr ins Formular

### Versandkosten-Auswahl
- Dropdown für Versandmethode (DHL, Hermes, Deutsche Post)
- Dynamische Paketoptionen mit Kosten pro Methode
- Auswahl wird im Item gespeichert

### Sales Monatsraster
- Skyscanner-ähnliches 3×4 Grid mit Monatskacheln
- Jede Kachel: Monatsname, Gewinn (€), Anzahl Verkäufe
- Jahr-Navigation mit ‹ › « »
- Klick auf Kachel: Popup mit detaillierter Verkaufsliste, Gesamtgewinn, Ø Marge

### Select-Modus für Verkäufe
- Langdruck auf Sales-Header → Checkboxen erscheinen
- Mehrere Items auswählen, als verkauft markieren
- Auswahl-Leiste mit Counter und "Als verkauft markieren"-Button

### UI/UX
- Gold (#FACC15) Akzente für Buttons, aktive Filter, Nav-Add-Button
- Dark Mode mit warmem Gold-Schema beibehalten
- Live-Gewinnrechner im Formular (Gewinn, Marge %, ROI %)
- Status-Buttons in Detailansicht (Bereit/Inseriert/Verkauft)
- Automatische PayPal-Gebührenberechnung beim Eintragen des Verkaufspreises

### Datenmodell-Erweiterungen
- `paypalFee`, `shippingMethod`, `shippingCost` pro Item
- `fSalePrice` statt `fSelling` (Formularfeld)
- `sellDate` für Verkaufsdatum

### Header & Dark Mode (Session 2)
- Vogel-Emoji 🐦 aus Header entfernt → App-Logo (icon-192.png) stattdessen
- Dark-Mode-Toggle (🌙/☀️) direkt im Header – sofort an/aus, kein Settings-Speichern
- Dark Mode aus Settings-Seite entfernt
- `manifest.json` theme-color auf `#1A1A2E` korrigiert
- Empty-State-Icon von 🐦 auf 📦 geändert
- `applyDarkMode()` setzt jetzt alle CSS-Variablen (`--bg`, `--card`, `--text`, `--border`)

## Status
- **Live:** https://hydr0fx.github.io/flippy-bird/ (GitHub Pages)
- **SW Cache:** v3.1.0
- **Kein Backend mehr** – reine Client-PWA
- **Keine automatische Kleinanzeigen-Postings** – nur Export + Copy

## Letzte Commits
```
245ad74 Remove bird emoji, add app icon in header, instant dark mode toggle in header
de96e35 Add .gitignore
8111f2b v3.1: Photo viewer, PayPal calculator, shipping cost selector, sales month grid, select mode
```
