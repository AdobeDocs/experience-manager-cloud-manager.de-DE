---
title: Quell-Code-Repository
description: Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
TQID: https://experienceleague.adobe.com/hdEpqKW0NluPs-w37SeLzpd-EHJNqb2nfSAMQ35man8
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: b24e9550f11486e7ed8da31d5da27f85ad5acaf2
workflow-type: tm+mt
source-wordcount: 236
ht-degree: 44%

---

# Quell-Code-Repository {#source-code-repository}

Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.

## Cloud Manager-Repository {#cloud-manager-repository}

Ihr [!UICONTROL AEM Managed Services]-Abonnement umfasst ein Quell-Code-Repository, das von Adobe bereitgestellt und verwaltet wird. Jedem Programm ist ein eindeutiges Git-Repository zugewiesen, in dem Ihr zugehöriger Code gespeichert und gesichert wird.

Verwenden Sie als Best Practice immer das leere Cloud Manager-Git-Repository ohne konfigurierte Verzweigungen oder Beispielprojekte. Cloud Manager bietet ein privates Zugriffs-Token für das Git-Repository, mit dem Sie beliebige Git-Clients verwenden können, um Verzweigungen zu erstellen, Code zu verwalten und den Commit-Verlauf abzurufen.

Weitere Informationen zum Einrichten von Verzweigungen in Git finden Sie unter [Konfigurieren von Versionsverzweigungen](/help/getting-started/configuring-branches.md).

Weitere Informationen zur Verwendung des Cloud Manager-Git-Repositorys mit der CI/CD-Pipeline finden Sie unter [Konfigurieren von Produktions](/help/using/production-pipelines.md)Pipelines und [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

## On-Premise-Repository {#on-premise-repository}

Wenn Sie über ein vorhandenes Git-Repository verfügen und es weiterhin verwenden möchten, verwenden Sie die Git-Funktion für mehrere Remote-Repositorys. Die Entwicklung in Ihrem Git-Repository wird fortgesetzt. Wenn eine Versionsverzweigung für die Bereitstellung in der Produktionsumgebung bereit ist, können Sie den neuesten Code per Push an das Cloud Manager-Git-Repository übertragen und die Cloud Manager CI/CD-Pipeline mit Trigger versehen.

Gängige Git-Befehle finden Sie im [Git-Referenzhandbuch](https://education.github.com/git-cheat-sheet-education.pdf).
