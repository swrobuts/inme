# INME Lab Companion Site Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build a complete 7-file GitHub Pages companion site for the INME course at THWS with Bauhaus design, bilingual DE/EN content, and a working CodePen app for a coffee machine trouble-shooter.

**Architecture:** Pure static HTML5 files, each self-contained with React 18 + Babel + Tailwind via CDN. Shared design system via inline CSS. No build tools, no npm. Each lab page has a fixed sidebar, fixed header, bilingual toggle, quiz, and code blocks with copy buttons.

**Tech Stack:** HTML5, React 18 (CDN), Babel standalone (CDN), Tailwind CSS (CDN), Google Fonts (Space Grotesk), Supabase JS (CDN for lab-06)

---

## Shared Design System (reference for ALL files)

```css
/* Colors */
--primary: #B91C1C;
--accent: #F59E0B;
--dark: #1A1A1A;
--light-bg: #FAFAFA;
--primary-light: rgba(185,28,28,0.08);

/* Bauhaus card: border:2px solid #1A1A1A; border-radius:0 */
/* bauhaus-accent-line: 48px wide, 4px tall, background accent */
/* bauhaus-badge: dark bg, white text, uppercase, letter-spacing, border-radius:0 */
```

### Reusable HTML snippets (copy into each lab page):

**Header (fixed):**
```html
<header style="position:fixed;top:0;left:0;right:0;height:56px;background:#fff;border-bottom:2px solid #1A1A1A;display:flex;align-items:center;justify-content:space-between;padding:0 1.5rem;z-index:100;">
  <div style="display:flex;align-items:center;gap:1rem;">
    <span style="font-family:'Space Grotesk',sans-serif;font-weight:800;font-size:1.1rem;color:#B91C1C;">INME Lab</span>
    <a href="index.html" style="font-size:0.8rem;color:#666;text-decoration:none;">← Übersicht</a>
  </div>
  <div id="langToggle"></div>
</header>
```

**Sidebar (fixed, 260px):**
```html
<nav id="sidebar" style="position:fixed;top:56px;left:0;width:260px;height:calc(100vh - 56px);overflow-y:auto;background:#fff;border-right:2px solid #1A1A1A;padding:1.5rem 0;">
  <!-- anchor links injected by React -->
</nav>
```

**Main content:** `margin-left:260px; padding-top:56px;`

---

### Task 1: index.html (Landing Page)

**File:** Create `/tmp/inme-lab/index.html`

**Requirements:**
- React 18 + Babel standalone via CDN (no build)
- Hero: dark background, animated geometric bauhaus shapes (subtle red circle + yellow square), white title "INME Lab", subtitle, course badges, 2 CTAs
- Stats bar: 4 stats on white strip
- Lab grid: 6 cards (3x2), each with red left border, lab number, title, description, link
- Use Case teaser: full-width dark section with coffee machine image
- Footer: dark bg, white text
- Bilingual DE/EN toggle (useState)
- Responsive

**Step 1: Create the file**

Full structure:
```html
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>INME Lab – Interaktive Medien</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700;800&display=swap" rel="stylesheet">
  <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  <style>
    /* ... full CSS ... */
  </style>
</head>
<body>
  <div id="root"></div>
  <script type="text/babel">/* full React component */</script>
</body>
</html>
```

**Step 2: Commit**
```bash
cd /tmp/inme-lab && git add index.html && git commit -m "feat: add index.html landing page"
```

---

### Task 2: lab-01-grundlagen.html

**File:** Create `/tmp/inme-lab/lab-01-grundlagen.html`

**Sections (sidebar anchors):**
1. `#ueberblick` – Überblick
2. `#definition` – Was sind interaktive Medien?
3. `#kategorisierung` – Kategorisierung
4. `#eigenschaften` – Eigenschaften
5. `#relevanz` – Relevanz & Anwendungsgebiete
6. `#technologien` – Technologien
7. `#quiz` – Quiz (5 Fragen)
8. `#zusammenfassung` – Zusammenfassung

**Quiz questions (bilingual):**
1. Was ist ein zentrales Merkmal interaktiver Medien? → A) Bidirektionale Kommunikation ✓ B) Einweg-Übertragung C) Analoges Signal D) Lineares Narrativ
2. Welche Medienart zählt zu den interaktiven Medien? → A) Zeitung B) Fitness-App ✓ C) Radio D) Fernsehen
3. Was unterscheidet Web 2.0 von Web 1.0? → A) Schnelleres Internet B) Nutzer als Prosumenten ✓ C) Mehr Bilder D) HTTPS
4. Welche Technologie ermöglicht Echtzeit-Interaktivität? → A) HTML B) CSS C) JavaScript ✓ D) XML
5. Was ist Tim Berners-Lees Vision des maschinell interpretierbaren Webs? → A) Web 4.0 B) Dark Web C) Semantic Web ✓ D) Deep Web

**Step 1: Create the file** (full React component with sidebar, header, content, quiz)
**Step 2: Commit:** `git commit -m "feat: add lab-01 Grundlagen"`

