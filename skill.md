---
name: saaspocalypse-scanner
description: >-
  SaaSpocalypse Survival Scanner — analysiert ob ein SaaS-Unternehmen durch
  einen Claude Skill (.md Datei) ersetzt werden kann. Erzeugt Disruption Score
  (0–100), unterhaltsame Analyse, Claudes Selbsteinschätzung und einen konkreten
  Replacement SKILL.md. Zwei Ausgabeformate: interaktives HTML-Artifact ODER
  professionelles PDF-Report. IMMER verwenden bei: SaaS analysieren, SaaS
  ersetzen, kann KI das ersetzen, SaaSpocalypse, SaaS Disruption, wird dieses
  Tool überleben, SaaS bewerten, Claude Skill Replacement, .md file replacement,
  SaaS Moat analysieren, AI disruption check, kann ein Claude Skill das,
  Software Disruption, SaaS Survival, Unternehmen scannen, Company Scanner, ist
  mein SaaS sicher, SaaS Roast, Tech Company Analyse. Auch bei: scanne diese
  Firma, kann Claude das ersetzen, wie sicher ist dieses SaaS, wird dieses
  Unternehmen überleben, Disruption Score, analysiere ob KI das ersetzen kann,
  oder wenn jemand eine SaaS-URL teilt und wissen will ob die Firma durch KI
  bedroht ist.
---

# SaaSpocalypse Survival Scanner

> "Are you just a .md file?"

## Zweck

Analysiere ein SaaS-Unternehmen und bewerte, ob es durch einen Claude Skill (eine `.md`-Datei) ersetzt werden kann. Liefere ein unterhaltsames, aber analytisch fundiertes Ergebnis mit charmantem Storytelling. Ausgabe wahlweise als interaktives HTML-Artifact oder als professionelles PDF-Report.

## Workflow

### Phase 1: Ziel identifizieren

Der Benutzer gibt eine **Firmen-URL**, einen **Firmennamen** oder eine **Produktbeschreibung** an. Falls unklar, frage nach.

### Phase 1b: Ausgabeformat bestimmen

Bestimme das gewünschte Ausgabeformat:

| Signal vom Benutzer                                                                            | Format   |
| ---------------------------------------------------------------------------------------------- | -------- |
| Sagt "PDF", "Report", "Bericht", "zum Ausdrucken", "zum Verschicken", "Dokument", "als Datei" | **PDF**  |
| Sagt "HTML", "interaktiv", "Artifact", "zum Anschauen", "Dashboard", "App"                    | **HTML** |
| Sagt nichts zum Format                                                                         | **HTML** (Standard) |
| Sagt "beides"                                                                                  | **Beide** — erst HTML-Artifact, dann PDF generieren |

Falls unklar, nimm **HTML** als Standard. Frage NICHT nach dem Format — wähle intelligent basierend auf dem Kontext.

### Phase 2: Recherche

1. **Web-Recherche durchführen** — Suche nach dem Unternehmen: Was macht es? Kernprodukt, Pricing, Zielgruppe, Tech-Stack, Moats (Netzwerkeffekte, Daten-Lock-in, Regulierung, physische Infrastruktur, etc.)
1. **Verwende `web_search`** mit Queries wie `[Firmenname] product features pricing`, `[Firmenname] competitors moat`, `[Firmenname] AI strategy`
1. **Verwende `web_fetch`** auf der Firmen-Website um das Produkt zu verstehen

### Phase 3: Disruption Score berechnen

Bewerte auf einer Skala von **0–100** (0 = Unantastbar, 100 = War nie nötig):

#### Scoring-Dimensionen (gewichtet):

