---
title: Versionshinweise für 2020.3.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.3.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.3.0.
translation-type: tm+mt
source-git-commit: e7da473a22bec1d3d9b3d39bf654af0c596fe86d

---

# Versionshinweise für 2020.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.3.0.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2020.3.0 is March 05, 2020.

## Neuerungen {#whats-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden für bessere Übersichtlichkeit geändert.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte Bereitstellungskonfigurationen konnten dazu führen, dass Protokolle für die Bereitstellungsschritte nicht verfügbar waren, wenn die Bereitstellung fehlschlug.
* Bestimmte Fehler innerhalb der Bereitstellungsschritte für Managed Services-Programme konnten dazu führen, dass nachfolgende Ausführungen nicht starten können.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Null Pointer-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.