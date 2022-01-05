---
title: Versionshinweise für 2021.11.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.11.0
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6852df51d4b9b4947f1d5ce0b5a284bef94d0589
workflow-type: ht
source-wordcount: '372'
ht-degree: 100%

---

# Versionshinweise für 2021.11.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.11.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.11.0 wurde am 4. November 2021 veröffentlicht.
Die nächste Version soll am 16. Dezember 2021 veröffentlicht werden.

## Neue Funktionen {#whats-new}

* Die Git-Commit-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Verfolgung des erstellten Codes erleichtert.

* Der Antwort-Header `x-request-id` ist jetzt im API Playground auf [www.adobe.io](https://www.adobe.io/) sichtbar. Dieser Header ist beim Senden von Problemen an die Kundenunterstützung zur Fehlerbehebung nützlich.

* Als Benutzer sehe ich die Pipeline-Karte mit null Pipelines, die mir eine entsprechende Anleitung bieten.

* Auf einer neuen Aktivitätsseite können jetzt Aktivitäten wie Pipeline- und Code-Ausführungen zusammen mit den zugehörigen Details angezeigt werden. Im Laufe der Zeit werden auf dieser Seite immer mehr Aktivitäten und Details aufgelistet.

* Die neue Pipelines-Seite enthält ein Status-Popover, in dem eine Zusammenfassung der Details eingeblendet wird, sobald der Mauszeiger über eine Aktivität bewegt wird. Pipeline-Ausführungen können zusammen mit den zugehörigen Details angezeigt werden.

* Die API zur Pipeline-Bearbeitung unterstützt jetzt das Festlegen der Pfade für Dispatcher-Invalidierung und -Leerung.

* Außerdem unterstützt sie jetzt das Ändern der in den Bereitstellungsphasen verwendeten Umgebung.

* Für große Pakete wurde eine Optimierung des OakPal-Scan-Prozesses eingeführt.

* Die CSV-Datei mit Qualitätsproblemen enthält jetzt für jedes Qualitätsproblem einen Zeitstempel.

* Die Schaltfläche „Verwalten“ auf der Seite „Umgebungen“ ist nicht mehr auf der Benutzeroberfläche sichtbar.

## Fehlerbehebungen {#bug-fixes}

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Beenden des Build-Containers zu überflüssigem Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn keine Bereitstellungsphase vorhanden ist.

* Die Qualitätsregel `ClientlibProxyResourceCheck` meldete falsch positive Probleme, wenn Client-Bibliotheken mit gemeinsamen Basispfaden vorhanden waren.

* In der Fehlermeldung beim Erreichen der maximalen Anzahl von Repositorys war kein Grund für den Fehler angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.
