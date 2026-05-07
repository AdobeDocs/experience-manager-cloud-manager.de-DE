---
title: Versionshinweise für Cloud Manager 2026.5.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.5.0 in Adobe Managed Services.
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
source-git-commit: 0c2a9a946df6d5e1b0e4d5edb2715d8db98e9974
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 15%

---


# Versionshinweise für Cloud Manager 2026.5.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.5.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2026.5.0 ist Donnerstag, der 7. Mai 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die nächste geplante Version ist Donnerstag, der 4. Juni 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}

In der Cloud Manager on AMS-Version vom Mai 2026 gibt es keine wesentlichen neuen Funktionen.

## Beta-Programme {#beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen können Mängel enthalten und werden „wie besehen“ ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Adobe empfiehlt Kunden, Vorsicht walten zu lassen und sich nicht auf die ordnungsgemäße Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien zu verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt daher ausschließlich auf eigene Gefahr des Kunden.

Die folgenden Möglichkeiten des Beta-Programms sind derzeit verfügbar:

### Web-Stufen-Pipelines für AEM Managed Services {#web-tier-pipelines}

Cloud Manager unterstützt jetzt dedizierte Web-Stufen-Pipelines für AMS-Programme, sodass Teams Dispatcher- und Web-Stufen-Konfigurationen unabhängig von Full-Stack-Bereitstellungen bereitstellen können. Dies ermöglicht eine schnellere Iteration bei Änderungen der Web-Stufe und reduziert gleichzeitig unnötige vollständige Pipeline-Ausführungen. Wenn eine Web-Stufen-Pipeline konfiguriert ist, überspringen Full-Stack-Pipelines automatisch die Web-Stufen-Bereitstellung für diese Umgebung, um Bereitstellungskonflikte zu vermeiden. Durch Entfernen der Web-Stufen-Pipeline wird das standardmäßige Bereitstellungsverhalten automatisch wiederhergestellt.

Um an der Beta teilzunehmen, wenden Sie sich an Ihren Customer Success Engineer für Adobe, um mehr zu erfahren.

### Schnellere Builds mit Modul-Caching {#quick-build-cm-pipelines}

Ein neues Build-Modell kompiliert nur geänderte Module (nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Erstellungszeiten zu verkürzen. Dies gilt für Code-Qualität- und Full-Stack-Pipelines.

![Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“](/help/release-notes/assets/non-production-pipeline-edit.png)
*Dialogfeld „Produktionsfremde Pipeline bearbeiten“ mit den beiden Optionen für die Build-Strategie „Vollständiger Build“ und „Intelligenter Build“.*

Im Dialogfeld **Pipeline hinzufügen/bearbeiten** auf der Registerkarte **Source-Code** können Sie mit dem Abschnitt **Erstellen-Strategie** eine der folgenden Build-Optionen auswählen:

* **Vollständiger Build** - Erstellt bei jeder Ausführung alle Module im Repository.
* **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden, was die Erstellungszeit insgesamt verkürzt.

Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline) und [Informationen zur Verwendung von Smart Build in einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#about-smart-build).

Sie steuern, welche Pipelines &quot;**Build“**. Während der Beta-Phase wird diese Option nur für Pipelines für **Code-Qualität** und **Bereitstellung von Full-Stack-Code** angezeigt.

Um sich der Beta anzuschließen, senden Sie eine E-Mail an [&#128279;](mailto:beta_quickbuild_cmpipelines@adobe.com)beta_quickbuild_cmpipelines@adobe.com) mit Ihrer Adobe Organisations-ID und Programm-ID.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager on AMS-Version vom Mai 2026.

<!--
Known Issues {#known-issues}

* A 
-->
