# SaaSpocalypse Survival Scanner

> **Hinweis:** Der Scanner ist Unterhaltung mit analytischem Kern — nicht als Investmentberatung zu verstehen. Die Ergebnisse dienen der spielerischen Analyse und ersetzen keine professionelle Bewertung von Unternehmen oder Technologien.

**"Are you just a .md file?"**

Analysiert SaaS-Unternehmen und bewertet, ob sie durch einen Claude Skill (eine `.md`-Datei) ersetzt werden könnten. Liefert einen Disruption Score (0–100), eine charmante Story, Claudes ehrliche Selbsteinschätzung und einen konkreten Replacement-SKILL.md-Entwurf.

---

## Was ist das?

Der SaaSpocalypse Survival Scanner ist ein Claude Skill, der jedes SaaS-Produkt auf sieben Dimensionen analysiert und einen gewichteten Disruption Score berechnet. Das Ergebnis wird wahlweise als **interaktives HTML-Artifact** oder als **professioneller PDF-Report** ausgegeben.

## Disruption Score

Der Score bewertet auf einer Skala von 0–100, wie ersetzbar ein SaaS-Produkt durch einen KI-Skill ist:

| Score  | Kategorie        | Bedeutung                                                     |
| ------ | ---------------- | ------------------------------------------------------------- |
| 0–10   | 🏛️ Unantastbar   | Fundamentale Infrastruktur. Kein .md-File kann das ersetzen.  |
| 11–25  | 🏰 Festung       | Starke Moats. Sehr schwer zu ersetzen.                        |
| 26–40  | 😰 Ins Schwitzen | Verwundbar in Teilen, aber Kern-Moat existiert.               |
| 41–60  | 🫠 Wackelkandidat | Signifikante Teile sind durch einen Skill abbildbar.          |
| 61–80  | 📉 Auf der Kippe | Der Großteil ist ein Workflow, den ein LLM direkt kann.       |
| 81–95  | 🫧 Fast weg      | Im Wesentlichen eine UI um einen Prozess, den Claude kann.    |
| 96–100 | 🪄 War nie nötig | Es ist buchstäblich ein Prompt.                               |

## Scoring-Dimensionen

| Dimension                | Gewicht | Was wird bewertet?                                 |
| ------------------------ | ------- | -------------------------------------------------- |
| Workflow-Komplexität     | 20%     | Einfache Transformation vs. Multi-System-Workflow  |
| Daten-Moat               | 20%     | Proprietäre Daten, Netzwerkeffekte, Lock-in        |
| Physische Infrastruktur  | 15%     | Hardware, Server, Echtzeit-Systeme                 |
| Regulatorischer Schutz   | 15%     | Lizenzen, Zertifizierungen, Compliance             |
| Integrations-Tiefe       | 15%     | API-Ökosystem, Marketplace, Partner-Netzwerk       |
| UI/UX-Abhängigkeit       | 10%     | Komplexe Echtzeit-UI jenseits von Text             |
| Preismodell-Vulnerabilität | 5%    | Überhöhtes Pricing für KI-triviale Leistungen      |

## Ausgabeformate

### HTML (Standard)

Interaktives React-Artifact mit Tab-Navigation, animiertem Score-Ring, Story, Claudes Selbsteinschätzung, kopierbarem SKILL.md und Analyse-Balkendiagramm. Modernes, helles Design im Teal/Indigo-Farbschema.

### PDF

Professioneller mehrseitiger Report (A4) mit Deckblatt, Score-Grafik, Story, Analyse-Tabelle und dem Replacement SKILL.md als Code-Block. Generiert mit ReportLab, bereit zum Verschicken oder Ausdrucken.

### Beide

Auf Wunsch werden beide Formate gleichzeitig erstellt — erst das interaktive Dashboard im Chat, dann das PDF als Download.

## Nutzung

Der Skill wird als Claude Skill (`.md`-Datei) in Claude eingebunden. Danach reicht eine einfache Nachricht:

```
Scanne Notion
```

```
Analysiere Grammarly als PDF
```

```
Kann Claude Jira ersetzen? Zeig mir beides.
```

Der Skill erkennt automatisch, welches Format gewünscht ist:
- **PDF:** "Report", "Bericht", "zum Ausdrucken", "als PDF"
- **HTML:** "interaktiv", "Dashboard", "Artifact" — oder einfach nichts sagen
- **Beide:** "beides", "HTML und PDF"

## Kalibrierung

Beispiel-Scores zur Einordnung:

| Unternehmen                        | Score   | Kategorie       |
| ---------------------------------- | ------- | --------------- |
| VeriSign (DNS Registry)            | ~4/100  | Unantastbar     |
| Stripe (Payment Infrastructure)    | ~12/100 | Festung         |
| Salesforce (CRM + Ecosystem)       | ~22/100 | Festung         |
| GoDaddy (Domains + Website Builder)| ~28/100 | Ins Schwitzen   |
| Grammarly (Schreibassistent)       | ~75/100 | Auf der Kippe   |
| Jasper AI (AI Content Generator)   | ~90/100 | Fast weg        |
| Prompt Wrapper ohne eigene Daten   | ~98/100 | War nie nötig   |

## Dateien

```
├── SKILL.md          # Der Claude Skill
├── README.md         # Diese Datei
└── index.html        # Landing Page / Demo
```

## Beispiel

Eine Live-Demo des Scanners (mit GitHub als Beispiel-Analyse) findest du in der `index.html` — einfach im Browser öffnen oder via GitHub Pages deployen.

## Stilregeln

- **Charmant-satirisch, nie gemein** — Humor auf Kosten des Geschäftsmodells, nicht der Menschen
- **Faktisch fundiert** — Jeder Witz basiert auf echten Features oder Pricing
- **Spezifisch** — Keine generischen Roasts, sondern konkrete Referenzen
- **Ehrlich bescheiden** — Claude übertreibt eigene Fähigkeiten nicht

## Lizenz

MIT — Nutze den Skill wie du möchtest. Vergiss nicht: Es ist Unterhaltung mit analytischem Kern.
