---
title: Versionshinweise für 2019.6.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.6.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.6.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur Version 2019.6.0 von AEM Cloud Manager.
feature: Versionshinweise
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# Versionshinweise für 2019.6.0 {#release-notes-for}

Die Version 2019.6.0 von [!UICONTROL Cloud Manager] enthält neue Code-Qualitätsregeln und einen neuen Assistenten für Produktaktualisierungen. Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.6.0 wurde am Donnerstag, 20. Juni 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Ein neuer Assistent für Produktaktualisierungen unterstützt Kunden bei der Ausführung einer AEM-Aktualisierung. Weitere Informationen finden Sie unter [Assistent für Produktaktualisierungen](overview-productupdate-wizard.md).
* Code-Qualitätsregeln zur Untersuchung von Inhaltsstrukturen. Weitere Informationen finden Sie unter [Benutzerspezifische Regeln für Code-Qualität](custom-code-quality-rules.md).
* Die maximale Größe eines Git-Pushs wurde auf 1 GB erhöht.

## Fehlerbehebungen {#bug-fixes}

* In einigen Fällen konnten Pipelines aufgrund eines vorherigen Fehlers nicht gestartet werden.

## Bekannte Probleme {#known-issues}

* Der Code-Qualität-CSV-Download wird nicht immer nach Schweregrad sortiert.
* Falsch-Positiv-Werte werden möglicherweise von der Regel *ConfigAndInstallShouldOnlyContainOsgiNodes* gemeldet, wenn sich OSGi-Konfigurationen in einem verschachtelten Ordner innerhalb eines *config*-Ordners befinden.