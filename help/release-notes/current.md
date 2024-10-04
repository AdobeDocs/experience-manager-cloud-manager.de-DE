---
title: Versionshinweise für Cloud Manager 2024.10.0
description: Dies sind die Versionshinweise für Cloud Manager 2024.10.0.
feature: Release Information
source-git-commit: 74e8f7c0f3896e0e33a02b62c003db322c0d50d8
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 27%

---

# Versionshinweise für Cloud Manager 2024.10.0 {#release-notes}

Auf dieser Seite sind die Versionshinweise für [!UICONTROL Cloud Manager] 2024.10.0 dokumentiert.

>[!NOTE]
>
>Die neuesten Versionshinweise für Cloud Manager in AEM as a Cloud Service finden Sie unter [Aktuelle Versionshinweise zu Cloud Manager in AEM as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)



## Veröffentlichungsdatum {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

Die Version von [!UICONTROL Cloud Manager] 2024.10.0 wurde am 3. Oktober 2024 veröffentlicht.

Die nächste Version ist für den Freitag, 14. November 2024 geplant.



## Neue Funktionen {#what-is-new}

* <!-- BOTH CS & AMS --> Die in Cloud Manager verwendete AEM Archetyp-Version wird jetzt auf Version 26 aktualisiert. Siehe [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## Early-Adopter-Programm {#early-adoption}

Nehmen Sie am Cloud Manager-Programm teil und haben Sie die Möglichkeit, bevorstehende Funktionen zu testen.

### Eigenes Git - jetzt mit Unterstützung für GitLab und Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

Die Funktion **Eigenes Git holen** wurde erweitert und unterstützt jetzt auch externe Repositorys wie GitLab und Bitbucket. Diese neue Unterstützung ergänzt die bereits vorhandene Unterstützung für private und Enterprise-GitHub-Repositorys. Wenn Sie diese neuen Repos hinzufügen, können Sie sie auch direkt mit Ihren Pipelines verknüpfen. Sie können diese Repositorys auf öffentlichen Cloud-Plattformen oder in Ihrer privaten Cloud oder Infrastruktur hosten. Durch diese Integration entfällt auch die Notwendigkeit einer konstanten Codesynchronisation mit dem Adobe-Repository und bietet die Möglichkeit, Pull-Anforderungen zu validieren, bevor sie in einer Hauptverzweigung zusammengeführt werden.

Siehe [Hinzufügen externer Repositorys in Cloud Manager](/help/managing-code/external-repositories.md).

![Dialogfeld „Repository hinzufügen“](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Derzeit sind die vordefinierten Qualitätsprüfungen für Pull-Anforderungscode ausschließlich für von GitHub gehostete Repositorys verfügbar. Es wird jedoch ein Update vorgenommen, um diese Funktion auf andere Git-Anbieter zu erweitern.

Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie eine E-Mail von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse an [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com). Stellen Sie sicher, dass Sie angeben, welche Git-Plattform Sie verwenden möchten und ob Sie sich in einer privaten/öffentlichen oder Enterprise-Repository-Struktur befinden.

### Reine Staging- und reine Produktions-Pipelines {#staging-production-only-pipelines}

Adobe kündigt die Einführung der Unterstützung für [reine Staging- und reine Produktionslinien](/help/using/stage-prod-only.md) an. Mit dieser neuen Funktion können Sie Full-Stack-Produktions-Bereitstellungs-Pipelines in kleinere, spezialisierte Bereitstellungen aufteilen.

Wenn Sie diese Funktion testen und Feedback geben möchten, senden Sie eine E-Mail an [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) aus Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse.

<!-- ## Bug fixes

* text
-->

<!-- Known Issues {#known-issues}

 -->
