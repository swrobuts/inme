# PREMIUM REDESIGN: coffee-app.html

## Aufgabe
Erstelle `/tmp/inme-lab/coffee-app.html` komplett neu. Die App muss aussehen wie eine echte Premium-Service-App von Jura, DeLonghi oder Krups – nicht wie eine generische KI-Demo.

## ABSOLUT VERBOTEN ("AI Slop" – niemals verwenden)
- ❌ Bunte Cards mit Emoji (🔧 💡 ✅ ☕) – NIEMALS
- ❌ Gradient-Backgrounds
- ❌ Bubble-UI, rounded-pill buttons (max border-radius: 4px)
- ❌ Alert-Box-Spam (grüne/rote/gelbe info-boxes)
- ❌ Spinner mit buntem Border
- ❌ "Lorem ipsum"-hafte Texte
- ❌ Mehr als 2 Akzentfarben
- ❌ box-shadow auf jeder Card
- ❌ Kindische Animationen

## Design-Referenz: Jura / DeLonghi / Krups
- **Primärfarbe:** Tiefes Anthrazit `#1C1C1C` als Header/Footer
- **Hintergrund:** Reines Weiß `#FFFFFF` + sehr helles Grau `#F5F5F5` für Sections
- **Akzent:** Einzige Farbe: Weinrot/Bordeaux `#8B1A1A` – sparsam eingesetzt
- **Typografie:** Dünn & elegant – `font-weight: 300` für Headlines, `font-weight: 400` für Body
- **Abstände:** Großzügig. Viel Luft. Wenig Inhalt pro Screen.
- **Buttons:** Rechteckig, 0–4px radius, border-based (outlined) oder solid dunkel
- **Bilder:** Groß, full-width, professionell
- **Icons:** Nur Linie-Icons (SVG), keine Emojis
- **Sprache:** Professionell, knapp, technisch. "Störungsanalyse" nicht "Foto hochladen 📷"

## Font
```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600&display=swap" rel="stylesheet">
```
body: `font-family: 'Inter', sans-serif;`

## Layout: Mobile-First, max-width: 480px, zentriert

## App-Struktur (5 Screens via JS show/hide)

---

### Screen 1: Startscreen / Upload
**Vorbild:** Jura "Service & Support" Seite

**Header (fest, dunkel):**
```
[INME Lab]          [Störungsanalyse]
```
- Hintergrund: `#1C1C1C`
- Schrift: weiß, font-weight 300, letter-spacing 0.15em, UPPERCASE
- Höhe: 56px

**Hero-Bild:**
- Großes Bild der Kaffeemaschine: `images/hero-kaffeemaschine.jpg`
- full-width, height: 220px, object-fit: cover
- Darüber (overlay): dunkles Gradient unten `linear-gradient(to top, rgba(0,0,0,0.6), transparent)`
- Im Bild-Overlay unten: "JURA E8" in weiß, font-weight 300

**Upload-Bereich:**
```
[Weißes Panel]

Störung erfassen

Fotografieren Sie das betroffene Bauteil.
Unsere KI analysiert den Zustand.

[                                        ]
|  Bild auswählen oder hierher ziehen   |
[                                        ]
← nur thin border, kein Dashed-Kinder-Style

[STÖRUNG ANALYSIEREN]   ← solid #1C1C1C button, full-width
```

**Maschinenmodell-Auswahl (Dropdown):**
```
Maschinenmodell
[▾ JURA E8                          ]   ← minimal dropdown, border-bottom only
```
Options: JURA E8, JURA S8, De'Longhi Magnifica, De'Longhi Eletta, Krups EA8108, Siemens EQ.9

**Optionaler API Key (diskret):**
```
Gemini API Key  ·  optional
[___________________________]  ← nur border-bottom, kein box
Ohne Key: Demo-Modus aktiv
```

---

