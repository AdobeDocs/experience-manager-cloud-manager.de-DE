---
title: Versionshinweise für 2021.5.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2021.5.0.
feature: Versionshinweise
source-git-commit: 3f17f252d89a1753c9cb121461b048f619d28415
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Versionshinweise für 2021.5.0 {#release-notes-for}

Im folgenden Abschnitt finden Sie allgemeine Versionshinweise zu [!UICONTROL Cloud Manager] 2021.5.0.

>[!NOTE]
>Unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=de#getting-access) finden Sie die neuesten Versionshinweise zu Cloud Manager in AEM as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2021.5.0 wurde am 6. Mai 2021 veröffentlicht.
Die nächste Version ist für den 10. Juni 2021 geplant.

## Neuigkeiten {#whats-new}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt, wenn dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, und zwar in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der Public API enthält jetzt die Git-URL.

* Im Programmbearbeitungs-Workflow kann der Benutzer nur Nicht-Dezimalzahlwerte für KPIs festlegen.

* Periodisch auftretende Fehler beim Übertragen von Code an Adobe Git wurden nun behoben.

* Programmbearbeitung wurde modernisiert.

## Fehlerbehebungen {#bug-fixes}

* Statt „gelöschte“ Variablen zu entfernen, markiert die API der Pipeline-Variablen sie nur mit dem Status „DELETED“.

* Einige Code-Smell-Qualitätsprobleme haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1:00 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer war als eine Version, die am Vortag erstellt wurde.

* Einige Adobe Managed Services-Kunden (AMS) konnten mit der Cloud Manager-API keine neuen Projekte in der Adobe I/O Developer Console erstellen.
