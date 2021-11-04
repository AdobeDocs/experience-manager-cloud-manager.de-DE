---
title: Versionshinweise für 2021.11.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.11.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0395fd4263ae37bce49c698e8e72ad7b08af046a
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 22%

---

# Versionshinweise für 2021.10.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.11.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.11.0 wurde am 04. November 2021 veröffentlicht.
Die nächste Version ist für den 9. Dezember 2021 geplant.

## Neue Funktionen {#whats-new}

* Die Git-Zusage-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Verfolgung des erstellten Codes erleichtert.

* Die `x-request-id` Die Antwort-Kopfzeile ist jetzt in der API-Wiedergabe auf [www.adobe.io](https://www.adobe.io/). Diese Kopfzeile ist beim Senden von Problemen bei der Kundenunterstützung zur Fehlerbehebung nützlich.

* Als Benutzer sehe ich die Pipeline-Karte mit Null-Pipelines, die mir eine entsprechende Anleitung bietet.

* Eine neue Pipelines-Seite mit einem On-Hover-Status-Popup für einen einfachen Überblick über die Zusammenfassung der Details ist jetzt verfügbar. Pipeline-Ausführungen können zusammen mit den zugehörigen Details angezeigt werden.

* Die API Pipeline bearbeiten unterstützt jetzt das Festlegen der Dispatcher-Invalidierungs- und Flush-Pfade.

* Die API &quot;Pipeline bearbeiten&quot;unterstützt jetzt das Ändern der in den Bereitstellungsphasen verwendeten Umgebung.

* Für große Packages wurde eine Optimierung des OakPal-Scanprozesses eingeführt.

* Die CSV-Datei mit dem Qualitätsproblem enthält jetzt den Zeitstempel für jedes Qualitätsproblem.

* Die Schaltfläche Verwalten auf der Seite Umgebungen ist nicht mehr in der Benutzeroberfläche sichtbar.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Beenden des Build-Containers zu irrelevanten Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn die Bereitstellungsphase nicht vorhanden ist.

* Die `ClientlibProxyResourceCheck` Qualitätsregel verursachte falsch positive Probleme, wenn es Client-Bibliotheken mit gemeinsamen Basispfaden gab.

* Die Fehlermeldung, wenn die maximale Anzahl von Repositorys erreicht wurde, hat den Grund für den Fehler nicht angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.
