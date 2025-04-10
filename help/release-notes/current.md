---
title: Versionshinweise für Cloud Manager 2025.4.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.4.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 40d093ce7d6839fff4ba16f790c61b96cb88dda5
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 92%

---

# Versionshinweise für Cloud Manager 2025.4.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.4.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.4.0 ist Donnerstag, der Freitag, 10. April 2025.

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 8. Mai 2025 geplant.

<!--
## What's new {#what-is-new}

* 
-->


## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adoption-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor deren allgemeiner Veröffentlichung zu erhalten.

Derzeit stehen die folgenden Möglichkeiten für eine frühzeitige Einführung zur Verfügung:

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

Die Funktion zum **Einbringen des eigenen Git** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Pipelines, die externe Repositorys (ausgenommen GitHub-gehostete Repositorys) und die Option **Bereitstellungsauslöser** **Bei Git-Änderungen** verwenden, starten jetzt automatisch.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

### Reine Staging- und reine Produktions-Pipelines {#staging-production-only-pipelines}

Adobe kündigt die Einführung von Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) an. Mit dieser neuen Funktion können Sie Full-Stack-Produktions-Bereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com).



<!--
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->



## Fehlerbehebungen {#bug-fixes}

* A

Bekannte Probleme {#known-issues}

* A —>
