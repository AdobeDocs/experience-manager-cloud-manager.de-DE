---
title: Git-Integration mit Adobe Cloud Manager
description: In dieser Videoreihe wird die Einrichtung und Integration eines kundenseitig verwalteten (lokalen) Git-Repositorys mit Adobe Cloud Manager beschrieben.
exl-id: e517f8a4-23f0-4486-8278-91396dba76ec
TQID: https://experienceleague.adobe.com/fyGrLuc1bIBY9ZAgYiULxxJQy-ZZBLYtAAdYgqzSLAM
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 2011f63c513689f571d21772752348388c2f342a
workflow-type: tm+mt
source-wordcount: 356
ht-degree: 76%

---

# Git-Integration mit Adobe Cloud Manager

Adobe Cloud Manager verfügt über ein einzelnes Git-Repository, das der Bereitstellung von Code unter Verwendung der CI/CD-Pipelines von Cloud Manager dient. Sie können das Git-Repository von Cloud Manager wie bereitgestellt verwenden oder ein lokales oder vom Kunden verwaltetes Git-Repository mit Cloud Manager integrieren.

## Überblick über die Git-Integration

>[!VIDEO](https://video.tv.adobe.com/v/28710/)

In dieser Videoreihe werden verschiedene Anwendungsfälle für die Integration eines kundenseitig verwalteten Git-Repositorys mit Cloud Manager untersucht.

* [Erstsynchronisierung](#initial-sync)
* [Grundlegende Verzweigungsstrategie](#branching-strategy)
* [Entwicklung von Funktionsverzweigungen](#feature-development)
* [Produktionsbereitstellung](#production-deployment)
* [Synchronisieren von Versions-Tags](#sync-tags)

Diese Videoreihe erfordert grundlegende Kenntnisse der Git- und Quell-Code-Verwaltung. Weitere Informationen zu Git finden Sie in den [folgenden zusätzlichen Ressourcen](#additional-resources).

Die Schritte und Benennungskonventionen in dieser Videoreihe präsentieren mehrere Best Practices für die Arbeit mit einem kundenseitig verwalteten Git-Repository und Cloud Manager. Die gezeigten Konventionen und Workflows sind für einzelne Entwicklungsteams angepasst.

Einen vollständigen Überblick über Cloud Manager liefert Ihnen die [Einführung in Cloud Manager](/help/introduction.md).

## Erstsynchronisierung {#initial-sync}

Erste Schritte zum Synchronisieren eines kundenverwalteten Git-Repository mit dem Git-Repository von Cloud Manager.

>[!VIDEO](https://video.tv.adobe.com/v/28711/?quality=12)

## Standard-Verzweigungsstrategie {#branching-strategy}

Konfigurieren Sie eine grundlegende Verzweigungsstrategie für die Verwendung [ Cloud Manager-Pipelines ](/help/using/production-pipelines.md)Produktion[ und produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

>[!VIDEO](https://video.tv.adobe.com/v/28712/?quality=12)

## Entwicklung von Funktionsverzweigungen {#feature-development}

Verwenden Sie eine Funktionsverzweigung, um Code-Änderungen in einem kundenseitig verwalteten Git-Repository zu isolieren und mit dem Git-Repository von Cloud Manager zu synchronisieren. So können Sie eine produktionsfremde Pipeline für Code-Qualitäts- und Validierungstests verwenden.

>[!VIDEO](https://video.tv.adobe.com/v/28723/?quality=12)

## Produktionsbereitstellung {#production-deployment}

Bereiten Sie Code für die Produktionsfreigabe in einem kundenseitig verwalteten Git-Repository vor und synchronisieren Sie mit dem Git-Repository von Cloud Manager, um eine Bereitstellung in Staging- und Produktionsumgebungen vorzunehmen.

>[!VIDEO](https://video.tv.adobe.com/v/28724/?quality=12)

## Synchronisieren von Versions-Tags {#sync-tags}

Sie können Versions-Tags aus einem Cloud Manager-Git-Repository in einem kundenseitig verwalteten Git-Repository synchronisieren. Diese Funktion sorgt für Sichtbarkeit des in Staging- und Produktionsumgebungen bereitgestellten Codes.

>[!VIDEO](https://video.tv.adobe.com/v/28725/?quality=12)

## Zusätzliche Ressourcen {#additional-resources}

* [Einführung in Cloud Manager](/help/introduction.md)
* [GitHub-Ressourcen](https://docs.github.com/en/get-started/git-basics/set-up-git)
* [Git-Tutorials von Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
* [Git-Schnellübersicht](https://education.github.com/git-cheat-sheet-education.pdf)
