---
title: Anmerkungen zur GitHub-Prüfung
description: Erfahren Sie, wie GitHub Pull-Anfragen an Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
source-git-commit: 210d40a5e12b40fd84efc461c6a1c48559120837
workflow-type: ht
source-wordcount: '252'
ht-degree: 100%

---


# Anmerkungen zur GitHub-Prüfung {#github-annotations}

Erfahren Sie, wie GitHub Pull-Anfragen an Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.

## Übersicht {#overview}

Wenn Sie [private Repositorys](private-repositories.md) für Ihr Cloud Manager-Programm verwenden, werden Prüfungen in GitHub automatisch bei jeder Pull-Anfrage ausgeführt. Diese werden mit nützlichen Informationen kommentiert, die Ihnen helfen, Probleme mit Ihrem Code so schnell wie möglich zu verstehen.

![Beispiel für Anmerkungen zur GitHub-Prüfung](assets/github-check-annotations.png)

Von [SonarQube](/help/using/custom-code-quality-rules.md) erkannte Probleme mit der [Code-Qualität](/help/using/code-quality-testing.md) werden eindeutig aufgeführt.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example.png)

Ihnen wird die genaue Code-Zeile mit dem Problem angegeben und Sie können darauf klicken, um den relevanten Code anzuzeigen. Diese Anmerkungen werden für alle Code-Probleme angezeigt, nicht nur für die in der Pull-Anfrage geänderten.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example-code.png)

Alle kommentierten Zeilen werden auf der Registerkarte **Geänderte Dateien** für die GitHub-Pull-Anfrage zusammengetragen. Anmerkungen zu Dateien, die in der Pull-Anfrage nicht geändert wurden, werden in einem eigenen Abschnitt angezeigt.

![Beispiel für Anmerkungen auf der Registerkarte „Geänderte Dateien“](assets/github-check-annotations-files-changed.png)

## Code-Qualitäts-Pipeline {#code-quality-pipelines}

Die Ergebnisse für die [Code-Qualität](/help/using/code-quality-testing.md) werden ebenfalls am unteren Rand der Registerkarte **Prüfungen** in der Pipeline angezeigt, die automatisch von Cloud Manager ausgelöst wird. Sie ist auch über die **Details** der Prüfung der Pull-Anfrage zugänglich.

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality.png)

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality-2.png)

Sie können die Probleme auch in Form einer CSV-Datei visualisieren. Diese kann abgerufen werden, indem Sie [die Details der Pipeline-Ausführung in Cloud Manager anzeigen.](/help/using/managing-pipelines.md)
