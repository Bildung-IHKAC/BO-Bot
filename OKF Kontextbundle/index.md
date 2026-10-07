---
type: Systemdokumentation
title: "Berufsorientierung 2026: OKF Flat Bundle Index"
description: "Navigation und Architektur des OKF-0.2-Wissensbundles Berufsorientierung."
resource: ""
tags: [berufsorientierung, okf, flat-bundle, ihk-aachen]
status: stable
generated:
  by: "DIKA/IHK-Architekt"
  at: 2026-08-13T10:00:00+02:00
stale_after: 2027-01-31
---

# Berufsorientierung 2026: OKF Flat Bundle Index

## Zweck

Dieses Flat Bundle bildet eine modulare Wissensbasis zur Berufsorientierung. Es verbindet bundesweite Grundlagen, NRW-spezifische Regelungen und regionale Informationen der IHK Aachen. Alle Dateien liegen im selben Verzeichnis und sind über relative Markdown-Links verbunden.

Die Wissensbasis unterstützt die sachliche Einordnung von Berufsorientierung für Lehrkräfte, Jugendliche, Eltern, Ausbildungsbetriebe und Bildungsakteure.

## Architektur

- **Wissensebene:** Kern; **Inhalt:** Bundesweit übertragbares Systemwissen, Instrumente, Zielgruppenwissen und Trends; **Austauschbarkeit:** für andere Länder und Regionen unverändert nutzbar
- **Wissensebene:** Landesmodul; **Inhalt:** Landesrechtliche und landesprogrammbezogene Informationen; **Austauschbarkeit:** gegen ein Modul eines anderen Bundeslandes austauschbar
- **Wissensebene:** Kammermodul; **Inhalt:** Regionale Kennzahlen, Kontakte, Angebote und Besonderheiten; **Austauschbarkeit:** gegen ein anderes IHK-Modul austauschbar
- **Wissensebene:** Metadaten; **Inhalt:** Navigation, Datenmodell und Pflegelogik; **Austauschbarkeit:** bundleweit gültig

## Dateiübersicht

- **Datei:** [bo-cluster-a-systemwissen.md](bo-cluster-a-systemwissen.md); **Typ:** Wissensdossier; **Ebene:** Kern; **Inhalt:** Rechtlicher Rahmen, Akteure und Übergangssystem; **Status:** stable
- **Datei:** [bo-cluster-b-instrumente.md](bo-cluster-b-instrumente.md); **Typ:** Wissensdossier; **Ebene:** Kern; **Inhalt:** Instrumente, Praktika, digitale Angebote und Begegnungsformate; **Status:** stable
- **Datei:** [bo-cluster-c-zielgruppen.md](bo-cluster-c-zielgruppen.md); **Typ:** Wissensdossier; **Ebene:** Kern; **Inhalt:** Wissen für Lehrkräfte, Jugendliche und Eltern; **Status:** stable
- **Datei:** [bo-cluster-d-trends.md](bo-cluster-d-trends.md); **Typ:** Wissensdossier; **Ebene:** Kern; **Inhalt:** Arbeitsmarkt, Nachhaltigkeit, Digitalisierung und KI; **Status:** stable
- **Datei:** [bo-landesmodul-nrw.md](bo-landesmodul-nrw.md); **Typ:** Wissensdossier; **Ebene:** Landesmodul; **Inhalt:** KAoA, StuBo, Berufswahlapp, G9-Effekt und AzubiTrain; **Status:** stable
- **Datei:** [bo-kammermodul-ihk-aachen.md](bo-kammermodul-ihk-aachen.md); **Typ:** Serviceangebot; **Ebene:** Kammermodul; **Inhalt:** IHK Aachen, Ausbildungsmarkt, Kontakte und Angebote; **Status:** stable
- **Datei:** [bo-kammermodul-template.md](bo-kammermodul-template.md); **Typ:** Datenmodell; **Ebene:** Metadaten; **Inhalt:** Struktur regionaler Kammermodule; **Status:** draft
- **Datei:** [bo-meta-pflege.md](bo-meta-pflege.md); **Typ:** Geschäftsprozess; **Ebene:** Metadaten; **Inhalt:** Aktualitäts- und Qualitätsmodell; **Status:** stable
- **Datei:** [index.md](index.md); **Typ:** Systemdokumentation; **Ebene:** Metadaten; **Inhalt:** Navigation und Architektur; **Status:** stable

## Verknüpfungslogik

Die Kerncluster verweisen auf das Landesmodul bei NRW-spezifischen Sachverhalten. Das Landesmodul verweist auf das Kammermodul bei regionalen Angeboten, Kontakten und Kennzahlen. Kammermodule können parallel bestehen, wenn Schulen oder Zielgruppen an Bezirksgrenzen Angebote mehrerer IHKs nutzen.

### Beispiel: Grenzregion

Eine Schule im Kreis Heinsberg nutzt die Kerncluster und das Landesmodul NRW. Ergänzend können ein Kammermodul der IHK Aachen und ein verfügbares Kammermodul eines angrenzenden IHK-Bezirks gelesen werden. Regionale Angebote bleiben dadurch erkennbar zugeordnet.

### Beispiel: Nutzung außerhalb von NRW

Ein anderes Bundesland verwendet die vier Kerncluster. Das Landesmodul NRW wird durch ein passendes Landesmodul ersetzt. Ein regionales Kammermodul ergänzt die Bundes- und Landesebene.

## Qualitätsstatus

Die Dateien wurden von OKF 0.1 auf OKF 0.2 überführt. Die Frontmatter enthalten Typ, Beschreibung, Ressource, Tags, Status, Erstellinformation und Aktualitätsdatum. Für zeitkritische und fachlich zentrale Aussagen werden, soweit verfügbar, strukturierte Quellen mit Titel, herausgebender Stelle, Ressource und Abrufdatum geführt. Nicht öffentlich hinreichend bestätigte Angaben erscheinen als Datenlücken.

## Versionsinformationen

Bundle-Version: 2.2
Datum: 24.08.2026
Überarbeitet von: IHK Aachen GPT auf Basis des bestehenden Bundle-Bestands und der Validierungsrecherche

*Diese Datei ist Teil eines Flat Bundles. Siehe [Index](index.md) für alle verfügbaren Dokumente.*
