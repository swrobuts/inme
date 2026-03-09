# Design Review – Umsetzungsbrief

**Alle Dateien:** `/tmp/inme-lab/lab-01-grundlagen.html`, `lab-02-kreativitaet.html`, `lab-03-gestaltung.html`, `lab-04-ux.html`, `lab-05-usecase.html`, `lab-06-implementation.html`, `coffee-app.html`, `index.html`

Nach allen Änderungen: `cd /tmp/inme-lab && git add -A && git commit -m "fix: design review – 23-point consistency audit" && git push origin main`

---

## #1 – Title-Tags vereinheitlichen

Zielformat: `Lab 0X – Titel | INME Lab`

Setze exakt:
- lab-01: `<title>Lab 01 – Grundlagen Interaktiver Medien | INME Lab</title>`
- lab-02: `<title>Lab 02 – Kreativtechniken &amp; Design Thinking | INME Lab</title>`
- lab-03: `<title>Lab 03 – Gestaltungsprinzipien &amp; Bauhaus | INME Lab</title>`
- lab-04: `<title>Lab 04 – UX Research &amp; Prototyping | INME Lab</title>`
- lab-05: `<title>Lab 05 – Use Case: Kaffeevollautomat | INME Lab</title>`
- lab-06: `<title>Lab 06 – Implementation: Supabase + CodePen | INME Lab</title>`
- coffee-app: `<title>Lab 05 – Kaffeevollautomat-Störungsmelder | INME Lab</title>`

---

## #2 – Sidebar-Labels vereinheitlichen

In allen 6 Lab-Dateien: Die Sidebar-Überschrift (das Label über den Nav-Links) muss überall `NAVIGATION` heißen (DE) und `NAVIGATION` (EN) – prüfe die translations-Objekte auf `navLabel` oder ähnliche Keys und setze alle auf `NAVIGATION`.

---

## #3 – Hero-Header: lab-05-usecase.html

In `lab-05-usecase.html` gibt es einen roten Hero-Header (`hero-section`-Klasse). Alle anderen Labs haben keinen Hero. Entferne den Hero aus lab-05-usecase.html – der Seitenaufbau soll wie Lab 01/04/06 aussehen: direkt mit Header + Sidebar + Content, ohne farbigen Intro-Block.

---

## #4 – Seitentitel Lab 03 rot

In `lab-03-gestaltung.html`: Der Hauptseitentitel (h1 oder prominente Überschrift über dem Content, falls vorhanden) soll rot sein wie bei den anderen Labs. Prüfe ob es eine `.page-title` oder ähnliche Klasse gibt, die schwarz ist, und setze sie auf `color: var(--primary)` oder `#B91C1C`.

---

## #5+#6 – Quiz-Format vereinheitlichen

In allen Quiz-Sections aller 6 Labs:
- Fragen-Nummern: immer `Q1`, `Q2`, `Q3` ... (nicht `F1.`, `1.`, `5.` etc.)
- Antwort-Prefixe: immer `A)`, `B)`, `C)`, `D)` vor jeder Antwortoption
- Such nach `num: '1.'`, `num: '1'`, `num: 'F1.'` und ersetze durch `num: 'Q1'` etc.
- Such nach Antwortoptionen die kein Label-Prefix haben (z.B. `{ text: 'Bidirektionale...' }`) und füge `label: 'A)'` hinzu wenn es fehlt. In Lab 06 fehlen die A/B/C/D Prefixe besonders.

---

## #7 – Footer-Navigation einheitlich

In allen 6 Labs: Footer-Navigationsbereich mit Prev/Next-Buttons.
- Layout: `display: flex; justify-content: space-between`
- Links: `← Zurück zur Übersicht` oder `← Lab 0X` (bleibt wie es ist, aber LEFT-aligned)
- Rechts: `Weiter: Lab 0X →` (RIGHT-aligned)
- Beide in EINEM Flex-Container mit `justify-content: space-between`
- Lab 04 hat beide Buttons links → fixe auf space-between
- Lab 06 hat zwei Zurück-Buttons → entferne Duplikat, behalte sinnvolles Paar

---

## #8 – Übersicht-Link im Header

In allen 6 Labs: Der `← Übersicht`-Link soll einheitlich im Header links vom Logo stehen (wie Lab 01).
In `lab-03-gestaltung.html` gibt es einen separaten Button oben rechts – entferne diesen und stelle sicher dass `← Übersicht` im Header ist (wie alle anderen Labs).

---

## #9 – Lernziele Heading-Farbe

In allen Labs: Der `<h3>` oder Heading "Lernziele" (bzw. "Learning Objectives" in EN) soll `color: #B91C1C` haben. In Lab 04 ist er schwarz – setze auf rot.

---

## #10 – coffee-app.html: Redirect einrichten

