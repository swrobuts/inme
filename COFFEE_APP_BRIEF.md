# coffee-app.html – Premium Redesign Brief

## ⚠️ WICHTIGSTE REGEL: KEIN AI SLOP!

Das ist eine Lehrdemonstration für eine Hochschule. Der Dozent (Prof. Dr. Robert Butscher, THWS) 
hat explizit gesagt: "die App sieht zu stark nach AI Slop aus". 

**Was AI Slop ist (VERBOTEN):**
- Emoji als UI-Elemente (kein ☕📷🔧⚠️ in Buttons oder Überschriften)
- Bunte Karten mit Farbverläufen
- Runde, "freundliche" Bubble-artlige Elemente
- Übermäßige Hover-Animationen
- Card-Grid mit farbigen Icons
- Alert-Boxen mit bunten Border-Left-Styles
- Generische "AI-Assistant"-Optik
- Chatbot-artige UI-Elemente
- Zu viele Farben gleichzeitig

**Was Premium ist (PFLICHT):**
Orientiere dich an den Websites von Jura (jura.com), De'Longhi (delonghi.com), Krups.
Diese Marken haben:
- Sehr viel Weißraum
- Dunkle, seriöse Header-Bereiche
- Klare, sachliche Typografie (groß, selbstsicher)
- Hochwertige Produktfotografie als Hero-Element
- Dezente, einheitliche Farbpalette (meist Schwarz/Weiß/Grau + 1 Akzentfarbe)
- Feine Linien statt fette Boxen
- Icons aus einem konsistenten Icon-Set (Linien, nicht Emoji)
- Sehr wenig Text, aber präzise formuliert
- Strikte Hierarchie: Was ist das Wichtigste? Das steht oben, groß.

---

## Design-Spezifikation

### Farbpalette (EXAKT so verwenden)
```css
--black:    #0A0A0A;   /* Fast-Schwarz für Headlines */
--dark:     #1C1C1E;   /* Dunkle Bereiche, Header */
--gray-900: #1D1D1F;   /* Apple-esque near-black */
--gray-700: #3D3D3F;
--gray-500: #6E6E73;   /* Secondary text */
--gray-300: #D1D1D6;   /* Borders */
--gray-100: #F5F5F7;   /* Backgrounds */
--white:    #FFFFFF;
--accent:   #DC2626;   /* Bauhaus-Rot, sparsam einsetzen – NUR für CTAs & Fehlermeldungen */
```

### Typografie
```css
font-family: -apple-system, BlinkMacSystemFont, 'SF Pro Display', 'Helvetica Neue', 'Arial', sans-serif;
/* Headlines: font-weight 600-700, letter-spacing: -0.02em */
/* Body: font-weight 400, color: #3D3D3F */
/* Labels: font-weight 500, letter-spacing: 0.05em, text-transform: uppercase, font-size: 0.7rem */
```

### Layout
- Mobile-First, max-width: 480px, zentriert
- Kein Border-Radius größer als 4px auf Karten/Containern (Jura-Stil: fast keine border-radius)
- Innenabstände: 24px Seitenabstand, 32px vertikaler Abstand zwischen Sektionen
- Trennlinien: `border-top: 1px solid #D1D1D6` statt farbige Boxen

---

## App-Struktur & Screen-Design

### HEADER (persistent, immer sichtbar)
```
┌─────────────────────────────┐
│ [←]     Service App    [DE] │  ← Dunkel (#1C1C1E), weiße Schrift
│         JURA × THWS         │  ← Subtitel, grau
└─────────────────────────────┘
```
- Hintergrund: `#1C1C1E`
- Schrift: weiß / grau
- Zurück-Button: nur wenn nicht auf Screen 1
- Kein Logo-Emoji

### SCREEN 1 – Störung erfassen
```
┌─────────────────────────────┐
│  [HEADER]                   │
├─────────────────────────────┤
│                             │
│  STÖRUNG MELDEN             │  ← Label, grau, uppercase, klein
│  Foto der Störung           │  ← H1, groß, schwarz
│  hochladen                  │
│                             │
│  ┌───────────────────────┐  │
│  │                       │  │
│  │   [Kamera-Icon SVG]   │  │  ← großes SVG-Icon, kein Emoji
│  │   Foto hochladen      │  │
│  │   JPG, PNG, HEIC      │  │
│  └───────────────────────┘  │
│         (dashed border)     │
│                             │
│  ─────────── oder ─────────  │
│                             │
│  MASCHINENTYP               │  ← Label
│  [────────────────── ▼]     │  ← Native Select, styled
│                             │
│  GEMINI API KEY (optional)  │  ← Label, eingeklappt
│  [Falls vorhanden...]       │
│                             │
│  [    Diagnose starten    ] │  ← Schwarzer Button, volle Breite
│                             │
└─────────────────────────────┘
```

