---
title: Versionshinweise für2023.8.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2023.8.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 39%

---


# Versionshinweise für Cloud Manager Version 2023.8.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2023.8.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2023.8.0 ist der 10. August 2023. Die nächste Version wird am 7. September 2023 veröffentlicht.

## Neue Funktionen {#what-is-new}

* Es wurden Verbesserungen vorgenommen, um die Verständlichkeit und das Erscheinungsbild von Fehlermeldungen in der Cloud Manager-Benutzeroberfläche zu verbessern.

## Fehlerbehebungen {#bug-fixes}

* Gelegentlich [Inhaltskopie](/help/using/content-copy.md) Prozesse, die blockiert werden, wurden behoben.
* Für Kunden, die New Relic One nicht verwenden, wurde ein vorübergehendes Testproblem behoben.
* [Die Qualitätsregeln für benutzerdefinierten Code](/help/using/custom-code-quality-rules.md) `SupportedRunmode` und `ImmutableMutableMixedPackage` wurden aus SonarQube entfernt, da sie nur für AEM as a Cloud Service gelten.
* Benutzer stoßen nicht mehr auf blockierte Pipelines, die sich im Ausführungsstatus zu befinden scheinen.
* Die **Umgebungen** Menü wird nun geschlossen, nachdem die **[Inhalt kopieren](/help/using/content-copy.md)** modal.
* [Neuausführung einer Pipeline](/help/using/code-deployment.md#reexecute-deployment) ist nicht mehr zulässig, wenn die vorherige Ausführung nicht über eine `commitId` wird auf den Build-Phase-Status gesetzt.
* Für seltene Fehler wird jetzt eine verständlichere Meldung angezeigt, wenn ein Benutzer auf eine Pipeline in der **Aktivität** oder **Pipeline** Bildschirme.
