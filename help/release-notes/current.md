---
title: Versionshinweise für Cloud Manager 2026.7.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.7.0 in Adobe Managed Services.
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
source-git-commit: 4c73ab16ff7eab406c31a6d26cdd09360a94b3ea
workflow-type: tm+mt
source-wordcount: 391
ht-degree: 14%

---


# Versionshinweise für Cloud Manager 2026.7.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.6.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2026.7.0 ist Donnerstag, der 9. Juli 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die nächste geplante Version ist Donnerstag, der 6. August 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **Verbesserte Build-Leistung mit Modul-Caching**
Ein neues Build-Modell kompiliert nur geänderte Module (und nicht das gesamte Repository) mithilfe des Caching auf Modulebene, um die Build-Leistung zu verbessern. Dies gilt für Produktions-Pipelines. Sie steuern, welche Produktions-Pipelines &quot;**Build“**.

  Weitere Informationen finden Sie in den folgenden Themen:

   * [Über die Verwendung von Smart Build in einer Produktions](/help/using/production-pipelines.md#about-smart-build)Pipeline und [Über die Verwendung von Smart Build in einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#about-smart-build)
   * [Produktions-Pipeline hinzufügen](/help/using/production-pipelines.md##adding-production-pipeline) und [produktionsfremde Pipeline hinzufügen](/help/using/non-production-pipelines.md#add-non-production-pipeline).

## Beta-Programme {#beta-program}

Nehmen Sie am Beta-Programm von Cloud Manager teil, um exklusiven Zugriff auf bevorstehende Funktionen vor ihrer regulären Veröffentlichung zu erhalten.

>[!IMPORTANT]
>
>Beta-Versionen enthalten Mängel und werden ohne Mängelgewähr und ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Kundinnen und Kunden verwenden Beta-Versionen auf eigenes Risiko und sollten sich nicht auf die korrekte Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien verlassen. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt ausschließlich auf eigene Gefahr des Kunden.

Die folgenden Möglichkeiten des Beta-Programms sind derzeit verfügbar:

### Web-Stufen-Pipelines für AEM Managed Services {#web-tier-pipelines}

Cloud Manager unterstützt jetzt dedizierte Web-Stufen-Pipelines für AMS-Programme, sodass Teams Dispatcher- und Web-Stufen-Konfigurationen unabhängig von Full-Stack-Bereitstellungen bereitstellen können. Dies ermöglicht eine schnellere Iteration bei Änderungen der Web-Stufe und reduziert gleichzeitig unnötige vollständige Pipeline-Ausführungen. Wenn eine Web-Stufen-Pipeline konfiguriert ist, überspringen Full-Stack-Pipelines automatisch die Web-Stufen-Bereitstellung für diese Umgebung, um Bereitstellungskonflikte zu vermeiden. Durch Entfernen der Web-Stufen-Pipeline wird das standardmäßige Bereitstellungsverhalten automatisch wiederhergestellt.

Um an der Beta teilzunehmen, wenden Sie sich an Ihren Customer Success Engineer für Adobe, um mehr zu erfahren.




## Fehlerbehebungen {#bug-fixes}

Es gibt keine signifikanten Fehlerbehebungen in der Cloud Manager on AMS-Version vom Juni 2026.

<!--
Known Issues {#known-issues}

* A 
-->
