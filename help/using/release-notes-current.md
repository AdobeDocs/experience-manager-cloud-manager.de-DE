---
title: Versionshinweise für 2020.7.0
seo-title: Versionshinweise für AEM Cloud Manager 2020.7.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2020.7.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2020.7.0.
translation-type: tm+mt
source-git-commit: 02515ac6e3ac54909e23a276a78f571ea5c249c4
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 35%

---

# Versionshinweise für 2020.7.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2020.7.0.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.7.0 von [!UICONTROL Cloud Manager] wurde am 09. Juli 2020 veröffentlicht.

## Neuerungen {#whats-new}

* Das Trennen und Anhängen von Dispatcher-Instanzen von den Lastenausgleichsmodulen während der Produktionsimplementierung funktioniert jetzt konsistenter.

* Der Cloud Manager Build Container unterstützt jetzt sowohl Java 8 als auch Java 11.

* Cloud Manager-Pipeline unterstützen jetzt kundenspezifische Variablen und Geheimnisse. Weitere Informationen finden Sie unter [Pipeline-Variablen](/help/using/create-an-application-project.md#pipeline-variables) .

## Fehlerbehebungen {#bug-fixes}

* Die **Optionen &quot;Abbrechen** &quot;und &quot; **Speichern** &quot;auf der Seite &quot;Bearbeiten in der Nicht-Produktion-Pipeline&quot;waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess können dazu führen, dass die Protokolldatei nicht korrekt generiert wird.

* Einige große Pipeline-Step-Protokolle konnten nicht konsistent über die Benutzeroberfläche heruntergeladen werden.

## Bekannte Probleme {#known-issues}

* Wenn eine AMS-Umgebung eine Standby-Instanz enthält, wird in der protokollierten Meldung angegeben, dass die Instanz im Gegensatz zum Standby-Modus ausfällt.