| Dimension                      | Gewicht | Beschreibung                                                                                                                                    |
| ------------------------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Workflow-Komplexität**       | 20%     | Wie komplex ist der Kern-Workflow? Einfache Text/Daten-Transformation = hoch ersetzbar. Komplexe Multi-System-Orchestrierung = schwer ersetzbar |
| **Daten-Moat**                 | 20%     | Hat das Unternehmen proprietäre Daten, die nicht replizierbar sind? Nutzerdaten, Netzwerkeffekte, historische Datasets                          |
| **Physische Infrastruktur**    | 15%     | Erfordert das Produkt physische Hardware, Server-Infrastruktur, Echtzeit-Systeme, die nicht als .md abbildbar sind?                             |
| **Regulatorischer Schutz**     | 15%     | Gibt es Lizenzen, Zertifizierungen, Compliance-Anforderungen, die eine .md nicht erfüllen kann?                                                |
| **Integrations-Tiefe**         | 15%     | Wie tief ist das Produkt in Kunden-Workflows eingebettet? API-Ökosystem, Marketplace, Partner-Netzwerk                                        |
| **UI/UX-Abhängigkeit**         | 10%     | Braucht das Produkt eine komplexe, interaktive Echtzeit-UI die über Textinteraktion hinausgeht?                                                |
| **Preismodell-Vulnerabilität** | 5%      | Ist das Pricing offensichtlich überhöht für das, was geliefert wird? Seat-based Pricing für Dinge, die ein LLM trivial kann?                   |

#### Score-Kategorien:

| Score  | Label              | Emoji | Bedeutung                                                                                                |
| ------ | ------------------ | ----- | -------------------------------------------------------------------------------------------------------- |
| 0–10   | **Unantastbar**    | 🏛️   | Physische Infrastruktur, Regulierung oder fundamentale Internet-Schicht. Kein .md-File kann das ersetzen |
| 11–25  | **Festung**        | 🏰   | Starke Moats: Daten, Netzwerkeffekte, tiefe Integration. Sehr schwer zu ersetzen                        |
| 26–40  | **Ins Schwitzen**  | 😰   | Verwundbar in Teilen. Kern-Moat existiert, aber AI knabbert an den Rändern                               |
| 41–60  | **Wackelkandidat** | 🫠   | Signifikante Teile des Produkts sind durch einen Skill abbildbar. Differenzierung schrumpft              |
| 61–80  | **Auf der Kippe**  | 📉   | Der Großteil des Produkts ist ein Workflow, den ein LLM direkt ausführen kann                            |
| 81–95  | **Fast weg**       | 🫧   | Das Produkt ist im Wesentlichen eine UI um einen Prozess, den Claude besser kann                         |
| 96–100 | **War nie nötig**  | 🪄   | Das Produkt hätte nie existieren sollen. Es ist buchstäblich ein Prompt                                  |

---

## Phase 4: Output generieren

Die Inhalte sind in beiden Formaten identisch. Der Unterschied liegt in der Darstellung.

### Gemeinsame Inhalts-Sektionen (für BEIDE Formate)

#### Sektion A: Header & Score-Anzeige
- Firmenname + stilisierter Bereich
- **Disruption Score** als prominente Zahl mit Farbcodierung (Teal→Amber→Koralle)
- Label + Emoji
- Ein-Zeiler-Verdict als eleganter Subtitle

#### Sektion B: Die Story
- **Charming, witzig, aber faktisch fundiert** — erzählt wie ein freundlicher Tech-Analyst
- Beginnt mit einem eingängigen Opener, z.B. "Es war einmal ein SaaS, das glaubte…" oder "Stellt euch vor: 2019, ein Pitch Deck…"
- Referenziert spezifische Produkt-Features, Pricing-Kuriositäten, historische Momente
- 3–5 Absätze, charmant-satirisch, **nie gemein**
- Wenn die Firma "Unantastbar" ist: Eine Hommage — Warum sie unersetzbar ist, mit ehrfürchtigem Unterton

#### Sektion C: Claudes Selbsteinschätzung
- Was Claude an diesem Produkt ersetzen KANN
- Was Claude NICHT ersetzen kann (und warum)
- Ehrlich, selbstironisch, mit konkreten Beispielen
- Format: Ich-Perspektive aus Claudes Sicht

#### Sektion D: Der Replacement SKILL.md
- Ein vollständiger, funktionaler SKILL.md-Entwurf der zeigt, wie ein Claude Skill das Produkt (teilweise) ersetzen würde
- Enthält: Purpose, Instructions, What NOT To Do (mit charmanten Seitenhieben auf das Original-Produkt)
- Bei "Unantastbar"-Firmen: Der SKILL.md endet mit einer humorvollen Kapitulation ("Status: IMPOSSIBLE — Claude ist smart, aber Claude ist kein globales DNS-Netzwerk")

