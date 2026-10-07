---
type: Playbook
title: Markdown-Output-Standards für KI-Generierung
description: Verbindliche Standards für Markdown-Generierung durch KI-Assistenten, OKF v0.2 konform.
resource: ""
tags: [markdown, standards, ki, output, formatierung]
status: stable
generated:
  by: DIKA/IHK-Architekt
  at: 2026-08-10T19:00:00Z
verified:
  by: human:ulrich.ivens
  at: 2026-08-10T20:00:00Z
sources:
  - id: ulrich-standards
    resource: ""
    title: Validierte Markdown-Standards von Ulrich Ivens
    author: human:ulrich.ivens
    last_modified: 2026-08-10
---

# 🎯 Markdown-Output-Generierung - Standards

## 📋 Übersicht

Dieses Dokument definiert verbindliche Standards und Anforderungen für die Ausgabe von Markdown-formatiertem Text durch KI-Assistenten, mit speziellem Fokus auf deutsche Inhalte der IHK Aachen und verschiedene Verwendungszwecke.

**Wichtiger Hinweis zur Terminologie:** Eine KI erzeugt technisch immer Markdown-Quelltext. Ob dieser gerendert (formatiert) oder als Rohtext erscheint, entscheidet die Anzeigeoberfläche, nicht der erzeugte Text selbst. Die folgenden Modi steuern daher, wie der Text verpackt wird, nicht ob er intern anders aufgebaut ist.

---

## 🔤 Zeichensatz & Encoding

### Deutsche Umlaute
- ✅ **Verwende echte deutsche Umlaute:** ä, ö, ü, ß, Ä, Ö, Ü
- ❌ **Vermeide HTML-Entities:** `&auml;`, `&ouml;`, `&uuml;`, `&szlig;`
- ❌ **Vermeide ASCII-Ersatz:** ae, oe, ue, ss

### Encoding
- **Standard:** UTF-8 **ohne BOM**
- **Begründung:** BOM (Byte Order Mark) verursacht Probleme bei Git-Diffs, YAML-Frontmatter, vielen Markdown-Parsern sowie auf Linux und macOS. Für GitHub und GitLab ist BOM schädlich.
- **Zielumgebungen:** Windows, macOS, Linux
- **Kompatibilität:** Outlook, Word, Teams, GitLab, GitHub

### Typografische Sonderzeichen (kritisch)
- ❌ **NIEMALS Em-Dash (`—`) oder En-Dash (`–`):** Stattdessen Minus (`-`) oder Klammern verwenden. Dies ist eine verbindliche Grundregel.
- ❌ **Keine typografischen Anführungszeichen in Code:** `"` `"` und `'` `'` brechen Code-Blöcke und Inline-Code. In Code ausschließlich gerade ASCII-Zeichen verwenden.
- ✅ **In Fließtext erlaubt:** deutsche Anführungszeichen `„..."`, sofern kein Code folgt.
- ❌ **Kein Ellipsis-Zeichen (`…`) in Codeblöcken:** stattdessen drei Punkte (`...`).

### Emojis
- ✅ **Vollständige Unicode-Unterstützung:** 🤖, 🎯, 📁, ⚙️, 💻, 📚, 🧠, 🔄
- ✅ **Semantische Zuordnung:** 🐛 für Bugs, 📈 für Statistiken, 🔐 für Sicherheit
- ⚠️ **Sparsam in Überschriften:** Emojis in H1/H2 können Inhaltsverzeichnis-Generatoren und Anker-Links (GitHub/GitLab) stören. Bei Dokumenten für Geschäftsführung, Politik oder externe Stellen zurückhaltend einsetzen.

---

## 📊 Strukturelemente

### Dateibaum-Darstellung
**Verwende ASCII-Zeichen für maximale Kompatibilität:**

```
projekt/
├── src/
│   ├── components/
│   │   ├── Header.js
│   │   └── Footer.js
│   └── utils/
│       └── helpers.js
├── docs/
│   └── README.md
└── package.json
```

**Zeichen-Set:**
- Verzweigung: `├──`
- Fortsetzung: `│   `
- Letzter Eintrag: `└──`

### Listen und Aufzählungen
```markdown
## ✅ Korrekte Verwendung:
- Punkt 1
  - Unterpunkt 1.1
  - Unterpunkt 1.2
- Punkt 2

## 🔢 Nummerierte Listen:
1. Erster Schritt
2. Zweiter Schritt
   1. Unterschritt 2.1
   2. Unterschritt 2.2
```

---

## 🎭 Ausgabe-Modi

### **Modus 1: Copy-Paste-Ready (Standard)**
**Verwendung:** Wenn formatierter Text direkt in Outlook, Word oder Teams weiterverwendet werden soll.

**Aktivierung:**
- Explizit: *"Erstelle copy-paste-ready Text"*
- Implizit: Bei Berichten, E-Mails, Dokumenten

**Eigenschaften:**
- ✅ Markdown wird in der Chatoberfläche **gerendert dargestellt**
- ✅ Formatierungen sind **visuell sichtbar**
- ✅ Kein Markdown-Block, der Rohtext erzwingt

