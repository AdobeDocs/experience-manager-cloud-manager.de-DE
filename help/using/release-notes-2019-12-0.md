---
title: Versionshinweise für 2019.12.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.12.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.12.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.12.0.
translation-type: tm+mt
source-git-commit: 0fa1fedccb013e82c8df5838a612ce26a1efb7e8

---


# Versionshinweise für 2019.12.0 {#release-notes-for}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!UICONTROL Cloud Manager] Version 2019.12.0 erläutert und aktuelle Informationen zur Pipeline-Ausführung sowie zu Verbesserungen bei Code-Qualitäts-Scans aufgeführt.
Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.12.0 wurde am Donnerstag, 12. Dezember 2019 veröffentlicht.

## Neuerungen {#whats-new}

* Die Schritte in der Pipeline-Ausführung enthalten jetzt einen Zeitstempel für die Fertigstellung jedes Schritts.
* Code-Qualitäts-Scans für Projekte, die keinen Java-Code enthalten, melden jetzt eine Abdeckungsquote von 100 %.
* Die Konsistenzprüfung „CQ-Dispatcher-Konfiguration“ wurde entfernt.

## Fehlerbehebungen {#bug-fixes}

* Datumsangaben wurden in bestimmten Browsern nicht korrekt angezeigt.
* In seltenen Fällen wechselte die Produktions-Pipeline in den Genehmigungsschritt wechseln, während der Performance-Test noch lief.
* Bei bestimmten Status wurden die Schaltflächen im oberen Bereich der Übersichtsseite nicht korrekt ausgerichtet.
* Unter bestimmten Umständen wurde unbefugten Benutzern eine Schaltfläche zum Starten der Pipeline angezeigt, ein Klick auf die Schaltfläche war jedoch nicht möglich.
* Die Aktionsschaltflächen für produktionsfremde Pipelines wurden gelegentlich an der falschen Stelle angezeigt.
* Pakete mit dem Knotentyp „granite:Ranking“ konnten nicht auf bestimmte Verstöße gegen Qualitätsregeln überprüft werden.
* Bestimmte Probleme im Code-Qualitätsprozess wurden fälschlicherweise als Fehler gezählt.
* Überwachungsdaten konnten für bestimmte Topologien nicht geladen werden.
