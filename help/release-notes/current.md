---
title: Versionshinweise für 2022.9.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.9.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e74d386d0b2d50a7e276bb7ead7594ef448742ae
workflow-type: ht
source-wordcount: '200'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2022.9.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.9.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2022.9.0 ist der 8. September 2022. Die Veröffentlichung der nächsten Version ist für den 6. Oktober 2022 geplant.

## Neue Funktionen {#what-is-new}

* Cloud Manager-Unterstützung für horizontales automatisches Skalieren mehrerer Regionen.
* Die neue Willkommensseitenkarte wurde für Benutzende angepasst, die nur über eine Cloud Manager-Benutzerrolle verfügen, und zeigt ihnen, wie sie auch bei eingeschränktem Programmzugriff zu AEM-Umgebungen navigieren können.
* Kunden ohne Cloud Manager-Rolle können nicht auf Programmdetails zugreifen. Sie können jedoch von der CM-Landingpage aus zu den Autoren-Endpunkten navigieren.
* Eliminierung von Pipeline-Fehlern, die durch Wiederholungsfehler verursacht werden, durch den Aufbau einer größeren Ausfallsicherheit.

## Fehlerbehebungen {#bug-fixes}

* Verbessertes Kunden-Feedback in Bezug auf die Erstellung von AEM-Programmen, wenn Maven Probleme mit der Verbindung zu privaten Repositorys hat.
* In seltenen Fällen, in denen das Konsistenzprüfungs-System keinen gültigen Konsistenzwert abrufen kann, wird kein Auto-Skalierungs-Ereignis ausgelöst.
