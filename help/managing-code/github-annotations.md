---
title: Anmerkungen zur GitHub-Prüfung
description: Erfahren Sie, wie GitHub PRs für Ihre privaten Repositorys mit Anmerkungen überprüft, um Ihnen hilfreiches Feedback zu geben.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 47%

---


# GitHub-Prüfungsnotationen {#github-annotations}

Erfahren Sie, wie GitHub PRs für Ihre privaten Repositorys mit Anmerkungen überprüft, um Ihnen hilfreiches Feedback zu geben.

## Überblick {#overview}

Wenn Sie [private Repositorys](private-repositories.md) für Ihr Cloud Manager-Programm verwenden, werden GitHub-Prüfungen automatisch für jede Pull-Anforderung ausgeführt. Diese Prüfungen werden mit nützlichen Informationen kommentiert, die Ihnen helfen, Probleme mit Ihrem Code so schnell wie möglich zu verstehen.

![Beispiel für Anmerkungen zur GitHub-Prüfung](assets/github-check-annotations.png)

Von [SonarQube](/help/using/custom-code-quality-rules.md) erkannte Probleme mit der [Code-Qualität](/help/using/code-quality-testing.md) werden eindeutig aufgeführt.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example.png)

Ihnen wird die genaue Code-Zeile mit dem Problem angegeben und Sie können darauf klicken, um den relevanten Code anzuzeigen. Diese Anmerkungen werden für alle Code-Probleme bereitgestellt, nicht nur für die Probleme, die in der Pull-Anforderung geändert wurden.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example-code.png)

Alle kommentierten Zeilen werden auf der Registerkarte **Geänderte Dateien** für die GitHub-Pull-Anfrage zusammengetragen. Anmerkungen zu Dateien, die in der Pull-Anfrage nicht geändert wurden, werden in einem eigenen Abschnitt angezeigt.

![Beispiel für Anmerkungen auf der Registerkarte „Geänderte Dateien“](assets/github-check-annotations-files-changed.png)

## Pipelines zur Code-Qualität {#code-quality-pipelines}

Die Ergebnisse der [Codequalität](/help/using/code-quality-testing.md) sind auch in der Pipeline sichtbar, die von Cloud Manager-Triggern automatisch unten auf der Registerkarte **Prüfungen** angezeigt werden. Sie ist auch über die **Details** der Prüfung der Pull-Anfrage zugänglich.

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality.png)

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality-2.png)

Sie können die Probleme auch in Form einer CSV-Datei visualisieren. Diese Methode kann abgerufen werden, indem [die Details der Pipeline-Ausführung in Cloud Manager anzeigen](/help/using/managing-pipelines.md).
