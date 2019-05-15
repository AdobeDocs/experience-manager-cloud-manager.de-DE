---
title: Versionshinweise für 2019.4.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.4.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.4.0.
translation-type: tm+mt
source-git-commit: 1dfb065c09569f811e5a006d3d74825d3bd7cc8d

---


# Versionshinweise für 2019.4.0 {#release-notes-for}

Die Cloud [!UICONTROL Manager] Release 2019.4.0 enthält keine wesentlichen Funktionsänderungen. Weitere Informationen finden Sie in den folgenden Abschnitten.

## Veröffentlichungsdatum {#release-date}

Das Release-Datum für [!UICONTROL Cloud Manager] Version 2019.4.0 ist 18. April 2019.

## Neuigkeiten {#whats-new}

* Die Cloud Manager-Benutzeroberfläche ist jetzt auf Englisch, Französisch, Deutsch und Japanisch verfügbar.
* Bereitstellungsschritte enthalten jetzt den derzeit ausgeführten Prozess, d. h. wenn eine Sicherung ausgeführt wird, werden Pakete installiert und Lastenausgleich wird neu konfiguriert.

## Fehlerbehebungen {#bug-fixes}

* Der Bereitstellungsansatz für Dispatcher-Änderungen wurde verbessert, um zusätzliche Anwendungsfälle zu verarbeiten.
* Einige Instanzgrößen wurden auf der Seite Umgebungen nicht korrekt angezeigt.
* Die Codequalitätsregeln CQBP -84-dependencies erzeugten falsch-positive Ergebnisse für eingebettete Adobe-Bibliotheken wie WCM Core Components und Asset Share Commons.
* Die Details für den Codescanschritt wurden aktiviert, wenn die Details nicht verfügbar waren.
* Die Fehlermeldung, wenn ein ungültiger Wert für die Seitenansichten pro Minute angegeben wurde, hatte die falsche untergrenze.
* Die Bereitstellungskategorie in einer Nicht-Produktions-Pipeline wurde falsch großgeschrieben.
* Der Aktionsaufruf auf der **Seite Überblick** enthielt fehlerhafte Text, wenn das git-Repository nicht ordnungsgemäß konfiguriert war.

## Bekannte Probleme {#known-issues}

* SLA-Werte können falsch gerundet werden.