**Praxis-Einschränkung (wichtig):** Beim Kopieren aus dem Chat in Office-Anwendungen wird Rich-Text-Formatierung nicht immer zuverlässig übernommen. Für garantiert formatierte Weitergabe an Word oder Outlook ist ein echtes `.docx` oder gerendertes HTML die sichere Wahl, nicht kopierter Markdown.

**Beispiel-Anfrage:**
> "Erstelle einen Bericht über unser Projekt für die Geschäftsführung"

### **Modus 2: Quellcode-Ausgabe (ungerendert)**
**Verwendung:** Wenn Markdown als Rohtext sichtbar bleiben muss, damit er woanders weiterverarbeitet wird.

Es gibt zwei Unterfälle mit demselben Ausgabeprinzip:

**2a) Repository-Dateien:** README.md, CHANGELOG.md, CONTRIBUTING.md für GitHub/GitLab.

**2b) Markdown als Nutzlast (Prompts & Wissen):** Der Markdown-Text ist selbst der Inhalt, der in ein anderes GPT, eine Wissensdatei oder ein Prompt-Feld eingesetzt wird. Er muss roh bleiben, weil ein anderes System ihn interpretiert.

**Aktivierung:**
- Explizit: *"Zeige mir den Markdown-Quellcode"*, *"Ich brauche den .md-Quelltext"*
- Explizit: *"Gib mir das als rohen Markdown aus"*, *"Das wird ein Prompt / Wissensbaustein"*

**Eigenschaften:**
- ✅ Gesamter Inhalt in **einem einzigen Code-Fence** eingeschlossen
- ✅ Markdown-Syntax bleibt sichtbar (`**fett**`, `*kursiv*`)
- ✅ Kein Mischen von gerendertem und ungerendertem Inhalt

**Verschachtelte Code-Blöcke (kritische Regel):** Wenn der Rohtext selbst Code-Blöcke enthält, muss der äußere Fence **mehr Backticks** haben als der innere. Faustregel: 4 Backticks außen, 3 innen. Bei noch tieferer Verschachtelung entsprechend eine Ebene mehr.

**Beispiel:**
`````markdown
````markdown
# Titel

**Fett**, *kursiv*, `inline-code`

```python
def hello():
    print("Hallo Welt!")
```
````
`````

### **Modus 3: Hybrid (Beide Modi)**
**Aktivierung:**
- Explizit: *"Zeige beides: formatiert und als Quellcode"*

**Ausgabe:**
1. Formatierte Vorschau (Modus 1)
2. Anschließend Quellcode-Block (Modus 2)

---

## 📜 Lizenz- und Rechtevermerke (optional, nur auf Anforderung)

**Standardverhalten:** Wird im Prompt nichts angegeben, wird **kein Lizenzblock** ausgegeben.

Auf Anforderung per Stichwort wird genau einer der folgenden Blöcke ans Dokumentende gesetzt. Der Rechteinhaber ist eine **Variable** und richtet sich nach dem Kontext (z. B. `IHK Aachen`, `Ulrich Ivens` oder beide).

### Stichwort: `intern`
Für IHK-interne Prozess- und Arbeitsdokumente, nicht zur Weitergabe.

```markdown
---
**Vertraulich - nur zur internen Verwendung**
Dieses Dokument ist ausschließlich für den internen Gebrauch der IHK Aachen bestimmt.
Weitergabe an Dritte nur mit ausdrücklicher Genehmigung.
```

### Stichwort: `copyright`
Klassischer Schutzvermerk, alle Rechte vorbehalten.

```markdown
---
© [Jahr] [Rechteinhaber]. Alle Rechte vorbehalten.
Vervielfältigung, Verbreitung oder Nutzung nur mit schriftlicher Genehmigung des Rechteinhabers.
```

Beispiel eingesetzt: `© 2026 IHK Aachen. Alle Rechte vorbehalten.`

### Stichwort: `CC` (offene Lizenz)
Nur wenn ausdrücklich eine Veröffentlichung unter offener Lizenz gewünscht ist.

```markdown
---
Dieses Werk von [Rechteinhaber] ist lizenziert unter CC BY-SA 4.0.
https://creativecommons.org/licenses/by-sa/4.0/deed.de
```

**Hinweis:** Die konkrete CC-Variante (BY, BY-SA, BY-NC usw.) im Prompt angeben, sonst Standard CC BY-SA 4.0.

---

## 🎨 Formatierungs-Standards

### Überschriften
```markdown
# 🎯 Hauptüberschrift (H1) - nur einmal pro Dokument
## 📋 Bereichsüberschrift (H2) - Hauptgliederung
### 🔧 Unterbereich (H3) - Detailgliederung
#### Feinunterteilung (H4) - sparsam verwenden
```

### Hervorhebungen
```markdown
**Fettdruck** für wichtige Begriffe
*Kursiv* für Betonungen
`Code` für technische Begriffe
> Zitate für wichtige Aussagen
```

### Code-Blöcke
Immer mit Sprach-Tag für Syntax-Highlighting:

````markdown
```python
def hello_world():
    print("Hallo Welt!")
```

```bash
cd /projekt && git commit -m "Update"
```
````