---

### Task 3: lab-02-kreativitaet.html

**File:** Create `/tmp/inme-lab/lab-02-kreativitaet.html`

**Sections:**
1. `#ueberblick`
2. `#design-thinking` – Die 5 Phasen
3. `#empathize` – mit Empathy Map Übung
4. `#define` – HMW-Fragen
5. `#ideate` – Brainstorming-Methoden
6. `#prototype` – Lo-Fi vs Hi-Fi
7. `#test` – Usability Testing
8. `#uebung` – Use Case starten
9. `#quiz`
10. `#figma` – Figma Quickstart

**Quiz questions:**
1. Welche Phase kommt nach "Empathize"? → Define ✓
2. Ziel der Ideate-Phase? → Möglichst viele Ideen ohne Bewertung ✓
3. Was ist ein HMW-Statement? → Frage die Problem in Designchance verwandelt ✓
4. Was bedeutet "Fail fast"? → Frühes Scheitern als Lernmöglichkeit ✓
5. Lo-Fi vs Hi-Fi? → Lo-Fi=Papier/grob, Hi-Fi=Figma/detailliert ✓

**Step 1: Create the file**
**Step 2: Commit:** `git commit -m "feat: add lab-02 Kreativitaet"`

---

### Task 4: lab-03-gestaltung.html

**File:** Create `/tmp/inme-lab/lab-03-gestaltung.html`

**Sections:**
1. `#ueberblick`
2. `#bauhaus` – Geschichte + Prinzipien
3. `#farblehre` – Farbkreis + Psychologie + CSS Code
4. `#typografie` – Kategorien + Hierarchie
5. `#layout` – Grid + 8px-System
6. `#gestaltgesetze` – Nähe, Ähnlichkeit, etc.
7. `#usability` – Norman's Principles
8. `#app-design` – Bauhaus auf unsere App
9. `#quiz`
10. `#uebung` – CodePen Übung

**CSS code example to include (copyable):**
```css
:root {
  --primary: #B91C1C;
  --warning: #F59E0B;
  --success: #16A34A;
  --neutral: #1A1A1A;
  --bg: #FAFAFA;
}
```

**Quiz questions:**
1. Was ist das Bauhaus-Credo? → Form follows function ✓
2. Was sind Komplementärfarben? → Gegenüberliegende Farben im Farbkreis ✓
3. Was ist das 8px-System? → Alle Abstände sind Vielfache von 8px ✓
4. Was ist "Affordance" nach Norman? → Wahrgenommene Verwendungsmöglichkeit ✓
5. Welche Farbe steht für Fehler in unserem System? → Rot #B91C1C ✓

**Step 1: Create the file**
**Step 2: Commit:** `git commit -m "feat: add lab-03 Gestaltung"`

---

### Task 5: lab-04-ux.html

**File:** Create `/tmp/inme-lab/lab-04-ux.html`

**Sections:**
1. `#ueberblick`
2. `#ux-vs-ui`
3. `#user-research`
4. `#personas` – Thomas, 34, Wartungstechniker
5. `#user-journey`
6. `#user-stories` – 5 stories
7. `#ia` – Information Architecture
8. `#wireframes` – ASCII wireframe
9. `#figma` – Figma Quickstart Anleitung
10. `#quiz`
11. `#ressourcen`

**ASCII Wireframe to include:**
```
┌─────────────────────┐
│  ◀  Störung melden  │
│─────────────────────│
│  ┌───────────────┐  │
│  │  📷 FOTO     │  │
│  │  aufnehmen   │  │
│  └───────────────┘  │
│  Maschinentyp:      │
│  [▼ Jura E8      ] │
│  Symptome:          │
│  ☐ Kein Kaffee     │
│  ☐ Fehlermeldung   │
│  ☐ Wasserleck      │
│  ☐ Geräusche       │
│  [Diagnose starten] │
└─────────────────────┘
```

**Quiz questions:**
1. Was ist der Unterschied UX vs UI? → UX=wie es funktioniert, UI=wie es aussieht ✓
2. Was ist eine Persona? → Fiktive Repräsentation eines Nutzersegments ✓
3. Was zeigt eine User Journey Map? → Alle Schritte + Emotionen eines Nutzers bei einer Aufgabe ✓
4. Format einer User Story? → Als [Rolle] möchte ich [Aktion], damit [Nutzen] ✓
5. Was ist Information Architecture? → Struktur und Organisation von Inhalten ✓

**Step 1: Create the file**
**Step 2: Commit:** `git commit -m "feat: add lab-04 UX"`

---

### Task 6: lab-05-usecase.html

**File:** Create `/tmp/inme-lab/lab-05-usecase.html`

**Sections:**
1. `#ueberblick` – Use Case Beschreibung
2. `#empathize` – Persona Thomas + Empathy Map + Störungsbilder
3. `#define` – Problem Statement + HMW-Fragen
4. `#ideate` – Crazy 8s Ergebnis (8 Ideen)
5. `#prototype-lofi` – Papier-Wireframe (ASCII)
6. `#prototype-hifi-design` – Bauhaus-Designentscheidungen
7. `#prototype-figma` – Figma Screens Beschreibung
8. `#zusammenfassung` – Ready for Implementation
9. `#quiz`

