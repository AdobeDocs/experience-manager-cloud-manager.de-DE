---
title: Versionshinweise für 2019.10.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.10.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.10.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.10.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 100%

---

# Versionshinweise für 2019.10.0 {#release-notes-for}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!UICONTROL Cloud Manager] Version 2019.10.0 erläutert und aktuelle Informationen über Bereitstellungsschritte und den Umgang mit Maven-Projektversionen aufgeführt.
Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

Die Version 2019.10.0 von [!UICONTROL Cloud Manager] wurde am 10. Oktober 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Wesentliche Bereiche der Implementierungsschritte sind nun leistungsfähiger.
* Gegebenenfalls enthält die Version des Maven-Build-Projekts jetzt die Projektversion in Git.
* Zum Build-Zeitpunkt sind neue Umgebungsvariablen verfügbar.
* Nicht-Produktions-Pipelines können sowohl aus der Karte auf der Seite **Übersicht** als auch der API gelöscht werden.
* Es gibt einen neuen optionalen Genehmigungsschritt unmittelbar nach dem Staging-Schritt, noch vor dem Sicherheitstest.
* Beim Konfigurieren einer CI/CD-Pipeline können das Trennen und Anfügen von Dispatcher-Instanzen vom Load-Balancer bei Entwicklungs- und Staging-Umgebungen übersprungen werden.
Weitere Informationen finden Sie unter **[Implementierungsverfahren](deploying-code.md#deployment-process)**.
* Die Befehlszeilenschnittstelle von Cloud Manager wurde erweitert, um Zugriff auf Protokolle für Ausführungsschritte zu unterstützen.
* Die Cloud Manager-API erlaubt nun eine Bearbeitung der konfigurierten Verzweigung einer Pipeline.
* Anfragen, die während eines Leistungstests ausgeführt werden, enthalten jetzt einen bestimmten Token ***CloudManagerTest*** im Agenten des Benutzers.

## Fehlerbehebungen {#bug-fixes}

* Einige Karten auf der Seite **Übersicht** waren nicht richtig vertikal ausgerichtet.
* Bestimmte Fehlerbedingungen haben dazu geführt, dass Pipeline-Ausführungen nicht ordnungsgemäß markiert wurden, und haben nachfolgende Ausführungen verhindert.
