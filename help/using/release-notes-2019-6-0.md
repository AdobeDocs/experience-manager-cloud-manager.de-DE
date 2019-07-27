---
title: Versionshinweise für 2019.6.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.6.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.6.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.6.0.
translation-type: tm+mt
source-git-commit: 7cfa0cf66efd5891263bfcc83a5149daec5c8b67

---

# Versionshinweise für 2019.6.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.6.0 Release adds new code quality rules and new Product Update wizard. Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is June 20, 2019 .

## Neuigkeiten {#whats-new}

* Neuer Assistent zur Produktaktualisierung, der Kunden bei der erfolgreichen Ausführung eines AEM-Updates unterstützt. Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* Codequalitätsregeln, die Inhaltsstrukturen untersuchen. Refer to [Custom Code Quality Rules](custom-code-quality-rules.md) for more information.
* Die maximale Größe eines Git-Pushs wurde auf 1 GB erhöht.

## Fehlerbehebungen {#bug-fixes}

* In einigen Fällen konnten Pipelines aufgrund eines früheren Fehlers nicht gestartet werden.

## Bekannte Probleme {#known-issues}

* Der CSV-Download der Codequalität wird nicht immer nach Schweregrad sortiert.
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a *config* folder.