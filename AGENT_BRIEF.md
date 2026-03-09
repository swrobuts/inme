# AGENT BRIEF: INME Lab – Interaktive Medien Companion Site

## Auftrag
Erstelle eine vollständige GitHub Pages Companion-Website für den Kurs "Interaktive Medien (INME)" an der THWS Business School (Bachelor Medienmanagement). Die Site folgt exakt dem bewährten Muster der DAV Lab Site, aber mit eigenem Design.

## Repo & Deployment
- Repo: `/tmp/inme-lab/` (git clone von swrobuts/inme)
- GitHub Pages: `https://swrobuts.github.io/inme/`
- Stack: React 18 + Babel + Tailwind CSS (alle via CDN, KEIN Build-Tool, kein npm)

## Design System

### Farben
```css
--primary: #B91C1C;      /* Bauhaus Rot – Primary */
--accent: #F59E0B;       /* Bauhaus Gelb – Accent */
--dark: #1A1A1A;         /* Fast-Schwarz */
--light-bg: #FAFAFA;     /* Seitenhintergrund */
--primary-light: rgba(185, 28, 28, 0.08);  /* Subtle backgrounds */
```

### Typografie
- Headings: `'Space Grotesk', sans-serif` (von Google Fonts – Bauhaus-nah, geometrisch)
- Body: System Font Stack (`-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`)
- Google Fonts Import: `https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700;800&display=swap`
- h2: color: var(--primary), font-weight: 800, font-family: Space Grotesk
- h3: color: var(--primary), font-weight: 700

### Geometrische Bauhaus-Elemente (CSS)
```css
/* Bauhaus-typisch: harte Kanten, kein border-radius, starke Kontraste */
.bauhaus-card { border: 2px solid #1A1A1A; border-radius: 0; }
.bauhaus-accent-line { width: 48px; height: 4px; background: var(--accent); margin: 0.5rem 0 1rem 0; }
.bauhaus-badge { background: var(--dark); color: white; padding: 0.2rem 0.7rem; font-size: 0.7rem; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; border-radius: 0; }
```

### Wiederverwendbare Komponenten (wie DAV Lab)
- `.code-block` – dunkel, `border-left: 4px solid var(--accent)`
- `.copy-btn` – wie DAV Lab
- `.tip-box` – `border-left: 4px solid #F59E0B; background: #fffbeb`
- `.challenge-box` – `border-left: 4px solid #22c55e; background: #f0fdf4`
- `.info-box` – `border-left: 4px solid #3b82f6; background: #eff6ff`
- `.concept-box` – `border-left: 4px solid var(--primary); background: var(--primary-light)`
- `.quiz-option` – interaktive Multiple-Choice Buttons
- `.lang-btn` – DE/EN Toggle (orange active state)

## Dateistruktur
```
/tmp/inme-lab/
├── index.html              ← Landing Page
├── lab-01-grundlagen.html  ← Grundlagen Interaktiver Medien
├── lab-02-kreativitaet.html ← Kreativtechniken & Design Thinking
├── lab-03-gestaltung.html  ← Gestaltungsprinzipien & Bauhaus
├── lab-04-ux.html          ← UX Research & Prototyping (Figma)
├── lab-05-usecase.html     ← Use Case: Von der Idee zum Prototyp
├── lab-06-implementation.html ← Implementierung: Supabase + CodePen
└── images/
    └── (bereits generierte Bilder)
```

## Sprachunterstützung
- Exakt wie DAV Lab: `const [lang, setLang] = useState('de')`
- Toggle-Button oben rechts: `DE | EN`
- Alle Texte in `const t = { de: {...}, en: {...} }` Objekt
- Alle UI-Strings, Sektions-Titel, Erklärungen, Quiz-Fragen – ALLES bilingual

## Sidebar-Navigation (auf Lab-Seiten)
Wie DAV Lab: Feste linke Sidebar mit Sprung-Ankern, `position: fixed`, Mobile: ausgeblendet, main-content hat `margin-left: 260px`.

