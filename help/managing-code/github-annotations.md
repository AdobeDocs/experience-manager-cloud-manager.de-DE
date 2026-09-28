---
title: Anmerkungen zur GitHub-Prüfung
description: Erfahren Sie, wie GitHub Pull-Anfragen an Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
    internal-label: Experience Manager Cloud Manager
source-git-commit: 26e8d7835883cd6a64913b3b4e3619041af63bf5
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 32%
---

# Anmerkungen zur GitHub-Prüfung {#github-annotations}

Erfahren Sie, wie GitHub-Prüfungen PRs für Ihre privaten Repositorys kommentieren, um Ihnen Feedback zu geben.

## Überblick {#overview}

Wenn Sie [private Repositorys](private-repositories.md) für Ihr Cloud Manager-Programm verwenden, werden bei jeder Pull-Anfrage automatisch Prüfungen in GitHub ausgeführt. Diesen Prüfungen werden Informationen hinzugefügt, die Ihnen helfen, Probleme mit Ihrem Code so schnell wie möglich zu identifizieren.

![Beispiel für Anmerkungen zur GitHub-Prüfung](assets/github-check-annotations.png)

Von [SonarQube](/help/using/custom-code-quality-rules.md) erkannte Probleme mit der [Code-Qualität](/help/using/code-quality-testing.md) werden eindeutig aufgeführt.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example.png)

Die genaue Codezeile mit dem Problem wird angegeben und Sie können sie auswählen, um den entsprechenden Code anzuzeigen. Diese Anmerkungen werden für alle Code-Probleme bereitgestellt, nicht nur für die in der Pull-Anfrage.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example-code.png)

Alle kommentierten Zeilen werden auf der Registerkarte **Geänderte Dateien** für die GitHub-Pull-Anfrage zusammengetragen. Anmerkungen für Dateien, die in der Pull-Anfrage nicht geändert wurden, werden in einem separaten Abschnitt angezeigt.

![Beispiel für Anmerkungen auf der Registerkarte „Geänderte Dateien“](assets/github-check-annotations-files-changed.png)

## Code-Qualitäts-Pipelines {#code-quality-pipelines}

Die [Code](/help/using/code-quality-testing.md)Qualitätsergebnisse sind auch in der Pipeline sichtbar, die von Cloud Manager automatisch Trigger wird, am unteren Rand der Registerkarte **Prüfungen**. Auf sie kann auch über die **Details** der Prüfung für die Pull-Anfrage zugegriffen werden.

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality.png)

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality-2.png)

Sie können die Probleme auch als CSV-Datei anzeigen. Sie können auf diese Informationen zugreifen, indem Sie [die Details der Pipeline-Ausführung in Cloud Manager anzeigen](/help/using/managing-pipelines.md).
