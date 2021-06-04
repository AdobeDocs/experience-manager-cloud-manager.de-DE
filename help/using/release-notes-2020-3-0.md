---
title: Versionshinweise für 2020.3.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.3.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.3.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.3.0.
feature: Versionshinweise
exl-id: 1bebb051-0936-445e-a5de-8bb9063f3fb8
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2020.3.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2020.3.0.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2020.3.0 wurde am 5. März 2020 veröffentlicht.

## Neuigkeiten {#whats-new}

* Das Protokoll für den Build-Schritt ist jetzt verfügbar, während der Build-Schritt ausgeführt wird.
* Einige der Meldungen auf der Seite mit Details zur Pipelineausführung wurden für bessere Übersichtlichkeit geändert.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte Bereitstellungskonfigurationen konnten dazu führen, dass Protokolle für die Bereitstellungsschritte nicht verfügbar waren, wenn die Bereitstellung fehlschlug.
* Bestimmte Fehler innerhalb der Bereitstellungsschritte für Managed Services-Programme konnten dazu führen, dass nachfolgende Ausführungen nicht starten können.
* Die im Build-Schritt verwendete temporäre SonarQube-Instanz konnte gelegentlich nicht innerhalb des konfigurierten Timeouts gestartet werden.
* In bestimmten Projekten erzeugte die Option *ResourceResolver-Objekte sollten immer geschlossen werden* eine Null Pointer-Ausnahme. Dies hatte jedoch keine Auswirkungen auf die Ausführung der Pipeline.
