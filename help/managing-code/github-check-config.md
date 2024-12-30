---
title: Konfiguration der GitHub-Prüfung für private Repositorys
description: Erfahren Sie, wie Sie die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 100%

---

# Konfiguration der GitHub-Prüfung für private Repositorys {#github-check-config}

Erfahren Sie, wie Sie die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren.

## Konfiguration von GitHub-Prüfungen {#configuration}

Bei der Verwendung von [privaten Repositorys](private-repositories.md#using) wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/overview/ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

Sie können diese Prüfungen steuern, indem Sie eine Datei namens `.cloudmanager/pr_pipelines.yml` in der Standardverzweigung des privaten Repositorys erstellen.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Mögliche Werte | Standard | Beschreibung |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` oder `false` | `false` | Ob bei dieser GitHub-Pull-Anfrage nur der letzte Kommentar oder alle Kommentare mit den Ergebnissen der Code-Scans beibehalten werden sollen. |
| `type` | `CI_CD` | Nicht zutreffend | Definiert das Verhalten einer CI/CD-Pipeline. |
| `template.programID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Sie können die [Pipeline-Variablen](/help/getting-started/build-environment.md#pipeline-variables) wiederverwenden, die auf einer vorhandenen Pipeline festgelegt sind, die jede Pull-Anfrage automatisch erstellt. |
| `template.pipelineID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Sie können die [Pipeline-Variablen](/help/getting-started/build-environment.md#pipeline-variables) wiederverwenden, die auf einer vorhandenen Pipeline festgelegt sind, die jede Pull-Anfrage automatisch erstellt. |
| `namePrefix` | Zeichenfolge | `Full Stack Code Quality Pipeline for PR` | Wird verwendet, um den Namen der automatisch erstellten Pipeline festzulegen. |
| `importantMetricsFailureBehavior` | `CONTINUE` oder `FAIL` oder `PAUSE` | `CONTINUE` | Legt das Verhalten der Pipeline für wichtige Metriken fest<br>`CONTINUE` = Wenn eine wichtige Metrik fehlschlägt, wird die Pipeline automatisch weitergeleitet<br>`FAIL` = Wenn eine wichtige Metrik fehlschlägt, endet die Pipeline mit dem Status FEHLGESCHLAGEN<br>`PAUSE` = Wenn eine wichtige Metrik fehlschlägt, erhält der Code-Scan-Schritt einen Status WARTEN und muss manuell wieder aufgenommen werden |
