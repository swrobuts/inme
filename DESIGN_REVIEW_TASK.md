# Design-Review Fix Task – INME Lab
# Alle 23 Punkte akribisch umsetzen

## Kontext
- Repo: /tmp/inme-lab/ (bereits gecloned, git init, remote=https://github.com/swrobuts/inme.git)
- Stack: React 18 + Babel CDN, kein Build-Tool. Alle Dateien sind plain HTML mit JSX inline.
- Bilingual: DE/EN Toggle via React useState. `data-lang={lang}` auf Root-Div jeder Seite.
- DE = Rot `#DC2626`/`#B91C1C`, EN = Mango `#F7CC00` — das ist BEWUSSTE Designentscheidung, NICHT ändern!
- Commit am Ende: EINE einzelne Commit-Message für alle Änderungen.

## Dateien
- index.html
- lab-01-grundlagen.html
- lab-02-kreativitaet.html
- lab-03-gestaltung.html
- lab-04-ux.html
- lab-05-usecase.html (Lab-Seite über den Use Case)
- lab-06-implementation.html
- coffee-app.html (Standalone Kaffeevollautomat-App mit Gemini Vision — KEIN Lab-Page-Layout!)

## Entscheidungen die du treffen musst (vorab geklärt)

- **#2 Sidebar-Label:** Einheitlich `INHALT` (nicht NAVIGATION)
- **#3 Hero-Header:** Hero von Lab 02 ENTFERNEN. Kein Hero auf irgendeinem Lab (nur index.html hat Hero). Lab 03 schwarze Card-Header ebenfalls entfernen — beide an Lab 01 angleichen.
- **#5/#6 Quiz-Format:** `Q1`, `Q2`... + Antworten als `A)`, `B)`, `C)`, `D)` — überall
- **#7 Footer-Nav:** `justify-content: space-between`, `← Zurück` links, `Weiter →` rechts
- **#10 Dateiname:** coffee-app.html BLEIBT (das ist die Standalone-App, kein Lab-Page). Eine Redirect-Datei ist NICHT nötig da die App von lab-05-usecase.html verlinkt wird.
- **#11 Title coffee-app.html:** Ändere zu `Lab 05 – Kaffeevollautomat-App | INME Lab`
- **#12 Namensinkonsistenz:** Einheitlicher Name = `Kaffeevollautomat-Störungsmelder`
- **#18 Zitat-Sprache:** Jony Ive Zitat in DE-Modus: Füge Quellenangabe hinzu: kleiner Zusatz `(Originalzitat, englisch)` — das Zitat selbst bleibt englisch
- **#19 EN-Farbschema:** BEWUSSTE Entscheidung — NICHT ändern, lediglich in einem HTML-Kommentar in index.html dokumentieren
- **#20 Zusammenfassungen:** Kurze `<section id="zusammenfassung">` am Ende von Lab 02, Lab 03, Lab 06 einfügen — passender Inhalt für das jeweilige Thema, DE+EN

---

## Checkliste der 23 Punkte

### #1 – Title-Tags (alle Dateien)
Einheitliches Format: `Lab 0X – Kurztitel | INME Lab`
- lab-01: `Lab 01 – Grundlagen Interaktiver Medien | INME Lab`
- lab-02: `Lab 02 – Kreativtechniken & Design Thinking | INME Lab`
- lab-03: `Lab 03 – Gestaltungsprinzipien & Bauhaus | INME Lab`
- lab-04: `Lab 04 – UX Research & Prototyping | INME Lab`
- lab-05: `Lab 05 – Use Case: Kaffeevollautomat | INME Lab`
- lab-06: `Lab 06 – Implementierung: Supabase + CodePen | INME Lab`
- coffee-app: `Lab 05 – Kaffeevollautomat-App | INME Lab`
- index: `INME Lab – Interaktive Medien | THWS Business School` (bleibt, ist ok)

### #2 – Sidebar-Label
In allen 6 Lab-Dateien das Sidebar-Label auf `INHALT` vereinheitlichen.
Suche nach: `'NAVIGATION'`, `'LAB 01'`–`'LAB 06'`, `'INHALT'` im Sidebar-Kontext.
Alle ersetzen durch `'INHALT'` (DE) und `'CONTENTS'` (EN).

### #3 – Hero-Header entfernen
- lab-02-kreativitaet.html: Roten Hero-Header-Block entfernen. Seitenstruktur wie Lab 01 (nur Sidebar + Content, kein Hero).
- lab-03-gestaltung.html: Falls es einen schwarzen Card-Header gibt, entfernen. Seitenstruktur wie Lab 01.

### #4 – Seitentitel-Farbe Lab 03
In lab-03-gestaltung.html: Der Haupttitel `Gestaltungsprinzipien & Bauhaus` muss in Rot `#DC2626` sein (wie alle anderen Labs). Suche nach `.page-title` oder dem `<h1>` style und ändere die Farbe.
Auch: der `[data-lang="en"]` Override muss `color: #1A1A1A` für EN sein.

### #5 + #6 – Quiz-Format vereinheitlichen
In allen Labs: Quiz-Nummern als `Q1`, `Q2`... und Antwortoptionen als `A)`, `B)`, `C)`, `D)`.
- lab-01: prüfen ob schon korrekt, ggf. anpassen
- lab-02: `F1.` → `Q1`, Antworten prüfen
- lab-04: `5.` ohne Prefix → `Q1`..., Antworten auf `A)` etc. setzen
- lab-06: Antworten ohne Buchstaben → `A)` etc. hinzufügen
Beide Sprachversionen (DE+EN) anpassen.

### #7 – Footer-Navigation
In allen 6 Lab-Dateien: Navigations-Footer (Zurück/Weiter-Buttons) mit `justify-content: space-between` gestalten.
Pattern:
```
[← Zurück]          [Weiter →]
```
Der "← Zurück zur Übersicht" Link auf lab-01 bleibt links. "Weiter →"-Button rechts.
Wo nur ein Button existiert (z.B. letztes Lab nur "← Zurück"), bleibt er links.
Keinen Button einfach "rechts" setzen ohne den Gegenpart.
Lab 06 hat anscheinend "Zwei Zurück-Buttons" — das muss gefixt werden (prüfen, einen entfernen oder umwandeln).

### #8 – "← Übersicht"-Link Position
lab-03 hat diesen Link als separaten Button oben rechts neben DE/EN — anpassen auf das Standard-Pattern wie lab-01 (Link im Header neben Logo links).

### #9 – Lernziele-Heading Farbe
In allen 6 Labs: `Lernziele`-Heading (h2 oder h3) auf `color: #DC2626` setzen.
EN-Override: `color: #1A1A1A`.

### #10 – coffee-app.html bleibt — kein Rename nötig
(Entscheidung: Dateiname bleibt, da Standalone-App)

### #11 – Title coffee-app.html
```html
<title>Lab 05 – Kaffeevollautomat-App | INME Lab</title>
```

### #12 – Namensinkonsistenz
coffee-app.html Header/Subtitle: Ändere "Service App – Frisia × THWS" auf "Kaffeevollautomat-Störungsmelder" oder ähnliches (INME-Kontext klar machen).
index.html Lab-Karte für Lab 05: prüfen ob "Kaffeevollautomat-Störungsmelder" steht — falls nicht, angleichen.

### #13 – Zurück-Navigation coffee-app.html
In coffee-app.html: Einen dezenten "← Zurück zum Lab" Link in den Header einfügen, der auf `lab-05-usecase.html` zeigt. Klein, dezent, kein eigenes Branding nötig — im bestehenden Header unterbringen.

### #14 – Leerraum coffee-app.html
Screen 0 (Home-Screen): Falls zwischen Beschreibungstext und "Störung analysieren"-Button ein großer Leerbereich ist (~300px), diesen entfernen. Screen 1 prüfen ob Upload-Bereich und Button sauber sitzen.

### #15 – Zeitangabe-Position
In allen Labs: Das Zeitangabe-Badge (z.B. "CA. 45 MIN") soll immer in der ersten Zeile neben dem Lab-Badge stehen.
- lab-01, lab-04: bereits korrekt (neben Badge)
- lab-06: "CA. 90 MIN" steht unter dem Titel → in die erste Zeile neben das Badge verschieben
- lab-02: unter Lernzielen → in erste Zeile verschieben

### #16 – Lernziele Box einheitlich
Alle Labs sollen eine identische Lernziele-Box haben:
- Hintergrund: `#FEF2F2` (sehr helles Rot/Pink)
- Border-Left: `4px solid #DC2626`
- Überschrift "Lernziele": `color: #DC2626`
- EN: Hintergrund bleibt, Überschrift `color: #1A1A1A`, Border `#1A1A1A`
Alle Labs prüfen und angleichen.

### #17 – Content-Breite
lab-03 nutzt breiteren Content-Bereich. Prüfe die `.content` oder `.main-content` CSS-Klasse in lab-03 und setze `max-width` auf denselben Wert wie die anderen Labs (vermutlich 860px oder 900px — prüfen in lab-01).

### #18 – Zitat-Sprache index.html
Das Jony Ive Zitat ist englisch. In der DE-Version: Füge unter dem Zitat eine kleine Quellenangabe hinzu:
```
— Jonathan Ive, Apple
(Originalzitat auf Englisch)
```
Beide Versionen (DE-Anmerkung + EN ohne Anmerkung) — via `{lang === 'de' && <span>...</span>}`.

### #19 – EN-Farbschema dokumentieren
In index.html, nach den CSS-Variablen oder am Anfang des `<style>`-Tags, einen Kommentar einfügen:
```html
<!-- DESIGN DECISION: DE=Bauhaus Red #DC2626, EN=Lamy Safari Mango #F7CC00.
     The language toggle intentionally switches the color scheme (bilingual Bauhaus concept). -->
```

### #20 – Fehlende Zusammenfassungen
Am Ende von lab-02, lab-03, lab-06 eine Section einfügen:

lab-02 (Kreativtechniken & Design Thinking):
- DE: Titel "Zusammenfassung", Kernpunkte: Design Thinking 5 Phasen, Kreativtechniken (Brainstorming, How Might We, Crazy 8s), Sketchnotes, Kreativität als erlernbare Kompetenz
- EN: "Summary"

lab-03 (Gestaltungsprinzipien & Bauhaus):
- DE: Bauhaus-Kernprinzipien, Form follows function, Farbe/Typografie als Kommunikationsmittel, Bewusste Designentscheidungen
- EN: entsprechend

lab-06 (Implementierung):
- DE: Supabase Setup, CodePen-Workflow, Realtime-Events, Next Steps für eigene Projekte
- EN: entsprechend

### #21 – Nav-Link "Interaktive Medien" in index.html
Im Header von index.html: Prüfe den "Interaktive Medien" Link. Falls er auf sich selbst oder # verweist, entweder entfernen oder durch einen sinnvollen Link ersetzen (z.B. `https://www.thws.de` oder einfach als plain Text ohne Link).

### #22 – "Sommersemester 2026" dynamisch
In index.html: Suche nach dem hardcodierten "Sommersemester 2026" Text.
Ersetze durch eine JavaScript-Konstante am Anfang des Scripts:
```js
const SEMESTER = 'Sommersemester 2026';
const SEMESTER_EN = 'Summer Semester 2026';
```
Und nutze diese im JSX. So ist es leicht zu ändern. (Kein wirklich dynamischer Code nötig.)

### #23 – Footer auf Lab-Seiten
Alle 6 Lab-Dateien: Füge am Ende der Seite (nach den Navigationsbuttons) einen minimalen Footer ein:
```
© 2026 Prof. Dr. Robert Butscher · THWS Business School · INME Lab
```
Style: `text-align: center; padding: 1.5rem; font-size: 0.75rem; color: #9ca3af; border-top: 1px solid #e5e7eb`
DE + EN Version (Name + Institution bleibt englisch, nur Text anpassen wenn nötig).

---

## EN-Overrides Pflicht
Für JEDE inhaltliche Änderung die Farben enthält:
- Wenn du in DE eine rote Farbe setzt, MUSS ein `[data-lang="en"]` Override existieren der sie auf `#1A1A1A` (oder `#F7CC00` für Hero) setzt.
- Pattern: `[data-lang="en"] .klasse { color: #1A1A1A !important; }`
- Das ist die wichtigste Invariante dieser Codebase.

---

## Abschluss
Nach allen Änderungen:
1. `cd /tmp/inme-lab && git add -A`
2. `git commit -m "fix: design review – 23 consistency issues resolved (titles, sidebar, quiz, nav, footer, colors, hero, content-width)"`
3. `git push origin main`
4. Bestätige mit: `openclaw system event --text "Done: INME design review 23 Punkte abgearbeitet und gepusht" --mode now`

WICHTIG: Nutze `OPENCLAW_CONFIG_PATH=/Users/robert/clawd/.openclaw-macbot/openclaw.json OPENCLAW_STATE_DIR=/Users/robert/clawd/.openclaw-macbot openclaw system event ...` für den openclaw Befehl.