## Header (auf Lab-Seiten)
`position: fixed; top: 0;` – Links: Brand + Back-Link, Rechts: Lang-Toggle

---

## SEITE 1: index.html (Landing Page)

### Hero Section
- Hintergrund: `#1A1A1A` (schwarz, Bauhaus)
- Geometrisches Muster als animierter Background (rote und gelbe Kreise, sehr subtil)
- Großer weißer Titel: "INME Lab" + "Interaktive Medien"
- Untertitel (weiß): "Companion Site für den Kurs INME · THWS Business School"
- Kurs-Badges (outlined, weiß): "Bachelor Medienmanagement" | "Sommersemester 2026" | "Prof. Dr. Robert Butscher"
- Zwei CTA-Buttons: "Zu den Labs →" (rot gefüllt) | "GitHub →" (outlined weiß)
- Bauhaus-Geometrie: ein roter Kreis und ein gelbes Quadrat als dekorative Elemente (absolute-positioned, semi-transparent)

### Stats Bar
Wie DAV: 4 Stats in weißem Strip
- `6 Labs` | `1 Use Case` | `Supabase + CodePen` | `DE / EN`

### Lab Overview Grid
6 Cards (3x2 Grid), jede mit:
- Roter linker Rand-Linie (Bauhaus-typisch)
- Labor-Nummer (groß, bold, rot, Hintergrund)
- Titel auf Deutsch + Englisch
- Kurze Beschreibung
- Emoji + Link-Button "Zum Lab →"

Lab Cards:
1. 🎯 "Grundlagen Interaktiver Medien" – Was sind interaktive Medien? Kategorien, Eigenschaften, Relevanz.
2. 💡 "Kreativtechniken & Design Thinking" – Empathize, Define, Ideate, Prototype, Test. Brainstorming, HMW.
3. 🎨 "Gestaltungsprinzipien & Bauhaus" – Farblehre, Typografie, Grid, Bauhaus-Design-Regeln.
4. 👥 "UX Research & Prototyping" – Personas, User Journey, Wireframes, Figma-Intro.
5. ☕ "Use Case: Kaffeevollautomat" – Von der Idee bis zum Prototyp. Design Thinking in der Praxis.
6. 🛠️ "Implementierung: Supabase + CodePen" – Vom Mockup zur lauffähigen Web-App.

### Use Case Teaser (volle Breite)
- Schwarzer Hintergrund
- Links: Bild der Kaffeemaschine (images/stoerung-kalk.jpg oder ähnliches, wenn verfügbar)
- Rechts: "Der Use Case: Kaffeevollautomat-Störungsmelder"
- Beschreibung: "Von der Erstidee bis zur lauffähigen Web-App – schrittweise entwickelt nach dem Design Thinking Prozess. Bauhaus-Gestaltungsprinzipien als roter Faden."

### Footer
Schwarz, weiße Schrift – "THWS Business School · INME · Prof. Dr. Robert Butscher · 2026"

---

## SEITE 2: lab-01-grundlagen.html

### Sektionen (Sidebar + Content)
1. **Überblick** – Was erwartet mich in Lab 1?
2. **Was sind interaktive Medien?** – Definition nach Malaka, Eigenschaften (bidirektional, dynamisch, personalisiert), Abgrenzung zu passiven Medien. Beispiele (Apps, Spiele, VR-Systeme, Datenjournalismus-Tools).
3. **Kategorisierung** – Datenträger, Kanäle, Systeme/Dienste. Interaktive vs. Massenmedien.
4. **Eigenschaften interaktiver Medien** – Interaktivität, Multimedia, Vernetzung, Personalisierung, Echtzeit. Jeweils mit kurzer Erklärung.
5. **Relevanz & Anwendungsgebiete** – Datenjournalismus, UX Design, E-Learning, Industrie 4.0, Smart Home, etc.
6. **Technologien im Überblick** – HTML/CSS/JS, React/Angular, Mobile (iOS/Android), Cloud, KI/ML. Brief overview, kein Deep-Dive (kommt später).
7. **Quiz** – 5 Fragen zu den Grundlagen
8. **Zusammenfassung** – Key Takeaways

