---
title: Versionshinweise für 2021.5.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.5.0.
feature: Versionshinweise
source-git-commit: 83fcc49c7e3e3742930a7179b27f899bff3c4ae1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 18%

---

# Versionshinweise für 2021.5.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise für [!UICONTROL Cloud Manager] 2021.5.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) finden Sie die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.5.0 wurde am 06. Mai 2021 veröffentlicht.
Die nächste Version ist für den 3. Juni 2021 geplant.

## Neue Funktionen {#whats-new}

* Die Qualitätsregel PackageOverlaps erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Im Workflow Programm bearbeiten darf der Benutzer nur nicht-Dezimalwerte für KPIs festlegen.

* Beim Pushen von Code an Adobe Git wurden zeitweise auftretende Fehler behoben.

* Das Erlebnis Bearbeiten des Programms wurde aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Anstatt &quot;gelöschte&quot;Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status &quot;DELETED&quot;.

* Einige Qualitätsprobleme vom Typ Code Smell wirkten sich fälschlicherweise auf die Zuverlässigkeitsbewertung aus.

* Wenn die Pipelineausführung zwischen Mitternacht und 1 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als die am Vortag erstellte Version.

* Manche Adobe Managed Services (AMS)-Kunden konnten keine neuen Projekte in der Adobe I/O Developer Console mithilfe der Cloud Manager-API erstellen.
