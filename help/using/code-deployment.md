---
title: Code-Bereitstellung
description: Erfahren Sie, wie Sie Code bereitstellen und was dabei in Cloud Manager passiert.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 200366e5db92b7ffc79b7a47ce8e7825b29b7969
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 96%

---


# Code-Bereitstellung {#code-deployment}

Erfahren Sie, wie Sie Code bereitstellen und was dabei in Cloud Manager passiert.

## Bereitstellen von Code mit Cloud Manager {#deploying-code-with-cloud-manager}

Sobald die Produktions-Pipeline einschließlich des erforderlichen Repositorys und der erforderlichen Umgebungen konfiguriert ist, kann der Code bereitgestellt werden.

1. Klicken Sie in Cloud Manager auf **Bereitstellen**, um den Bereitstellungsprozess zu starten.

   ![Schaltfläche „Bereitstellen“](/help/assets/Deploy1.png)

1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt. Klicken Sie auf **Build**, um den Prozess zu starten.

   ![Schaltfläche „Erstellen“](/help/assets/Deploy2.png)

Der Build-Prozess startet den Code-Bereitstellungsprozess einschließlich der folgenden Schritte:

* Staging-Bereitstellung
* Staging-Tests
* Produktionsbereitstellung

Sie können die Schritte verschiedener Bereitstellungsprozesse überprüfen, indem Sie die Protokolle lesen oder die Ergebnisse anhand der Testkriterien durchgehen.

## Bereitstellungsschritte {#deployment-steps}

