---
title: Git-Integration mit Adobe Cloud Manager
description: Eine Videoreihe, in der die Einrichtung und Integration eines kundenverwalteten (On-Premise) Git-Repository mit Adobe Cloud Manager beschrieben werden.
seo-title: Git-Integration mit Adobe Cloud Manager
seo-description: Eine Videoreihe, in der die Einrichtung und Integration eines kundenverwalteten (On-Premise) Git-Repository mit Adobe Cloud Manager beschrieben werden.
feature: Git-Repositorys
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
source-git-commit: 43bb3c477ef9c1ce178509b8180479d7616edc66
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 99%

---

# Git-Integration mit Adobe Cloud Manager

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient. Kunden können das Git-Repository von Cloud Manager sofort verwenden. Außerdem haben Kunden die Möglichkeit, ein On-Premise- oder **kundenverwaltetes** Git-Repository mit Cloud Manager zu integrieren.

## Übersicht über die Git-Integration

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In dieser Videoreihe werden verschiedene Anwendungsfälle bei der Integration eines kundenverwalteten Git-Repository mit Cloud Manager untersucht, darunter:

* [Erstsynchronisierung](#initial-sync)
* [Standard-Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsimplementierung](#production-deployment)
* [Synchronisieren von Release-Tags](#sync-tags)

Eine vollständige Übersicht finden Sie im [Cloud Manager-Benutzerhandbuch](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html). Die Videoreihe setzt grundlegende Kenntnisse der Git- und Quellcodeverwaltung voraus. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

>[!NOTE]
>
> Die Schritte und Benennungskonventionen in dieser Videoreihe präsentieren mehrere Best Practices für die Arbeit mit einem kundenverwalteten Git-Repository und Cloud Manager. Es wird erwartet, dass die dargelegten Konventionen und Arbeitsabläufe für einzelne Entwicklungsteams angepasst werden.

## Erstsynchronisierung {#initial-sync}

Erste Schritte zum Synchronisieren eines kundenverwalteten Git-Repository mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Standard-Verzweigungsstrategie {#branching-strategy}

Richten Sie eine Standard-Verzweigungsstrategie ein, um die [Produktions- und Nicht-Produktions-Pipelines](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/how-to-use/configuring-pipeline.html) von Cloud Manager zu nutzen.

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Codeänderungen in einem kundenverwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren; so können Sie eine Nicht-Produktions-Pipeline für Codequalität- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für die Produktionsfreigabe in einem kundenverwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Release-Tags {#sync-tags}

Synchronisieren Sie Release-Tags aus einem Cloud Manager-Git-Repository in einem kundenverwalteten Git-Repository, um für Sichtbarkeit des in Staging- und Produktionsumgebungen bereitgestellten Codes zu sorgen.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [Dokumentation für Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
* [GitHub-Ressourcen](https://try.github.io)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