### Quiz-Fragen (bilingual):
1. Was ist ein zentrales Merkmal interaktiver Medien? → Bidirektionale Kommunikation (Nutzer kann aktiv eingreifen)
2. Welche Medienart zählt zu den interaktiven Medien? → Eine Fitness-App mit personalisierten Trainingsplänen
3. Was unterscheidet Web 2.0 von Web 1.0? → Nutzer sind Produzenten und Konsumenten ("Prosumenten")
4. Welche Technologie ermöglicht Echtzeit-Interaktivität im Web? → JavaScript
5. Welches Konzept beschreibt Tim Berners-Lees Vision des maschinell interpretierbaren Webs? → Semantic Web / Web 3.0

---

## SEITE 3: lab-02-kreativitaet.html

### Sektionen
1. **Überblick** – Design Thinking als roter Faden durch alle Labs
2. **Design Thinking** – Die 5 Phasen: Empathize, Define, Ideate, Prototype, Test. Jede Phase mit Beschreibung, Ziel, Methoden.
3. **Empathize** – User Research, Interviews, Beobachtung, Empathy Maps. Übung: Empathy Map für Kaffeemaschinen-Nutzer erstellen.
4. **Define** – Problem Statement, "How Might We"-Fragen, Point of View. Übung: HMW für Kaffeemaschinen-Störungen.
5. **Ideate** – Brainstorming, Brainwriting 6-3-5, SCAMPER, Crazy 8s. Übung: 8 Lösungsideen in 8 Minuten für die Störungsmelder-App.
6. **Prototype** – Papierprototypen, digitale Wireframes, Low-Fi vs Hi-Fi. Einführung in Figma.
7. **Test** – Usability-Tests, Feedback-Methoden, Iterieren. "Fail fast to succeed sooner."
8. **Übung: Use Case starten** – Step-by-Step: Persona für den Kaffeemaschinen-Techniker erstellen. Vorlage in Markdown/Figma.
9. **Quiz** – 5 Fragen zu Design Thinking
10. **Figma-Quickstart** – Embedded Figma-Link oder Beschreibung + Screenshot

### Quiz-Fragen:
1. Welche Phase kommt im Design Thinking nach "Empathize"? → Define
2. Was ist das Ziel der "Ideate"-Phase? → Möglichst viele kreative Ideen generieren ohne Bewertung
3. Was ist ein "How Might We"-Statement? → Eine Frage, die ein Problem in eine Designchance verwandelt
4. Was bedeutet "Fail fast to succeed sooner"? → Frühes Scheitern als Lernmöglichkeit nutzen
5. Was ist der Unterschied zwischen Lo-Fi und Hi-Fi Prototypen? → Lo-Fi: grob/schnell (Papier); Hi-Fi: detailliert/realistisch (Figma)

---

## SEITE 4: lab-03-gestaltung.html

### Sektionen
1. **Überblick** – Warum Gestaltung? "Form follows function" (Bauhaus-Credo)
2. **Das Bauhaus** – Geschichte (1919 Weimar, Walter Gropius), Philosophie, Einfluss auf modernes Design. Kernprinzipien: Geometrisch, Primary Colors, Typografie, Funktionalität.
3. **Farblehre** – Farbkreis, Komplementärfarben, Analogfarben. Farbpsychologie (Rot=Energie/Warnung, Gelb=Aufmerksamkeit/Optimismus, Blau=Vertrauen, Schwarz=Eleganz/Stärke). Code: CSS Custom Properties definieren.
4. **Typografie** – Schriftarten-Kategorien (Serif, Sans-Serif, Monospace). Hierarchie (H1-H6, Body, Caption). Bauhaus-Schriften (Futura, DIN, Helvetica). Zeilenabstand, Zeichenabstand, Lesbarkeit.
5. **Layout & Grid** – 12-Spalten-Grid, Abstände (8px-System), Whitespace, Asymmetrie vs. Symmetrie. CSS Grid und Flexbox kurz erklärt.
6. **Gestaltgesetze** – Nähe, Ähnlichkeit, Kontinuität, Geschlossenheit. Praxisbeispiele.
7. **Usability-Grundlagen** – Norman's Design Principles (Visibility, Feedback, Constraints, Mapping, Consistency, Affordance). "Don't make me think" Prinzip.
8. **Bauhaus-Anwendung auf unsere App** – Zeige wie die Kaffeemaschinen-App die Bauhaus-Prinzipien anwendet: Farbwahl (Rot für Fehler, Gelb für Warnung, Grün für OK), Grid-Layout, klare Typografie-Hierarchie.
9. **Quiz** – 5 Fragen
10. **Praktische Übung** – Color Palette in CSS definieren + Typografie-System für die App in CodePen.

