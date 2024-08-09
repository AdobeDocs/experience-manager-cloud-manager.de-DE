---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 97%

---


# CI/CD-Pipelines {#ci-cd-pipeline}

Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.

## Übersicht {#overview}

[!UICONTROL Cloud Manager] enthält ein CI/CD-Framework (Continuous Integration/Continuous Delivery), mit dem Implementierungs-Teams schnell neuen oder aktualisierten Code testen und bereitstellen können. Beispielsweise können Implementierungs-Teams eine automatisierte CI/CD-Pipeline einrichten, konfigurieren und starten, die Best Practices von Adobe für die Kodierung nutzt, um einen umfassenden Codescan durchzuführen und die höchste Code-Qualität sicherzustellen.

Die CI/CD-Pipeline automatisiert außerdem die Unit- und Leistungstests, um die Bereitstellungseffizienz zu erhöhen und proaktiv wichtige Probleme zu erkennen, deren Behebung nach der Bereitstellung hohe Kosten verursacht. Implementierungs-Teams können auf einen umfassenden Code-Leistungsbericht zugreifen, um einen Überblick über die potenziellen Auswirkungen auf KPIs und kritische Sicherheitsprüfungen für den Fall zu erhalten, dass der Code in der Produktion bereitgestellt wird.

## Der Pipeline-Prozess {#pipeline-process}

Dieses Diagramm zeigt, was passiert, wenn eine Freigabe unter Verwendung einer Pipeline in [!UICONTROL Cloud Manager] ausgelöst wird.

![Der Pipeline-Prozess](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipeline-Schritt | Beschreibung |
|---|---|
| 1. Start einer Release-Veröffentlichung | Ein Bereitstellungs-Manager löst die Freigabe entweder manuell (per Git-Commit) oder basierend auf einem wiederkehrenden Zeitplan aus. |
| 2. Erstellen des Release-Tags | [!UICONTROL Cloud Manager] erstellt ein Git-Tag, um die Release-Version mit einer automatisch generierten Versionsnummer zu kennzeichnen, z. B. `2018.531.245527.0000001222`. |
| 3. Erstellung als Release-Version mit automatisch generierter Versionsnummer | [!UICONTROL Cloud Manager] erstellt das Programm mit der neu zugewiesenen Versionsnummer. |
| 4. Bewertung der Code-Qualität | [!UICONTROL Cloud Manager] scannt den Quell-Code und stellt eine Zusammenfassung bereit, bevor der Code in der Staging-Umgebung bereitgestellt werden kann. |
| 5. Speichern versionierter Artefakte | Die Release-Artefakte werden zur späteren Verwendung in den Bereitstellungsschritten gespeichert. |
| 6. Automatische Bereitstellung von Artefakten für AMS AEM-Staging-Umgebung | Das Release-Artefakt wird in der Staging-Umgebung bereitgestellt. |
| 7. Auslösen automatisierter Tests | [!UICONTROL Cloud Manager] führt die Leistungs- und Sicherheitstests für das Artefakt aus. |
| 8. Bereitstellung für Produktionsauslöser | Sobald die automatisierten Tests abgeschlossen sind, startet [!UICONTROL Cloud Manager] die Bereitstellung in der Produktionsumgebung. |
| 9. Abruf der Artefakte durch [!UICONTROL Cloud Manager] für die Bereitstellung | [!UICONTROL Cloud Manager] ruft die gespeicherten Release-Artefakte ab. |
| 10. Bereitstellung der Artefakte in der Produktionsumgebung | Die Release-Artefakte werden in der Produktionsumgebung bereitgestellt. |

### Einrichten einer CI/CD-Pipeline {#how-to-setup-a-ci-cd-pipeline}

Weitere Informationen zur Pipelinekonfiguration finden Sie in den Dokumenten [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md).

## Qualitäts-Gates {#quality-gates}

Die CI/CD-Pipeline bietet Quality Gates (bzw. Akzeptanzkriterien), die erfüllt werden müssen, bevor der Code aus der Staging-Umgebung in die Bereitstellungsumgebung verschoben werden kann. Die Pipeline muss drei Akzeptanztests bestehen:

* Code-Qualität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests sind drei Stufen von Problemen definiert:

* **Kritisch:** Beim Test festgestellte ausschlaggebende Probleme, die ein sofortiges Fehlschlagen der Pipeline verursachen.
* **Wichtig:** Beim Test festgestellte wichtige Probleme, durch die die Pipeline angehalten wird. Bereitstellungs-Manager, Projekt-Manager oder Geschäftsinhaber können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.
* **Information:** Beim Test festgestellte Probleme informativer Natur, die ausschließlich zu Informationszwecken genannt werden und keine Auswirkungen auf die Pipeline-Ausführung haben.

Dies ist ein Beispiel für eine Code-Prüfung mit festgestellten Problemen.

![Beispiel für Code-Prüfung](/help/assets/quality-gate-failed.png)

### Einrichten eines Akzeptanztests {#how-to-setup-gates}

Weitere Informationen zum Einrichten von Code-, Qualitäts- und Leistungs-Akzeptanztests finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md).
