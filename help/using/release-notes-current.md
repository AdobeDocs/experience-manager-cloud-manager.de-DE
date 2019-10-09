---
title: Versionshinweise für 2019.10.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.10.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.10.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.10.0.
translation-type: tm+mt
source-git-commit: 1e927076e6bc84e8e1761e33a86cff61a3be0d2f

---

# Versionshinweise für 2019.10.0 {#release-notes-for}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!UICONTROL Cloud Manager] Release 2018.10.0 erläutert. Außerdem werden die Schritte zur Bereitstellung und die Handhabung der Projektversion durch Updates ergänzt.
Folgen Sie der unten stehenden Seite für weitere Details.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.10.0 is October 12, 2019.

## Neuigkeiten {#whats-new}

* Erhebliche Teile der Implementierungsschritte wurden leistungsfähiger gemacht.
* Gegebenenfalls wird die Version des Maven-Build-Projekts jetzt die Projektversion in git enthalten.
* Zur Buildzeit sind neue Umgebungsvariablen verfügbar.
* Nicht-Produktionslinien können sowohl von der Karte auf der Seite Überblick als auch von der API gelöscht werden.
* Es gibt einen neuen optionalen Genehmigungsschritt unmittelbar nach dem Bereitstellungsschritt der Stufe, jedoch vor dem Schritt des Sicherheitstests.
* Beim Konfigurieren einer CI/CD-Pipeline können das Abtrennen und Anfügen von Dispatcher-Instanzen vom Lastenausgleich für Entwicklungs- und Bereitstellungsumgebungen übersprungen werden.
Weitere Informationen finden Sie unter **[Bereitstellungsprozess](deploying-code.md#deployment-process)** .
* Die Cloud Manager-Befehlszeilenschnittstelle wurde erweitert, um den Zugriff auf ausführbare Protokolle zu unterstützen.
* Die Cloud Manager-API unterstützt jetzt die Bearbeitung der konfigurierten Verzweigung einer Pipeline.
* Anforderungen, die während des Leistungstests ausgeführt werden, enthalten jetzt einen bestimmten Token ***CloudManagerTest*** im Benutzeragent.

## Fehlerbehebungen {#bug-fixes}

* Einige Karten auf der Seite **Überblick** wurden nicht vertikal ausgerichtet.
* Bestimmte Fehlerbedingungen haben nicht dazu geführt, dass Pipeline-Hinrichtungen ordnungsgemäß markiert wurden und die Ausführung von Teilfolgen verhindert wurde.
