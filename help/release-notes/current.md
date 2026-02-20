---
title: Versionshinweise für Cloud Manager 2026.1.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.1.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 28841719e820e47577b411a4034ebc7a8e1bb556
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 51%

---

# Versionshinweise für Cloud Manager 2026.1.0 in Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.1.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum von [!UICONTROL Cloud Manager] 2026.1.0 ist Donnerstag, der Freitag, 22. Januar 2026.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die Veröffentlichung der nächsten Version ist für Donnerstag, den Freitag, 5. Februar 2026 geplant.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}

* **Konfigurations-Pipelines unterstützen jetzt verwaltete Geheimnisse**

  Benutzende können jetzt Geheimnisse direkt in Cloud Manager-Konfigurations-Pipelines hinzufügen und verwalten. Diese geheimen Daten überschreiben sicher Werte in der Pipeline-Konfigurationsspezifikation und unterstützen flexible, umgebungsspezifische Bereitstellungen.

  ![Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline](/help/release-notes/assets/view-edit-variables-option.png)
  *Option „Variablen anzeigen/bearbeiten“ im Dropdown-Menü für eine ausgewählte Pipeline.*

  ![Dialogfeld „Variablenkonfiguration &#x200B;](/help/release-notes/assets/view-edit-variables-variablesconfig-dialogbox.png)*Dialogfeld „Variablenkonfiguration“.*

* **Verbesserte Stabilität, Leistung und Zuverlässigkeit**

  Diese Version umfasst Optimierungs- und Wartungsaktualisierungen, die die Stabilität, Leistung und Zuverlässigkeit von Cloud Manager verbessert haben.


## Beta-Programme {#beta-program}

Nehmen Sie an den Beta-Programmen von Cloud Manager teil, um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf bevorstehende Funktionen zu erhalten.

Derzeit stehen die folgenden Möglichkeiten zur Verfügung:

### Erweiterbarkeit und Anpassung von Experience Hub {#exp-hub-extensibility}

[Experience Hub](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/experience-hub/experience-hub) dient als Einstiegspunkt für AEM und ist an die Anforderungen Ihres Unternehmens angepasst. Teilen Sie Adobe Ihre bestehenden Erweiterungen der AEM-Benutzeroberfläche mit, damit Sie sie mit minimalem Aufwand in Experience Hub aktivieren können.

![Diagramm des Erweiterbarkeits- und Anpassungs-Workflows von Experience Hub](/help/release-notes/assets/experience-hub-extensibility-customization.png)

Betten Sie benutzerdefinierte Erlebnisse in Experience Hub ein, um das Dashboard Ihres Unternehmens zu erweitern und zu personalisieren. Zusätzlich zu den integrierten Widgets von Adobe können Sie Ihre eigenen mit dem Framework für die [Erweiterbarkeit der Benutzeroberfläche](https://developer.adobe.com/uix/docs/) hinzufügen. Erstellen Sie auf JavaScript basierte Benutzeroberflächen-Apps und stellen Sie sie Ihren Benutzenden zur Verfügung, um geschäftsspezifische Anforderungen und Workflows zu erfüllen.

Sie interessieren sich für die Beta-Version? Senden Sie eine E-Mail an [beta_exphubextensibility@adobe.com](mailto:beta_exphubextensibility@adobe.com) mit Ihrer Adobe-OrgID und einer kurzen Beschreibung der Anpassung, die Sie vornehmen möchten.

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

Es gibt keine signifikanten Fehlerbehebungen in der Version vom Januar 2026 von Cloud Manager on AMS.

<!--
Known Issues {#known-issues}

* A -->
