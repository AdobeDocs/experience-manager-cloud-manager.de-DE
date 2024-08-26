---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 59%

---


# CI/CD-Pipelines {#ci-cd-pipeline}

Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.

## Übersicht {#overview}

[!UICONTROL Cloud Manager] enthält ein Framework für die kontinuierliche Integration/kontinuierliche Bereitstellung (CI/CD), mit dem Implementierungsteams schnell testen und neuen oder aktualisierten Code bereitstellen können. Implementierungsteams können eine automatisierte CI/CD-Pipeline einrichten, konfigurieren und starten. Diese Pipeline folgt den Best Practices für die Adobe-Codierung, um einen umfassenden Codescan durchzuführen und die höchste Codequalität zu gewährleisten.

Die CI/CD-Pipeline automatisiert außerdem die Unit- und Leistungstests, um die Bereitstellungseffizienz zu erhöhen und proaktiv wichtige Probleme zu erkennen, deren Behebung nach der Bereitstellung hohe Kosten verursacht. Implementierungs-Teams können auf einen umfassenden Code-Leistungsbericht zugreifen, um einen Überblick über die potenziellen Auswirkungen auf KPIs und kritische Sicherheitsprüfungen für den Fall zu erhalten, dass der Code in der Produktion bereitgestellt wird.

## Über den Pipeline-Prozess {#pipeline-process}

Das folgende Diagramm zeigt, was passiert, wenn eine Veröffentlichung in [!UICONTROL Cloud Manager] mithilfe einer Pipeline ausgelöst wird.

![Der Pipeline-Prozess](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipeline-Schritt | Beschreibung |
| --- | --- |
| 1. Start einer Release-Veröffentlichung | Ein Bereitstellungsmanager Trigger eine Version entweder manuell, mit einem Git-Commit oder basierend auf einem wiederkehrenden Zeitplan. |
| 2. Release-Tag erstellen | [!UICONTROL Cloud Manager] erstellt ein Git-Tag, um die Version mit einer automatisch generierten Versionsnummer zu kennzeichnen, z. B. `2018.531.245527.0000001222`. |
| 3. Erstellung als Release-Version mit automatisch generierter Versionsnummer | [!UICONTROL Cloud Manager] erstellt die Anwendung mit der neu zugewiesenen Versionsnummer. |
| 4. Bewertung der Code-Qualität | [!UICONTROL Cloud Manager] scannt den Quellcode und stellt eine Zusammenfassung bereit, bevor der Code in der Staging-Umgebung bereitgestellt werden kann. |
| 5. Speicherung von versionierten Artefakten | Die Release-Artefakte werden zur späteren Verwendung in den Bereitstellungsschritten gespeichert. |
| 6. Automatische Bereitstellung von Artefakten für AMS-AEM-Staging | Das Release-Artefakt wird in der Staging-Umgebung bereitgestellt. |
| 7. Auslösen automatisierter Tests | [!UICONTROL Cloud Manager] führt die Leistungs- und Sicherheitstests für das Artefakt aus. |
| 8. Bereitstellung für Produktionsauslöser | Sobald die automatisierten Tests abgeschlossen sind, startet [!UICONTROL Cloud Manager] die Bereitstellung in der Produktionsumgebung. |
| 9. Abruf der Artefakte durch [!UICONTROL Cloud Manager] für die Bereitstellung | [!UICONTROL Cloud Manager] ruft die gespeicherten Release-Artefakte ab. |
| 10. Bereitstellen von Artefakten für die Produktion | Die Release-Artefakte werden in der Produktionsumgebung bereitgestellt. |

### Einrichten einer CI/CD-Pipeline {#how-to-setup-a-ci-cd-pipeline}

Weitere Informationen zur Pipeline-Konfiguration finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

## Quality Gates {#quality-gates}

Die CI/CD-Pipeline bietet Quality Gates (bzw. Akzeptanzkriterien), die erfüllt werden müssen, bevor der Code aus der Staging-Umgebung in die Bereitstellungsumgebung verschoben werden kann. Die Pipeline muss drei Akzeptanztests bestehen:

* Code-Qualität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests sind drei Stufen von Problemen definiert:

* **Kritisch:** Beim Test festgestellte ausschlaggebende Probleme, die ein sofortiges Fehlschlagen der Pipeline verursachen.
* **Wichtig:** Beim Test festgestellte wichtige Probleme, durch die die Pipeline angehalten wird. Ein Bereitstellungsmanager, Projektmanager oder Business Owner kann die Probleme außer Kraft setzen, sodass die Pipeline fortgesetzt werden kann. Alternativ können sie die Probleme akzeptieren, wodurch die Pipeline bei einem Fehler angehalten wird.
* **Information:** Beim Test festgestellte Probleme informativer Natur, die ausschließlich zu Informationszwecken genannt werden und keine Auswirkungen auf die Pipeline-Ausführung haben.

Im Folgenden finden Sie ein Beispiel für eine Codescan mit identifizierten Problemen.

![Beispiel für Code-Prüfung](/help/assets/quality-gate-failed.png)

### Einrichten von Gates {#how-to-setup-gates}

Weitere Informationen zum Einrichten von Code-, Qualitäts- und Leistungs-Akzeptanztests finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md).
