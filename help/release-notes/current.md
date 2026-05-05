---
title: Versionshinweise für Cloud Manager 2026.4.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.4.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 8964aad406d3e7fc5b911b98f928ad0427511230
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 14%

---


# Versionshinweise für Cloud Manager 2026.4.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.4.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2026.4.0 ist Donnerstag, der 2. April 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die nächste geplante Version ist Donnerstag, der 7. Mai 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}

* **Unterstützung der Erweiterbarkeit der Benutzeroberfläche in AEM Experience Hub.**

  Die Unterstützung für Benutzeroberflächenerweiterungen in [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) ist jetzt aktiviert, sodass Entwicklerinnen und Entwickler die Schnittstelle mit benutzerdefinierten Funktionen und Widgets erweitern können, die mit Adobe App Builder erstellt wurden.

  Weitere Informationen finden Sie unter [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Konfigurations-Pipelines unterstützen jetzt verwaltete Geheimnisse.**

  Benutzende können jetzt Geheimnisse direkt in Cloud Manager-Konfigurations-Pipelines hinzufügen und verwalten. Diese geheimen Daten überschreiben sicher Werte in der Pipeline-Konfigurationsspezifikation und unterstützen flexible, umgebungsspezifische Bereitstellungen.

  ![&#x200B; Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline](/help/release-notes/assets/view-edit-variables-option.png)
  *Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline.*

  ![Dialogfeld „Variablenkonfiguration &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Dialogfeld „Variablenkonfiguration“.*

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit.**

  Diese Version umfasst Optimierungs- und Wartungsaktualisierungen, die die Stabilität, Leistung und Zuverlässigkeit von Cloud Manager verbessert haben.


## Beta-Programme {#beta-program}

Nehmen Sie an den Beta-Programmen von Cloud Manager teil, um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf bevorstehende Funktionen zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:

<!--
### Experience Hub Extensibility and Customization {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) serves as your entry point to AEM, customized for your organization's needs. Tell Adobe about your existing AEM UI extensions so they can help you enable them in Experience Hub with minimal effort.

![Diagram of Experience Hub extensibility and customization workflow](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Embed custom experiences in Experience Hub to extend and personalize your organization's dashboard. In addition to Adobe's built-in widgets, add your own using the [UI Extensibility](https://developer.adobe.com/uix/docs/) framework. Build JavaScript-based UI apps and surface them to your users to meet business-specific requirements and workflows. 

Interested in the beta? Email [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) with your Adobe OrgID and a short description of the customization you intend to create.
-->

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Dies gilt für Code-Qualität- und Full-Stack-Pipelines.

![Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“](/help/release-notes/assets/non-production-pipeline-edit.png)
*Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“.*

Im Dialogfeld **Pipeline hinzufügen/bearbeiten** auf der Registerkarte **Source-Code** können Sie mit dem Abschnitt **Erstellen-Strategie** eine der folgenden Build-Optionen auswählen:

* **Vollständiger Build** - Erstellt bei jeder Ausführung alle Module im Repository.
* **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden, was die Erstellungszeit insgesamt verkürzt.

Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline) und [Informationen zur Verwendung von Smart Build in einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#about-smart-build).

Sie steuern, welche Pipelines „Smart **Build“**. Während der Beta-Phase wird diese Option nur für Pipelines für **Code-Qualität** und **Bereitstellung von Full-Stack-Code** angezeigt.

Um sich der Beta anzuschließen, senden Sie eine E-Mail an [&#128279;](mailto:beta_quickbuild_cmpipelines@adobe.com)beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager on AMS-Version vom April 2026.

<!--
Known Issues {#known-issues}

* A 
-->
