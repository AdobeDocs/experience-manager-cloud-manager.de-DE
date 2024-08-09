---
title: Versionshinweise für 2024.7.0
description: Informationen zu den Versionshinweisen für Cloud Manager 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 7%

---


# Versionshinweise für Cloud Manager 2024.7.0 {#release-notes}

Auf dieser Seite finden Sie die Versionshinweise für [!UICONTROL Cloud Manager] 2024.7.0.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Cloud Manager in den aktuellen Versionshinweisen zu AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Veröffentlichungsdatum {#release-date}

Die Version von [!UICONTROL Cloud Manager] 2024.7.0 wurde am 18. Juli 2024 veröffentlicht. Die nächste Version wird am Mittwoch, 13. August 2024 veröffentlicht.

## Neuerungen {#what-is-new}

* Die [Produktions-Pipeline](/help/using/production-pipelines.md#adding-production-pipeline) und der Trigger **On Git Changes** (Nicht-Produktions-Pipeline](/help/using/non-production-pipelines.md#adding-non-production-pipeline)), um die Pipeline bei einem Commit zu starten, sind jetzt für [private Repositorys](/help/managing-code/private-repositories.md) verfügbar.[
* Eine Pre-Production-Pipeline kann nur manuell ausgelöst werden und nicht als **On Git Changes** konfiguriert werden.
* Bei produktionsreinen Pipelines umfasst die Liste der förderbaren Ausführungen Ausführungen Ausführungen mit einer Artefaktversion, die größer ist als die in der Produktionsumgebung bereitgestellte Artefaktversion.
* [Der AEM Projektarchetyp](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview) wurde auf [Version 49](https://github.com/adobe/aem-project-archetype/tree/aem-project-archetype-49) aktualisiert.

## Frühzeitige Annahme {#early-adoption}

Nehmen Sie am Programm zur frühzeitigen Übernahme von Cloud Manager teil und haben Sie die Möglichkeit, einige bevorstehende Funktionen zu testen.

### Nur-Staging- und reine Produktions-Pipelines {#staging-production-only-pipelines}

Die Unterstützung für [ Nur-Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) ist jetzt eingeführt, sodass Sie produktionsübergreifende Produktions-Bereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen können.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com` von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse.
