# REDESIGN BRIEF: INME Lab v2.0

## Feedback vom Kunden (Robert)

1. **Design zu dunkel/hart** – Schwarzer Hero-Hintergrund zu aggressiv, braucht moderne, freundliche Ästhetik
2. **Fehlende Live-Demo** – Studis brauchen fertige App zum Ausprobieren, nicht nur Code
3. **Zu wenig interaktiv** – Mehr interaktive Elemente, sonst werden Studis abgehängt
4. **Bessere Diagramme** – Statt ASCII-Art echte Diagramme (Mermaid.js statt Excalidraw)

---

## Redesign-Anforderungen

### 1. Design-Überarbeitung (moderneres, helleres Design)

**Hero Section (index.html):**
- Schwarz `#1A1A1A` → **Gradient:** `linear-gradient(135deg, #667eea 0%, #764ba2 100%)` oder ähnlich modern
- ODER: Helles Design mit **sanften Grautönen:** `#F8F9FA` als BG, Akzentfarbe `#6366F1` (Indigo)
- Geometrische Bauhaus-Elemente bleiben, aber **subtiler** (opacity 0.1)
- **Empfehlung:** Gradient-Hero (lila/blau) + weiße Karten mit Schatten = modern & freundlich

**Lab-Seiten Header:**
- Fixer Header bleibt, aber **weiß mit leichtem Schatten** statt schwarzer Border
- Sidebar: hellgrauer Hintergrund `#F8F9FA` statt weiß

**Farben:**
- Primary: `#6366F1` (Indigo) – modern, freundlich, professionell
- Accent: `#F59E0B` (Amber) – bleibt
- Dark Text: `#1F2937` statt `#1A1A1A`
- Backgrounds: `#FFFFFF`, `#F9FAFB`, `#F3F4F6` (gestaffelte Grautöne)

**Buttons:**
- Runde Ecken `border-radius: 8px` (statt 0) – moderner
- Schatten: `box-shadow: 0 4px 6px rgba(99, 102, 241, 0.1)`

---

### 2. Live-Demo der Kaffeemaschinen-App

**Ziel:** Fertige, lauffähige App zum Ausprobieren

**Umsetzung:**
- Erstelle `coffee-app.html` im Repo (standalone, vollständig)
- Nutzt **Supabase öffentliches Demo-Projekt** (bereits angelegt, read-only für Studis)
- 4 Screens funktionieren: Upload → Diagnose → Shop → Bestellung
- Mock-Daten falls Supabase offline
- Link von Lab 05 + Lab 06 + index.html

**Supabase Demo-Setup:**
- Öffentliches Projekt mit Demo-Daten (6 Ersatzteile)
- Row Level Security: Studis können nur lesen, nicht schreiben (außer stoerungen-Tabelle)
- Anon Key öffentlich im Code

---

### 3. Interaktivität erhöhen

**Mermaid.js-Diagramme** (ersetzen ASCII):
- Lab 02: Design Thinking 5-Phasen-Diagramm
- Lab 04: User Journey als Mermaid-Diagramm
- Lab 04: Wireframe als Mermaid-Diagramm (flowchart)
- Lab 05: App-Flow (3 Screens) als Mermaid

**Interaktive CodePen-Embeds:**
- Lab 03: Live Color-Picker (CSS Custom Properties editierbar)
- Lab 06: Eingebetteter CodePen mit der App (iframe)

**Interaktive Quiz-Verbesserung:**
- Nach Beantwortung: Erklärung anzeigen (warum richtig/falsch)
- Fortschrittsbalken (3 von 5 beantwortet)

**Click-to-Expand Boxen:**
- "Mehr erfahren"-Buttons für optionale Deep-Dives
- Code-Blöcke: "Erklärung anzeigen"-Toggle

---

### 4. Mermaid.js Integration

**CDN einbinden:**
```html
<script src="https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.min.js"></script>
<script>mermaid.initialize({ startOnLoad: true, theme: 'neutral' });</script>
```

**Beispiel: User Journey (Lab 04):**
```html
<div class="mermaid">
journey
  title User Journey: Techniker Thomas
  section Störung bemerken
    Kaffeemaschine defekt: 1: Thomas
    Handy zücken: 3: Thomas
  section App nutzen
    App öffnen: 4: Thomas
    Foto machen: 5: Thomas
    Diagnose erhalten: 5: Thomas
  section Problem lösen
    Anleitung folgen: 4: Thomas
    Ersatzteil bestellen: 5: Thomas
    Problem gelöst: 5: Thomas
</div>
```

**Beispiel: Design Thinking Flow (Lab 02):**
```html
<div class="mermaid">
graph LR
  A[Empathize] --> B[Define]
  B --> C[Ideate]
  C --> D[Prototype]
  D --> E[Test]
  E --> C
  E --> B
</div>
```

---

## Umsetzungsplan (Claude Code)

### Task 1: Design-Update (index.html)
- Hero: Gradient-Hintergrund
- Karten: weiße BG mit Schatten
- Buttons: rounded corners
- Stats-Bar: moderner

### Task 2: Design-Update (alle Lab-Seiten)
- Header: weiß mit Schatten
- Sidebar: hellgrau
- Neue Farbpalette durchziehen

### Task 3: Mermaid.js einbauen
- CDN in alle Lab-Seiten
- ASCII-Diagramme durch Mermaid ersetzen (Lab 02, 04, 05)

### Task 4: coffee-app.html erstellen
- Standalone-App mit Supabase
- Öffentliches Demo-Projekt (URL + Anon Key im Code)
- Verlinkung von allen relevanten Seiten

### Task 5: Interaktivität
- Quiz-Erklärungen
- CodePen-Embeds
- Click-to-Expand

### Task 6: Commit & Push
```bash
git add .
git commit -m "feat: INME Lab v2.0 – Modern design, live demo, Mermaid diagrams, interactivity"
git push origin main
```

---

## Farb-Palette v2.0

```css
:root {
  /* Primary Colors */
  --primary: #6366F1;           /* Indigo – modern, freundlich */
  --primary-light: #818CF8;
  --primary-dark: #4F46E5;
  
  /* Accent */
  --accent: #F59E0B;            /* Amber */
  --accent-light: #FBBF24;
  
  /* Neutrals */
  --gray-50: #F9FAFB;
  --gray-100: #F3F4F6;
  --gray-200: #E5E7EB;
  --gray-600: #4B5563;
  --gray-900: #111827;
  
  /* Text */
  --text-primary: #1F2937;
  --text-secondary: #6B7280;
  
  /* Backgrounds */
  --bg-page: #FFFFFF;
  --bg-sidebar: #F9FAFB;
  --bg-code: #1E293B;
}
```

---

## Supabase Demo-Projekt Setup

**Projekt:** `inme-coffee-demo`  
**URL:** `https://PROJEKT-ID.supabase.co`  
**Anon Key:** öffentlich, read-only außer für stoerungen-Tabelle

**RLS Policies:**
```sql
-- Ersatzteile: alle können lesen
CREATE POLICY "Public read ersatzteile" ON ersatzteile FOR SELECT USING (true);

-- Störungen: alle können einfügen
CREATE POLICY "Public insert stoerungen" ON stoerungen FOR INSERT WITH CHECK (true);
```

**Demo-Daten:** bereits aus Lab 06 übernehmen (6 Ersatzteile)