### Code-Beispiele (zum Kopieren):
```css
/* Bauhaus Color System */
:root {
  --primary: #B91C1C;    /* Rot: Fehler, CTAs */
  --warning: #F59E0B;    /* Gelb: Warnungen */
  --success: #16A34A;    /* Grün: Erfolg */
  --neutral: #1A1A1A;    /* Schwarz: Text */
  --bg: #FAFAFA;         /* Hintergrund */
}
```

---

## SEITE 5: lab-04-ux.html

### Sektionen
1. **Überblick** – Vom Konzept zum Klickprototyp
2. **UX vs. UI** – Unterschied und Zusammenspiel. "UX is how it works, UI is how it looks."
3. **User Research** – Interviews, Umfragen, Beobachtung, Contextual Inquiry. Was wollen Techniker, die Kaffeemaschinen warten?
4. **Personas** – Was ist eine Persona? Vorlage zeigen. Beispiel: "Thomas, 34, Wartungstechniker" – Ziele, Frustrationen, Kontext, Technik-Affinität.
5. **User Journey Map** – Die Reise von Thomas: Störung bemerken → Handy zücken → App öffnen → Foto machen → Diagnose lesen → Anleitung folgen → Ersatzteil bestellen → Problem gelöst. Als Tabelle + visuell.
6. **User Stories** – "Als Techniker möchte ich eine Störung fotografieren können, damit das System automatisch eine Diagnose erstellt." 5 User Stories für die App.
7. **Information Architecture** – Sitemap der App (3 Screens: Upload → Diagnose → Shop)
8. **Wireframes** – Lo-Fi Papier-Wireframe zeigen (als ASCII-Art oder einfache Grafik), dann Hi-Fi-Übergang.
9. **Figma Quickstart** – Link zu Figma Community Template. Anleitung: Account erstellen, Frame anlegen, Mobile-Format (390x844), Komponenten nutzen. Direkte Übung: Screen 1 "Störung aufnehmen" in Figma nachbauen.
10. **Quiz** – 5 Fragen
11. **Figma-Ressourcen** – Links zu Figma Community, Tutorials.

### Wireframe (ASCII, zum Visualisieren):
```
┌─────────────────────┐
│  ◀  Störung melden  │
│─────────────────────│
│                     │
│  ┌───────────────┐  │
│  │   📷 FOTO    │  │
│  │   aufnehmen  │  │
│  └───────────────┘  │
│                     │
│  Maschinentyp:      │
│  [▼ Jura E8      ] │
│                     │
│  Symptome:          │
│  ☐ Kein Kaffee     │
│  ☐ Fehlermeldung   │
│  ☐ Wasserleck      │
│  ☐ Geräusche       │
│                     │
│  [  Diagnose starten  ] │
└─────────────────────┘
```

---

## SEITE 6: lab-05-usecase.html

### Der Use Case: Kaffeevollautomat-Störungsmelder

**Beschreibung des Use Case:**
Ein Industrie-Wartungstechniker meldet per Smartphone eine Störung eines Kaffeevollautomaten. Das System analysiert Foto + Symptome, liefert eine Diagnose und eine Schritt-für-Schritt-Reparaturanleitung. Wenn nötig, wird der Techniker zum Ersatzteilshop weitergeleitet.

