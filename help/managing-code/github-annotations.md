---
title: GitHub - Anmerkungen prüfen
description: Erfahren Sie, wie GitHub PRs für Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 210d40a5e12b40fd84efc461c6a1c48559120837
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# GitHub - Anmerkungen prüfen {#github-annotations}

Erfahren Sie, wie GitHub PRs für Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.

## Überblick {#overview}

Wenn Sie [private Repositorys](private-repositories.md) für Ihr Cloud Manager-Programm werden Prüfungen in GitHub automatisch bei jeder Pull-Anforderung ausgeführt. Diese werden mit nützlichen Informationen kommentiert, die Ihnen helfen, Probleme mit Ihrem Code so schnell wie möglich zu verstehen.

![Beispiel für GitHub-Prüfanmerkungen](assets/github-check-annotations.png)

[Codequalität](/help/using/code-quality-testing.md) aufgedeckte Probleme [SonarQube](/help/using/custom-code-quality-rules.md) eindeutig aufgeführt sind.

![Beispiel für eine Anmerkung zu Codeproblemen](assets/github-check-annotations-example.png)

Die genaue Codezeile mit dem Problem wird bereitgestellt und Sie können darauf klicken, um den relevanten Code anzuzeigen. Diese Anmerkungen werden für alle Code-Probleme bereitgestellt, nicht nur für die in der Pull-Anforderung geänderten.

![Beispiel für eine Anmerkung zu Codeproblemen](assets/github-check-annotations-example-code.png)

Alle kommentierten Zeilen werden auf der **Geänderte Dateien** auf der GitHub-Pull-Anforderung. Anmerkungen zu Dateien, die in der Pull-Anforderung nicht geändert wurden, werden in ihrem eigenen Abschnitt angezeigt.

![Beispiel für Anmerkungen auf der Registerkarte für geänderte Dateien](assets/github-check-annotations-files-changed.png)

## Code-Qualitäts-Pipelines {#code-quality-pipelines}

Die [Codequalität](/help/using/code-quality-testing.md) Ergebnisse sind auch in der Pipeline sichtbar, die automatisch von Cloud Manager am unteren Rand der **Prüfungen** Registerkarte. Sie ist auch über die **Details** der Prüfung der Pull-Anforderung.

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality.png)

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality-2.png)

Sie können die Probleme auch in Form einer CSV-Datei visualisieren. Dies kann abgerufen werden durch [die Details der Pipeline-Ausführung in Cloud Manager anzeigen.](/help/using/managing-pipelines.md)