**10 Störungen to include:**
1. E4/E5 – Entkalkung nötig
2. Mahlwerk mahlt nicht
3. Kein Kaffee-Fluss
4. Dampflanze defekt
5. Wassertank-Sensor
6. Kaffeesatz-Behälter voll
7. Maschine startet nicht
8. Kaffeepulver in Tasse
9. Ungewöhnliche Geräusche
10. Display tot

**Image usage:** `<img src="images/stoerung-kalk.jpg">` and `<img src="images/stoerung-mahlwerk.jpg">`

**Quiz questions:**
1. Was ist der erste Schritt im Design Thinking? → Empathize ✓
2. Was ist ein Problem Statement? → Konkrete Formulierung des Kernproblems ✓
3. Was ist Crazy 8s? → 8 Ideen in 8 Minuten skizzieren ✓
4. Warum Bauhaus Rot für Fehlermeldungen? → Starker Kontrast, universell als Warnung verstanden ✓
5. Wie viele Screens hat der Prototyp? → 4 ✓

**Step 1: Create the file**
**Step 2: Commit:** `git commit -m "feat: add lab-05 Use Case"`

---

### Task 7: lab-06-implementation.html

**File:** Create `/tmp/inme-lab/lab-06-implementation.html`

**Sections:**
1. `#ueberblick`
2. `#tech-stack`
3. `#supabase-setup` – Step-by-step with screenshots description
4. `#datenbank` – Full SQL schema (copyable)
5. `#app-html` – Full HTML code for CodePen (copyable)
6. `#app-css` – Full CSS code for CodePen (copyable)
7. `#app-js` – Full JS code for CodePen (copyable)
8. `#codepen-anleitung` – Step-by-step testing guide
9. `#erweiterungen` – Advanced ideas
10. `#quiz`

**Full SQL schema (include complete, copyable):**
```sql
CREATE TABLE stoerungen (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  maschinentyp TEXT NOT NULL,
  fehlercode TEXT,
  symptome TEXT[],
  beschreibung TEXT,
  diagnose TEXT,
  status TEXT DEFAULT 'offen' CHECK (status IN ('offen', 'in_bearbeitung', 'geloest')),
  loesung TEXT
);
-- + ersatzteile, bestellungen, bestellpositionen tables
-- + INSERT demo data (6 ersatzteile)
```

**Full CodePen JS (include complete with DIAGNOSE_REGELN, screen management, Supabase calls):**
- SUPABASE_URL and ANON_KEY as clear placeholders
- Offline fallback with demo data
- 4 screens: Störung erfassen → Diagnose → Shop → Bestellung
- German comments with === separators

**Quiz questions:**
1. Was ist Supabase? → Open-source Firebase-Alternative (BaaS) ✓
2. Was macht gen_random_uuid()? → Generiert eine zufällige UUID ✓
3. Was ist ein Foreign Key? → Verweis auf Primärschlüssel einer anderen Tabelle ✓
4. Was ist der anon key in Supabase? → Öffentlicher API-Schlüssel für Lesezugriff ✓
5. Was ist navigator.mediaDevices? → Web API für Kamera-/Mikrofon-Zugriff ✓

**Step 1: Create the file**
**Step 2: Commit:** `git commit -m "feat: add lab-06 Implementation"`

---

### Task 8: Final commit & push

**Step 1: Final git operations**
```bash
cd /tmp/inme-lab
git add .
git status
git push origin main
```

**Step 2: Trigger openclaw notification**
```bash
OPENCLAW_CONFIG_PATH=/Users/robert/clawd/.openclaw-macbot/openclaw.json \
OPENCLAW_STATE_DIR=/Users/robert/clawd/.openclaw-macbot \
openclaw system event --text "✅ INME Lab fertig! 6 Labs + Use Case + CodePen App gebaut. Repo: swrobuts/inme. Bitte git push prüfen und GitHub Pages aktivieren." --mode now
```

---

## Notes for implementors

- Each HTML file is a **complete, self-contained** React 18 + Babel app
- Every page includes: Google Fonts, React/ReactDOM/Babel CDNs
- Bilingual: `const [lang, setLang] = useState('de')` + `const t = { de: {...}, en: {...} }`
- Quiz component: 4 options per question, green correct / red wrong reveal on click
- Code blocks: dark bg, yellow left border, copy button that shows "Copied!" feedback
- Sidebar: `position:fixed; top:56px; left:0; width:260px` – hidden on mobile (`@media (max-width: 768px)`)
- Main content: `margin-left:260px; padding-top:56px` – full width on mobile
- bauhaus aesthetic: NO border-radius on cards/buttons (hardcoded 0)
- Images in `images/` dir: stoerung-kalk.jpg, stoerung-mahlwerk.jpg
