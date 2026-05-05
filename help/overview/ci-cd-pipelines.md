---
title: CI/CD-Pipelines
description: Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.
exl-id: 7130e5b7-6986-48c8-900c-90f3e4187f91
TQID: https://experienceleague.adobe.com/BwkZH2MIbXrzSxf0yk9yeDZZIpw7-Ldue-OPQPkWrdg
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
  - id: ff09c71c-26a9-449a-85f8-2aeb8ce96100
subfeature_v2:
  - id: c14b2f98-ee16-4c49-b87b-919c91b01d9d
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 50eb58593d7f78492fd384c99c3727c5f731c989
workflow-type: tm+mt
source-wordcount: 639
ht-degree: 81%

---

# CI/CD-Pipelines {#ci-cd-pipeline}

Erfahren Sie mehr über CI/CD-Pipelines und wie sie Bereitstellungen in Staging- und Produktionsumgebungen in Cloud Manager handhaben.

## Überblick {#overview}

[!UICONTROL Cloud Manager] enthält ein Continuous Integration/Continuous Delivery (CI/CD) Framework, mit dem Implementierungs-Teams schnell neuen oder aktualisierten Code testen und bereitstellen können. Implementierungs-Teams können eine automatisierte CI/CD-Pipeline einrichten, konfigurieren und starten. Diese Pipeline folgt den Adobe Best Practices beim Programmieren, um einen umfassenden Codescan durchzuführen und höchste Code-Qualität sicherzustellen.

Die CI/CD-Pipeline automatisiert außerdem die Unit- und Leistungstests, um die Bereitstellungseffizienz zu erhöhen und proaktiv wichtige Probleme zu erkennen, deren Behebung nach der Bereitstellung hohe Kosten verursacht. Implementierungs-Teams können auf einen umfassenden Code-Leistungsbericht zugreifen, um einen Überblick über die potenziellen Auswirkungen auf KPIs und kritische Sicherheitsprüfungen für den Fall zu erhalten, dass der Code in der Produktion bereitgestellt wird.

## Über den Pipeline-Prozess {#pipeline-process}

Das folgende Diagramm zeigt, was passiert, wenn eine Release-Veröffentlichung unter Verwendung einer Pipeline in [!UICONTROL Cloud Manager] ausgelöst wird.

![Der Pipeline-Prozess](/help/assets/screen_shot_2018-05-30at82457pm.png)

| Pipeline-Schritt | Beschreibung |
| --- | --- |
| &#x200B;1. Starten einer Version | Ein Bereitstellungs-Manager löst die Release-Veröffentlichung entweder manuell (per Git-Commit) oder basierend auf einem wiederkehrenden Zeitplan aus. |
| &#x200B;2. Erstellen eines Release-Tags | [!UICONTROL Cloud Manager] erstellt ein Git-Tag, um die Release-Version mit einer automatisch generierten Versionsnummer zu kennzeichnen, z. B. `2018.531.245527.0000001222`. |
| &#x200B;3. Als Version mit automatisch generierter Version erstellt | [!UICONTROL Cloud Manager] erstellt die Anwendung mit der neu zugewiesenen Versionsnummer. |
| &#x200B;4. Bewertung der Code-Qualität | [!UICONTROL Cloud Manager] scannt den Quell-Code und stellt eine Zusammenfassung bereit, bevor der Code in der Staging-Umgebung bereitgestellt werden kann. |
| &#x200B;5. Gespeicherte versionierte Artefakte | Die Release-Artefakte werden zur späteren Verwendung in den Bereitstellungsschritten gespeichert. |
| &#x200B;6. Automatische Bereitstellung von Artefakten für AMS AEM-Staging | Das Release-Artefakt wird in der Staging-Umgebung bereitgestellt. |
| &#x200B;7. Automatisierte Trigger-Tests | [!UICONTROL Cloud Manager] führt die Leistungs- und Sicherheitstests für das Artefakt aus. |
| &#x200B;8. Bereitstellung von Produktions-Trigger | Sobald die automatisierten Tests abgeschlossen sind, startet [!UICONTROL Cloud Manager] die Bereitstellung in der Produktionsumgebung. |
| &#x200B;9. [!UICONTROL Cloud Manager] ruft Artefakte zur Bereitstellung ab | [!UICONTROL Cloud Manager] ruft die gespeicherten Release-Artefakte ab. |
| &#x200B;10. Bereitstellen von Artefakten für die Produktion | Die Release-Artefakte werden in der Produktionsumgebung bereitgestellt. |

### Schnellere Builds mit Smart Build {#use=smart-build}

Cloud Manager verwendet jetzt eine optimierte Build-Strategie namens **Smart Build**, die Caching auf Modulebene verwendet, um den Build-Prozess zu beschleunigen. Bei jedem Build werden nur geänderte Module neu erstellt, während unveränderte Module aus dem Cache wiederverwendet werden.

Smarter Build ist nur für Code-Qualitäts- und Entwicklungs-Full-Stack-Bereitstellungs-Pipelines verfügbar.

Siehe [Hinzufügen einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#add-non-production-pipeline) und [Informationen zur Verwendung von Smart Build in einer produktionsfremden Pipeline](/help/using/non-production-pipelines.md#about-smart-build).


### Einrichten einer CI/CD-Pipeline {#how-to-setup-a-ci-cd-pipeline}

Weitere Informationen zur Pipeline-Konfiguration finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

## Quality Gates {#quality-gates}

Die CI/CD-Pipeline bietet Quality Gates (bzw. Akzeptanzkriterien), die erfüllt werden müssen, bevor der Code aus der Staging-Umgebung in die Bereitstellungsumgebung verschoben werden kann. Die Pipeline muss drei Akzeptanztests bestehen:

* Code-Qualität
* Leistungstests
* Sicherheitstests

Für jeden dieser Akzeptanztests sind drei Stufen von Problemen definiert:

* **Kritisch:** Beim Test festgestellte ausschlaggebende Probleme, die ein sofortiges Fehlschlagen der Pipeline verursachen.
* **Wichtig:** Beim Test festgestellte wichtige Probleme, durch die die Pipeline angehalten wird. Bereitstellungs-Managerinnen bzw. -Manager, Projekt-Managerinnen bzw. -Manager oder Geschäftsinhaberinnen bzw. -inhaber können die Probleme übergehen, sodass die Pipeline fortgesetzt werden kann. Alternativ können sie die Probleme akzeptieren, wodurch die Pipeline mit einem Fehler angehalten wird.
* **Information:** Beim Test festgestellte Probleme informativer Natur, die ausschließlich zu Informationszwecken genannt werden und keine Auswirkungen auf die Pipeline-Ausführung haben.

Dies ist ein Beispiel für einen Codescan mit festgestellten Problemen:

![Beispiel für Code-Prüfung](/help/assets/quality-gate-failed.png)

### Einrichten von Gates {#how-to-setup-gates}

Weitere Informationen zum Einrichten von Code-, Qualitäts- und Leistungs-Akzeptanztests finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md).
