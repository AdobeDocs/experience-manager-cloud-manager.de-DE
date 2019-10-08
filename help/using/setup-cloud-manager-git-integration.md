---
title: Git-Integration mit Adobe Cloud Manager
description: Eine Videoreihe, die die Einrichtung und Integration eines kundenverwalteten (lokalen) Git-Repositorys mit Adobe Cloud Manager durchläuft.
seo-title: Git-Integration mit Adobe Cloud Manager
seo-description: Eine Videoreihe, die die Einrichtung und Integration eines kundenverwalteten (lokalen) Git-Repositorys mit Adobe Cloud Manager durchläuft.
translation-type: tm+mt
source-git-commit: 519f43ff16e0474951f97798a8e070141e5c124b

---


# Git-Integration mit Adobe Cloud Manager

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, mit dem Code mithilfe der CI/CD-Pipelines von Cloud Manager bereitgestellt wird. Kunden können das Git-Repository von Cloud Manager standardmäßig verwenden. Kunden haben auch die Möglichkeit, ein lokal oder **kundenverwaltetes** Git-Repository mit Cloud Manager zu integrieren.

## Übersicht über die Git-Integration

>[!VIDEO](https://video.tv.adobe.com/v/28710/?captions=ger)

Diese Videoreihe untersucht mehrere Anwendungsfälle bei der Integration eines kundenverwalteten Git-Repositorys mit Cloud Manager, darunter:

* [Erstsynchronisierung](#initial-sync)
* [Grundlegende Zweigstellenstrategie](#branching-strategy)
* [Entwicklung von Funktionsbereichen](#feature-development)
* [Produktionsbereitstellung](#production-deployment)
* [Synchronisieren von Release-Tags](#sync-tags)

Eine vollständige Übersicht finden Sie im [Cloud Manager-Benutzerhandbuch](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html). Die Videoserie setzt grundlegende Kenntnisse des Git- und Quellcodeverwaltungs-Managements voraus. Weitere Informationen zu git finden Sie in den [zusätzlichen Ressourcen unten](#additional-resources) .

>[!NOTE]
>
> Die Schritte und Benennungskonventionen in dieser Videoreihe stellen einige bewährte Verfahren für die Arbeit mit einem kundenverwalteten Git-Repository und Cloud Manager dar. Es wird erwartet, dass die dargelegten Konventionen und Arbeitsabläufe für einzelne Entwicklungsteams angepasst werden.

## Erstsynchronisierung {#initial-sync}

Erste Schritte zum Synchronisieren eines kundenverwalteten Git-Repositorys mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12&captions=ger)

## Grundlegende Zweigstellenstrategie {#branching-strategy}

Richten Sie eine grundlegende Verzweigungsstrategie ein, um die [Produktions- und Nicht-Produktionslinien](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html)von Cloud Manager zu nutzen.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12&captions=ger)

## Entwicklung von Funktionsbereichen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Codeänderungen in einem kundenverwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren, um eine Nicht-Produktions-Pipeline für Codequalität- und Validierungstests zu verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12&captions=ger)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für eine Produktionsversion in einem kundenverwalteten Git-Repository vor und synchronisieren Sie diese mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in der stage- und produktionsumgebung zu ermöglichen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12&captions=ger)

## Synchronisieren von Release-Tags {#sync-tags}

Synchronisieren Sie Release-Tags aus einem Cloud Manager-Git-Repository in einem vom Kunden verwalteten Git-Repository, um die Bereitstellung von Code in der stage- und production-Umgebung zu veranschaulichen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12&captions=ger)

## Zusätzliche Ressourcen {#additional-resources}

* [Dokumentation zu Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [GitHub-Ressourcen](https://try.github.io)
* [Atlassische Git-Lehrgänge](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)