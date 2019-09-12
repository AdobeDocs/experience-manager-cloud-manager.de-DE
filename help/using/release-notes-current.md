---
title: Versionshinweise für 2019.9.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.9.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.9.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.9.0.
translation-type: tm+mt
source-git-commit: 548d18f251cf8c4c827d2208fec04cde235ce731

---

# Versionshinweise für 2019.9.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager] Release 2019.9.0 enthält Aktualisierungen für Sling Referrer-Filter-Prüfungs- und -überwachungsdiagramme.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.9.0 wurde am 11. September 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Die Kategorisierung der Überprüfung der Sling Referrer-Filter wurde von kritischer Bedeutung geändert.
* Die Kategorisierung der Konfiguration der HTML-Bibliotheksmanager-Konfiguration wurde von kritischer in wichtig geändert.
* Überwachungsdiagramme können jetzt heruntergeladen werden. Weitere Informationen finden Sie unter [Überwachen Ihrer Umgebungen](monitor-your-environments.md).
* Wenn ein Programm nicht über eine AEM-Produktions-Produktionsumgebung verfügt, wird durch Klicken auf die Programmkarte von der Einstiegsseite auf der Übersichtsseite Cloud Manager kein Fehler ausgegeben.
* Die Pipeline-Einstellungskarte auf der Seite Überblick wurde auf **die Produktionspipeline-Einstellungen eingestellt**.
* Die Optionsfelder "Wichtige Fehler" -Optionsfelder wurden nur aus der Codequalität entfernt.
* Auf der Aktivitätsseite wird nun der Name der Pipeline für jede Ausführung angezeigt.
* Auf der Ausführungsseite wird nun der Name der Pipeline angezeigt.
* Im Dialogfeld zur Codequalität wird nun eine Beschreibung für jede Bewertung angezeigt.

## Fehlerbehebungen {#bug-fixes}

* Einige Benutzer konnten keine Ausführungsdetails anzeigen, wenn sie auf Genehmigung warten.
* Auf der Übersichtsseite war der rechte Rand nicht konsistent.
* Der Build-Container kann in großen Projekten nicht mehr genügend Speicher haben.
* Unter bestimmten Umständen konnte die oakpal-Regel "bannedpaths" installierte Inhalte unter /libs nicht identifizieren.
* Wenn ein Qualitätsgate abgelehnt wurde, wird in der Dialogfeldüberschrift immer noch "Teilweise weitergereicht" angezeigt.

## Bekannte Probleme {#known-issues}

Das Herunterladen von Überwachungsdiagrammen ist in Safari nicht möglich.
