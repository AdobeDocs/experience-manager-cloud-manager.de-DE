---
title: Versionshinweise für 2021.8.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.8.0.
feature: Release Information
source-git-commit: c4deb06615652736ff7584566507a2b42a88bfb1
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---

# Versionshinweise für 2021.8.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] Version 2021.8.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.8.0 wurde am 12. August 2021 veröffentlicht.
Die nächste Version wird am 9. September 2021 veröffentlicht.

## Neue Funktionen {#whats-new}

* Self-Service-Funktion, mit der Benutzer über die Cloud Manager-Benutzeroberfläche mehrere Repositorys erstellen und verwalten können.

* SonarQube hat unnötigerweise Git-Verlaufsdaten gelesen. Auf großen Code-Basien konnte dies zu einer unnötigen Build-Leistungsbeeinträchtigung führen.

* Es ist jetzt eine API verfügbar, um den Maven-Abhängigkeits-Cache pro Pipeline zu invalidieren.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 29 aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Fehlerkorrektur – Wenn eine Pipeline gelegentlich aus irgendeinem Grund zweimal ausgelöst wird, führt dies nicht mehr dazu, dass eine der Ausführungen mit dem Fehler *Pipeline-Ausführungsstatus konnte nicht aktualisiert werden* fehlschlägt.
