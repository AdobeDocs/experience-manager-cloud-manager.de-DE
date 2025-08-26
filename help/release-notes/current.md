---
title: Versionshinweise für Cloud Manager 2025.8.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.8.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: b34fe26f8c9a2d59a7df3d03717f302fe4456352
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 63%

---

# Versionshinweise für Cloud Manager 2025.8.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.8.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.8.0 ist Donnerstag, der Freitag, 7. August 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die Veröffentlichung der nächsten Version ist für den 4. September 2025 geplant.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Neue Funktionen {#what-is-new}

* **Adobe Experience Hub in Kürze verfügbar**

  Ab dem 19. August 2025 beginnt Adobe mit dem schrittweisen Rollout des neuen Experience Hub für alle Adobe Experience Manager-Benutzer.

  Experience Hub ist ein einheitlicher Ausgangspunkt, der personalisierte, kontextuelle Erlebnisse bereitstellt, mit denen Benutzende Ziele schneller erreichen können. Der Rollout endet am 26. August 2025, sodass er für alle Benutzer verfügbar ist. Die neue Experience Hub ist direkt unter [experience.adobe.com](https://experience.adobe.com/) verfügbar. Weitere Informationen finden Sie unter [Adobe Experience Hub](/help/experience-hub.md).

* **Pipelines nur für Staging und Produktion**

  Cloud Manager unterstützt jetzt Pipelines, die nur für Staging und Produktion vorgesehen sind. Mit dieser Funktion können Sie Full-Stack-Produktionsbereitstellungen in kleinere, zweckspezifische Pipelines aufteilen. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“ mit aktiviertem Optionsfeld „Full-Stack-Code“ und ausgewählter Staging-Umgebung](/help/release-notes/assets/add-non-production-pipeline.png)

  Siehe [Staging- und Nur-Produktions-Pipelines](/help/using/stage-prod-only.md).

* **Favoriten-Pipelines**

  In dieser Version bietet Cloud Manager die Möglichkeit, Favoriten-Pipelines anzuheften, sodass Sie bestimmte Pipelines als Favoriten markieren können, sodass sie oben in der Liste auf der Seite **Pipelines** angezeigt werden. Diese Verbesserung erleichtert das Auffinden und Ausführen häufig verwendeter Pipelines. <!-- CMGR-68293 -->

  ![Pipelines, die als Favoriten markiert sind](/help/release-notes/assets/pipeline-favorites.png) *Zwei Pipelines, die als Favoriten markiert sind.*

  Siehe [Markieren von Pipeline-Favoriten](/help/using/managing-pipelines.md#pipeline-favorites).


## Beta-Programme {#beta-program}

Nehmen Sie an den Beta-Programmen von Cloud Manager teil, um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf bevorstehende Funktionen zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:


### Bring Your Own Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Kundinnen und Kunden können nun ihre Azure DevOps-Git-Repositorys in Cloud Manager integrieren, wobei sowohl moderne Azure DevOps- als auch ältere VSTS(Visual Studio Team Services)-Repositorys unterstützt werden.

* Für Edge Delivery Services-Benutzende kann das integrierte Repository zum Synchronisieren und Bereitstellen von Sitecode verwendet werden.
* Für Benutzende von AEM as a Cloud Service und Adobe Managed Services (AMS) kann das Repository mit Fullstack- und Frontend-Pipelines verknüpft werden.

Zusätzliche Pipeline-Typen und die Validierung von Pull-Anfragen durch Code-Qualitäts-Pipelines werden demnächst unterstützt.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/release-notes/assets/azure-repo.png)

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

#### Zugriffstoken verwalten{#manage-access-tokens}

Verwenden Sie **Zugriffstoken verwalten** in Cloud Manager, um Zugriffstoken in Verbindung mit externen BYOG-Repositorys wie GitHub Enterprise, GitLab, Bitbucket und Azure DevOps anzuzeigen, umzubenennen und zu löschen.

Siehe [Verwalten von Zugriffstoken](/help/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerkorrekturen in der August-Version von Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