### Typische Störungen (realistisch):
1. **E4/E5 Fehler – Entkalkung nötig** → Lösung: Entkalker-Programm, Entkalker bestellen
2. **Mahlwerk mahlt nicht** → Bohnen leer ODER Fremdkörper → Lösung: Bohnenbehälter füllen / Mahlwerk reinigen
3. **Kein Kaffee-Fluss** → Verstopfte Brühgruppe → Lösung: Brühgruppe entnehmen und reinigen
4. **Dampflanze defekt** → Kalkablagerungen im Ventil → Lösung: Entkalken, ggf. Dichtung tauschen
5. **Wassertank läuft leer** → Sensor defekt oder Tank nicht eingesetzt → Lösung: Sensor prüfen
6. **Kaffeesatz-Behälter voll** → Automat stoppt → Lösung: Tresterbehälter leeren
7. **Maschine startet nicht** → Sicherung, Stromversorgung → Lösung: Sicherung prüfen
8. **Kaffeepulver in der Tasse** → Defektes Sieb → Lösung: Sieb austauschen (→ Shop)
9. **Ungewöhnliche Geräusche** → Pumpe defekt → Lösung: Pumpe tauschen (→ Shop)
10. **Display tot** → Elektronik-Defekt → Lösung: Servicekundendienst

### Sektionen
1. **Überblick & Use Case Beschreibung**
2. **Phase 1: Empathize** – Persona Thomas, Pain Points, Empathy Map. Bilder der Störungen (aus images/ Ordner).
3. **Phase 2: Define** – Problem Statement, HMW-Fragen (3 Beispiele)
4. **Phase 3: Ideate** – 8 Lösungsideen (Crazy 8s Ergebnis), dann Konvergenz auf die App-Idee
5. **Phase 4: Prototype – Lo-Fi** – Papier-Wireframe (ASCII im Code, dazu Beschreibung), App-Flow (3 Screens)
6. **Phase 5: Prototype – Hi-Fi Design** – Bauhaus-Designentscheidungen erklärt:
   - Primärfarbe Rot → Fehlermeldungen, dringliche Aktionen
   - Gelb → Warnungen (E4 Fehler)
   - Grün → Erfolgreich behoben
   - Grid: 4-Spalten-Layout auf Desktop, 1-Spalte Mobile
   - Typografie: Space Grotesk für Headlines, System Font für Body
   - Geometrische Buttons (kein Border-Radius = Bauhaus)
7. **Phase 5: Prototype – Figma** – Screenshot/Mock des Hi-Fi Prototyps. Figma-Link-Platzhalter. Screen-Beschreibungen:
   - Screen 1: "Störung erfassen" (Foto + Symptome)
   - Screen 2: "Diagnose" (Störungsname + Ursache + Lösung)
   - Screen 3: "Ersatzteilshop" (Produktliste mit Preisen)
   - Screen 4: "Bestellung bestätigt"
8. **Zusammenfassung: Ready for Implementation** → Weiter zu Lab 6
9. **Quiz** – 5 Fragen zu Design Thinking + Use Case

---

## SEITE 7: lab-06-implementation.html

### Sektionen
1. **Überblick** – Vom Prototyp zur lauffähigen App
2. **Technologie-Stack** – HTML5, CSS3, Vanilla JavaScript, Supabase (BaaS), CodePen
3. **Supabase Setup** – Step-by-Step:
   - Schritt 1: Account anlegen auf supabase.com (kostenlos)
   - Schritt 2: Neues Projekt erstellen
   - Schritt 3: Datenbank-Schema erstellen (SQL Code zum Kopieren)
   - Schritt 4: Supabase URL + anon key kopieren
