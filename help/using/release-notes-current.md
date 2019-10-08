---
title: Versionshinweise für 2019.10.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.10.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.10.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.10.0.
translation-type: tm+mt
source-git-commit: de9d2834ffa6c235e580227bd020fb8a0b94d22c

---

# Versionshinweise für 2019.10.0 {#release-notes-for}

In der [!UICONTROL Cloud Manager]-Version 2019.10.0 wurden die Tests für Sicherheitskriterien aktualisiert, herunterladbare Überwachungsgrafiken hinzugefügt und einige von Kunden gemeldete Nutzungsprobleme korrigiert.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.10.0 is October 12, 2019.

## Neuigkeiten {#whats-new}

* Erhebliche Teile der Implementierungsschritte wurden leistungsfähiger gemacht.
* Gegebenenfalls wird die Version des Maven-Build-Projekts jetzt die Projektversion in git enthalten.
* Zur Buildzeit sind neue Umgebungsvariablen verfügbar.
* Nicht-Produktionslinien können sowohl von der Karte auf der Seite Überblick als auch von der API gelöscht werden.
* Es gibt einen neuen optionalen Genehmigungsschritt unmittelbar nach dem Bereitstellungsschritt der Stufe, jedoch vor dem Schritt des Sicherheitstests.
* Beim Konfigurieren einer CI/CD-Pipeline können das Abtrennen und Anfügen von Dispatcher-Instanzen vom Lastenausgleich für Entwicklungs- und Bereitstellungsumgebungen übersprungen werden.
* Die Cloud Manager-Befehlszeilenschnittstelle wurde erweitert, um den Zugriff auf ausführbare Protokolle zu unterstützen.
* Die Cloud Manager-API unterstützt jetzt die Bearbeitung der konfigurierten Verzweigung einer Pipeline.
* Anforderungen, die während des Leistungstests ausgeführt werden, enthalten jetzt ein bestimmtes Token ("CloudManagerTest") im Benutzeragent.

## Fehlerbehebungen {#bug-fixes}

* Einige Karten auf der Seite Überblick wurden nicht vertikal ausgerichtet.
* Bestimmte Fehlerbedingungen haben nicht dazu geführt, dass Pipeline-Hinrichtungen ordnungsgemäß markiert wurden und die Ausführung von Teilfolgen verhindert wurde.
