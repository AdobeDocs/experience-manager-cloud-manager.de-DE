---
title: Quell-Code-Repository
description: Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4c977cdfbef438fdabd90ee104d98887f2467b49
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 20%

---


# Source-Code-Repository {#source-code-repository}

Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.

## Cloud Manager-Repository {#cloud-manager-repository}

Ihr [!UICONTROL AEM Managed Services]-Abonnement umfasst ein Quell-Code-Repository, das von Adobe bereitgestellt und verwaltet wird. Jedem Programm wird ein einzelnes und eindeutiges Git-Repository zugewiesen, in dem Ihr verknüpfter Code gespeichert und gesichert wird.

Als Best Practice sollten Sie immer das Cloud Manager-Git-Repository verwenden, das ohne konfigurierte Verzweigungen oder Beispielprojekte bereitgestellt wird. Cloud Manager bietet ein privates Zugriffstoken für das Git-Repository, mit dem Sie beliebige Git-Clients verwenden können, um Verzweigungen zu erstellen, Code zu verwalten, den Commitverlauf abzurufen und vieles mehr.

Weitere Informationen zum Einrichten von Verzweigungen in Git finden Sie unter [Konfigurieren von Versionsverzweigungen](/help/getting-started/configuring-branches.md).

Weitere Informationen zur Verwendung des Git-Repositorys von Cloud Manager mit der CI/CD-Pipeline finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md) .

## On-Premise Repository {#on-premise-repository}

Möglicherweise verfügen Sie über ein vorhandenes Git-Repository und möchten es weiterhin verwenden. In diesem Fall können Sie die Git-Funktion für mehrere Remote-Repositorys verwenden. Die tägliche Entwicklung erfolgt weiterhin in Ihrem Git-Repository. Wenn eine Versionsverzweigung für die Bereitstellung in der Produktionsumgebung bereit ist, können Sie Ihren aktuellen Code per Push an das Cloud Manager-Git-Repository senden und die Cloud Manager CI/CD-Pipeline Trigger geben.

Allgemeine Git-Befehle finden Sie im [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf).
