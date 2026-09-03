---
title: Versionshinweise für Cloud Manager 2026.9.0
description: Erfahren Sie mehr über die Version Cloud Manager 2026.9.0 in Adobe Managed Services.
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
source-git-commit: e10c3c15c01c28f6bad0a9cf0464288937402cb7
workflow-type: tm+mt
source-wordcount: 403
ht-degree: 8%

---


# Versionshinweise für Cloud Manager 2026.9.0 in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Erfahren Sie mehr über die Version [!UICONTROL Cloud Manager] 2026.9.0 in Adobe Managed Services.

Hier finden Sie die [aktuellen Versionshinweise für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/release-notes/home).

## Veröffentlichungsdaten {#release-date}

Das Veröffentlichungsdatum für [!UICONTROL Cloud Manager] 2026.9.0 ist Donnerstag, der 3. September 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

Die nächste geplante Version ist Donnerstag, der 1. Oktober 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Neue Funktionen {#what-is-new}

In der Cloud Manager on AMS-Version vom September 2026 gibt es keine wesentlichen neuen Funktionen.


## Beta-Programme {#beta-program}

Um vor der allgemeinen Veröffentlichung exklusiven Zugriff auf kommende Funktionen zu erhalten, nehmen Sie an den Beta-Programmen von Cloud Manager teil.

>[!IMPORTANT]
>
>Beta-Versionen enthalten Mängel und werden ohne Gewährleistung jeglicher Art bereitgestellt. Adobe ist nicht verpflichtet, die Beta-Versionen zu pflegen, zu korrigieren, zu aktualisieren, zu ändern oder anderweitig zu unterstützen (durch Adobe Support Services oder anderweitig). Kunden verwenden Beta-Versionen auf eigenes Risiko. Verlassen Sie sich nicht auf die korrekte Funktionsweise oder Leistung von Beta-Versionen oder auf begleitende Dokumentationen oder Materialien. Funktionen und APIs in der Beta-Version können ohne Vorankündigung geändert werden. Jede Nutzung der Beta-Versionen erfolgt ausschließlich auf eigene Gefahr des Kunden.

Die folgende Beta-Programm-Gelegenheit ist derzeit verfügbar:

### Web-Stufen-Pipelines für AEM Managed Services {#web-tier-pipelines}

Cloud Manager unterstützt jetzt dedizierte Web-Stufen-Pipelines für AMS-Programme, sodass Teams Dispatcher- und Web-Stufen-Konfigurationen unabhängig von Full-Stack-Bereitstellungen bereitstellen können. Dies ermöglicht eine schnellere Iteration bei Änderungen der Web-Stufe und reduziert gleichzeitig unnötige vollständige Pipeline-Ausführungen. Wenn eine Web-Stufen-Pipeline konfiguriert ist, überspringen Full-Stack-Pipelines automatisch die Web-Stufen-Bereitstellung für diese Umgebung, um Bereitstellungskonflikte zu vermeiden. Durch Entfernen der Web-Stufen-Pipeline wird das standardmäßige Bereitstellungsverhalten automatisch wiederhergestellt.

Um an der Beta teilzunehmen, wenden Sie sich an Ihren Customer Success Engineer für Adobe, um mehr zu erfahren.


## Fehlerbehebungen {#bug-fixes}

* Durch das erneute Generieren eines Repository-Zugriffskennworts wird jetzt das alte Kennwort ungültig. Zuvor wurde durch das erneute Generieren des Git-Repository-Zugriffs-Kennworts das vorherige Kennwort nicht sofort ungültig, sodass die alten Anmeldeinformationen verwendet werden können. Durch die Neuerstellung des Kennworts wird das alte sofort ungültig, sodass die vorherige Berechtigung nicht mehr verwendet werden kann. (CMGR-41820)

* Berechtigungsprüfungen wurden aktualisiert, um das Eigentum an Ressourcen zu erzwingen. Es wurde ein Problem bei der Auswertung von Berechtigungsprüfungen behoben, sodass der Zugriff auf ein Programm immer anhand der Organisation validiert wird, die Eigentümer des Programms ist. Dies stärkt die Isolation zwischen Organisationen für Vorgänge mit Berechtigungstests. (CMGR-79156)

<!--
Known Issues {#known-issues}
-->
