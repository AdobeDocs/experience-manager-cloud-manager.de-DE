---
title: Versionshinweise für Cloud Manager 2025.6.0
description: Erfahren Sie mehr über die Version Cloud Manager 2025.5.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 71%

---

# Versionshinweise für Cloud Manager 2025.6.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2025.6.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2025.6.0 ist Donnerstag, der Freitag, 5. Juni 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die Veröffentlichung der nächsten Version ist für den 10. Juli 2025 geplant.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Neue Funktionen {#what-is-new}

* **Pipelines nur für Staging und Produktion**

  Cloud Manager unterstützt jetzt Pipelines, die nur für Staging und Produktion vorgesehen sind. Mit dieser Funktion können Sie Full-Stack-Produktionsbereitstellungen in kleinere, zweckspezifische Pipelines aufteilen. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“ mit aktiviertem Optionsfeld „Full-Stack-Code“ und ausgewählter Staging-Umgebung](/help/release-notes/assets/add-non-production-pipeline.png)

  Siehe [Staging- und Nur-Produktions-Pipelines](/help/using/stage-prod-only.md).

* **Favoriten-Pipelines**

  In dieser Version bietet Cloud Manager die Möglichkeit, Favoriten-Pipelines anzuheften, sodass Sie bestimmte Pipelines als Favoriten markieren können, sodass sie oben in der Liste auf der Seite **Pipelines** angezeigt werden. Diese Verbesserung erleichtert das Auffinden und Ausführen häufig verwendeter Pipelines. <!-- CMGR-68293 -->

  ![Pipelines, die als Favoriten markiert sind](/help/release-notes/assets/pipeline-favorites.png) *Zwei Pipelines, die als Favoriten markiert sind.*

  Siehe [Markieren von Pipeline-Favoriten](/help/using/managing-pipelines.md#pipeline-favorites).


## Privates Beta-Programm {#beta-program}

Nehmen Sie am privaten Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor deren allgemeiner Veröffentlichung zu erhalten.

Die folgenden privaten Beta-Gelegenheiten sind derzeit verfügbar:


### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

Die Funktion **Bring Your Own Git** (BYOG) wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Pipelines, die externe Repositorys (ausgenommen GitHub-gehostete Repositorys) und die Option **Bereitstellungsauslöser** **Bei Git-Änderungen** verwenden, starten jetzt automatisch.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

#### Zugriffstoken verwalten{#access-tokens}

Verwenden Sie **Zugriffs-Token verwalten** mit BYOG, um Zugriffs-Token anzuzeigen, umzubenennen und zu löschen, die mit externen Bring-Your-Own-Git-Repositorys verknüpft sind, z. B. GitHub Enterprise, GitLab, Bitbucket und Azure DevOps.

Siehe [Verwalten von Zugriffstoken](/help/managing-code/manage-access-tokens.md).

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.


## Fehlerbehebung {#bug-fixes}

* AEM Cloud Manager ordnet jetzt Maven-Build-Fehler, die durch 409-Fehler (Konflikte) verursacht wurden, beim Abrufen von Kundenartefakten korrekt einem kundenbedingten Fehler zu. Diese Änderung verbessert das Fehlermeldungssystem, indem jetzt zwischen internen Fehlern und Problemen im Zusammenhang mit der Einrichtung der Kundenumgebung unterschieden wird. <!-- CMGR-66673 -->

<!--
Known Issues {#known-issues}

* A -->
