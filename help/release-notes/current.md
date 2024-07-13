---
title: Versionshinweise für 2024.6.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.6.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 851b556c0917d9f6d97d958a0c8e8aeff4141079
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 100%

---


# Versionshinweise für Cloud Manager Version 2024.6.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.6.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2024.6.0 ist der 6. Juni 2024. Die nächste Version ist für den 18. Juli 2024 geplant.

## Neue Funktionen {#what-is-new}

* Jetzt ist die [Verwendung Ihrer eigenen GitHub-Repositorys](/help/managing-code/private-repositories.md) als Quellen für Full-Stack-Pipelines möglich.
   * Darüber hinaus können Sie GitHub-Repositorys mit [Git-Untermodulen](/help/managing-code/git-submodules.md) nutzen. So haben Sie mehr Kontrolle über die automatisch generierten Pipelines, die zur Prüfung von Pull-Anfragen verwendet werden, und können das Verhalten für wichtige Metriken während der Code-Scan-Phase definieren.
   * [Sie haben auch die Möglichkeit](/help/managing-code/github-check-config.md), den Berichtsverlauf auf GitHub beizubehalten, die Pipeline zu benennen und Pipeline-Variablen entsprechend Ihren Anforderungen festzulegen.
* Es wurden neue OakPal-Regeln zur [Code-Qualitätsprüfung von Cloud Manager hinzugefügt.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * Jede neue Regel, die ab Juni 2024 hinzugefügt wurde, ist eine unterbrechungsfreie Änderung.
   * Sie werden dringend aufgefordert, sich dieser so bald wie möglich anzunehmen, da diese neuen Regeln dazu führen, dass Pipelines ab der Cloud Manager-Version August 2024 fehlschlagen.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Reine Staging- und Produktions-Pipelines {#staging-production-only-pipelines}

Die Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) wurde eingeführt, sodass Sie Full-Stack-Produktionsbereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen können.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com`.
