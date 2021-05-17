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
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) finden Sie die neuesten Versionshinweise für Cloud Manager in AEM als Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.5.0 wurde am 06. Mai 2021 veröffentlicht.
Die nächste Version ist für den 03. Juni 2021 geplant.

## Neue Funktionen {#whats-new}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, und zwar in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Im Arbeitsablauf &quot;Programm bearbeiten&quot;kann der Benutzer nur Nicht-Dezimalzahl-KPI-Werte festlegen.

* Zwischenweise auftretende Fehler beim Senden von Code an Adobe Git wurden nun behoben.

* Das Erlebnis &quot;Programm bearbeiten&quot;wurde aktualisiert.

## Fehlerbehebungen {#bug-fixes}

* Statt &#39;gelöschte&#39; Variablen zu entfernen, markiert die API der Pipelines-Variablen sie nur mit dem Status &#39;DELETED&#39;.

* Einige Qualitätsprobleme mit Code-Geruch haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1am UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als eine Version, die am Vortag erstellt wurde.

* Einige Adobe Managed Services-Kunden (AMS) konnten mit der Cloud Manager-API keine neuen Projekte in der Adobe I/O Developer Console erstellen.
