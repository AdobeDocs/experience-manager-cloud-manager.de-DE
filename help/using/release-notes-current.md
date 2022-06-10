---
title: Versionshinweise für 2022.6.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.6.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6dce1f48b66c6970c3ba025031f0adcbd01195dd
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 42%

---


# Versionshinweise für Cloud Manager Version 2022.6.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.6.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2022.6.0 wurde am 9. Juni 2022 veröffentlicht. Die nächste Version ist für den 30. Juni 2022 geplant.

## Neue Funktionen {#what-is-new}

* Eine neue Willkommenskarte auf der Landingpage von Cloud Manager bietet Benutzern schnellen Zugriff auf Onboarding-Tutorials und Fortschrittsmetriken zum Mandanten.
   * Diese Funktion wird in der Woche nach der Version 2022.06.0 schrittweise eingeführt.
* [Build-Artefakte können jetzt wiederverwendet werden](/help/using/setting-up-project.md#build-artifact-reuse) bei Verwendung von Git-Spiegeln.

## API-Änderungen {#api-changes}

* Die [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms) Die API wird nicht mehr unterstützt und [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) verwendet werden.
   * `List Programs` funktioniert weiterhin, aber die Verwendung erzeugt Warnmeldungen in Protokollen.
   * Es wird nach drei Monaten nicht mehr unterstützt.
