---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 30%

---


# CI/CD-Pipelines {#ci-cd-pipeline}

Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.

## Übersicht {#overview}

[!UICONTROL Cloud Manager] umfasst ein Framework für die kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD), mit dem Implementierungsteams neuen oder aktualisierten Code schnell testen und bereitstellen können. Beispielsweise können Implementierungs-Teams eine automatisierte CI/CD-Pipeline einrichten, konfigurieren und starten, die Best Practices von Adobe für die Kodierung nutzt, um einen umfassenden Codescan durchzuführen und die höchste Code-Qualität sicherzustellen.

Die CI/CD-Pipeline automatisiert außerdem Prozess zum Einheiten- und Leistungstest, um die Bereitstellungseffizienz zu steigern und kritische Probleme, die nach der Bereitstellung zu beheben sind, proaktiv zu identifizieren. Implementierungs-Teams können auf einen umfassenden Codeleistungsbericht zugreifen, um einen Überblick über die potenziellen Auswirkungen auf KPIs und kritische Sicherheitsprüfungen für den Fall zu erhalten, dass der Code in der Produktion bereitgestellt wird.

## Pipeline-Prozess {#pipeline-process}

Dieses Diagramm zeigt, was passiert, wenn eine Version in [!UICONTROL Cloud Manager] Verwendung einer Pipeline.

![Der Pipeline-Prozess](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipeline-Schritt | Beschreibung |
|---|---|
| 1. Start einer Release-Veröffentlichung | Ein Bereitstellungsmanager Trigger eine Version entweder manuell, mit einem Git-Commit oder basierend auf einem wiederkehrenden Zeitplan. |
| 2. Release-Tag erstellen | [!UICONTROL Cloud Manager] erstellt ein Git-Tag, um die Version mit einer automatisch generierten Versionsnummer zu kennzeichnen, z. B. `2018.531.245527.0000001222`. |
| 3. Als Version mit automatisch generierter Version erstellt | [!UICONTROL Cloud Manager] erstellt die Anwendung mit der neu zugewiesenen Versionsnummer. |
| 4. Bewerten der Codequalität | [!UICONTROL Cloud Manager] scannt den Quellcode und stellt eine Zusammenfassung bereit, bevor der Code in der Staging-Umgebung bereitgestellt werden kann. |
| 5. Speicherung versionierter Artefakte | Die Release-Artefakte werden zur späteren Verwendung in den Implementierungsschritten gespeichert. |
| 6. Automatische Bereitstellung von Artefakten in AMS AEM Staging | Das Release-Artefakt wird in der Staging-Umgebung bereitgestellt. |
| 7. Automatisierte Trigger-Tests | [!UICONTROL Cloud Manager] führt Leistungs- und Sicherheitstests für das Artefakt durch. |
| 8. Bereitstellung des Produktions-Triggers | Nach Abschluss der automatisierten Tests [!UICONTROL Cloud Manager] startet die Bereitstellung in der Produktion. |
| 9. [!UICONTROL Cloud Manager] Abrufen der bereitzustellenden Artefakte | [!UICONTROL Cloud Manager] ruft die gespeicherten Release-Artefakte ab. |
| 10. Bereitstellung von Artefakten für die Produktion | Die Release-Artefakte werden in der Produktionsumgebung bereitgestellt. |

### Einrichten einer CI/CD-Pipeline {#how-to-setup-a-ci-cd-pipeline}

Weitere Informationen zur Pipeline-Konfiguration finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

## Quality Gates {#quality-gates}

Die CI/CD-Pipeline bietet Quality Gates (oder Akzeptanzkriterien), die erfüllt sein müssen, bevor der Code aus der Staging-Umgebung in die Bereitstellungsumgebung verschoben werden kann. Die Pipeline muss drei Akzeptanztests bestehen:

* Code-Qualität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests gibt es drei Stufen von Problemen, die identifiziert werden können:

* **Kritisch** - Kritische Probleme, die vom Test erkannt werden, führen zu einem sofortigen Pipelinefehler.
* **Wichtig** - Wichtige vom Test identifizierte Probleme führen dazu, dass die Pipeline angehalten wird. Implementierungs-Manager, Projekt-Manager oder Geschäftsinhaber können die Probleme außer Kraft setzen. In diesem Fall wird die Pipeline fortgesetzt. Sie können die Probleme aber auch akzeptieren. In diesem Fall stoppt die Pipeline mit einem Fehler.
* **Informationen** - Beim Test festgestellte Informationsprobleme werden ausschließlich zu Informationszwecken bereitgestellt und haben keine Auswirkungen auf die Pipelineausführung.

Dies ist ein Beispiel für eine Codescan mit identifizierten Problemen.

![Code-Scan-Beispiel](/help/assets/quality-gate-failed.png)

### Einrichten von Gates {#how-to-setup-gates}

Weitere Informationen zum Einrichten von Code-, Qualitäts- und Leistungs-Gates finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md).
