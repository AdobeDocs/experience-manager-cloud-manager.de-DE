---
title: Quell-Code-Repository
description: Erfahren Sie mehr über das Git-Repository, das für jedes Programm bereitgestellt wird, das Sie in Cloud Manager haben.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 4%

---


# Quell-Code-Repository {#source-code-repository}

Erfahren Sie mehr über das Git-Repository, das für jedes Programm bereitgestellt wird, das Sie in Cloud Manager haben.

## Cloud Manager-Repository {#cloud-manager-repository}

Ihre [!UICONTROL AEM Managed Services] Abonnement umfasst ein Quellcode-Repository, das von Adobe bereitgestellt und verwaltet wird. Jedem Programm wird ein einzelnes und eindeutiges Git-Repository zugewiesen, in dem Ihr verknüpfter Code gespeichert und gesichert wird.

Als Best Practice sollten Sie immer das Git-Repository von Cloud Manager verwenden, das ohne konfigurierte Verzweigungen oder Beispielprojekte bereitgestellt wird. Um das Git-Repository von Cloud Manager zu verwenden, erhalten Sie ein Token für den privaten Zugriff, mit dem Sie mithilfe eines beliebigen Git-Clients Verzweigungen erstellen, Ihren Code speichern und abrufen, den Commitverlauf auflisten können usw.

Weitere Informationen zum Einrichten von Verzweigungen in Git finden Sie unter [Konfigurieren von Release-Verzweigungen.](/help/getting-started/configuring-branches.md)

Weitere Informationen zur Verwendung des Git-Repositorys von Cloud Manager mit der CI/CD-Pipeline finden Sie in den Dokumenten [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md) , um mehr zu erfahren.

## On-Premise-Repository {#on-premise-repository}

Möglicherweise verfügen Sie über ein vorhandenes Git-Repository und möchten es weiterhin verwenden. In diesem Fall können Sie die Git-Funktion für mehrere Remote-Repositorys verwenden. Die tägliche Entwicklung erfolgt weiterhin in Ihrem Git-Repository. Wenn eine Versionsverzweigung für eine Bereitstellung in der Produktion bereit ist, können Sie Ihren aktuellen Code per Push an das Git-Repository von Cloud Manager senden und die CI/CD-Pipeline von Cloud Manager Trigger geben.

Informationen zu allgemeinen Git-Befehlen finden Sie in der [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) auf der GitHub-Website.
