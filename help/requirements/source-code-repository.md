---
title: Quell-Code-Repository
description: Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '245'
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
