---
title: Versionshinweise für 2019.6.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.6.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.6.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.6.0.
translation-type: tm+mt
source-git-commit: 75563d3f4b2a27d943c052993c97d830338ead9c

---

# Versionshinweise für 2019.6.0 {#release-notes-for}

Die [!UICONTROL Cloud Manager]-Version 2019.6.0 enthält keine wesentlichen Funktionsänderungen. Weitere Informationen erhalten Sie im Folgenden.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is .

## Neuigkeiten {#whats-new}

* Neuer Assistent zur Produktaktualisierung, der Kunden bei der erfolgreichen Ausführung eines AEM-Updates unterstützt. (Link zur Seite des Produktaktualisierungsassistenten)
* Codequalitätsregeln, die Inhaltsstrukturen untersuchen. (Link zu Regelregeln für benutzerspezifische Code-Regeln)
* Die maximale Größe eines Git-Pushs wurde auf 1 GB erhöht.

## Fehlerbehebungen {#bug-fixes}

* In einigen Fällen konnten Pipelines aufgrund eines früheren Fehlers nicht gestartet werden.

## Bekannte Probleme {#known-issues}

* Der CSV-Download der Codequalität wird nicht immer nach Schweregrad sortiert.
* Falsch-Positiv-Werte können von der Regel configandinstallshouldonlycontainosginodes gemeldet werden, wenn osgi-Konfigurationen in einem verschachtelten Ordner unter einem config-Ordner platziert werden.
