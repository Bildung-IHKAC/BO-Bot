---
type: Datenmodell
title: "Datenmodell für regionale Kammermodule Berufsorientierung"
description: "Feldstruktur eines austauschbaren IHK-bezirksspezifischen Berufsorientierungsmoduls."
resource: ""
tags: [berufsorientierung, kammermodul, datenmodell, ihk]
status: draft
generated:
  by: "DIKA/IHK-Architekt"
  at: 2026-08-13T10:00:00+02:00
stale_after: 2027-01-31
---

# Datenmodell für regionale Kammermodule Berufsorientierung

## Zweck und Geltungsbereich

Ein Kammermodul ergänzt bundesweite und landesbezogene Berufsorientierungsinformationen um Daten eines konkreten IHK-Bezirks. Es enthält regionale Angebote, Kontakte, Kennzahlen und Besonderheiten. Die strukturelle Trennung ermöglicht den Austausch einzelner Kammermodule ohne Veränderung der Kerncluster oder Landesmodule.

Das ausgefüllte Referenzbeispiel ist das [Kammermodul IHK Aachen](bo-kammermodul-ihk-aachen.md).

## Grundstruktur eines Kammermoduls

- **Datenbereich:** Geltungsbereich; **Inhalt:** IHK, Kreise, kreisfreie Städte und Grenzbezüge; **Aktualität:** bei Gebiets- oder Strukturänderung
- **Datenbereich:** Kammerprofil; **Inhalt:** Mitgliedsunternehmen, Branchen, Ausbildungsbetriebe; **Aktualität:** jährlich
- **Datenbereich:** Ausbildungsmarkt; **Inhalt:** Verträge, Veränderungen, freie Stellen, Stichtage; **Aktualität:** jährlich und anlassbezogen
- **Datenbereich:** Kontakte; **Inhalt:** Funktionen, öffentliche Kontaktwege, Zuständigkeiten; **Aktualität:** bei Personal- oder Kontaktänderung
- **Datenbereich:** Angebote; **Inhalt:** Atlas, Lehrstellenbörse, Ausbildungsbotschafter, Veranstaltungen; **Aktualität:** laufend
- **Datenbereich:** Regionale Besonderheiten; **Inhalt:** Strukturwandel, Branchencluster, Kooperationen; **Aktualität:** jährlich
- **Datenbereich:** Datenlücken; **Inhalt:** Nicht bestätigte oder fehlende Angaben; **Aktualität:** bei jeder Aktualisierung

## Metadatenprofil

- **Feld:** type; **Datentyp:** OKF-Typ; **Beispielwert:** Serviceangebot
- **Feld:** title; **Datentyp:** Text; **Beispielwert:** Berufsorientierung 2026: Kammermodul IHK Beispielstadt
- **Feld:** description; **Datentyp:** Text bis 150 Zeichen; **Beispielwert:** Regionale Angebote und Ausbildungsmarktdaten einer IHK
- **Feld:** resource; **Datentyp:** URL oder leerer Text; **Beispielwert:** leerer Text bei abgeleitetem Wissensdokument
- **Feld:** tags; **Datentyp:** Liste; **Beispielwert:** berufsorientierung, ihk-beispielstadt, kammermodul
- **Feld:** status; **Datentyp:** Lebenszykluswert; **Beispielwert:** draft oder stable
- **Feld:** generated; **Datentyp:** Objekt; **Beispielwert:** Ersteller und Zeitstempel
- **Feld:** stale_after; **Datentyp:** Datum; **Beispielwert:** nächster regelmäßiger Prüfzeitpunkt

## Datenobjekte

### Kammerprofil

- **Attribut:** Kammername; **Bedeutung:** Vollständige Bezeichnung der IHK
- **Attribut:** Bezirk; **Bedeutung:** Räumliche Zuständigkeit
- **Attribut:** Mitgliedsunternehmen; **Bedeutung:** Bezugsjahr und Zahl
- **Attribut:** Schwerpunktbranchen; **Bedeutung:** Regionale Branchen oder Cluster
- **Attribut:** Ausbildende Betriebe; **Bedeutung:** Zahl und Stichtag

