---
title: Versionshinweise für Cloud Manager 2024.10.0
description: Dies sind die Versionshinweise für Cloud Manager 2024.10.0.
feature: Release Information
source-git-commit: 74e8f7c0f3896e0e33a02b62c003db322c0d50d8
workflow-type: ht
source-wordcount: '369'
ht-degree: 100%

---

# Versionshinweise für Cloud Manager 2024.10.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] 2024.10.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)



## Veröffentlichungsdatum {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2024.10.0 ist der 3. Oktober 2024.

Die nächste Version ist für den 14. November 2024 geplant.



## Neue Funktionen {#what-is-new}

* <!-- BOTH CS & AMS --> Die in Cloud Manager verwendete AEM-Archetyp-Version wird jetzt auf Version 26 aktualisiert. Siehe [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Early-Adopter-Programm von Cloud Manager teil und nutzen Sie die Möglichkeit, zukünftige Funktionen zu testen.

### Bringen Sie Ihren eigenen Git mit – jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion **Bringen Sie Ihren eigenen Git mit** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Unternehmens-GitHub-Repositorys. Wenn Sie diese neuen Repositorys hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit der konstanten Code-Synchronisation mit dem Adobe-Repository. Sie bietet weiterhin die Möglichkeit, Pull-Anfragen zu überprüfen, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Siehe [Hinzufügen von externen Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind vorkonfigurierte Code-Qualitätsprüfungen für Pull-Anfragen ausschließlich für von GitHub gehostete Repositorys verfügbar. Es ist jedoch ein Update in Arbeit, um diese Funktionen auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und uns Ihr Feedback mitteilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Geben Sie unbedingt an, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder einer Unternehmens-Repository-Struktur befinden.

### Reine Staging- und reine Produktions-Pipelines {#staging-production-only-pipelines}

Adobe kündigt die Einführung von Unterstützung für [reine Staging- und reine Produktions-Pipelines](/help/using/stage-prod-only.md) an. Mit dieser neuen Funktion können Sie Full-Stack-Produktions-Bereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com).

<!-- ## Bug fixes

* text
-->

<!-- Known Issues {#known-issues}

 -->