In jedem Schritt der Bereitstellung werden verschiedene Aktionen ausgeführt, die in diesem Abschnitt beschrieben werden. Im Abschnitt [Details zum Bereitstellungsprozess](#deployment-process) finden Sie technische Details dazu, wie der Code selbst hinter den Kulissen bereitgestellt wird.

### Staging-Bereitstellung {#stage-deployment}

Der Schritt **Staging-Bereitstellung** umfasst die folgenden Aktionen:

* **Validierung**: Dieser Schritt stellt sicher, dass die Pipeline so konfiguriert ist, dass die derzeit verfügbaren Ressourcen verwendet werden. So wird z. B. überprüft, ob die konfigurierte Verzweigung vorhanden ist und die Umgebungen verfügbar sind.
* **Build- und Unit-Tests**: Dieser Schritt führt einen containerisierten Build-Prozess aus. Einzelheiten finden Sie im Dokument [Die Build-Umgebung](/help/getting-started/build-environment.md).
* **Codescan**: Dieser Schritt bewertet die Qualität des Programm-Codes. Einzelheiten zum Testverfahren finden Sie im Dokument [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md).
* **Staging-Bereitstellung**

![Staging-Bereitstellung](/help/assets/Stage_Deployment1.png)

### Staging-Tests {#stage-testing}

Der Schritt **Staging-Tests** umfasst die folgenden Aktionen:

* **Sicherheitstests**: Dieser Schritt bewertet die Auswirkungen des Programm-Codes auf die Sicherheit der AEM-Umgebung. Einzelheiten zum Testverfahren finden Sie im Dokument [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md).
   * **Leistungstests**: Dieser Schritt bewertet die Leistung des Codes. Einzelheiten zum Testverfahren finden Sie in unter [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md).

### Schritt zur Produktionsbereitstellung {#production-deployment}

Der Schritt **Produktionsbereitstellung** umfasst die folgenden Aktionen:

* **Genehmigungsantrag**
   * Diese Option ist beim Konfigurieren der Pipeline aktiviert.
   * Mit dieser Option können Sie die Produktionsbereitstellung planen. Oder klicken Sie auf **Jetzt**, um die Produktionsbereitstellung sofort auszuführen.
* **Planen der Bereitstellung für die Produktion**
   * Diese Option ist beim Konfigurieren der Pipeline aktiviert.
   * Datum und Uhrzeit für den Zeitplan beziehen sich auf die Zeitzone des Benutzers.
     ![Bereitstellung planen](/help/assets/Production_Deployment1.png)
* **CSE-Unterstützung** (sofern aktiviert)
* **Bereitstellung für Produktion**

![Produktionsbereitstellung](/help/assets/Prod_Deployment1.png)

Sobald die Bereitstellung abgeschlossen ist, befindet sich der Code in der Zielumgebung und Sie können die Protokolle anzeigen.

![Bereitstellung abgeschlossen](/help/assets/Production_Deployment2.png)

## Zeitüberschreitungen {#timeouts}

Die folgenden Schritte führen zu einer Zeitüberschreitung, wenn auf Benutzer-Feedback gewartet wird:

| Schritt | Zeitüberschreitung |
|--- |--- |
| Testen der Code-Qualität | 7 Tage |
| Sicherheitstests | 7 Tage |
| Leistungstests | 7 Tage |
| Genehmigungsantrag (Staging) | 7 Tage |
| Genehmigungsantrag (Produktion) | 14 Tage |
| Planen der Bereitstellung für die Produktion | 14 Tage |
| Verwaltete Produktionsbereitstellung | 14 Tage |

## Details zum Bereitstellungsprozess {#deployment-process}

Cloud Manager lädt alle beim Build-Prozess generierten target/*.zip-Dateien in einen Speicherort hoch. Diese Artefakte werden in der Pipeline-Bereitstellungsphase von diesem Speicherort abgerufen.

Wenn Cloud Manager in produktionsfremden Topologien bereitgestellt wird, besteht das Ziel darin, die Bereitstellung so schnell wie möglich abzuschließen. Daher werden die Artefakte wie folgt auf allen Knoten gleichzeitig bereitgestellt:

1. Cloud Manager bestimmt für jedes Artefakt, ob es sich um ein AEM- oder Dispatcher-Paket handelt.
1. Cloud Manager entfernt alle Dispatcher aus dem Lastenausgleich, um die Umgebung während der Bereitstellung zu isolieren.

   * Sofern nicht anders konfiguriert, können Sie Änderungen am Lastenausgleich in Entwicklungs- und Staging-Bereitstellungen überspringen, d. h. für die Entwicklungsumgebung, das Trennen und Anfügen von Schritten in beiden produktionsfremden Pipelines sowie für die Staging-Umgebung in der Produktions-Pipeline.

   ![Lastenausgleich überspringen](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Diese Funktion wird voraussichtlich hauptsächlich von 1-1-1-Kunden verwendet.

1. Jedes AEM-Artefakt wird über Package Manager-APIs in jeder AEM-Instanz bereitgestellt, wobei Paketabhängigkeiten die Bereitstellungsreihenfolge bestimmen.

   * Weitere Informationen dazu, wie Sie Pakete verwenden können, um neue Funktionen zu installieren, Inhalte zwischen Instanzen zu übertragen und Repository-Inhalte zu sichern, finden Sie unter [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html?lang=de).

   >[!NOTE]
   >
   >Alle AEM-Artefakte werden für Autor und Veröffentlichung bereitgestellt. Wenn knotenspezifische Konfigurationen erforderlich sind, sollten Ausführungsmodi genutzt werden. Weitere Informationen dazu, wie Sie mit den Ausführungsmodi Ihre AEM-Instanz für einen bestimmten Zweck anpassen können, finden Sie im Abschnitt &quot;[Ausführungsmodi&quot;des Dokuments &quot;In AEM as a Cloud Service bereitstellen&quot;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=de#runmodes).

1. Das Dispatcher-Artefakt wird wie folgt für jeden Dispatcher bereitgestellt:

   1. Aktuelle Konfigurationen werden gesichert und in einen temporären Speicherort kopiert.
   1. Alle Konfigurationen (mit Ausnahme der unveränderlichen Dateien) werden gelöscht. Weitere Informationen finden Sie unter [Dispatcher-Konfigurationen](/help/getting-started/dispatcher-configurations.md) . Mit diesem Schritt werden die Verzeichnisse gelöscht, damit keine verwaisten Dateien übrig bleiben.
   1. Das Artefakt wird in das `httpd`-Verzeichnis extrahiert. Unveränderliche Dateien werden nicht überschrieben. Alle Änderungen an unveränderlichen Dateien im Git-Repository werden bei der Bereitstellung ignoriert. Diese Dateien bilden den Kern des AMS Dispatcher-Frameworks und können nicht geändert werden.
   1. Apache führt einen Konfigurationstest durch. Wenn keine Fehler gefunden werden, wird der Service neu geladen. Falls ein Fehler auftritt, werden die Konfigurationen aus der Sicherung wiederhergestellt, der Service wird neu geladen und der Fehler wird an Cloud Manager gemeldet.
   1. Jeder in der Pipeline-Konfiguration angegebene Pfad wird ungültig oder aus dem Dispatcher-Cache entfernt.

   >[!NOTE]
   >
   >Cloud Manager geht davon aus, dass das Dispatcher-Artefakt alle Dateien enthält. Alle Dispatcher-Konfigurationsdateien müssen im Git-Repository vorhanden sein. Fehlende Dateien oder Ordner führen zu Bereitstellungsfehlern.

1. Nach der erfolgreichen Bereitstellung aller AEM- und Dispatcher-Pakete auf allen Knoten werden die Dispatcher wieder zum Lastenausgleich hinzugefügt und die Bereitstellung wird abgeschlossen.

   >[!NOTE]
   >
   >Sie können Änderungen am Lastenausgleich in Entwicklungs- und Staging-Bereitstellungen überspringen, d. h. für die Entwicklungsumgebung, das Trennen und Anfügen in beiden produktionsfremden Pipelines sowie für die Staging-Umgebung in der Produktions-Pipeline.

### Bereitstellung in der Produktionsphase {#deployment-production-phase}

Der Prozess zur Bereitstellung auf Produktionstopologien unterscheidet sich geringfügig, um die Auswirkungen auf die Besucher von AEM-Websites zu minimieren.

Produktionsbereitstellungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise:

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. AEM-Pakete werden in publish1 und das Dispatcher-Paket parallel in dispatcher1 bereitgestellt, der Dispatcher-Cache wird geleert
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. AEM-Pakete werden in publish2 und das Dispatcher-Paket parallel in dispatcher2 bereitgestellt, der Dispatcher-Cache wird geleert
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt.

Dieser Vorgang wird fortgesetzt, bis die Bereitstellung alle Publisher und Dispatcher in der Topologie erreicht hat.

## Notfall-Pipeline-Ausführungsmodus {#emergency-pipeline}

In kritischen Situationen müssen Adobe Managed Services-Kunden möglicherweise Code-Änderungen in ihrer Staging- und Produktionsumgebung bereitstellen, ohne auf die Ausführung eines vollständigen Cloud Manager-Testzyklus zu warten.

Um diese Situationen zu beheben, kann die Cloud Manager-Produktions-Pipeline in einem Notfall-Modus ausgeführt werden. Wenn dieser Modus verwendet wird, werden die Sicherheits- und Leistungstestschritte nicht ausgeführt. Alle anderen Schritte, einschließlich aller konfigurierten Genehmigungsschritte, werden wie im normalen Pipeline-Ausführungsmodus ausgeführt.

>[!NOTE]
>
>Die Funktion „Notfall-Pipeline-Ausführungsmodus“ wird vom Customer Success Engineer auf der Programmebene aktiviert.

### Verwenden des Notfall-Pipeline-Ausführungsmodus {#using-emergency-pipeline}

Wenn beim Starten der Ausführung einer Produktions-Pipeline die Funktion „Notfall-Pipeline-Ausführungsmodus“ für das Programm aktiviert wurde, können Sie über ein Dialogfeld die Ausführung im normalen Modus oder im Notfallmodus starten.

![Optionen für die Ausführung von Pipelines](/help/assets/execution-emergency1.png)

Wenn Sie die Seite mit den Pipeline-Ausführungsdetails für eine im Notfallmodus ausgeführte Ausführung anzeigen, wird in den Breadcrumbs am oberen Bildschirmrand ein Hinweis darauf angezeigt, dass die Pipeline im Notfallmodus ausgeführt wird.

![Breadcrumbs für den Notfallmodus](/help/assets/execution-emergency2.png)

Die Ausführung einer Pipeline im Notfallmodus kann auch über die Cloud Manager-API oder die CLI erfolgen. Um eine Ausführung im Notfallmodus zu starten, senden Sie mit dem Abfrageparameter `?pipelineExecutionMode=EMERGENCY` eine `PUT`-Anfrage an den Ausführungsendpunkt der Pipeline. Alternativ haben Sie bei Verwendung der CLI folgende Möglichkeit:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Erneutes Ausführen einer Produktionsbereitstellung {#reexecute-deployment}

In seltenen Fällen kann es vorkommen, dass Schritte der Produktionsbereitstellung aus vorübergehenden Gründen fehlschlagen. In solchen Fällen wird die erneute Ausführung des Schritts der Produktionsbereitstellung unterstützt, solange der Schritt der Produktionsbereitstellung abgeschlossen ist, unabhängig von der Art des Abschlusses (wie zum Beispiel erfolgreich, abgebrochen oder fehlgeschlagen). Bei der erneuten Ausführung wird eine neue Ausführung mit derselben Pipeline erstellt, die aus drei Schritten besteht.

1. **Der Validierungsschritt** – Dies ist im Wesentlichen dieselbe Validierung wie bei einer normalen Pipeline-Ausführung.
1. **Der Build-Schritt** – Im Rahmen einer erneuten Ausführung kopiert der Build-Schritt Artefakte und führt keinen wirklich neuen Build-Prozess aus.
1. **Der Produktionsbereitstellungsschritt** – Dieser Schritt verwendet dieselbe Konfiguration und dieselben Optionen wie der Produktionsbereitstellungsschritt bei einer normalen Pipeline-Ausführung.

In solchen Fällen, in denen eine erneute Ausführung möglich ist, bietet die Statusseite der Produktions-Pipeline neben der üblichen Option **Build-Protokoll herunterladen** auch die Option **Erneut ausführen**.

![Die Option „Erneut ausführen“ im Pipeline-Übersichtsfenster](/help/assets/re-execute.png)

>[!NOTE]
>
>Bei einer erneuten Ausführung wird der Build-Schritt in der Benutzeroberfläche mit dem Hinweis versehen, dass er Artefakte kopiert und nicht neu erstellt.

### Einschränkungen {#limitations}

* Das erneute Ausführen des Produktionsbereitstellungsschritts ist nur für die letzte Ausführung verfügbar.
* Die erneute Ausführung ist nicht für Rollback-Ausführungen oder Push-Update-Ausführungen verfügbar.
* Wenn die letzte Ausführung vor dem Produktionsbereitstellungsschritt fehlschlug, ist eine erneute Ausführung nicht möglich.


### Erneutes Ausführen der API {#reexecute-api}

Zusätzlich zur Verfügbarkeit in der Benutzeroberfläche können Sie [die Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) verwenden, um erneute Ausführungen auszulösen und Ausführungen zu identifizieren, die als erneute Ausführungen ausgelöst wurden.

#### Auslösen einer erneuten Ausführung {#triggering}

Um eine erneute Ausführung auszulösen, muss eine `PUT`-Anfrage an die HAL-Verknüpfung `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` im Status des Schritts der Produktionsbereitstellung erfolgen.

* Wenn diese Verknüpfung vorhanden ist, kann die Ausführung von diesem Schritt aus neu gestartet werden.
* Fehlt sie, kann die Ausführung ab diesem Schritt nicht wieder aufgenommen werden.

Diese Verknüpfung ist immer nur für den Schritt der Produktionsbereitstellung verfügbar.

```javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```

Die Syntax für den Wert `href` der HAL-Verknüpfung ist nur ein Beispiel, und der tatsächliche Wert sollte immer aus der HAL-Verknüpfung ausgelesen und nicht generiert werden.

Das Senden einer `PUT`-Anfrage an diesen Endpunkt führt zu einer `201`-Antwort bei Erfolg, wobei der Antworttext die Darstellung der neuen Ausführung ist. Dies ähnelt dem Starten einer regulären Ausführung über die API.

#### Identifizieren einer Ausführung mit erneuter Ausführung {#identifying}

Erneute Ausführungen können durch den Wert `RE_EXECUTE` im Feld `trigger` identifiziert werden.
