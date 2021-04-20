---
title: Versionshinweise für 2019.8.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.8.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.8.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.8.0.
feature: Release Information
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 100%

---

# Versionshinweise für 2019.8.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager] 2019.8.0-Version enthält die Unterstützung von strukturierten Inhalten, verbessert die Leistung und behebt eine Vielzahl von kleineren Fehlern.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.8.0 wurde am 19. August 2019 veröffentlicht.

## Neuerungen {#whats-new}

* Neue Befehlszeilenschnittstelle zur Cloud Manager-API, mit Unterstützung von [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager).
* Bestimmte durch den Build erzeugte Inhaltspakete können als übersprungen deklariert werden und werden nicht bereitgestellt. Weitere Informationen finden Sie unter [Überspringen von Inhaltspaketen](/help/using/setting-up-project.md#skipping-content-packages).
* Der Satz vorab geladener Abhängigkeiten im Build-Container wurde überarbeitet, um einige unnötige Netzwerkanforderungen zu vermeiden.
* Die Meldung auf der Übersichtsseite für bestimmte falsch konfigurierte Programme wurde verbessert.

## Fehlerbehebungen {#bug-fixes}

* Beim Zugriff auf SLA-Berichte war das Standardjahr 2018, nicht 2019.
* Bei langen Umgebungsnamen wurde die Umgebungsauswahl im Bildschirm „Berichte“ nicht ordnungsgemäß vergrößert.
* Die Code-Qualitätsregel ***ConfigAndInstallShouldOnlyContainOsgiNodes*** erzeugte Fehlalarme, wenn die Sling-Rewriter-Komponente verwendet wurde.
* Die Code-Qualitätsregel ***ConfigAndInstallShouldOnlyContainOsgiNodes*** erzeugte Fehlalarme für bestimmte ungewöhnliche Pfadstrukturen.
* Nur-Assets-Kunden konnten nicht unterbrechungsfrei zu ihren AEM-Umgebungen navigieren.
* Das Dialogfeld „Verzweigung und Projekt erstellen“ wird in verschiedenen Browsern unterschiedlich dargestellt.
