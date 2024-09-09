---
title: Git-Integration mit Adobe Cloud Manager
description: Diese Videoreihe führt Sie durch die Einrichtung und Integration eines kundenverwalteten (On-Premise) Git-Repositorys mit Adobe Cloud Manager.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 51bd685a17eb9d68b1ec8245e6167cab02101fc1
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 23%

---


# Git-Integration mit Adobe Cloud Manager

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das zur Bereitstellung von Code mithilfe der CI/CD-Pipelines von Cloud Manager verwendet wird. Sie können das Git-Repository von Cloud Manager nativ verwenden oder Sie können auch ein On-Premise- oder kundenverwaltetes Git-Repository in Cloud Manager integrieren.

## Übersicht über die Git-Integration

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In dieser Videoreihe werden verschiedene Anwendungsfälle zur Integration eines kundenverwalteten Git-Repositorys in Cloud Manager untersucht.

* [Erstsynchronisierung](#initial-sync)
* [Standard-Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsbereitstellung](#production-deployment)
* [Synchronisieren von Versions-Tags](#sync-tags)

Diese Videoreihe setzt grundlegende Kenntnisse der Git- und Quellcodeverwaltung voraus. Weitere Informationen zu Git finden Sie in den [zusätzlichen Ressourcen unter ](#additional-resources) .

Die Schritte und Benennungskonventionen, die in dieser Videoreihe beschrieben werden, stellen einige Best Practices für die Arbeit mit einem kundenverwalteten Git-Repository und Cloud Manager dar. Es wird erwartet, dass die dargelegten Konventionen und Arbeitsabläufe für einzelne Entwicklungsteams angepasst werden.

Einen vollständigen Überblick über Cloud Manager liefert Ihnen die [Einführung in Cloud Manager](/help/introduction.md).

## Erstsynchronisierung {#initial-sync}

Erste Schritte zum Synchronisieren eines kundenverwalteten Git-Repository mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Grundlegende Verzweigungsstrategie {#branching-strategy}

Richten Sie eine grundlegende Verzweigungsstrategie ein, um die Vorteile der Cloud Manager-Pipeline [Produktion](/help/using/production-pipelines.md) und [Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md) zu nutzen.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Codeänderungen in einem kundenverwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren, um eine Nicht-Produktions-Pipeline für Codequalität- und Validierungstests zu verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für eine Produktionsversion in einem kundenverwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um es in Staging- und Produktionsumgebungen bereitzustellen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Release-Tags {#sync-tags}

Sie können Release-Tags aus einem Cloud Manager-Git-Repository in ein kundenverwaltetes Git-Repository synchronisieren. Diese Funktion bietet Einblicke in den Code, der sowohl in der Staging- als auch in der Produktionsumgebung bereitgestellt wurde.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [Einführung in Cloud Manager](/help/introduction.md)
* [GitHub-Ressourcen](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
