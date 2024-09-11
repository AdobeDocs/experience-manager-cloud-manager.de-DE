---
title: Git-Integration mit Adobe Cloud Manager
description: In dieser Videoreihe wird die Einrichtung und Integration eines kundenseitig verwalteten (lokalen) Git-Repositorys mit Adobe Cloud Manager beschrieben.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 99%

---


# Git-Integration mit Adobe Cloud Manager

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient. Sie können das vorkonfigurierte Git-Repository von Cloud Manager verwenden, oder Sie haben die Möglichkeit, ein lokales oder kundenseitig verwaltetes Git-Repository in Cloud Manager zu integrieren.

## Überblick über die Git-Integration

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In dieser Videoreihe werden verschiedene Anwendungsfälle für die Integration eines kundenseitig verwalteten Git-Repositorys mit Cloud Manager untersucht.

* [Erstsynchronisierung](#initial-sync)
* [Standard-Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsbereitstellung](#production-deployment)
* [Synchronisieren von Versions-Tags](#sync-tags)

Diese Videoreihe setzt Grundkenntnisse über Git und die Verwaltung von Quellenkontrollen voraus. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

Die Schritte und Benennungskonventionen in dieser Videoreihe präsentieren mehrere Best Practices für die Arbeit mit einem kundenseitig verwalteten Git-Repository und Cloud Manager. Es wird erwartet, dass die dargelegten Konventionen und Arbeitsabläufe für einzelne Entwicklungs-Teams angepasst werden.

Einen vollständigen Überblick über Cloud Manager liefert Ihnen die [Einführung in Cloud Manager](/help/introduction.md).

## Erstsynchronisierung {#initial-sync}

Erste Schritte zum Synchronisieren eines kundenverwalteten Git-Repository mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Standard-Verzweigungsstrategie {#branching-strategy}

Richten Sie eine grundlegende Verzweigungsstrategie ein, um sowohl die [Produktions-Pipelines](/help/using/production-pipelines.md) als auch die [produktionsfremden Pipelines](/help/using/non-production-pipelines.md) von Cloud Manager zu nutzen.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Code-Änderungen in einem kundenseitig verwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren. So können Sie eine produktionsfremde Pipeline für Code-Qualitäts- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für die Produktionsfreigabe in einem kundenseitig verwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Release-Tags {#sync-tags}

Sie können Versions-Tags aus einem Cloud Manager-Git-Repository in einem kundenseitig verwalteten Git-Repository synchronisieren. Diese Funktion sorgt für Sichtbarkeit des in Staging- und Produktionsumgebungen bereitgestellten Codes.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [Einführung in Cloud Manager](/help/introduction.md)
* [GitHub-Ressourcen](https://docs.github.com/de/get-started/getting-started-with-git/set-up-git)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
