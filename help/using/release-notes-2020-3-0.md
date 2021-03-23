---
title: Versionshinweise für 2020.3.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.3.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.3.0.
feature: Versionshinweise
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 100%

---

# Versionshinweise für 2020.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.3.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.3.0 wurde am 05. März 2020 veröffentlicht.

## Neuerungen {#whats-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden für bessere Übersichtlichkeit geändert.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte Bereitstellungskonfigurationen konnten dazu führen, dass Protokolle für die Bereitstellungsschritte nicht verfügbar waren, wenn die Bereitstellung fehlschlug.
* Bestimmte Fehler innerhalb der Bereitstellungsschritte für Managed Services-Programme konnten dazu führen, dass nachfolgende Ausführungen nicht starten können.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Null Pointer-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.