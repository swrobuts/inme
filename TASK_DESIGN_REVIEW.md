# TASK: Design-Review Fixes – INME Lab (alle 23 Punkte)

**Repo:** `/tmp/inme-lab/` (git repo, remote: https://github.com/swrobuts/inme)
**Server:** http://localhost:8766 (läuft bereits)
**Files:** index.html, lab-01-grundlagen.html, lab-02-kreativitaet.html, lab-03-gestaltung.html, lab-04-ux.html, lab-05-usecase.html, lab-06-implementation.html, coffee-app.html

## Rahmenbedingungen

- React 18 + Babel + Tailwind via CDN – KEIN npm, KEIN build
- Bilingual DE/EN: `data-lang={lang}` auf Root-Div jeder Seite
- EN-Overrides: CSS `[data-lang="en"] .element { ... }` für alle roten Elemente
- DE-Farbe: `#DC2626` / EN-Farbe: `#F7CC00` (BEWUSSTE Designentscheidung, NICHT ändern)
- CSS-Var: `--primary: #B91C1C`
- Kein Border-Radius auf Cards/Buttons (Bauhaus-Regel)
- Keine Gradienten
- Keine Emoji in Buttons/Labels

## Zu behebende Probleme

### #1 – Title-Tags vereinheitlichen
Zielformat: `Lab 0X – {Titel} | INME Lab`

Aktuell:
- lab-01: `Lab 01 – Grundlagen Interaktiver Medien | INME` → `Lab 01 – Grundlagen Interaktiver Medien | INME Lab`
- lab-02: `Lab 02 – Kreativtechniken & Design Thinking · INME Lab` → `Lab 02 – Kreativtechniken & Design Thinking | INME Lab`
- lab-03: `INME Lab 03 – Gestaltungsprinzipien & Bauhaus` → `Lab 03 – Gestaltungsprinzipien & Bauhaus | INME Lab`
- lab-04: `Lab 04 – UX Research & Prototyping | INME` → `Lab 04 – UX Research & Prototyping | INME Lab`
- lab-05: `Lab 05 – Use Case: Kaffeevollautomat-Störungsmelder | INME` → `Lab 05 – Use Case: Kaffeevollautomat-Störungsmelder | INME Lab`
- lab-06: `Lab 06 – Implementierung: Supabase + CodePen | INME` → `Lab 06 – Implementierung: Supabase + CodePen | INME Lab`
- coffee-app.html: `Service App – Frisia × THWS` → `Lab 05 – Störungsmelder | INME Lab`
- index.html: bleibt `INME Lab – Interaktive Medien | THWS Business School`

### #2 – Sidebar-Label vereinheitlichen
In ALLEN lab-*.html: Den Sidebar-Nav-Label auf `NAVIGATION` setzen.
Suche nach: `'NAVIGATION'`, `'LAB 01'`...`'LAB 06'`, `'INHALT'`, `"NAVIGATION"` etc. als String-Literal in den React-Komponenten.
Jede Lab-Seite hat eine Sidebar-Komponente mit einem Label – alle auf `NAVIGATION` (DE) / `NAVIGATION` (EN) setzen.

### #3 – Hero-Header entfernen (nur Lab 02 hat einen)
Lab 02 hat einen roten Hero-Bereich mit `background: #DC2626` oder ähnlich am Anfang.
Alle anderen Labs haben keinen Hero-Header → Hero in Lab 02 entfernen, damit alle Labs konsistent sind.
WICHTIG: Nur den Hero-Bereich entfernen, nicht den restlichen Inhalt von Lab 02.

### #4 – Seitentitel-Farbe in Lab 03
In `lab-03-gestaltung.html`: Der Haupt-H1/H2-Seitentitel (mit dem Lab-Namen "Gestaltungsprinzipien & Bauhaus") ist schwarz.
Alle anderen Labs haben roten Seitentitel. 
Fix: Den Seitentitel in Lab 03 auf `color: #DC2626` setzen (und EN-Override: `#F7CC00`).
Suche nach dem Lab-Titel-Element in Lab 03 und korrigiere die Farbe.

### #5 + #6 – Quiz-Format vereinheitlichen
Zielformat überall:
- Fragen: `Q1`, `Q2`, `Q3` etc. (kein `F1.`, kein `5.`, kein `1)`)
- Antworten: Immer `A)`, `B)`, `C)`, `D)` als Präfix vor dem Antworttext

Vorgehen:
- In lab-01: Quiz-Format prüfen – wenn `Q1` verwendet wird, als Referenz nehmen
- In lab-02: `F1.`, `F2.` etc. → `Q1`, `Q2` etc.
- In lab-04: Numerische Prefixe → `Q1`, `Q2`; Antworten ohne Buchstaben → `A)`, `B)`, `C)`, `D)` hinzufügen
- In lab-06: Gleiche Korrekturen

Hinweis: Die Quiz-Komponenten sind in React/JSX. Suche nach dem Quiz-Daten-Array (questions/fragen/quiz) in jeder Datei.

### #7 – Footer-Navigation vereinheitlichen
In ALLEN lab-*.html: Die untere Navigation (Zurück/Weiter-Buttons) auf dieses Pattern bringen:
```
justify-content: space-between
← Zurück zum Lab / ← Zurück     [LINKS]
Weiter →                          [RECHTS]
```

Lab 01 als mögliche Referenz. Wenn Lab X nur "Zurück" (kein Weiter), dann Button links, rechts leer.
Container-Style: `display: flex; justify-content: space-between; align-items: center; padding: 1.5rem 0;`

Für lab-06 (hat angeblich zwei Zurück-Buttons links): Korrigieren auf ein Zurück links, kein Weiter (letzte Seite).

### #8 – "← Übersicht"-Link im Header
In ALLEN lab-*.html: Der Link "← Übersicht" bzw. "← Back" soll als Link **neben dem Logo im Header** sein.
Lab 01/02/04/06 als Referenz: Link ist Teil des Headers, nicht als separater Button irgendwo.
Lab 03 hat einen separaten Übersicht-Button neben DE/EN – diesen entfernen und durch Header-Link ersetzen (wie die anderen Labs).

### #9 – Lernziele-Heading-Farbe
In ALLEN lab-*.html: Die Überschrift des Lernziele-Abschnitts (`h3` oder ähnlich) auf `color: var(--primary)` bzw. `#DC2626` setzen.
Lab 04 hat sie schwarz – auf Rot ändern.

### #10 + #11 + #12 – coffee-app.html umbenennen und vereinheitlichen
1. Datei umbenennen: `coffee-app.html` → `lab-05-app.html`
2. Redirect anlegen: `coffee-app.html` neu erstellen mit:
   ```html
   <!DOCTYPE html><html><head><meta http-equiv="refresh" content="0;url=lab-05-app.html"><title>Redirect</title></head><body></body></html>
   ```
3. In `index.html`: Alle Links auf `coffee-app.html` → `lab-05-app.html` ändern
4. In `lab-05-usecase.html`: Alle Links auf `coffee-app.html` → `lab-05-app.html` ändern
5. In `lab-05-app.html`: Titel ändern zu `Lab 05 – Störungsmelder | INME Lab`

### #13 – Zurück-Navigation in lab-05-app.html
In `lab-05-app.html` (ehemals coffee-app.html):
Der App-Header hat eine schwarze Leiste. Dort gibt es bereits einen "←" Button links.
Stelle sicher, dass dieser Button auf `lab-05-usecase.html` zurückverlinkt (nicht nur History-Back).
Ergänze ggf. den Text: der Back-Pfeil soll beim Screen 0 (Home) auf `lab-05-usecase.html` zeigen.
Beim anderen Screens zeigt der Back-Pfeil weiter wie bisher (zur vorherigen App-Seite).

### #14 – Leerraum in lab-05-app.html (Screen 0)
In Screen 0 (Startseite der App) gibt es ca. 300px Leerraum.
Suche im `screen0`-DIV nach leeren divs oder übermäßigem padding/margin und entferne sie.
Der "Störung analysieren"-Button soll näher am Hero-Text sein.

### #15 – Zeitangabe-Position
In ALLEN lab-*.html: Das Zeit-Badge ("CA. 45 MIN", "CA. 90 MIN" etc.) soll immer neben dem Lab-Badge in der ersten Zeile stehen.
Lab 01 als Referenz. In Lab 06 steht es unter dem Titel – nach oben neben das Lab-Badge verschieben.
Lab 02 hat es unter den Lernzielen – gleichfalls nach oben neben Lab-Badge.

### #16 – Lernziele-Box vereinheitlichen
Alle Labs: Lernziele-Abschnitt soll gleiches Design haben:
- Hintergrund: leichtes Grau `#F9FAFB` oder `#F3F4F6`
- Border-left: 4px solid `#DC2626` (EN: `#F7CC00`)
- Überschrift: `color: #DC2626` (EN: `#F7CC00`)
- Kein border-radius

### #17 – Content-Breite vereinheitlichen
In `lab-03-gestaltung.html`: Die `.content`-Klasse oder `max-width` ist breiter als die anderen Labs.
Finde die `max-width` von lab-01 (wahrscheinlich 900px oder ähnlich) und setze dieselbe in lab-03.

### #18 – Jony Ive Zitat auf Englisch
In `index.html`: Das Zitat von Jonathan Ive ist auf Englisch.
Im DE-Modus: Füge unter dem englischen Zitat (in kleinerem Text, `color: #9ca3af`) hinzu:
"Originalzitat auf Englisch – Jonathan Ive, ehem. Chief Design Officer, Apple Inc."
Im EN-Modus: Nur die Quellenangabe ohne Sprachhinweis.

Das Zitat selbst NICHT übersetzen – es soll authentisch bleiben.

### #19 – EN-Farbschema
**KEINE ÄNDERUNG.** Dies ist eine bewusste Designentscheidung.
DE = Bauhaus Rot `#DC2626`, EN = Lamy Safari Mango `#F7CC00`. Dokumentiert.

### #20 – Zusammenfassung in Lab 02, 03, 06
In `lab-02-kreativitaet.html`, `lab-03-gestaltung.html`, `lab-06-implementation.html`:
Einen Zusammenfassungs-Abschnitt am Ende der React-App einfügen (vor den Footer-Nav-Buttons).
Orientiere dich an Lab 01 für das Format.

Inhalt der Zusammenfassungen:

**Lab 02 DE:**
- Titeltext: "Zusammenfassung"
- Punkte: "Design Thinking als menschenzentrierter Innovationsprozess", "5 Phasen: Empathize → Define → Ideate → Prototype → Test", "Kreativtechniken gezielt einsetzen: Brainstorming, SCAMPER, How Might We", "Divergentes und konvergentes Denken im Wechsel"

**Lab 02 EN:**
- Title: "Summary"  
- Points: "Design Thinking as human-centered innovation process", "5 phases: Empathize → Define → Ideate → Prototype → Test", "Using creativity techniques: Brainstorming, SCAMPER, How Might We", "Alternating divergent and convergent thinking"

**Lab 03 DE:**
- Titeltext: "Zusammenfassung"
- Punkte: "Bauhaus als bewusste Designentscheidung: Klarheit, Funktion, Wiederholbarkeit", "Farbe, Typografie und Komposition als visuelle Sprache", "CSS-Design-Systeme aus Bauhaus-Prinzipien ableiten", "Gestaltgesetze als Grundlage für intuitive UI"

**Lab 03 EN:**
- Title: "Summary"
- Points: "Bauhaus as deliberate design choice: clarity, function, repeatability", "Color, typography, and composition as visual language", "Deriving CSS design systems from Bauhaus principles", "Gestalt laws as foundation for intuitive UI"

**Lab 06 DE:**
- Titeltext: "Zusammenfassung"
- Punkte: "Supabase als serverloser Backend-as-a-Service für Echtzeitdaten", "CodePen als schnelle Prototyping-Plattform ohne Build-Tooling", "Gemini Vision API für KI-gestützte Bildanalyse", "Frontend-Backend-Integration ohne eigenen Server"

**Lab 06 EN:**
- Title: "Summary"
- Points: "Supabase as serverless Backend-as-a-Service for real-time data", "CodePen as rapid prototyping platform without build tooling", "Gemini Vision API for AI-powered image analysis", "Frontend-backend integration without own server"

### #21 – "Interaktive Medien"-Link in index.html
Im Header von `index.html` steht "INME Lab | Interaktive Medien".
"Interaktive Medien" ist vermutlich ein `<a>`-Tag oder Link.
Diesen Link entfernen oder zu reinem Text machen (kein `href` mehr).

### #22 – Semester dynamisch
In `index.html`: "Sommersemester 2026" als Konstante/Variable am Anfang des Scripts auslagern:
```js
const SEMESTER = 'Sommersemester 2026'; // ← hier ändern
```
Und im JSX: `{SEMESTER}` verwenden statt dem hardcodierten String.

### #23 – Footer auf Lab-Seiten
In ALLEN lab-*.html: Nach den Navigationsbuttons (ganz am Ende) einen minimalen Footer einfügen:

```jsx
<footer style={{borderTop:'1px solid #e5e7eb', marginTop:'3rem', padding:'1.5rem 0', textAlign:'center', fontSize:'0.8rem', color:'#9ca3af'}}>
  INME Lab · THWS Business School · Prof. Dr. Robert Butscher
</footer>
```

WICHTIG: Dieser Footer kommt NACH den Navigationsbuttons.

---

## Wichtige Hinweise

1. **EN-Overrides nicht vergessen:** Für jede Farbänderung (rot→mango) einen `[data-lang="en"]` CSS-Override hinzufügen
2. **data-lang Attribut:** Jede Lab-Seite hat `data-lang={lang}` auf dem Root-Div – voraussetzen, dass es existiert
3. **Keine Gradienten** hinzufügen
4. **Kein border-radius** auf neuen Cards/Buttons
5. **Kein npm/build** – nur CDN
6. **Nach allen Änderungen:** `git add -A && git commit -m "fix: design review #1-23 – consistency pass" && git push origin main`
7. Nach dem Commit: `openclaw system event --text "Done: Design-Review alle 23 Punkte umgesetzt, committed + gepusht" --mode now`

## Arbeitsweise

- Lies jede Datei sorgfältig bevor du sie änderst
- Ändere immer DE und EN gleichzeitig
- Prüfe nach jeder Datei ob die Änderung syntaktisch korrekt ist
- Committe am Ende EINMAL mit allem zusammen
