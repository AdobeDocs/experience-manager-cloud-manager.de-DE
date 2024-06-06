---
title: GitHub-Prüfkonfiguration für private Repositorys
description: Erfahren Sie, wie Sie die automatisch erstellten Pipelines steuern, um jede Pull-Anforderung in ein privates Repository zu validieren.
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 7%

---


# GitHub-Prüfkonfiguration für private Repositorys {#github-check-config}

Erfahren Sie, wie Sie die automatisch erstellten Pipelines steuern, um jede Pull-Anforderung in ein privates Repository zu validieren.

## Konfiguration von GitHub-Prüfungen {#configuration}

Bei Verwendung von [private Repositorys,](private-repositories.md#using) a [Vollständige Stack-Code-Qualitäts-Pipeline](/help/overview/ci-cd-pipelines.md) automatisch erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

Sie können diese Prüfungen steuern, indem Sie eine `.cloudmanager/pr_pipelines.yml` -Datei in der Standardverzweigung des privaten Repositorys.

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
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` oder `false` ermöglichen | `false` | Ob nur der letzte Kommentar mit den Codescans bei dieser GitHub-Pull-Anforderung beibehalten werden soll oder ob alle |
| `type` | `CI_CD` | Nicht zutreffend | Definiert das Verhalten einer CI/CD-Pipeline |
| `template.programID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Kann verwendet werden, um die [Pipeline-Variablen](/help/getting-started/build-environment.md#pipeline-variables) die auf einer der vorhandenen Pipelines festgelegt sind, die automatisch von jeder PA erstellt werden. |
| `template.pipelineID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Kann verwendet werden, um die [Pipeline-Variablen](/help/getting-started/build-environment.md#pipeline-variables) die auf einer der vorhandenen Pipelines festgelegt sind, die automatisch von jeder PA erstellt werden. |
| `namePrefix` | Zeichenfolge | `Full Stack Code Quality Pipeline for PR` | Wird verwendet, um den Namen der automatisch erstellten Pipeline festzulegen |
| `importantMetricsFailureBehavior` | `CONTINUE` oder `FAIL` oder `PAUSE` | `CONTINUE` | Legt das wichtige Metrikverhalten der Pipeline fest<br>`CONTINUE` = Wenn eine wichtige Metrik fehlschlägt, wird die Pipeline automatisch weitergeleitet<br>`FAIL` = Die Pipeline endet mit dem Status FEHLGESCHLAGEN , wenn eine wichtige Metrik fehlschlägt<br>`PAUSE` = Der Codescans-Schritt erhält einen WARING-Status, wenn eine wichtige Metrik fehlschlägt, und muss manuell wieder aufgenommen werden |
