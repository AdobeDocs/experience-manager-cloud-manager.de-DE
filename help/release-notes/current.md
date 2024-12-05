---
title: Versionshinweise für Cloud Manager 2024.12.0
description: Erfahren Sie mehr über die Version von Cloud Manager 2024.12.0 auf Adobe Managed Services.
feature: Release Information
source-git-commit: ee79124a012106e53ffaaf9462202712f7078809
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 65%

---

# Versionshinweise für Cloud Manager 2024.12.0 auf Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Erfahren Sie mehr über die Version von [!UICONTROL Cloud Manager] 2024.12.0 auf Adobe Managed Services.

>[!NOTE]
>
>Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

Die Version von [!UICONTROL Cloud Manager] 2024.12.0 wurde am 5. Dezember 2024 veröffentlicht.

Die Veröffentlichung der nächsten Version ist für den Freitag, 23. Januar 2025 geplant.

## Neue Funktionen {#what-is-new}

* Der Schritt AEM Code-Qualität verwendet jetzt den SonarQube 9.9-Server, der die ältere Version 7.4 ersetzt. Durch dieses Upgrade erhalten Sie zusätzliche Sicherheits-, Leistungs- und Code-Qualitätsprüfungen, die eine umfassendere Analyse und Abdeckung Ihrer Projekte ermöglichen. <!-- CMGR-45683 -->

## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil und nutzen Sie die Möglichkeit, zukünftige Funktionen zu testen.

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion **Eigenes Git holen** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Pipelines, die externe Repositorys verwenden (außer von GitHub gehostete) und der **Bereitstellungs-Trigger** auf **On Git Changes** eingestellt sind, starten jetzt automatisch.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
