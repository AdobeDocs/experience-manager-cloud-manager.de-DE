---
title: Versionshinweise für 2024.7.0
description: Dies sind die Versionshinweise für Cloud Manager Version 2024.7.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: d536cd96d135e48039f94fd01142a63305b6eeae
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 61%

---


# Versionshinweise für Cloud Manager Version 2024.7.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] Version 2024.7.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2024.7.0 von [!UICONTROL Cloud Manager] wurde am 18. Juli 2024 veröffentlicht. Die nächste Version ist für den 8. August 2024 geplant.

## Neue Funktionen {#what-is-new}

* Die [Produktions-Pipeline](/help/using/production-pipelines.md#adding-production-pipeline) und der Trigger **On Git Changes** (Nicht-Produktions-Pipeline](/help/using/non-production-pipelines.md#adding-non-production-pipeline)), um die Pipeline bei einem Commit zu starten, sind jetzt für [private Repositorys verfügbar.](/help/managing-code/private-repositories.md)[
* Eine Pre-Production-Pipeline kann nur manuell ausgelöst werden und nicht als **On Git Changes** konfiguriert werden.
* Bei Pipelines, die nur für die Produktion vorgesehen sind, enthält die Liste der förderbaren Ausführungen diejenigen, deren Artefaktversion größer ist als die in der Produktionsumgebung bereitgestellte Artefaktversion.

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie an unserem Early-Adopter-Programm teil und nutzen Sie die Möglichkeit, einige zukünftige Funktionen zu testen

### Reine Staging- und Produktions-Pipelines {#staging-production-only-pipelines}

Die Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) wurde eingeführt, sodass Sie Full-Stack-Produktionsbereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen können.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe-ID verknüpfte E-Mail-Adresse eine E-Mail an `Grp-cloudmanager_splitpipelines@adobe.com`.
