---
title: Versionshinweise für 2024.7.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d7c4c87bbc3c66ca9517c4d0c97e25a2302e1e8a
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 96%

---


# Versionshinweise für Cloud Manager Version 2024.7.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.7.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] Version 2024.7.0 ist der 18. Juli 2024. Die nächste Version ist für den 12. August 2024 geplant.

## Neue Funktionen {#what-is-new}

* Für [Produktions-Pipeline](/help/using/production-pipelines.md#adding-production-pipeline) und [produktionsfremde Pipeline](/help/using/non-production-pipelines.md#adding-non-production-pipeline) ist jetzt der Trigger **Bei Git-Änderungen** für [private Repositorys](/help/managing-code/private-repositories.md) verfügbar, um die Pipeline bei einem Commit zu starten.
* Eine Vorproduktions-Pipeline ist nur manuell auslösbar und kann nicht als **Bei Git-Änderungen** konfiguriert werden.
* Bei reinen Produktions-Pipelines enthält die Liste der heraufstufbaren Ausführungen diejenigen, die eine höhere Artefaktversion als die in der Produktionsumgebung bereitgestellte Artefaktversion haben.
* [Der AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) wurde auf [Version 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49) aktualisiert.


## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Reine Staging- und Produktions-Pipelines {#staging-production-only-pipelines}

Die Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) wurde eingeführt, sodass Sie Full-Stack-Produktionsbereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen können.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com`.
