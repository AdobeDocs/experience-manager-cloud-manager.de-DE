---
title: Versionshinweise für Cloud Manager 2025.9.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.9.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 68e546c1337122f823d63529ebd68d6966bb132a
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 75%

---

# Versionshinweise für Cloud Manager 2025.9.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.9.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.9.0 ist Donnerstag, der Freitag, 4. September 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die Veröffentlichung der nächsten Version ist für den Freitag, 2. Oktober 2025 geplant.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Neue Funktionen {#what-is-new}

* **Unterstützung für private Azure DevOps-Repositorys wurde hinzugefügt**

  Zu den Aktualisierungen der Dokumentation gehören Konfigurationsschritte für Bring Your Own Git with Azure DevOps und die Validierung von Pull-Anfragen. Siehe [Hinzufügen externer Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

* **Pull-Anforderungsprüfungen für private Repositorys**

  Cloud Manager unterstützt jetzt Konfigurations-Pipelines mit privaten Repositorys in GitHub, Bitbucket, Azure DevOps und GitLab. Siehe ![Pull-Anforderungsprüfungen für private Repositorys](/help/managing-code/github-check-config.md).

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
