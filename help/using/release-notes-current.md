---
title: Versionshinweise für 2019.9.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.9.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.9.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.9.0.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Versionshinweise für 2019.9.0 {#release-notes-for}

The Cloud Manager 2019.9.0 Release updates the security test criteria, adds downloadable monitoring graphs, and fixes some customer-reported usability issues.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.9.0 wurde am 12. September 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Die Kategorisierung des Sling Referrer Filter-Gesundheitschecks wurde von "Wichtig"in "Wichtig"geändert.
* The categorization of the HTML Library Manager Config health check has been changed from Critical to Important.
* Monitoring graphs can now be downloaded. Weitere Informationen finden Sie unter [Überwachen Ihrer Umgebungen](monitor-your-environments.md).
* Wenn in einem Programm keine Produktions-AEM-Umgebung vorhanden ist, wird durch Klicken auf die Programmkarte auf der Einstiegsseite zur Übersichtsseite von Cloud Manager navigiert, es wird kein Fehlerdialogfeld angezeigt.
* Die **Pipeline-Einstellungskarte** auf der Seite " **Übersicht** "wurde auf **Produktions-Pipeline-Einstellungen** eingestellt.
* Die Optionsfelder "Wichtiges Fehlerverhalten"wurden aus reinen Codequalitätslinien entfernt.
* Auf der Seite " **Aktivität** "wird nun der Name der Pipeline für jede Ausführung angezeigt.
* Auf der Ausführungsseite wird nun der Name der Pipeline angezeigt.
* Im Dialogfeld "Codequalitätszusammenfassung"wird nun eine Beschreibung für jede Bewertung angezeigt.

## Fehlerbehebungen {#bug-fixes}

* Einige Benutzer konnten keine Ausführungsdetails anzeigen, während sie auf die Genehmigung warteten.
* Auf der Seite **Übersicht** war der rechte Rand nicht konsistent.
* Dem Buildcontainer könnte in großen Projekten der Arbeitsspeicher ausgehen.
* Unter bestimmten Umständen hat die BallowedPaths OakPAL-Regel nicht den installierten Inhalt unter /libs identifiziert.
* Als ein Qualitätsgate abgelehnt wurde, zeigte die Überschrift des Dialogfelds weiterhin *teilweise bestanden*.

## Bekannte Probleme {#known-issues}

* Das Herunterladen von Überwachungsdiagrammen ist in Safari nicht verfügbar.
