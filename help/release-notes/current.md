---
title: Versionshinweise für Cloud Manager 2026.3.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.3.0 auf Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ee49b0732fdb870c4f768764aa75b240fd101b59
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 19%

---

# Versionshinweise für Cloud Manager 2026.3.0 auf Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.3.0 auf Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2026.3.0 ist Donnerstag, der 5. März 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die nächste geplante Version ist Donnerstag, der 2. April 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}

* **Unterstützung der Erweiterbarkeit der Benutzeroberfläche in AEM Experience Hub**
Die Unterstützung für Benutzeroberflächenerweiterungen in [AEM Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) ist jetzt aktiviert, sodass Entwicklerinnen und Entwickler die Benutzeroberfläche mit benutzerdefinierten Funktionen und Widgets erweitern können, die mit Adobe App Builder erstellt wurden.

  Weitere Informationen finden Sie unter [AEM Experience Hub](https://developer.adobe.com/uix/docs/services/aem-experience-hub/).

* **Konfigurations-Pipelines unterstützen jetzt verwaltete Geheimnisse**

  Benutzende können jetzt Geheimnisse direkt in Cloud Manager-Konfigurations-Pipelines hinzufügen und verwalten. Diese geheimen Daten überschreiben sicher Werte in der Pipeline-Konfigurationsspezifikation und unterstützen flexible, umgebungsspezifische Bereitstellungen.

  ![Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline](/help/release-notes/assets/view-edit-variables-option.png)
  *Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline.*

  ![Dialogfeld „Variablenkonfiguration ](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Dialogfeld „Variablenkonfiguration“.*

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit**

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

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Es kann für Code-Qualitäts-, Full-Stack- und reine Staging-Pipelines angewendet werden.

![Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“](/help/release-notes/assets/non-production-pipeline-edit.png)
*Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“.*

Im Dialogfeld **Pipeline hinzufügen/bearbeiten** auf der Registerkarte **Source-Code** können Sie mit dem Abschnitt **Erstellen-Strategie** eine der folgenden Build-Optionen auswählen:

* **Vollständiger Build** - Erstellt bei jeder Ausführung alle Module im Repository.
* **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden, was die Erstellungszeit insgesamt verkürzt.

Sie steuern, welche Pipelines „Smart **Build“**. Während der Beta-Phase wird diese Option nur für Pipelines **Code-Qualität** und **Bereitstellung durch Entwicklung** angezeigt.

Sie sind interessiert? Senden Sie eine E-Mail an [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe-OrgID und Programm-ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager on AMS-Version vom März 2026.

<!--
Known Issues {#known-issues}

* A 
-->
