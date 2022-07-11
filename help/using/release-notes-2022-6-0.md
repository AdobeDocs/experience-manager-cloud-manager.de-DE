---
title: Versionshinweise für 2022.6.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2022.6.0.
feature: Release Information
source-git-commit: f202b245f35bcffa56b43f26a13b97d42fdb474e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2022.6.0 {#release-notes}

Auf dieser Seite werden die Versionshinweise für [!UICONTROL Cloud Manager] Version 2022.6.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2022.6.0 ist der 9. Juni 2022. Die nächste Version ist für den 30. Juni 2022 geplant.

## Neue Funktionen {#what-is-new}

* Eine neue Willkommenskarte auf der Landingpage von Cloud Manager bietet Benutzern schnellen Zugriff auf Onboarding-Tutorials und Fortschrittsmetriken zum Mandanten.
   * Diese Funktion wird in der Woche nach der Veröffentlichung von 2022.06.0 schrittweise eingeführt.
* [Build-Artefakte können jetzt bei Verwendung der Git-Spiegelung wiederverwendet werden](/help/using/setting-up-project.md#build-artifact-reuse).

## API-Änderungen {#api-changes}

* Die [`List Programs`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getPrograms)-API wird nicht mehr unterstützt und stattdessen sollte [`List Programs for Tenant`](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#operation/getProgramsForTenant) verwendet werden.
   * `List Programs` funktioniert weiterhin, aber die Verwendung führt zu Warnmeldungen in den Protokollen.
   * Es wird nach Ablauf von drei Monaten nicht mehr unterstützt.