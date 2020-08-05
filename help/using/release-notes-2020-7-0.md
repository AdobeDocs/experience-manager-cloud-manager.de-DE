---
title: Versionshinweise für 2020.7.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.7.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.7.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.7.0.
translation-type: tm+mt
source-git-commit: 3be958aa21d5423ddf371c286825d01afd554c4b
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 100%

---

# Versionshinweise für 2020.7.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.7.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.7.0 von [!UICONTROL Cloud Manager] wurde am 09. Juli 2020 veröffentlicht.

## Neuerungen {#whats-new}

* Das Trennen und Anhängen von Dispatcher-Instanzen von den Load Balancern während der Produktionsimplementierung funktioniert jetzt konsistenter.

* Der Cloud Manager-Build-Container unterstützt jetzt sowohl Java 8 als auch Java 11.

* Cloud Manager-Pipelines unterstützen jetzt benutzerspezifische Variablen und Geheimnisse.
Weitere Informationen finden Sie unter [Pipeline-Variablen](/help/using/create-an-application-project.md#pipeline-variables).

## Fehlerbehebungen {#bug-fixes}

* Die Optionen **Abbrechen** und **Speichern** auf der Seite „Bearbeiten“ für produktionsfremde Pipelines waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

## Bekannte Probleme {#known-issues}

* Wenn eine AMS-Umgebung eine Standby-Instanz enthält, wird in der protokollierten Meldung angegeben, dass die Instanz deaktiviert und nicht im Standby-Modus ist.

* Aufgrund einer Änderung bei der Berechnung der Code-Abdeckung ist die erforderliche _Mindestversion_ des Jacoco-Plugins jetzt 0.7.5.201505241946 (veröffentlicht im Mai 2015). Kunden, die eine ältere Version verwenden, erhalten eine Fehlermeldung im Code-Qualitätsprozess.
