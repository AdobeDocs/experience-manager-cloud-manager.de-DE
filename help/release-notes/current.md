---
title: Versionshinweise für Cloud Manager 2025.10.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.10.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 03fc811a1a617263efd0f1d5667bba6975826a0e
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 59%

---

# Versionshinweise für Cloud Manager 2025.10.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.10.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.10.0 ist Donnerstag, der Freitag, 2. Oktober 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die Veröffentlichung der nächsten Version ist für den Freitag, 6. November 2025 geplant.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}







## Beta-Programme {#beta-program}

Nehmen Sie an den Beta-Programmen von Cloud Manager teil, um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf bevorstehende Funktionen zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:

### Erweiterbarkeit und Anpassung von Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) dient als Einstiegspunkt für AEM, angepasst an die Anforderungen Ihres Unternehmens. Teilen Sie Adobe Ihre bestehenden Erweiterungen der AEM-Benutzeroberfläche mit, damit Sie sie mit minimalem Aufwand in Experience Hub aktivieren können.

![Abbildung des Erweiterbarkeits- und Anpassungs-Workflows von Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Betten Sie benutzerdefinierte Erlebnisse in Experience Hub ein, um das Dashboard Ihres Unternehmens zu erweitern und zu personalisieren. Zusätzlich zu den integrierten Widgets von Adobe können Sie Ihre eigenen mit dem [UI Extensibility](https://developer.adobe.com/uix/docs/)-Framework hinzufügen. Erstellen Sie JavaScript-basierte Benutzeroberflächen-Apps und stellen Sie sie Ihren Benutzern zur Verfügung, um geschäftsspezifische Anforderungen und Workflows zu erfüllen.

Sie interessieren sich für die Beta-Version? Senden Sie eine E-[&#x200B; an &#x200B;](mailto:beta_exphubextensibility@adobe.com)beta_exphubextensibility@adobe.commit Ihrer Adobe-OrgID und einer kurzen Beschreibung der Anpassung, die Sie erstellen möchten.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (und nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Sie gilt für Pipelines in Code-Qualität, mit vollem Stapel und nur Staging.

Sie interessieren sich für die Beta-Version? Senden Sie eine E-Mail an [0&rbrace;beta_quickbuild_cmpipelines@adobe.com&quot; mit Ihrer Adobe-OrgID und Programm-ID.](mailto:beta_quickbuild_cmpipelines@adobe.com)

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->


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

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager-Version vom Oktober.

<!--
Known Issues {#known-issues}

* A -->
