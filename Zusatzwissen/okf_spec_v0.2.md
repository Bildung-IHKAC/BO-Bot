# Open Knowledge Format (OKF) v0.2 - Format-Spezifikation

**Format-Technische Spezifikation, unabhängig von inhaltlichen Taxonomien**

OKF ist ein offenes, herstellerneutrales Format zur Wissensdarstellung als
Markdown-Dateien mit YAML-Frontmatter. Jede OKF-Datei ist ein konformes
OKF Concept Document - interoperabel mit allen KI-Systemen, Agenten und
Wissenstools, die OKF verstehen.

---

## Core Principle

OKF v0.2 macht **Provenienz, Vertrauen, Aktualität und Lebenszyklus** zu
first-class Signalen im Frontmatter. Ein KI-System kann sofort erkennen:

- Woher der Inhalt kommt (`sources`)
- Wer ihn erzeugt und geprüft hat (`generated`, `verified`)
- Wie vertrauenswürdig er ist (`trust_tier`)
- Ob er noch aktuell ist (`status`, `stale_after`)

---

## Pflicht-Frontmatter-Struktur

Jede OKF-Datei beginnt zwingend mit diesem YAML-Block:

```yaml
---
type: <Typ aus der jeweiligen Domänen-Taxonomie oder freier deskriptiver Typ>
title: <Aussagekräftiger Titel des Konzepts>
description: <Ein Satz, max. 150 Zeichen - Kernaussage des Dokuments>
resource: <URL/URI zum Originaldokument | "" wenn kein Verweis vorhanden>
tags: [<tag1>, <tag2>, <tag3>]
status: stable          # draft | stable | deprecated
generated:
  by: <Ersteller/Agent>
  at: 2026-08-10T12:00:00Z
---
```

**Hinweis**: `okf_version` ist optional und kann bei Bedarf in `index.md`
am Bundle-Root angegeben werden. Die `type`-Werte stammen aus der jeweiligen
Domänen-Taxonomie (siehe Taxonomie-Index).

---

## Feldregeln

| Feld | Status | Regel |
|---|---|---|
| `type` | **Pflicht** | Aus Domänen-Taxonomie wählen oder freien Typ vergeben |
| `title` | Empfohlen | Menschenlesbarer Anzeigename des Konzepts |
| `description` | Empfohlen | Ein Satz, max. 150 Zeichen |
| `resource` | **Immer aktiv abfragen** | URL/URI zum Original; `""` wenn kein Verweis existiert |
| `tags` | Empfohlen | 2-5 Schlagwörter in Kleinschreibung |
| `status` | Empfohlen | `draft`, `stable` (default), oder `deprecated` |
| `generated` | Empfohlen | `{ by, at }` - wer und wann erzeugt |
| `verified` | Optional | `{ by, at }` - wer und wann geprüft |
| `sources` | Optional | Liste von Quellen mit `id`, `resource`, `title` |
| `stale_after` | Optional | Datum ab dem Inhalt als veraltet gilt |

---

## Provenienz und Quellen (`sources`)

Quellen werden **nicht** mehr als `# Citations` im Body, sondern als strukturierte
Frontmatter-Liste erfasst:

```yaml
sources:
  - id: quelle-1
    resource: https://example.com/dokument
    title: Beispiel-Dokument
    author: Autor-Name
    last_modified: 2024-03-15
```

Einzelne Aussagen im Body können über Markdown-Fußnoten auf Quellen verweisen:

```markdown
Die Abschlussprüfung besteht aus drei Teilen.[^quelle-1]

[^quelle-1]: Beispiel-Dokument
```

### Vertrauenssignale pro Quelle

Jede Quelle kann zusätzliche Signale enthalten:

- `author`: Wer hat die Quelle erstellt
- `usage_count`: Wie oft die Quelle genutzt wurde (optional)
- `last_modified`: Wann die Quelle zuletzt geändert wurde

---

## Vertrauen und Prüfung (`verified`, `trust_tier`)

```yaml
verified:
  - by: human:ulrich.ivens
    at: 2026-08-15T09:00:00Z
```

Daraus leitet sich automatisch die Vertrauensstufe ab:

- **unverified**: Kein `verified` vorhanden
- **machine-confirmed**: Nur maschinelle Prüfung
- **human-reviewed**: Mindestens eine menschliche Prüfung (`human:<id>`)

---

## Aktualität und Lebenszyklus

```yaml
status: stable
stale_after: 2027-08-10
```

- `status`: `draft` (noch nicht geprüft), `stable` (default), `deprecated` (veraltet)
- `stale_after`: Absolutes Datum ab dem der Inhalt als veraltet gilt

---

## Attested Computation (optional, für Berechnungen)

Für Kennzahlen und berechenbare Werte kann ein eigener Konzepttyp verwendet werden:

```yaml
type: Attested Computation
runtime: bigquery
parameters:
  - name: jahr
    type: integer
    required: true
executor:
  resource: references/skills/run-on-bq.md
  receipt:
    - job_id
    - executed_sql
    - result
attester:
  resource: references/attesters/umsatz.py
```

Dies beschreibt **wie** eine Berechnung verbindlich durchgeführt wird.

---

## Flat Bundle Option (für große Wissensdomänen)

Ein Flat Bundle besteht aus mehreren OKF-Einzeldokumenten im selben
Verzeichnis (Root), die sich gegenseitig via Markdown-Links referenzieren.
Jede Datei ist ein eigenständiges Concept Document. Eine optionale `index.md`
dient als Inhaltsverzeichnis und Navigationshilfe.

Vorteil: KI-Systeme laden gezielt nur die relevanten Dateien - messbare
Token-Ersparnis bei großen Wissensbasen. Anbieten wenn die Wissensdomäne
mehrere klar trennbare Konzepte mit je eigenem Scope enthält (Faustregel:
mehr als ca. 5.000 Token Gesamtinhalt).

---

## Abgrenzung zu OKF v0.1

| OKF 0.1 | OKF 0.2 |
|---|---|
| `timestamp` | `generated: { by, at }` |
| `# Citations` im Body | `sources` im Frontmatter |
| Keine Vertrauenssignale | `verified`, `trust_tier`, `status`, `stale_after` |
| Keine Attestation | `type: Attested Computation` (optional) |

**Rückwärtskompatibilität**: V0.2-Systeme dürfen `timestamp` und `# Citations`
für ältere Dokumente weiterhin lesen.

---

## Taxonomie-Referenz

Die `type`-Werte stammen aus der jeweiligen Domänen-Taxonomie:

- **IHK-Anwendungen**: `okf_taxonomien/ihk_taxonomy.md`
- **Generic-Anwendungen**: `okf_taxonomien/generic_taxonomy.md`
- **Andere Domänen**: Eigene Taxonomie-Datei im selben Format

Siehe auch: `okf_taxonomien/index.md`

---

## Quellen

- [OKF v0.2 Spezifikation (GitHub)](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
- [OKF v0.2 Migrations-Commit](https://github.com/GoogleCloudPlatform/knowledge-catalog/commit/780fe9d30b5bbca8931256edf1d0290d6bda5462)

---

## Historie

- 2026-08-10: Erste Version, Format-Spezifikation unabhängig von Taxonomien