### Ausbildungsmarkt

- **Attribut:** neu eingetragene Verträge; **Bedeutung:** Zahl, Stichtag und Ausbildungsjahr
- **Attribut:** Veränderung; **Bedeutung:** Vergleichswert und Bezugsjahr
- **Attribut:** freie Ausbildungsplätze; **Bedeutung:** Zahl, Quelle und Stichtag
- **Attribut:** Besonderheiten; **Bedeutung:** etwa Schulstruktur, Branchenlage oder demografische Effekte

### Kontakt

- **Attribut:** Funktion; **Bedeutung:** fachliche Zuständigkeit
- **Attribut:** Name; **Bedeutung:** nur öffentlich bestätigte Person
- **Attribut:** Telefon; **Bedeutung:** öffentliche Durchwahl oder zentrale Nummer
- **Attribut:** E-Mail; **Bedeutung:** öffentliche Funktions- oder Personenadresse
- **Attribut:** Gültigkeit; **Bedeutung:** Prüfdatum der Kontaktinformation

### Angebot

- **Attribut:** Bezeichnung; **Bedeutung:** Name des Angebots
- **Attribut:** Zielgruppe; **Bedeutung:** Schule, Jugendliche, Eltern, Betrieb oder weitere Gruppen
- **Attribut:** Inhalt; **Bedeutung:** fachliche Kurzbeschreibung
- **Attribut:** Zugang; **Bedeutung:** öffentliches Kontakt- oder Buchungsformat
- **Attribut:** Aktualität; **Bedeutung:** Gültigkeitszeitraum oder Stichtag

## Beispiele für modulare Nutzung

### Beispiel 1: Grenzregion

Eine Schule im Grenzraum zweier IHK-Bezirke nutzt das Landesmodul sowie zwei Kammermodule. Berufsangebote und Ansprechpartner bleiben den jeweiligen Bezirken zugeordnet.

### Beispiel 2: Neuer Ausbildungsmarktjahrgang

Ein neues Marktjahr verändert Kennzahlen und regionale Einordnung. Der aktualisierte Abschnitt Ausbildungsmarkt ersetzt die vorherige Fassung. Die Struktur der anderen Datenbereiche bleibt erhalten.

### Beispiel 3: Fehlende Programmdaten

Die Zahl aktiver Ausbildungsbotschafter ist nicht öffentlich bestätigt. Das Attribut erhält keinen geschätzten Wert. Die Information erscheint als dokumentierte Datenlücke.

## Qualitätskriterien

- Jede quantitative Angabe enthält Bezugsjahr und Stichtag.
- Kontaktinformationen stammen aus öffentlichen oder intern bestätigten Quellen.
- Platzhalter und Schätzwerte sind von bestätigten Angaben unterscheidbar.
- Regionale Daten stehen nicht in Kern- oder Landesmodulen.
- Das Modul verlinkt auf den [Index](index.md) und relevante Kern- sowie Landesdateien.
- Jedes ausgefüllte Kammermodul verweist auf die fachlich relevanten Kern- und Landesdateien.

## Glossar

- **Begriff:** Kammermodul; **Bedeutung:** Regional austauschbares Wissensdokument einer IHK
- **Begriff:** Stichtag; **Bedeutung:** Zeitpunkt einer Kennzahl oder Sachinformation
- **Begriff:** Datenlücke; **Bedeutung:** Bekannter Informationsbedarf ohne bestätigten Wert
- **Begriff:** Geltungsbereich; **Bedeutung:** Räumlicher und sachlicher Anwendungsbereich eines Dokuments

## Versionsinformationen

Version: 2.0
Datum: 13.08.2026
Erstellt von: DIKA/IHK-Architekt

*Diese Datei ist Teil eines Flat Bundles. Siehe [Index](index.md) für alle verfügbaren Dokumente.*
