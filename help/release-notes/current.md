---
title: Versionshinweise für Cloud Manager 2026.11.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.11.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: 'https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro'
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: b48085c8209c0802f6f2d321865bd1a1ee786139
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 10%
---

# Versionshinweise für Cloud Manager 2026.11.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.11.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2026.11.0 ist Donnerstag, der 5. November 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die nächste geplante Version ist Donnerstag, der 3. Dezember 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#new-features}

### Web-Stufen-Pipelines für AEM Managed Services {#web-tier-pipelines}

Cloud Manager unterstützt jetzt dedizierte Web-Stufen-Pipelines für AMS-Programme, sodass Teams Dispatcher- und Web-Stufen-Konfigurationen unabhängig von Full-Stack-Bereitstellungen bereitstellen können. Dies ermöglicht eine schnellere Iteration bei Änderungen der Web-Stufe und reduziert gleichzeitig unnötige vollständige Pipeline-Ausführungen.

Wenn eine Web-Stufen-Pipeline konfiguriert ist, überspringen Full-Stack-Pipelines automatisch die Web-Stufen-Bereitstellung für diese Umgebung, um Bereitstellungskonflikte zu vermeiden. Durch Entfernen der Web-Stufen-Pipeline wird das standardmäßige Bereitstellungsverhalten automatisch wiederhergestellt. <!-- CMGR-27553 -->

Siehe [Web-Stufen-Konfigurations-Pipelines](/help/overview/ci-cd-pipelines.md#web-tier-config-pipelines).

## Beta-Programme {#beta-program}

Es sind derzeit keine Gelegenheiten für das Beta-Programm verfügbar.

<!--
To get exclusive access to upcoming features before their general release, participate in Cloud Manager's beta programs.

>[!IMPORTANT]
>
>Beta releases contain issues and are provided without warranty of any kind. Adobe has no obligation to maintain, correct, update, change, modify or otherwise support (through Adobe Support Services or otherwise) the beta releases. Customers use beta releases at their own risk. Do not rely on the correct functioning or performance of beta releases, or on any accompanying documentation or materials. Features and APIs in beta are subject to change without notice. Any use of the beta releases is entirely at the customer's own risk.

The following beta program opportunity is currently available:
-->

## Fehlerbehebungen {#bug-fixes}


* Die Überprüfung der Code-Qualität schlägt bei großen Projekten fehl. Die Überprüfung der Code-Qualität (SonarQube) generiert Multi-Gigabyte-Debug-Protokolle und wird beim Überprüfen bestimmter gebündelter Bibliotheken abgebrochen, wodurch der Build fehlschlägt. Die Überprüfung wurde korrigiert, sodass sie bei den betroffenen Projekten normal abgeschlossen wird. (CMGR-80025)

* Beim CSV-Export der Sites-Nutzung wurden die Monatskennzeichnungen um einen Monat verschoben. Auf der Seite Lizenz > Sites-Nutzungsdetails zeigt der CSV-Export Monatsbezeichnungen, die für Benutzer in Zeitzonen hinter UTC einen Monat früher verschoben wurden. Der Export zeigt nun die richtigen Monatsbezeichnungen unabhängig von der Zeitzone des Benutzers an. (CMGR-80903)

* Durch die Wiederverwendung eines Zugriffstoken-Namens wird das vorhandene Token nicht mehr überschrieben. Durch die Wiederverwendung eines vorhandenen Zugriffstoken-Namens innerhalb eines Programms wird das freigegebene Token überschrieben und es werden doppelte Zugriffsgeheimnisse erstellt. Cloud Manager verarbeitet jetzt die korrekte Wiederverwendung von Token-Namen, um versehentliches Überschreiben und Duplikate zu verhindern. (CMGR-81236)


<!--
Known Issues {#known-issues}
-->
