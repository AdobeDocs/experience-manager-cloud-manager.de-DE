---
title: Versionshinweise für 2019.9.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.9.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.9.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.9.0.
translation-type: ht
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Versionshinweise für 2019.9.0 {#release-notes-for}

In der [!UICONTROL Cloud Manager]-Version 2019.9.0 wurden die Tests für Sicherheitskriterien aktualisiert, herunterladbare Überwachungsgrafiken hinzugefügt und einige von Kunden gemeldete Nutzungsprobleme korrigiert.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.9.0 wurde am 12. September 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Die Kategorisierung der Konsistenzprüfung des Sling Referrer Filters wurde von „Kritisch“ zu „Wichtig“ geändert.
* Die Kategorisierung der Konsistenzprüfung der Konfiguration des HTML-Bibliotheksmanagers wurde von „Kritisch“ zu „Wichtig“ geändert.
* Überwachungsdiagramme können jetzt heruntergeladen werden. Weitere Informationen finden Sie unter [Überwachen Ihrer Umgebungen](monitor-your-environments.md).
* Wenn in einem Programm keine AEM-Produktionsumgebung vorhanden ist, wird durch Klicken auf die Programmkarte auf der Landingpage zur Übersichtsseite von Cloud Manager navigiert, und es wird kein Fehlerdialogfeld angezeigt.
* Die Karte **Pipeline-Einstellungen** auf der Seite **Übersicht** wurde in **Einstellungen der Produktions-Pipeline** umbenannt.
* Die Optionsfelder für „Verhalten bei wichtigen Fehlern“ wurden aus Pipelines mit ausschließlichem Bezug zur Code-Qualität entfernt.
* Auf der Seite **Aktivität** wird nun der Name der Pipeline für jede Ausführung angezeigt.
* Auf der Ausführungsseite wird nun der Name der Pipeline angezeigt.
* Im Zusammenfassungsdialogfeld für die Code-Qualität wird nun eine Beschreibung für jede Bewertung angezeigt.

## Fehlerbehebungen {#bug-fixes}

* Einige Benutzer konnten keine Ausführungsdetails anzeigen, während die Genehmigung ausstand.
* Auf der Seite **Übersicht** war der rechte Rand nicht konsistent.
* Dem Buildcontainer konnte bei großen Projekten der Arbeitsspeicher ausgehen.
* Unter bestimmten Umständen hat die Regel „BannedPaths OakPAL“ nicht den installierten Inhalt unter „/libs“ identifiziert.
* Wenn ein Qualitäts-Gate abgelehnt wurde, wurde in der Überschrift des Dialogfelds weiterhin *Teilweise bestanden* angezeigt.

## Bekannte Probleme {#known-issues}

* Das Herunterladen von Überwachungsdiagrammen ist in Safari nicht verfügbar.
