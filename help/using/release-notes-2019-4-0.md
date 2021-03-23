---
title: Versionshinweise für 2019.4.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.4.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.4.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.4.0.
feature: Versionshinweise
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 100%

---


# Versionshinweise für 2019.4.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager]-Version 2019.4.0 enthält keine wesentlichen Funktionsänderungen. Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.4.0 wurde am 18. April 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Die Cloud Manager-Benutzeroberfläche ist jetzt auf Englisch, Französisch, Deutsch und Japanisch verfügbar.
* Die Bereitstellungsschritte enthalten nun den derzeit ausgeführten Prozess. Beim Ausführen einer Sicherung werden also Pakete installiert und der Lastenausgleich neu konfiguriert.

## Fehlerbehebungen {#bug-fixes}

* Die Bereitstellung für Dispatcher-Änderungen wurde verbessert, damit zusätzliche Anwendungsfälle verarbeitet werden können.
* Einige Instanzgrößen wurden auf der Seite „Umgebungen“ nicht korrekt angezeigt.
* Die Code-Qualitätsregeln „CQBP-84-dependencies“ resultierten in falsch positiven Ergebnissen für eingebettete Adobe-Bibliotheken wie „WCM Core Components“ und „Asset Share Commons“.
* Die Schaltfläche „Details“ für den Codescan-Schritt war aktiviert, wenn die Details nicht verfügbar waren.
* Die Fehlermeldung bei Angabe eines ungültigen Werts für die KPI „Seitenansichten pro Minute“ hatte die falsche Untergrenze.
* Die Bereitstellungskategorie in einer Nicht-Produktions-Pipeline war fälschlicherweise großgeschrieben.
* Der Aktionsaufruf auf der Seite **Überblick** enthielt einen fehlerhaften Text, wenn das Git-Repository nicht ordnungsgemäß konfiguriert war.

## Bekannte Probleme {#known-issues}

* SLA-Werte werden eventuell nicht korrekt gerundet.