Erstelle `/tmp/inme-lab/coffee-app.html` als HTML-Redirect zu `lab-05-usecase.html`:

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta http-equiv="refresh" content="0; url=lab-05-usecase.html">
<title>Redirect – INME Lab</title>
</head>
<body><a href="lab-05-usecase.html">Weiter zu Lab 05 →</a></body>
</html>
```

WICHTIG: Die echte App-Datei bleibt `lab-05-usecase.html` – coffee-app.html redirectet nur.
Warte: `lab-05-usecase.html` existiert bereits als die Lab-Begleitseite (Theorie). Die App selbst ist `coffee-app.html`.

Daher neue Lösung: Behalte `coffee-app.html` als App. Ändere nur den Titel (bereits #11). Kein Umbenennen nötig.

---

## #11+#12 – coffee-app.html Naming

- Titel: bereits als `<title>Lab 05 – Kaffeevollautomat-Störungsmelder | INME Lab</title>` in #1 definiert ✓
- Im Header der App (`.header-title`): Ändere "Service App" zu "Störungsmelder"
- Im Header der App (`.header-subtitle`): Ändere "Frisia × THWS" zu "Lab 05 · INME"

---

## #13 – Zurück-Navigation in coffee-app.html

Füge in `coffee-app.html` im Header-Bereich (`.header-right`) einen dezenten Link ein:
```html
<a href="lab-05-usecase.html" style="font-size:0.72rem;color:var(--gray-500);text-decoration:none;letter-spacing:0.06em;text-transform:uppercase;">← Lab 05</a>
```

---

## #14 – Leerraum in coffee-app.html Home-Screen

In Screen 0 (`.screen#screen0`): Entferne überflüssigen `margin-top` oder leere `<div style="margin-top: ...px">` Abstände zwischen Beschreibungstext und CTA-Button. Der Abstand soll max. 2rem sein.

---

## #15 – Zeitangabe-Position

In allen Labs: Die Zeitangabe ("ca. 45 Min", "ca. 90 Min") soll als Badge **neben** dem Lab-Nummern-Badge stehen (erste Zeile), nicht darunter oder woanders. Prüfe lab-02 und lab-06 ob das schon stimmt, korrigiere falls nötig.

---

## #17 – Content-Breite Lab 03

In `lab-03-gestaltung.html`: Das `.main-content` oder der Content-Bereich hat eine andere (breitere) `max-width` als die anderen Labs. Setze die `max-width` auf denselben Wert wie Lab 01 (schaue nach `.main-content { max-width: ... }` in lab-01 und setze lab-03 identisch).

---

## #18 – Zitat-Sprache index.html

Das Jony Ive Zitat auf der Startseite ist immer auf Englisch. Im DE-Modus füge oberhalb des englischen Zitats eine deutsche Übersetzung als primären Text ein, und das englische Original darunter in kleinerer Schrift als Quellenangabe:

DE-Version:
```
„Ich glaube, es gibt eine tiefe und beständige Schönheit in der Einfachheit; in der Klarheit, in der Effizienz. Wahre Einfachheit ist weit mehr als nur die Abwesenheit von Unordnung und Ornament. Es geht darum, Ordnung in die Komplexität zu bringen."
— Jonathan Ive
```
(Original in klein darunter: *"I think there is a profound..."*)

EN-Version: nur das englische Original (bleibt wie es ist).

Passe das translations-Objekt in index.html für `quoteBody` (DE) und `quoteBodyEn` an.

---

## #20 – Zusammenfassung in Lab 02, 03, 06

In `lab-02-kreativitaet.html`, `lab-03-gestaltung.html`, `lab-06-implementation.html`: Füge am Ende des Inhalts (vor den Footer-Nav-Buttons) je eine kurze Zusammenfassungs-Section ein. Format wie Lab 01:

```jsx
<section id="zusammenfassung" className="section">
  <h2>Zusammenfassung</h2>  // EN: Summary
  <div className="bauhaus-accent-line" />
  <ul className="summary-list">
    <li>...</li>  // 4-5 Kernpunkte
  </ul>
  ...nav-buttons...
</section>
```

Für Lab 02: Kernpunkte = Design Thinking (Empathize–Define–Ideate–Prototype–Test), HMW-Fragen, Kreativtechniken
Für Lab 03: Kernpunkte = Bauhaus-Prinzipien, Farbe/Typo/Grid/Gestaltgesetze, Bauhaus als bewusste Wahl
Für Lab 06: Kernpunkte = Supabase-Schema, CodePen-Workflow, Gemini API, Von Mock zu Live

Füge auch den Sidebar-Nav-Link `{ href: '#zusammenfassung', label: 'Zusammenfassung' }` zu diesen Labs hinzu.

---

## #21 – "Interaktive Medien" Nav-Link index.html

In `index.html` im Header: Der Text "Interaktive Medien" neben "INME Lab" soll kein `<a href>` sein sondern ein `<span>` (nicht klickbar).

---

## #23 – Footer auf Lab-Seiten

In allen 6 Lab-Dateien: Füge am absoluten Ende (nach allen Sections, nach den Nav-Buttons) einen minimalen Footer ein:

```html
<footer style="text-align:center;padding:1.5rem;font-size:0.75rem;color:#9CA3AF;border-top:1px solid #F3F4F6;margin-top:2rem;">
  THWS Business School · INME · Prof. Dr. Robert Butscher · 2026
</footer>
```

---

## #19 – EN-Farbschema: bewusste Entscheidung

Dies ist eine **bewusste Designentscheidung** (DE=Rot, EN=Mango-Gelb). Keine Änderung nötig. Dokumentiere dies als Kommentar in `index.html`:
```html
<!-- Bewusste Designentscheidung: DE=Rot #DC2626, EN=Mango #F7CC00 (Sprachumschalter = Farbschema-Wechsel) -->
```

---

## Commit am Ende

```bash
cd /tmp/inme-lab && git add -A && git commit -m "fix: design review – 23-point consistency audit (titles, quiz format, footer nav, colors, redirects, summary sections)" && git push origin main
```

Dann:
```bash
OPENCLAW_CONFIG_PATH=/Users/robert/clawd/.openclaw-macbot/openclaw.json OPENCLAW_STATE_DIR=/Users/robert/clawd/.openclaw-macbot openclaw system event --text "Design-Review fertig: 23 Punkte abgearbeitet, gepusht" --mode now
```