4. **Datenbankschema (SQL)** – Kompletter Code:
```sql
-- Störungsmeldungen
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

-- Ersatzteilkatalog
CREATE TABLE ersatzteile (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  name TEXT NOT NULL,
  beschreibung TEXT,
  preis DECIMAL(10,2),
  kategorie TEXT,
  lagerbestand INT DEFAULT 0,
  bild_url TEXT
);

-- Bestellungen
CREATE TABLE bestellungen (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  created_at TIMESTAMPTZ DEFAULT NOW(),
  stoerung_id UUID REFERENCES stoerungen(id),
  kundename TEXT,
  email TEXT,
  status TEXT DEFAULT 'offen'
);

-- Bestellpositionen
CREATE TABLE bestellpositionen (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  bestellung_id UUID REFERENCES bestellungen(id),
  ersatzteil_id UUID REFERENCES ersatzteile(id),
  menge INT DEFAULT 1
);

-- Demo-Daten: Ersatzteile
INSERT INTO ersatzteile (name, beschreibung, preis, kategorie, lagerbestand) VALUES
('Entkalker Jura 3-Pack', 'Original Jura Entkalker, 3 Tabletten für 3 Entkalkungsvorgänge', 12.90, 'Reinigung', 150),
('Brühgruppe Komplett', 'Komplette Brühgruppe als Ersatz, kompatibel mit Jura E-Serie', 89.00, 'Mechanik', 12),
('Dichtungsset Universal', '10-teiliges Dichtungsset für alle gängigen Kaffeevollautomaten', 8.50, 'Dichtungen', 200),
('Pumpe VibraFoam 15 Bar', 'Ersatzpumpe, 15 Bar, Vibrationstyp, universell kompatibel', 45.00, 'Mechanik', 25),
('Dampfventil komplett', 'Ersatz-Dampfventil inkl. Dichtungen und Schrauben', 28.90, 'Mechanik', 30),
('Reinigungstabletten 30er', 'Monatliche Reinigung, 30 Tabletten', 14.90, 'Reinigung', 300);
```

5. **Die App: HTML/CSS/JS für CodePen** – Vollständiger, kommentierter Code in 3 Tabs:

### HTML (für CodePen HTML-Tab):
Vollständige App-HTML-Struktur mit:
- Header mit Logo (Bauhaus-Stil)
- 4 "Screens" (via CSS show/hide: `display: none / block`)
- Screen 1: Störung erfassen (Select Maschinentyp, Symptom-Checkboxes, Beschreibungsfeld, Foto-Upload-Button)
- Screen 2: Diagnose-Anzeige (Diagnose-Text, Lösung, CTA "Ersatzteil bestellen")
- Screen 3: Shop (Produkt-Karten aus Supabase geladen)
- Screen 4: Bestellbestätigung (Fake-Checkout mit Name + E-Mail)
- Supabase CDN Script-Tag

### CSS (für CodePen CSS-Tab):
Bauhaus-Styling:
- CSS Custom Properties (Colors, Fonts)
- Kein border-radius auf Buttons/Karten (Bauhaus!)
- Farbcodierung: Rot für Fehler, Gelb für Warnung, Grün für Erfolg
- Mobile-first, responsive
- Grid-Layout

### JavaScript (für CodePen JS-Tab):
```javascript
// === SUPABASE CONFIG ===
// ⚠️ Ersetze DEINE_PROJECT_URL und DEINEN_ANON_KEY
const SUPABASE_URL = 'https://DEIN-PROJEKT.supabase.co';
const SUPABASE_ANON_KEY = 'DEIN_ANON_KEY';
const { createClient } = supabase;
const db = createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

// Diagnose-Logik (regelbasiert)
const DIAGNOSE_REGELN = {
  'keine_bohnen': { diagnose: 'Bohnenbehälter leer', loesung: 'Bohnenbehälter mit frischen Kaffeebohnen auffüllen.', ersatzteil: null },
  'fehlercode_e4': { diagnose: 'Entkalkung erforderlich (E4)', loesung: 'Entkalkungs-Programm starten. Benötigtes Material: Jura Entkalker.', ersatzteil: 'Entkalker Jura 3-Pack' },
  'kein_kaffee': { diagnose: 'Brühgruppe verstopft', loesung: 'Brühgruppe entnehmen, unter fließendem Wasser reinigen, ggf. ersetzen.', ersatzteil: 'Brühgruppe Komplett' },
  'geraeusche': { diagnose: 'Pumpe defekt', loesung: 'Pumpe austauschen. Professionelle Wartung empfohlen.', ersatzteil: 'Pumpe VibraFoam 15 Bar' },
  'dampf_defekt': { diagnose: 'Dampfventil defekt', loesung: 'Dampfventil auf Kalkablagerungen prüfen, ggf. austauschen.', ersatzteil: 'Dampfventil komplett' },
};

// Screen-Management
let currentScreen = 1;
let aktuelleStorung = null;

function zeigeScreen(n) { ... }
function diagnoseDurchfuehren() { ... }
async function stoerungSpeichern(data) { ... }
async function ladeErsatzteile() { ... }
async function bestellungAbschicken() { ... }
```