**Upload-Zone Stil:**
- `border: 1.5px dashed #D1D1D6`
- `background: #F5F5F7`
- Kamera-Icon: SVG (kein Emoji!)
- Bei Hover: border-color: #0A0A0A
- Nach Upload: Foto wird angezeigt, Upload-Zone verschwindet

**Maschinentyp-Select:**
Optionen: Jura E8, Jura S8, De'Longhi Magnifica, Krups EA8180, Andere

**Diagnose-Button:**
- `background: #0A0A0A; color: white; border: none; border-radius: 0;`
- `padding: 18px 24px; font-size: 1rem; font-weight: 600; letter-spacing: 0.03em;`
- Disabled wenn kein Foto

### SCREEN 2 – Analyse läuft
```
┌─────────────────────────────┐
│  [HEADER]                   │
├─────────────────────────────┤
│                             │
│  [Foto als kleines Preview] │  ← 120px hoch, volle Breite, object-fit:cover
│                             │
│  ─────────────────────────  │
│                             │
│  ANALYSE                    │  ← Label
│  KI-Diagnose läuft          │  ← H2
│                             │
│  ————                       │  ← Animated loading line (kein Spinner!)
│                             │
│  Gemini Vision analysiert   │  ← Body-Text, grau
│  das hochgeladene Bild...   │
│                             │
└─────────────────────────────┘
```

**Loading-Animation:** Kein Kreis-Spinner! Stattdessen:
```css
.loading-bar {
  height: 2px;
  background: #DC2626;
  animation: loadBar 1.5s ease-in-out infinite;
}
@keyframes loadBar {
  0% { width: 0%; }
  50% { width: 70%; }
  100% { width: 100%; opacity: 0; }
}
```

### SCREEN 3 – Diagnose
```
┌─────────────────────────────┐
│  [HEADER]                   │
├─────────────────────────────┤
│  [Foto, 200px hoch]         │
├─────────────────────────────┤
│                             │
│  FEHLERDIAGNOSE             │  ← Label, Rot, uppercase
│  Entkalkung erforderlich    │  ← H1, schwarz, groß
│                             │
│  ─────────────────────────  │  ← Trennlinie
│                             │
│  URSACHE                    │  ← Label
│  Kalkablagerungen im        │  ← Body
│  Heizsystem beeinträchtigen │
│  den Wasserdurchfluss.      │
│                             │
│  ─────────────────────────  │
│                             │
│  LÖSUNGSWEG                 │  ← Label
│  1.  Entkalker bereitstellen│  ← Nummerierte Liste
│  2.  Entkalkungsprogramm    │
│      starten (Taste 5 Sek.) │
│  3.  Programm abwarten      │
│      (ca. 25 Minuten)       │
│                             │
│  ─────────────────────────  │
│                             │
│  Ersatzteil benötigt?       │  ← Kleine Überschrift
│  [  Zum Service-Shop  →  ] │  ← Outlined Button, Akzentfarbe
│                             │
│  [  Neue Störung melden  ] │  ← Text-Link, grau
│                             │
└─────────────────────────────┘
```

### SCREEN 4 – Shop
```
┌─────────────────────────────┐
│  [HEADER]                   │
├─────────────────────────────┤
│                             │
│  SERVICE-SHOP               │  ← Label
│  Empfohlenes Ersatzteil     │  ← H1
│                             │
│  ┌─────────────────────────┐│
│  │ [Produktbild 80x80]     ││
│  │                         ││
│  │ Entkalker Jura 3-Pack   ││  ← Produktname
│  │ Art.-Nr. JU-ENT-003     ││  ← Artikelnummer
│  │                         ││
│  │ € 12,90                 ││  ← Preis, groß
│  │ Inkl. MwSt., versandkostenfrei ││
│  └─────────────────────────┘│
│                             │
│  LIEFERZEIT                 │  ← Label
│  2–3 Werktage               │
│                             │
│  ─────────────────────────  │
│                             │
│  NAME                       │  ← Label
│  [─────────────────────]    │
│  E-MAIL                     │  ← Label
│  [─────────────────────]    │
│                             │
│  [    Jetzt bestellen    ] │  ← Schwarzer Button
│                             │
│  [  Weiter ohne Kauf  ]    │  ← Text-Link
└─────────────────────────────┘
```

