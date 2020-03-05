---
title: Versionshinweise für 2020.3.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.3.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.3.0.
translation-type: tm+mt
source-git-commit: 44671d89edad0ccb6ded998b62beb5fa012678e9

---

# Versionshinweise für 2020.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.3.0.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.3.0 is March 05, 2020.

## Neuerungen {#whats-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden aus Gründen der Klarheit bearbeitet.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte Bereitstellungskonfigurationen können dazu führen, dass Protokolle für die Bereitstellungsschritte nicht verfügbar sind, wenn die Bereitstellung fehlschlug.
* Spezifische Fehler innerhalb der Implementierungsschritte für Managed Services-Programme können dazu führen, dass nachfolgende Ausführungen nicht gestartet werden können.
* Die im Buildschritt verwendete Kurzzeitinstanz SonarQube konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* In bestimmten Projekten sollte das *ResourceResolver-Objekt immer geschlossen* sein, wodurch eine Null-Zeiger-Ausnahme entsteht. Dies hatte jedoch keine Auswirkungen auf die Durchführung der Pipeline.