#### Sektion E: Analyse-Breakdown
- Visualisierung der 7 Scoring-Dimensionen mit Einzelwerten
- Kurze Erklärung je Dimension warum der Score so ausgefallen ist

---

## Phase 5a: HTML-Ausgabe (Interaktives Artifact)

Wenn das Format **HTML** ist, erstelle ein **React-Artifact** (.jsx):

### Design-System

Das Artifact verwendet ein **modernes, helles, freundliches Design**:

- **Hintergrund:** Weiß bis zartes Off-White (#FAFBFC) mit subtilen Farbverläufen
- **Primärfarben:** Warmes Teal (#0D9488) als Akzent, sanftes Indigo (#6366F1) als Sekundärfarbe
- **Score-Farben:** Smooth Gradient von Teal (sicher) → Amber (mittel) → Koralle (#F43F5E, gefährdet) — KEIN Rot, kein Schwarz
- **Typografie:** System-Font-Stack, großzügige Zeilenabstände, klare Hierarchie
- **Cards:** Abgerundete Ecken (16px), dezente Schatten, leichte Border in Grau
- **Spacing:** Viel Weißraum, luftiges Layout
- **Icons & Emojis:** Freundlich, keine Totenköpfe — stattdessen Wetter-Metaphern, Natur-Bilder, Architektur
- **Animationen:** Sanfte Einblendungen, smooth Score-Counter, keine harten Übergänge
- **Gesamtanmutung:** Wie eine moderne Analytics-App (Vercel/Linear/Notion-Vibes), nicht wie ein Horror-Game

### HTML-spezifische Features

- **Tab-Navigation** mit Tabs: "Score", "Story", "Claude sagt…", "SKILL.md", "Analyse"
- **Score-Animation** beim Laden (smooth counter von 0 zum Zielwert)
- **SKILL.md als Code-Block** mit Copy-Button
- **Radar-Chart oder horizontale Balken** der 7 Scoring-Dimensionen mit Hover-Effekten
- **Responsive:** funktioniert auf Desktop und Mobile

---

## Phase 5b: PDF-Ausgabe (Professionelles Report-Dokument)

Wenn das Format **PDF** ist, erstelle ein **mehrseitiges PDF** mit ReportLab.

### WICHTIG: Lies zuerst den PDF-Skill

Vor der PDF-Erstellung IMMER den PDF-Skill lesen:
```
view /mnt/skills/public/pdf/SKILL.md
```

### PDF Design-System

Das PDF übersetzt das freundliche Design in Druckformat:

- **Seitenformat:** A4
- **Ränder:** 2cm links/rechts, 2.5cm oben, 2cm unten
- **Primärfarben:** Teal (#0D9488) für Überschriften und Akzente, Indigo (#6366F1) als Sekundär
- **Score-Farben:** Gleiche Teal→Amber→Koralle-Palette wie HTML
- **Typografie:** Helvetica (in ReportLab verfügbar), klare Größen-Hierarchie:
  - Titel: 28pt Bold, Teal
  - H1: 20pt Bold, Slate (#1E293B)
  - H2: 16pt Bold, Indigo
  - Body: 11pt Regular, Slate (#334155)
  - Caption: 9pt Regular, Muted (#64748B)
- **Trennlinien:** 0.5pt in hellem Grau (#E2E8F0) zwischen Sektionen
- **Code-Blöcke:** Hellgrauer Hintergrund (#F8FAFC), Courier-Schrift, 9pt
- **Fußzeile:** Seitenzahl + "SaaSpocalypse Survival Scanner" + Datum

### PDF-Seitenstruktur

#### Seite 1: Deckblatt
- Großer Firmenname (28pt, Bold)
- "SaaSpocalypse Survival Scanner" als Untertitel
- **Disruption Score** als großer Kreis (ReportLab Drawing):
  - Äußerer Ring in Score-Farbe
  - Zahl in der Mitte (48pt, Bold)
  - Label darunter
- Ein-Zeiler-Verdict
- Datum der Analyse

#### Seite 2: Die Story
- Überschrift "Die Story" mit Teal-Akzent
- Der vollständige Story-Text als Fließtext
- Absätze mit ausreichend Abstand (6pt after)

#### Seite 3: Claudes Selbsteinschätzung
- Überschrift "Claudes Selbsteinschätzung"
- Aufgeteilt in "Was Claude ersetzen kann" und "Was Claude nicht ersetzen kann"
- Fließtext in Ich-Perspektive

#### Seite 4: Analyse-Breakdown
- Überschrift "Analyse im Detail"
- **Tabelle** der 7 Dimensionen:
  - Spalten: Dimension | Score (0–100) | Bewertung
  - Farbcodierte Header-Zeile in Teal
  - Alternierend weiße/hellgraue Zeilen
- Kurze Erklärung je Dimension als Text unter der Tabelle

#### Seite 5: Replacement SKILL.md
- Überschrift "Replacement SKILL.md"
- Der vollständige SKILL.md-Code in Courier-Schrift
- Hellgrauer Hintergrund-Block
- Hinweis: "Dieser Skill-Entwurf zeigt, wie ein Claude Skill Teile des Produkts ersetzen könnte."

#### Letzte Seite: Disclaimer
- Kleiner Text: "Dieser Report ist eine analytisch fundierte Unterhaltung — keine Investmentberatung."
- Datum der Erstellung

### PDF-Erstellungs-Workflow

1. Erstelle ein Python-Script unter `/home/claude/generate_report.py`
2. Definiere alle Styles und Farben als Konstanten
3. Baue den Content programmatisch auf (Sektionen als Funktionen)
4. Generiere das PDF nach `/home/claude/[firmenname]_saaspocalypse_report.pdf`
5. Kopiere das fertige PDF nach `/mnt/user-data/outputs/`
6. Präsentiere es dem Benutzer mit `present_files`

### Score-Farb-Mapping (für beide Formate)

```python
def get_score_color(score):
    """Gibt die passende Farbe für den Score zurück."""
    if score <= 10:
        return '#0D9488'   # Teal — Unantastbar
    elif score <= 25:
        return '#0D9488'   # Teal — Festung
    elif score <= 40:
        return '#D97706'   # Amber — Ins Schwitzen
    elif score <= 60:
        return '#D97706'   # Amber — Wackelkandidat
    elif score <= 80:
        return '#EA580C'   # Orange — Auf der Kippe
    elif score <= 95:
        return '#F43F5E'   # Koralle — Fast weg
    else:
        return '#F43F5E'   # Koralle — War nie nötig
```

### Score-Kreis für PDF (ReportLab Drawing)

```python
from reportlab.graphics.shapes import Drawing, Circle, Wedge, String
from reportlab.lib.colors import HexColor

def draw_score_circle(score, color_hex, label):
    """Zeichnet den Disruption Score als Ring-Grafik."""
    d = Drawing(200, 200)
    
    # Hintergrund-Kreis
    d.add(Circle(100, 100, 80, fillColor=HexColor('#F1F5F9'), strokeColor=None))
    
    # Score-Ring
    angle = score * 3.6
    if score > 0:
        d.add(Wedge(100, 100, 80, 90, 90 - angle,
                     fillColor=HexColor(color_hex), strokeColor=None))
    
    # Innerer weißer Kreis
    d.add(Circle(100, 100, 60, fillColor=HexColor('#FFFFFF'), strokeColor=None))
    
    # Score-Zahl
    d.add(String(100, 90, str(score), fontSize=36, fontName='Helvetica-Bold',
                 fillColor=HexColor(color_hex), textAnchor='middle'))
    
    # Label
    d.add(String(100, 70, label, fontSize=10, fontName='Helvetica',
                 fillColor=HexColor('#64748B'), textAnchor='middle'))
    
    return d
```

### Dimensions-Tabelle für PDF

```python
from reportlab.platypus import Table, TableStyle
from reportlab.lib.units import cm
from reportlab.lib.colors import HexColor

def create_dimension_table(dimensions):
    """Erstellt die Score-Tabelle."""
    data = [['Dimension', 'Score', 'Bewertung']]
    
    for dim in dimensions:
        data.append([dim['name'], f"{dim['score']}/100", dim['note']])
    
    table = Table(data, colWidths=[6*cm, 3*cm, 8*cm])
    table.setStyle(TableStyle([
        ('BACKGROUND', (0, 0), (-1, 0), HexColor('#0D9488')),
        ('TEXTCOLOR', (0, 0), (-1, 0), HexColor('#FFFFFF')),
        ('FONTNAME', (0, 0), (-1, 0), 'Helvetica-Bold'),
        ('FONTSIZE', (0, 0), (-1, -1), 10),
        ('ROWBACKGROUNDS', (0, 1), (-1, -1), [HexColor('#FFFFFF'), HexColor('#F8FAFC')]),
        ('GRID', (0, 0), (-1, -1), 0.5, HexColor('#E2E8F0')),
        ('VALIGN', (0, 0), (-1, -1), 'MIDDLE'),
        ('TOPPADDING', (0, 0), (-1, -1), 8),
        ('BOTTOMPADDING', (0, 0), (-1, -1), 8),
    ]))
    return table
```

---

## Phase 5c: Beide Ausgaben

Wenn der Benutzer "beides" möchte:

1. **Zuerst** das HTML-Artifact erstellen (sofort sichtbar im Chat)
2. **Dann** das PDF generieren und als Download bereitstellen
3. Kurze Notiz: "Hier ist dein interaktives Dashboard — und das PDF zum Verschicken liegt bereit."

---

## Stilregeln

### Ton der Story

- **Charmant-satirisch, nie gemein** — Humor auf Kosten des Geschäftsmodells, nicht der Menschen
- **Faktisch fundiert** — Jeder Witz basiert auf echten Produkt-Features oder Pricing
- **Spezifisch** — Keine generischen Roasts. Referenziere konkrete Features, Preise, Strategien
- **Storytelling** — Erzähle eine Geschichte, keine Anklagerede. Der Ton ist "liebevoller Tech-Freund der die Wahrheit sagt"

### Ton von Claudes Selbsteinschätzung

- **Ehrlich bescheiden** — Keine Übertreibung der eigenen Fähigkeiten
- **Selbstironisch** — Claude darf über eigene Limitierungen Witze machen
- **Konkret** — Nenne spezifische Dinge die Claude kann/nicht kann

### Sprache

- **Standard: Deutsch** — alle Texte (Story, Claudes Selbsteinschätzung, Analyse, UI-Labels) auf Deutsch
- Falls der Benutzer auf Englisch fragt, liefere das Ergebnis auf Englisch
- Die Replacement-SKILL.md-Sektion ist auf Englisch (da Skills auf Englisch geschrieben werden)
- Score-Kategorien auf Deutsch (Unantastbar, Festung, etc.)

## Beispiel-Scores zur Kalibrierung

Diese Beispiele helfen bei der Score-Einordnung:

- **VeriSign** (DNS-Root-Server, .com/.net Registry) → ~4/100 (Unantastbar)
- **Stripe** (Payment Infrastructure) → ~12/100 (Festung)
- **Salesforce** (CRM + Ecosystem) → ~22/100 (Festung)
- **GoDaddy** (Domains + Website Builder) → ~28/100 (Ins Schwitzen)
- **Grammarly** (Schreibassistent) → ~75/100 (Auf der Kippe)
- **Jasper AI** (AI Content Generator) → ~90/100 (Fast weg)
- **Simple Prompt Wrapper ohne eigene Daten** → ~98/100 (War nie nötig)

## Hinweise

- Wenn die Firma nicht gefunden wird oder zu klein ist für öffentliche Daten: Sage das ehrlich und schätze basierend auf der Produktbeschreibung
- Bei Firmen die bereits aggressiv AI einsetzen: Berücksichtige ob ihre AI-Strategie sie schützt oder ob sie damit nur Zeit kaufen
- Der Scanner ist Unterhaltung mit analytischem Kern — nicht als Investmentberatung zu verstehen
- **Format-Wahl:** Nicht nachfragen — intelligent aus dem Kontext ableiten. HTML ist Standard, PDF wenn der Benutzer es signalisiert