### Screen 2: Analyse läuft
**Minimalistisch:**
- Weißer Hintergrund
- Kleines Bild das analysiert wird (border: 1px solid #E0E0E0)
- Schmaler Progress-Indikator: dünne Linie die fließt (kein bunter Spinner!)
  ```css
  .progress-line {
    height: 2px;
    background: #E0E0E0;
    position: relative;
  }
  .progress-line::after {
    content: '';
    position: absolute;
    top: 0; left: 0;
    height: 2px;
    width: 40%;
    background: #1C1C1C;
    animation: slide 1.2s ease-in-out infinite alternate;
  }
  @keyframes slide { from { left: 0; } to { left: 60%; } }
  ```
- Text: "Analysiere Bild..." in grau, font-weight: 300
- Darunter kleiner: "Powered by Gemini Vision"

---

### Screen 3: Diagnose-Ergebnis
**Vorbild:** Apple Support / Jura Service Diagnose

**Layout:**
```
[Header dunkel]

[Bild: analysiertes Foto, full-width 220px]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
DIAGNOSE                   ● KRITISCH
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Kalkablagerung im Brühsystem

Schweregrad: Hoch
Erkanntes Bauteil: Brühgruppe / Heizsystem
Fehlercode: E4

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
EMPFOHLENE MASSNAHME
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. Entkalkungsprogramm starten
2. Jura Entkalker (3-Tab) verwenden
3. Wassertank mit 1 L Wasser füllen
4. Programm ca. 30 Min laufen lassen

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[ERSATZTEIL BESTELLEN]   ← full-width, #1C1C1C
[Neue Analyse]           ← outlined, dezent
```

**Farb-Codierung (NUR über einen dünnen Streifen/Punkt, nicht über ganze Cards):**
- Kritisch: `#8B1A1A` (Bordeaux-Rot)
- Warnung: `#6B5A2A` (Dunkeloliv/Beige)
- OK/Hinweis: `#2A4A2A` (Dunkelgrün)

---

### Screen 4: Fehler – Kein Kaffeemaschinenbauteil
```
[Header dunkel]

[Weißes Panel]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
ANALYSE FEHLGESCHLAGEN
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Das hochgeladene Bild zeigt kein 
erkennbares Kaffeemaschinenbauteil.

Bitte laden Sie ein Foto eines der 
folgenden Bauteile hoch:

— Brühgruppe
— Mahlwerk  
— Heizsystem
— Display
— Wassertank
— Dampfdüse

[ERNEUT VERSUCHEN]   ← full-width
```

---

### Screen 5: Ersatzteilshop
**Vorbild:** Jura/DeLonghi Produktseite

```
[Header dunkel]

EMPFOHLENES ERSATZTEIL

────────────────────────────────────
[Produktbild: 160x160, zentriert]
────────────────────────────────────

JURA Entkalker
Artikel-Nr. 64553 · Für alle JURA Modelle

Entkalkt schonend und gründlich.
3 Tabs für 3 Entkalkungs-
vorgänge.

Preis                          12,90 €
Verfügbarkeit          Auf Lager ●

[IN DEN WARENKORB]   ← full-width, #1C1C1C

[Weitere Produkte anzeigen]   ← text-link, kein button
────────────────────────────────────
Sicherer Kauf · 30 Tage Rückgabe
```

---

### Screen 6: Bestellbestätigung
```
[Header dunkel]

[Großes Bild der Maschine, leicht abgedunkelt]

VIELEN DANK FÜR IHRE BESTELLUNG

Ihre Bestellnummer: #24-00847

Das Ersatzteil wird innerhalb von 
1–3 Werktagen geliefert.

──────────────────────────────────
Was jetzt?
──────────────────────────────────

1.  Warten bis das Ersatzteil eintrifft
2.  Unsere Einbauanleitung herunterladen
3.  Maschine in Betrieb nehmen

[NEUE STÖRUNG MELDEN]   ← outlined
```

---

## Technische Umsetzung

### Gemini Vision API (unverändert von coffee-app.html v1)
```javascript
const response = await fetch(
  `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent?key=${apiKey}`,
  {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      contents: [{
        parts: [
          { text: `You are a coffee machine service technician AI. Analyze this image.
          
Is this an image of a coffee machine or coffee machine component?
If YES: identify the problem. Return JSON:
{
  "is_coffee_machine": true,
  "component": "brew_group|grinder|heating|display|tank|steam|seal|unknown",
  "problem": "short description in German",
  "severity": "critical|warning|info",
  "error_code": "E4|E5|E6|null",
  "solution_steps": ["Step 1", "Step 2", "Step 3"],
  "spare_part_needed": true|false,
  "spare_part": "product name or null"
}

If NO (not a coffee machine): Return JSON:
{ "is_coffee_machine": false }

Return ONLY the JSON, no other text.` },
          { inline_data: { mime_type: 'image/jpeg', data: BASE64_IMAGE } }
        ]
      }],
      generationConfig: { temperature: 0.2, maxOutputTokens: 600 }
    })
  }
);
```

### Mock-Daten (wenn kein API Key)
```javascript
const MOCK_DIAGNOSES = [
  {
    is_coffee_machine: true,
    component: 'heating',
    problem: 'Starke Kalkablagerungen im Heizsystem',
    severity: 'critical',
    error_code: 'E4',
    solution_steps: [
      'Entkalkungsprogramm über das Menü starten',
      'JURA Entkalker-Tablette in Wassertank geben',
      'Wassertank mit 1 Liter frischem Wasser füllen',
      'Programm vollständig durchlaufen lassen (ca. 30 Min.)'
    ],
    spare_part_needed: true,
    spare_part: 'JURA Entkalker 3er-Pack'
  },
  {
    is_coffee_machine: true,
    component: 'grinder',
    problem: 'Mahlwerk verstopft – Fremdkörper oder verklumpter Kaffee',
    severity: 'warning',
    error_code: null,
    solution_steps: [
      'Kaffeebohnenbehälter vollständig leeren',
      'Bohnenbehälter mit warmem Wasser reinigen',
      'Mahlwerk mit Reinigungstablette durchlaufen lassen',
      'Bei Weiterbestehen: Mahlwerk ausbauen und prüfen'
    ],
    spare_part_needed: false,
    spare_part: null
  },
  {
    is_coffee_machine: true,
    component: 'brew_group',
    problem: 'Brühgruppe defekt – kein Kaffeedurchfluss',
    severity: 'critical',
    error_code: null,
    solution_steps: [
      'Brühgruppe durch Seitenöffnung entnehmen',
      'Unter fließendem Wasser reinigen',
      'Dichtungen auf Beschädigungen prüfen',
      'Bei Beschädigung: Brühgruppe ersetzen'
    ],
    spare_part_needed: true,
    spare_part: 'Brühgruppe Komplett'
  }
];
```

### Ersatzteil-Katalog
```javascript
const ERSATZTEILE = {
  'JURA Entkalker 3er-Pack':      { artikelnr: '64553', preis: 12.90, lagernd: true },
  'Brühgruppe Komplett':          { artikelnr: '67007', preis: 89.00, lagernd: true },
  'Pumpe VibraFoam 15 Bar':       { artikelnr: '68555', preis: 45.00, lagernd: true },
  'Dampfventil Set':              { artikelnr: '68821', preis: 28.90, lagernd: false },
  'Mahlwerk-Reinigungsset':       { artikelnr: '25045', preis: 18.50, lagernd: true },
  'O-Ring Dichtungsset 10-tlg.':  { artikelnr: '60958', preis:  8.50, lagernd: true },
};
```

---

## CSS Grundgerüst

```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Inter', -apple-system, sans-serif;
  font-weight: 400;
  font-size: 15px;
  color: #1C1C1C;
  background: #FFFFFF;
  max-width: 480px;
  margin: 0 auto;
  min-height: 100vh;
}

/* Header */
.app-header {
  position: fixed; top: 0; left: 0; right: 0;
  max-width: 480px; margin: 0 auto;
  height: 56px;
  background: #1C1C1C;
  display: flex; align-items: center; justify-content: space-between;
  padding: 0 20px;
  z-index: 100;
}
.app-header .brand {
  font-size: 11px; font-weight: 300; letter-spacing: 0.2em;
  color: white; text-transform: uppercase;
}
.app-header .section-title {
  font-size: 11px; font-weight: 300; letter-spacing: 0.15em;
  color: rgba(255,255,255,0.5); text-transform: uppercase;
}

/* Screens */
.screen { display: none; padding-top: 56px; min-height: 100vh; }
.screen.active { display: block; }

/* Dividers (statt Cards/Boxen) */
.divider {
  border: none;
  border-top: 1px solid #E0E0E0;
  margin: 24px 0;
}
.section-label {
  font-size: 10px; font-weight: 500; letter-spacing: 0.18em;
  color: #888; text-transform: uppercase;
  padding: 24px 20px 12px;
}

/* Upload Zone – premium, minimal */
.upload-zone {
  border: 1px solid #D0D0D0;
  margin: 0 20px;
  padding: 40px 20px;
  text-align: center;
  cursor: pointer;
  transition: border-color 0.2s;
}
.upload-zone:hover { border-color: #1C1C1C; }
.upload-zone svg { opacity: 0.3; margin-bottom: 12px; }
.upload-zone p { font-size: 13px; color: #888; font-weight: 300; }

/* Buttons */
.btn-primary {
  display: block; width: calc(100% - 40px); margin: 16px 20px;
  padding: 16px;
  background: #1C1C1C; color: white;
  border: none; border-radius: 0;
  font-size: 11px; font-weight: 500; letter-spacing: 0.18em;
  text-transform: uppercase;
  cursor: pointer; transition: background 0.2s;
}
.btn-primary:hover { background: #333; }
.btn-primary:disabled { background: #D0D0D0; cursor: not-allowed; }

.btn-secondary {
  display: block; width: calc(100% - 40px); margin: 8px 20px;
  padding: 15px;
  background: transparent; color: #1C1C1C;
  border: 1px solid #1C1C1C; border-radius: 0;
  font-size: 11px; font-weight: 500; letter-spacing: 0.18em;
  text-transform: uppercase;
  cursor: pointer; transition: all 0.2s;
}
.btn-secondary:hover { background: #1C1C1C; color: white; }

/* Dropdown/Input – nur border-bottom */
.field { margin: 0 20px 20px; }
.field label { font-size: 10px; letter-spacing: 0.15em; color: #888; text-transform: uppercase; display: block; margin-bottom: 6px; }
.field select, .field input {
  width: 100%;
  border: none; border-bottom: 1px solid #D0D0D0;
  padding: 8px 0;
  font-size: 14px; font-family: inherit;
  background: transparent;
  color: #1C1C1C;
  outline: none;
  border-radius: 0;
}
.field select:focus, .field input:focus { border-bottom-color: #1C1C1C; }

/* Hero Image */
.hero-image { width: 100%; height: 220px; object-fit: cover; display: block; position: relative; }
.hero-image-wrap { position: relative; }
.hero-overlay {
  position: absolute; bottom: 0; left: 0; right: 0;
  background: linear-gradient(to top, rgba(0,0,0,0.65), transparent);
  padding: 20px;
  color: white;
}
.hero-overlay .model { font-size: 11px; letter-spacing: 0.2em; text-transform: uppercase; opacity: 0.7; }

/* Diagnose */
.diagnosis-header {
  display: flex; justify-content: space-between; align-items: center;
  padding: 20px;
  border-bottom: 1px solid #E0E0E0;
}
.diagnosis-title { font-size: 18px; font-weight: 300; }
.severity-badge {
  font-size: 10px; letter-spacing: 0.12em; text-transform: uppercase;
  padding: 4px 8px; font-weight: 500;
}
.severity-critical { color: #8B1A1A; border: 1px solid #8B1A1A; }
.severity-warning   { color: #7A6020; border: 1px solid #7A6020; }
.severity-info      { color: #2A5A2A; border: 1px solid #2A5A2A; }

.meta-row {
  display: flex; justify-content: space-between;
  padding: 12px 20px;
  border-bottom: 1px solid #F0F0F0;
  font-size: 13px;
}
.meta-row .label { color: #888; font-weight: 300; }
.meta-row .value { font-weight: 400; }

.steps { padding: 20px; }
.steps h4 { font-size: 10px; letter-spacing: 0.15em; text-transform: uppercase; color: #888; margin-bottom: 16px; }
.step { display: flex; gap: 16px; margin-bottom: 16px; align-items: flex-start; }
.step-num { font-size: 12px; font-weight: 300; color: #888; min-width: 24px; padding-top: 1px; }
.step-text { font-size: 14px; font-weight: 300; line-height: 1.5; }

/* Shop */
.product { padding: 24px 20px; }
.product-image { width: 120px; height: 120px; object-fit: contain; display: block; margin: 0 auto 20px; }
.product-name { font-size: 18px; font-weight: 300; margin-bottom: 4px; }
.product-sku { font-size: 12px; color: #888; margin-bottom: 12px; letter-spacing: 0.05em; }
.product-desc { font-size: 14px; font-weight: 300; color: #444; line-height: 1.6; margin-bottom: 20px; }
.product-meta { border-top: 1px solid #E0E0E0; padding-top: 16px; }
.product-price-row { display: flex; justify-content: space-between; margin-bottom: 6px; font-size: 14px; }
.product-price-row .price { font-weight: 500; font-size: 16px; }
.availability { display: flex; align-items: center; gap: 6px; font-size: 12px; color: #2A5A2A; }
.availability::before { content: '●'; font-size: 8px; }

/* Progress line */
.progress-wrap { padding: 24px 20px; }
.progress-line { height: 1px; background: #E0E0E0; position: relative; overflow: hidden; }
.progress-line::after {
  content: ''; position: absolute; top: 0; left: 0; height: 1px;
  width: 40%; background: #1C1C1C;
  animation: slide 1.4s ease-in-out infinite alternate;
}
@keyframes slide { from { left: 0; } to { left: 60%; } }
```

---

## Finale Aufgabe für Claude

1. Erstelle `/tmp/inme-lab/coffee-app.html` komplett nach dieser Spezifikation
2. Alle 6 Screens vollständig implementieren
3. Gemini Vision API-Integration (aus Brief) + Mock-Fallback
4. Vollständig responsiv, max-width: 480px, zentriert
5. NUR Inter-Font, NUR die definierten Farben, KEINE Extras
6. Kein Emoji im UI. Svgs als Icons wenn nötig.
7. Deutsche Texte, technisch-professionell formuliert
8. Nach Fertigstellung: git add coffee-app.html && git commit -m "feat: Premium coffee app redesign (Jura/DeLonghi style)" && git push
9. Dann: openclaw system event --text "Premium App fertig!" --mode now
