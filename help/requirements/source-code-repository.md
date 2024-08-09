---
title: Quell-Code-Repository
description: Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 83%

---


# Quell-Code-Repository {#source-code-repository}

Hier erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.

## Cloud Manager-Repository {#cloud-manager-repository}

Ihr [!UICONTROL AEM Managed Services]-Abonnement umfasst ein Quell-Code-Repository, das von Adobe bereitgestellt und verwaltet wird. Jedem Programm ist ein einzelnes und eindeutiges Git-Repository zugewiesen, in dem Ihr Code gespeichert und gesichert wird.

Als Best Practice sollten Sie immer das Git-Repository von Cloud Manager verwenden, das ohne konfigurierte Verzweigungen oder Beispielprojekte bereitgestellt wird. Um das Git-Repository von Cloud Manager zu verwenden, erhalten Sie ein Token zum privaten Zugriff, mit dem Sie über einen beliebigen Git-Client Verzweigungen erstellen, Code speichern und abrufen, den Commit-Verlauf auflisten können usw.

Weitere Informationen zum Einrichten von Verzweigungen in Git finden Sie unter [Konfigurieren von Versionsverzweigungen](/help/getting-started/configuring-branches.md).

Weitere Informationen zur Verwendung des Git-Repositorys von Cloud Manager mit der CI/CD-Pipeline finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md) .

## On-Premise-Repository {#on-premise-repository}

Möglicherweise haben Sie ein bestehendes Git-Repository und möchten es weiter verwenden. In diesem Fall können Sie die Git-Funktion für mehrere Remote-Repositorys nutzen. Die tägliche Entwicklungsarbeit erfolgt weiterhin in Ihrem Git-Repository. Wenn eine Versionsverzweigung für die Produktion bereitgestellt werden kann, übertragen Sie den neuesten Code per Push in das Git-Repository von Cloud Manager und lösen Sie die Cloud Manager-CI/CD-Pipeline aus.

Gängige Git-Befehle finden Sie in der [Git-Kurzübersicht](https://education.github.com/git-cheat-sheet-education.pdf) auf der GitHub-Website.