### Tabellen
```markdown
| Spalte 1 | Spalte 2 | Spalte 3 |
|----------|----------|----------|
| Wert A   | Wert B   | Wert C   |
| Wert D   | Wert E   | Wert F   |
```

**Grenzen von Markdown-Tabellen:** Keine Zeilenumbrüche innerhalb einer Zelle, kein Zusammenführen (Merge) von Zellen. Bei komplexen Inhalten auf eine HTML-Tabelle oder eine gegliederte Liste ausweichen.

---

## 🎯 Verwendungsszenarien

| Szenario | Modus | Besonderheiten |
|----------|-------|----------------|
| E-Mail (Outlook) | Copy-Paste-Ready | Kompakt, professionell, klare Aufzählungen |
| Bericht / Dokument | Copy-Paste-Ready | Gliederung, Inhaltsverzeichnis bei > 5 Abschnitten |
| README / Repository | Quellcode (2a) | Syntax-Highlighting, relative Links |
| Prompt / Wissensbaustein | Quellcode (2b) | Kompletter Inhalt in Fence, Backtick-Ebenen beachten |
| Checkliste / Workflow | Copy-Paste-Ready | Checkboxen `- [ ]` und `- [x]` |

---

## 🔧 Technische Spezifikationen

### Zeilenumbruch
- **Empfehlung:** Kein harter manueller Zeilenumbruch in Fließtext (verschlechtert Git-Diffs, ohne Renderwirkung). Alternativ ein Satz pro Zeile.
- **Feste Zeichengrenzen** (80-120) nur dort, wo sie technisch sinnvoll sind (Code, Konfigurationsdateien).

### Leerzeilen
```markdown
# Überschrift

Absatz mit Inhalt.

## Neue Sektion

Neuer Absatz nach Überschrift.

- Liste nach Leerzeile
- Zweiter Listenpunkt
```

### Escape-Zeichen
- `\*` für literale Sterne
- `\_` für literale Unterstriche
- **Literale Backticks:** nicht per Backslash, sondern durch Einrahmen mit mehr Backticks. Ein einzelnes Backtick zeigt man als `` ` `` mit doppelten Backticks außen.

---

## 🎪 Spezielle Anforderungen

### IHK-Kontext
- **Fachbegriffe:** Vollständig ausgeschrieben bei erster Erwähnung, Abkürzung in Klammern, z. B. "Industrie- und Handelskammer (IHK)"
- **Rechtschreibung:** Neue deutsche Rechtschreibung
- **Stil:** Professionell, direkt, zugänglich, kein Schmeicheln

### Mehrsprachigkeit
- **Primär:** Deutsch mit echten Umlauten
- **Code-Kommentare:** Englisch erlaubt
- **Fachbegriffe:** deutsche Übersetzung in Klammern

---

## 🚨 Häufige Fehler vermeiden

### ❌ Falsch
```markdown
# Ueberschrift ohne Umlaute
- [ ] Aufgabe mit &auml;
Text mit Em-Dash — hier falsch
**Fett** ohne Leerzeichen**falsch**
```

### ✅ Richtig
```markdown
# Überschrift mit Umlauten
- [ ] Aufgabe mit ä
Text mit Minus - hier korrekt (oder Klammern)
**Fett** mit Leerzeichen **korrekt**
```

---

## 🎯 Qualitätskontrolle

### Checkliste vor Ausgabe
- [ ] Deutsche Umlaute korrekt verwendet (kein ae/oe/ue, kein HTML-Entity)
- [ ] Kein Em-Dash (`—`) oder En-Dash (`–`) im gesamten Dokument
- [ ] Typografische Anführungszeichen in Code vermieden
- [ ] Richtiger Ausgabe-Modus gewählt (1, 2a, 2b oder 3)
- [ ] Bei Quellcode-Modus: Inhalt vollständig im Fence, Backtick-Ebenen korrekt (4 außen, 3 innen)
- [ ] Lizenzblock nur bei ausdrücklicher Anforderung, Rechteinhaber passend gesetzt
- [ ] UTF-8 ohne BOM
- [ ] Code-Blöcke mit Sprach-Tag
- [ ] Leerzeilen korrekt gesetzt

---

## Verknüpfungen

- Format-Spezifikation: [okf_spec_v0.2.md](okf_spec_v0.2.md)
- IHK Taxonomie: [ihk_taxonomy.md](ihk_taxonomy.md)
- Generic Taxonomie: [generic_taxonomy.md](generic_taxonomy.md)
- DIKA-IHK Prompt: [dika_ihk_prompt_v0.2.md](dika_ihk_prompt_v0.2.md)
- DIKA-Generic Prompt: [dika_generic_prompt_v0.2.md](dika_generic_prompt_v0.2.md)

---

*Diese Datei ist Teil eines Flat Bundles. Siehe [Index](index.md) für alle verfügbaren Dokumente.*

---

**Version:** 2.0
**Erstellt:** Oktober 2025 - Überarbeitet: Juli 2026
**Autor:** Ulrich Ivens, IHK Aachen
**Verwendung:** KI-Kontext für Markdown-Generierung
