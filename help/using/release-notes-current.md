---
title: Versionshinweise für 2019.9.0
seo-title: Versionshinweise für AEM Cloud Manager 2019.9.0
description: Auf dieser Seite erhalten Sie Informationen zur Cloud Manager-Version 2019.9.0.
seo-description: Auf dieser Seite erhalten Sie Informationen zur AEM Cloud Manager-Version 2019.9.0.
translation-type: tm+mt
source-git-commit: 26014cfabfee6226033ba2fc1167d8f5509e17c6

---

# Versionshinweise für 2019.9.0 {#release-notes-for}

Mit der Version [!UICONTROL Cloud Manager] 2019.9.0 werden die Kriterien für den Sicherheitstest aktualisiert, herunterladbare Überwachungsdiagramme hinzugefügt und einige von Kunden gemeldete Probleme bei der Benutzerfreundlichkeit behoben.

## Veröffentlichungsdatum {#release-date}

Die [!UICONTROL Cloud Manager]-Version 2019.9.0 wurde am 12. September 2019 veröffentlicht.

## Neuigkeiten {#whats-new}

* Die Kategorisierung des Sling Referrer Filter-Gesundheitschecks wurde von "Wichtig"in "Wichtig"geändert.
* Die Kategorisierung der Überprüfung der Konfigurationsstatus von HTML Library Manager wurde von "Wichtig"in "Wichtig"geändert.
* Überwachungsdiagramme können jetzt heruntergeladen werden. Weitere Informationen finden Sie unter [Überwachen Ihrer Umgebungen](monitor-your-environments.md).
* If a program does not have a production AEM environment, clicking on the program card from the landing page will navigate to the Cloud Manager overview page, not produce an error dialog.
* Die **Pipeline-Einstellungskarte** auf der Seite " **Übersicht** "wurde auf **Produktions-Pipeline-Einstellungen** eingestellt.
* The Important Failure Behavior radio buttons have been removed from code-quality only pipelines.
* Auf der Seite " **Aktivität** "wird nun der Name der Pipeline für jede Ausführung angezeigt.
* The execution page now displays the name of the pipeline.
* The Code Quality summary dialog now shows a description for each rating.

## Fehlerbehebungen {#bug-fixes}

* Some users could not view an execution details when it was waiting for approval.
* On Overview page, the right margin was not consistent.****
* The build container could run out of memory in large projects.
* Under certain circumstances, the BannedPaths OakPAL rule did not identify installed content under /libs.
* When a quality gate was rejected, the dialog heading still showed Partially Passed.**

## Bekannte Probleme {#known-issues}

* Downloading of monitoring graphs is not available in Safari.
