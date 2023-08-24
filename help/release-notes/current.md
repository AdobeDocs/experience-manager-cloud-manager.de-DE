---
title: Versionshinweise für 2023.8.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2023.8.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: ht
source-wordcount: '216'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2023.8.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2023.8.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2023.8.0 ist der 10. August 2023. Die nächste Version ist für den 7. September 2023 geplant.

## Neue Funktionen {#what-is-new}

* Es wurden Verbesserungen vorgenommen, um die Verständlichkeit und die Anzeige von Fehlermeldungen in der Benutzeroberfläche des Cloud Managers zu verbessern.

## Fehlerbehebungen {#bug-fixes}

* Seltene Fälle, in denen Prozesse der [Inhaltskopie](/help/using/content-copy.md) stecken blieben, wurden behoben.
* Für Kunden, die New Relic One nicht verwenden, wurde ein vorübergehendes Testproblem behoben.
* [Die Qualitätsregeln für benutzerspezifischen Code](/help/using/custom-code-quality-rules.md) `SupportedRunmode` und `ImmutableMutableMixedPackage` wurden aus SonarQube entfernt, da sie nur für AEM as a Cloud Service gelten.
* Benutzerinnen und Benutzer werden nicht mehr auf hängende Pipelines stoßen, die scheinbar in Betrieb sind.
* Das Menü **Umgebungen** wird nun geschlossen, nachdem das Modal **[Inhalt kopieren](/help/using/content-copy.md)** ausgelöst wurde.
* [Eine erneute Ausführung der Pipeline](/help/using/code-deployment.md#reexecute-deployment) ist nicht mehr zulässig, wenn die vorherige Ausführung keine `commitId` auf den Status „Build-Phase“ gesetzt hat.
* Bei seltenen Fehlern wird nun eine verständlichere Meldung angezeigt, wenn eine Benutzerin bzw. ein Benutzer in den Bildschirmen **Aktivität** oder **Pipeline** auf eine Pipeline klickt.