**Produkt-Card Stil:**
- Keine bunte Card! Weißer Hintergrund, `border: 1px solid #D1D1D6`
- Produktbild: echtes Foto (images/ersatzteile-sortiment.jpg) oder neutrales Grau-Square
- Preis: `font-size: 1.75rem; font-weight: 700;`

**Formularfelder:**
```css
.form-field {
  border: none;
  border-bottom: 1px solid #D1D1D6;
  border-radius: 0;
  padding: 12px 0;
  font-size: 1rem;
  background: transparent;
  width: 100%;
}
```
(Nur untere Linie – wie Apple-Formulare)

### SCREEN 5 – Bestätigung
```
┌─────────────────────────────┐
│  [HEADER]                   │
├─────────────────────────────┤
│                             │
│  ─────────────────────────  │  ← Rote Linie (2px, 48px breit)
│                             │
│  Bestellung                 │  ← H1, schwarz
│  erfolgreich.               │
│                             │
│  Eine Bestätigung wurde an  │  ← Body, grau
│  Ihre E-Mail gesendet.      │
│                             │
│  ─────────────────────────  │
│                             │
│  BESTELLNUMMER              │  ← Label
│  INME-2026-0847             │  ← Mono-Font, generiert
│                             │
│  LIEFERZEIT                 │
│  2–3 Werktage               │
│                             │
│  [  Neue Störung melden  ] │  ← Outlined Button
└─────────────────────────────┘
```

### ERROR STATE – Kein Kaffeebauteil erkannt
```
┌─────────────────────────────┐
│  [Hochgeladenes Bild]       │
├─────────────────────────────┤
│                             │
│  ─ ─ Rote Trennlinie ─ ─   │
│                             │
│  ERKENNUNG FEHLGESCHLAGEN   │  ← Label, Rot
│  Kein Kaffeemaschinenteil   │  ← H1
│  erkannt.                   │
│                             │
│  Das hochgeladene Bild      │  ← Body, grau
│  enthält kein identifizier- │
│  bares Bauteil einer        │
│  Kaffeemaschine.            │
│                             │
│  [   Anderes Foto wählen ] │  ← Schwarzer Button
└─────────────────────────────┘
```

---

## SVG Icons (kein Emoji!)

Kamera-Icon für Upload-Zone:
```svg
<svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#6E6E73" stroke-width="1.5">
  <path d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"/>
  <circle cx="12" cy="13" r="4"/>
</svg>
```

Erfolgs-Check für Bestätigung:
```svg
<svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="#DC2626" stroke-width="1.5">
  <polyline points="20 6 9 17 4 12"/>
</svg>
```

---

## Diagnose-Logik

```javascript
const DIAGNOSE = {
  kalk: {
    label: 'Entkalkung erforderlich',
    ursache: 'Kalkablagerungen im Heizsystem beeinträchtigen den Wasserdurchfluss und reduzieren die Heizleistung.',
    loesung: ['Entkalker vorbereiten (Jura-Tablette in Wassertank)', 'Entkalkungsprogramm starten (Taste 5 Sek. halten)', 'Programm abwarten (ca. 25 Minuten)', 'Tank spülen und neu befüllen'],
    ersatzteil: 'Entkalker Jura 3-Pack',
    preis: 12.90
  },
  mahlwerk: {
    label: 'Mahlwerk blockiert',
    ursache: 'Das Mahlwerk ist durch Kaffeeöl-Rückstände oder Fremdkörper blockiert.',
    loesung: ['Bohnenbehälter leeren', 'Mahlwerk-Reinigungstablette einlegen', 'Reinigungsprogramm starten', 'Mahlwerk auf Fremdkörper prüfen'],
    ersatzteil: 'Mahlwerk-Reinigungsset',
    preis: 18.50
  },
  bruehgruppe: {
    label: 'Brühgruppe defekt',
    ursache: 'Die Brühgruppe ist verstopft oder das Dichtungssystem ist undicht.',
    loesung: ['Brühgruppe entnehmen (Hebel links)', 'Unter fließendem Wasser reinigen', 'Dichtungen auf Risse prüfen', 'Einsetzen und Testlauf starten'],
    ersatzteil: 'Brühgruppen-Dichtungsset',
    preis: 8.50
  },
  dampf: {
    label: 'Dampfventil verstopft',
    ursache: 'Milchrückstände oder Kalk blockieren die Dampfdüse.',
    loesung: ['Dampfdüse abschrauben', 'In Entkalkungslösung einlegen (30 Min.)', 'Mit Nadel freispülen', 'Wieder einschrauben und testen'],
    ersatzteil: 'Dampfventil komplett',
    preis: 28.90
  },
  pumpe: {
    label: 'Pumpe defekt',
    ursache: 'Die Vibrationspumpe erzeugt keinen ausreichenden Wasserdruck.',
    loesung: ['Wassertank auf Füllstand prüfen', 'Zu- und Ableitungen auf Blockagen prüfen', 'Professionellen Service kontaktieren', 'Austausch der Vibrationspumpe empfohlen'],
    ersatzteil: 'Pumpe VibraFoam 15 Bar',
    preis: 45.00
  }
};
```

