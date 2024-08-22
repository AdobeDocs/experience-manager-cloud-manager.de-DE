---
title: Konfiguration der GitHub-Prüfung für private Repositorys
description: Erfahren Sie, wie Sie die automatisch erstellten Pipelines steuern, um jede Pull-Anfrage an ein privates Repository zu validieren.
exl-id: 29c9e487-e196-411a-8cda-6751b0a56066
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 39%

---

# GitHub-Prüfkonfiguration für private Repositorys {#github-check-config}

Erfahren Sie, wie Sie die automatisch erstellten Pipelines steuern, um jede Pull-Anfrage an ein privates Repository zu validieren.

## Konfiguration von GitHub-Prüfungen {#configuration}

Bei Verwendung von [privaten Repositorys](private-repositories.md#using) wird automatisch eine [vollständige Stack-Code-Qualitäts-Pipeline](/help/overview/ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

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
| `shouldDeletePreviousComment` | `true` oder `false` | `false` | Gibt an, ob nur der letzte Kommentar mit den Ergebnissen der Codescans für diese GitHub-Pull-Anforderung beibehalten werden soll oder ob alle beibehalten werden sollen. |
| `type` | `CI_CD` | Nicht zutreffend | Definiert das Verhalten einer CI/CD-Pipeline. |
| `template.programID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Sie können die [Pipeline-Variablen](/help/getting-started/build-environment.md#pipeline-variables) wiederverwenden, die in einer vorhandenen Pipeline festgelegt sind, die von jedem PA automatisch erstellt wird. |
| `template.pipelineID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Sie können die [Pipeline-Variablen](/help/getting-started/build-environment.md#pipeline-variables) wiederverwenden, die in einer vorhandenen Pipeline festgelegt sind, die von jedem PA automatisch erstellt wird. |
| `namePrefix` | Zeichenfolge | `Full Stack Code Quality Pipeline for PR` | Wird verwendet, um den Namen der automatisch erstellten Pipeline festzulegen. |
| `importantMetricsFailureBehavior` | `CONTINUE` oder `FAIL` oder `PAUSE` | `CONTINUE` | Legt das wichtige Metrikverhalten der Pipeline fest<br>`CONTINUE` = Wenn eine wichtige Metrik fehlschlägt, wechselt die Pipeline automatisch vorwärts.<br>`FAIL` = Die Pipeline endet mit dem Status FEHLGESCHLAGEN , wenn eine wichtige Metrik fehlschlägt.<br>`PAUSE` = Der Codescan-Schritt erhält einen WARING-Status, wenn eine wichtige Metrik fehlschlägt, und muss manuell fortgesetzt werden. |
