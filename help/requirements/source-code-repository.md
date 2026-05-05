---
title: Quell-Code-Repository
description: Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 254
ht-degree: 100%

---

# Quell-Code-Repository {#source-code-repository}

Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.

## Cloud Manager-Repository {#cloud-manager-repository}

Ihr [!UICONTROL AEM Managed Services]-Abonnement umfasst ein Quell-Code-Repository, das von Adobe bereitgestellt und verwaltet wird. Jedem Programm ist ein einzelnes und eindeutiges Git-Repository zugewiesen, in dem Ihr verknüpfter Code gespeichert und gesichert wird.

Als Best Practice sollten Sie immer das Git-Repository von Cloud Manager verwenden, das ohne konfigurierte Verzweigungen oder Beispielprojekte bereitgestellt wird. Cloud Manager bietet ein privates Zugriffs-Token für das Git-Repository, mit dem Sie beliebige Git-Clients verwenden können, um Verzweigungen zu erstellen, Code zu verwalten und den Commit-Verlauf abzurufen.

Weitere Informationen zum Einrichten von Verzweigungen in Git finden Sie unter [Konfigurieren von Versionsverzweigungen](/help/getting-started/configuring-branches.md).

Weitere Informationen zur Verwendung des Git-Repositorys von Cloud Manager mit der CI/CD-Pipeline finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

## On-Premise-Repository {#on-premise-repository}

Möglicherweise haben Sie ein bestehendes Git-Repository und möchten es weiter verwenden. In diesem Fall können Sie die Git-Funktion für mehrere Remote-Repositorys nutzen. Die tägliche Entwicklungsarbeit erfolgt weiterhin in Ihrem Git-Repository. Wenn eine Versionsverzweigung für die Produktion bereitgestellt werden kann, übertragen Sie den neuesten Code per Push in das Git-Repository von Cloud Manager und lösen Sie die Cloud Manager-CI/CD-Pipeline aus.

Die gebräuchlichen Git-Befehle finden Sie in der [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf).