---

## Gemini Vision API Integration

```javascript
async function analyzeWithGemini(apiKey, base64Image) {
  const prompt = `Analyze this image carefully. 
  
  First: Is this an image of a coffee machine, coffee maker, or a component/part of one?
  
  If NO: Return exactly: {"is_coffee_machine": false}
  
  If YES: Identify the problem and return:
  {
    "is_coffee_machine": true,
    "problem_type": "kalk|mahlwerk|bruehgruppe|dampf|pumpe|other",
    "confidence": "high|medium|low",
    "problem_description": "Brief description in German"
  }
  
  Return ONLY valid JSON, no markdown, no explanation.`;
  
  const response = await fetch(
    `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash-exp:generateContent?key=${apiKey}`,
    {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({
        contents: [{ parts: [
          { text: prompt },
          { inline_data: { mime_type: 'image/jpeg', data: base64Image }}
        ]}],
        generationConfig: { temperature: 0.1, maxOutputTokens: 200 }
      })
    }
  );
  
  const data = await response.json();
  const text = data.candidates?.[0]?.content?.parts?.[0]?.text || '{}';
  return JSON.parse(text.replace(/```json\n?|\n?```/g, '').trim());
}
```

---

## Mock-Modus (ohne API Key)

Wenn kein API Key: 2 Sekunden Delay, dann zufällige Diagnose aus DIAGNOSE-Objekt.
Zeige dabei einen dezenten Hinweis: `"Demo-Modus: Simulierte KI-Diagnose"` – kleiner grauer Text.

---

## Technische Anforderungen

1. **Kein Framework** – Vanilla HTML/CSS/JS
2. **Kein CDN für Libs** außer optional für Supabase (aber Supabase ist OPTIONAL – nicht nötig für die App)
3. **Responsive** – funktioniert auf iPhone (390px) und Desktop (bis 600px)
4. **5 Screens** implementiert und funktionsfähig
5. **Error State** für Nicht-Kaffeemaschinen-Bilder
6. **Deutsche Sprache** (App-Texte auf Deutsch)

---

## Qualitätskontrolle

Bevor du fertig sagst, prüfe:
- [ ] Kein einziges Emoji in der App-UI (Upload, Buttons, Labels)
- [ ] Alle Icons sind SVG
- [ ] Kein einziger Farbverlauf (gradient)
- [ ] Formularfelder haben NUR eine untere Linie, kein Border-Rahmen
- [ ] Loading-Animation ist eine Linie, kein Kreis-Spinner
- [ ] Produktkarte sieht aus wie bei einem echten Shopify-Store, nicht wie eine bunte Infokarte
- [ ] Alle 5 Screens implementiert
- [ ] Error-State implementiert

---

## Datei: /tmp/inme-lab/coffee-app.html

Überschreibe die bestehende Datei komplett. Das Ergebnis soll aussehen wie eine App von Jura oder De'Longhi, nicht wie ein generiertes AI-Demo.

## Am Ende:
```bash
cd /tmp/inme-lab
git add coffee-app.html
git commit -m "feat: premium coffee-app redesign – Jura/DeLonghi style"
git push origin main

OPENCLAW_CONFIG_PATH=/Users/robert/clawd/.openclaw-macbot/openclaw.json \
OPENCLAW_STATE_DIR=/Users/robert/clawd/.openclaw-macbot \
openclaw system event --text "Premium coffee-app.html fertig – kein AI Slop mehr, Jura/DeLonghi-Stil" --mode now
```
