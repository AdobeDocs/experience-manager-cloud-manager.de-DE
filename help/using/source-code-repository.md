---
title: Quell-Code-Repository
seo-title: Source Code Repository for Adobe AEM Cloud Manager
description: Auf dieser Seite erfahren Sie mehr über das Git-Repository, das für jedes in Cloud Manager enthaltene Programm bereitgestellt wird.
seo-description: Follow this page to learn about the git repository that is provisioned for each program you have in Adobe AEM Cloud Manager.
uuid: 2c42775f-8703-43f7-bad2-7dc086ea9dd7
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: requirements
discoiquuid: f90f0f4c-c1ff-47f6-8d97-ff5018561bf2
feature: Provisioning
exl-id: af551e33-3623-4fcd-8d25-4362d8871411
source-git-commit: 4f0e1d163001fd18cfa838256c813152d65c3b4c
workflow-type: ht
source-wordcount: '261'
ht-degree: 100%

---

# Quell-Code-Repository {#source-code-repository}

## Cloud Manager-Repository {#cloud-manager-repository}

Ihr [!UICONTROL AEM Managed Services]-Abonnement umfasst ein Quell-Code-Repository, das von Adobe bereitgestellt und verwaltet wird. Jedem Kundenprogramm ist ein einzelnes und eindeutiges **Git-Repository** zugewiesen, in dem Ihr Code gespeichert und gesichert wird.

Als Best Practice sollten Sie immer das Cloud Manager-Git-Repository verwenden, das ohne konfigurierte Verzweigungen oder Beispielprojekte bereitgestellt wird. Um das Cloud Manager-Git-Repository zu verwenden, erhalten Sie ein **Token zum privaten Zugriff**, mit dem Sie über einen beliebigen Git-kompatiblen Client Verzweigungen erstellen, Code speichern und abrufen, den Commitverlauf auflisten können usw.

Weitere Informationen zum Einrichten von Verzweigungen in Git finden Sie unter [Konfigurieren von Versionsverzweigungen](configure-your-release-branches.md).

Weitere Informationen zur Verwendung des **Git-Repositorys** von Cloud Manager mit der CI/CD-Pipeline finden Sie unter [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](configuring-non-production-pipelines.md).

## On-Premise-Repository {#on-premise-repository}

Unter Umständen verfügen Sie über ein vorhandenes Git-Repository, das Sie weiterhin verwenden möchten. In diesen Fällen können Sie die von Git unterstützte Funktion für mehrere Remoterepositorys verwenden. Die tägliche Entwicklerarbeit erfolgt weiterhin in Ihrem Git-Repository. Wenn eine Versionsverzweigung für die Produktion bereitgestellt werden kann, übertragen Sie den neuesten Code per Push in das Cloud Manager-Git-Repository und lösen Sie die Cloud Manager-CI/CD-Pipeline aus.

>[!NOTE]
>
>Die gebräuchlichen Git-Befehle finden Sie auf der [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf).