6. **Schritt-für-Schritt: App in CodePen testen** – 
   - Schritt 1: codepen.io aufrufen, neues Pen anlegen
   - Schritt 2: HTML/CSS/JS einfügen
   - Schritt 3: Supabase URL + Key einsetzen
   - Schritt 4: App testen
   - Schritt 5: Störung melden → Diagnose sehen → Ersatzteil bestellen

7. **Erweiterungsideen** – Für Fortgeschrittene:
   - Kamera-Integration (navigator.mediaDevices.getUserMedia)
   - Foto-Upload zu Supabase Storage
   - Push-Notifications (Service Worker)
   - KI-gestützte Diagnose (OpenAI Vision API)
   - Admin-Dashboard (alle Meldungen anzeigen)

8. **Quiz** – 5 Fragen zu Supabase, SQL, Web-APIs

---

## VOLLSTÄNDIGER CODE-ANFORDERUNGEN

### Der CodePen-Code soll VOLLSTÄNDIG und LAUFFÄHIG sein:
- Alle 4 Screens implementiert
- Supabase-Anbindung (mit klar markierten Platzhaltern für URL/Key)
- Offline-Fallback: Wenn keine Supabase-Verbindung, zeige Demo-Daten
- Bauhaus-Styling konsequent durchgehalten
- Kommentiert auf Deutsch für Studis

### Stil der Code-Kommentare:
```javascript
// ═══════════════════════════════════════════
// SCREEN 1: Störung erfassen
// Hier wählt der Nutzer Maschinentyp + Symptome
// ═══════════════════════════════════════════
```

---

## GIT & DEPLOYMENT

Am Ende ALLE Dateien commiten und pushen:
```bash
cd /tmp/inme-lab
git add .
git commit -m "feat: INME Lab v1.0 – Complete companion site with 6 labs, Bauhaus design, Kaffeevollautomat use case"
git push origin main
```

Dann GitHub Pages aktivieren (falls noch nicht): Settings → Pages → Branch: main, folder: / (root).

---

## QUALITÄTSANFORDERUNGEN
1. Alle HTML-Dateien sind valides HTML5
2. Responsive (Mobile + Desktop)
3. Alle Texte bilingual (DE + EN)
4. Alle Quiz-Fragen haben 4 Antwortmöglichkeiten
5. Code-Beispiele haben Copy-Buttons
6. Interne Links funktionieren (index.html ↔ alle Labs)
7. Der vollständige CodePen-Code ist lauffähig
8. Kein npm, kein Build-Tool, nur CDN

---

## WENN DU FERTIG BIST

Führe aus:
```bash
OPENCLAW_CONFIG_PATH=/Users/robert/clawd/.openclaw-macbot/openclaw.json \
OPENCLAW_STATE_DIR=/Users/robert/clawd/.openclaw-macbot \
openclaw system event --text "✅ INME Lab fertig! 6 Labs + Use Case + CodePen App gebaut. Repo: swrobuts/inme. Bitte git push prüfen und GitHub Pages aktivieren." --mode now
```
