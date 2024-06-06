---
title: Versionshinweise für 2024.6.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.6.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 48%

---


# Versionshinweise für Cloud Manager Version 2024.6.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.6.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] Version 2024.6.0 wurde am 6. Juni 2024 veröffentlicht. Die nächste Version ist für den 11. Juli 2024 geplant.

## Neue Funktionen {#what-is-new}

* Sie können jetzt [Verwenden Ihrer eigenen GitHub-Repositorys](/help/managing-code/private-repositories.md) als Quellen für Vollstapel- und Frontend-Pipelines.
   * Darüber hinaus können Sie GitHub-Repositorys mit [Git-Untermodule,](/help/managing-code/git-submodules.md) erhalten Sie eine verbesserte Kontrolle über die automatisch generierten Pipelines, die zur Überprüfung von Pull-Anforderungen verwendet werden, und können Verhalten für wichtige Metriken während der Codescan-Phase definieren.
   * [Sie haben auch die Wahl](/help/managing-code/github-check-config.md) Um den Berichtsverlauf auf GitHub beizubehalten, benennen Sie die Pipeline und legen Sie Pipeline-Variablen entsprechend Ihren Anforderungen fest.
* Neue OakPal-Regeln wurden zum [Überprüfung der Code-Qualität von Cloud Manager.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * Jede neue Regel, die ab Juni 2024 hinzugefügt wurde, ist eine ununterbrochene Änderung.
   * Sie werden dringend aufgefordert, diese so bald wie möglich zu beheben, da diese neuen Regeln dazu führen werden, dass Pipelines ab der Cloud Manager-Version vom August 2024 fehlschlagen.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Reine Staging- und Produktions-Pipelines {#staging-production-only-pipelines}

Die Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) wurde eingeführt, sodass Sie Full-Stack-Produktionsbereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen können.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com`.
