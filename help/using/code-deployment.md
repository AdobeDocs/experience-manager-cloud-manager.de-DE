---
title: Code-Bereitstellung
description: Erfahren Sie, wie Sie Ihren Code bereitstellen und was in Cloud Manager passiert, wenn Sie dies tun.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 6572c16aea2c5d2d1032ca5b0f5d75ade65c3a19
workflow-type: tm+mt
source-wordcount: '1609'
ht-degree: 40%

---


# Code-Bereitstellung {#code-deployment}

Erfahren Sie, wie Sie Ihren Code bereitstellen und was in Cloud Manager passiert, wenn Sie dies tun.

## Bereitstellen von Code mit Cloud Manager {#deploying-code-with-cloud-manager}

Sobald Sie Ihre Produktions-Pipeline einschließlich des erforderlichen Repositorys und der erforderlichen Umgebungen konfiguriert haben, können Sie Ihren Code bereitstellen.

1. Klicken Sie in Cloud Manager auf **Bereitstellen**, um den Implementierungsprozess zu starten.

   ![Schaltfläche &quot;Bereitstellen&quot;](/help/assets/Deploy1.png)

1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt. Klicken Sie auf **Build**, um den Prozess zu starten.

   ![Schaltfläche &quot;Erstellen&quot;](/help/assets/Deploy2.png)

Der Build-Prozess startet den Code-Bereitstellungsprozess einschließlich der folgenden Schritte:

* Staging-Bereitstellung
* Stage-Testing
* Produktionsbereitstellung

Sie können die Schritte aus verschiedenen Bereitstellungsprozessen überprüfen, indem Sie Protokolle anzeigen oder die Ergebnisse auf die Testkriterien überprüfen.

## Implementierungsschritte {#deployment-steps}

In jedem Schritt der Implementierung werden verschiedene Aktionen ausgeführt, die in diesem Abschnitt beschrieben werden. Siehe Abschnitt . [Details zum Implementierungsprozess](#deployment-process) für technische Details, wie der Code selbst hinter den Kulissen bereitgestellt wird.

### Schritt zur Staging-Bereitstellung {#stage-deployment}

Die **Staging-Bereitstellung** Dieser Schritt umfasst die folgenden Aktionen:

* **Validierung**: Dieser Schritt stellt sicher, dass die Pipeline für die Verwendung der derzeit verfügbaren Ressourcen konfiguriert ist, z. B. dass die konfigurierte Verzweigung vorhanden ist und die Umgebungen verfügbar sind.
* **Build- und Unit-Tests**: Dieser Schritt führt einen containerisierten Build-Prozess aus. Siehe Dokument . [Die Build-Umgebung](/help/getting-started/build-environment.md) für Details.
* **Codescans**: Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes. Siehe Dokument . [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) für Details zum Testprozess.
* **Bereitstellung für Staging**

![Staging-Bereitstellung](/help/assets/Stage_Deployment1.png)

### Schritt &quot;Staging-Tests&quot; {#stage-testing}

Die **Staging-Tests** Dieser Schritt umfasst die folgenden Aktionen:

* **Sicherheitstests**: Dieser Schritt bewertet die Auswirkungen Ihres Codes auf die Sicherheit der AEM. Siehe Dokument . [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) für Details zum Testprozess.
   * **Leistungstests**: Dieser Schritt bewertet die Leistung Ihres Codes. Siehe [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) für Details zum Testprozess.

   ![Stage-Testing](/help/assets/Stage_Testing1.png)

### Schritt zur Produktionsbereitstellung {#production-deployment}

Die **Produktionsbereitstellung** -Schritt umfasst die folgenden Aktionen:

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

Sobald Ihre Implementierung abgeschlossen ist, befindet sich Ihr Code in der Zielumgebung und Sie können die Protokolle anzeigen.

![Bereitstellung abgeschlossen](/help/assets/Production_Deployment2.png)

## Zeitüberschreitungen {#timeouts}

Die folgenden Schritte führen zu einer Zeitüberschreitung, wenn auf Benutzer-Feedback gewartet wird:

| Schritt | Zeitüberschreitung |
|--- |--- |
| Testen der Code-Qualität | 14 Tage |
| Sicherheitstests | 14 Tage |
| Leistungstests | 14 Tage |
| Genehmigungsantrag | 14 Tage |
| Planen der Bereitstellung für die Produktion | 14 Tage |
| CSE-Unterstützung | 14 Tage |

## Details zum Implementierungsprozess {#deployment-process}

Cloud Manager lädt alle beim Build-Prozess generierten target/*.zip-Dateien in einen Speicherort hoch. Diese Artefakte werden in der Pipeline-Bereitstellungsphase von diesem Speicherort abgerufen.

Wenn Cloud Manager in produktionsfremden Topologien bereitgestellt wird, besteht das Ziel darin, die Implementierung so schnell wie möglich abzuschließen. Daher werden die Artefakte wie folgt auf allen Knoten gleichzeitig bereitgestellt:

1. Cloud Manager bestimmt für jedes Artefakt, ob es sich um ein AEM- oder Dispatcher-Paket handelt.
1. Cloud Manager entfernt alle Dispatcher aus dem Lastenausgleich, um die Umgebung während der Bereitstellung zu isolieren.

   * Sofern nicht anders konfiguriert, können Sie Änderungen am Load-Balancer in Entwicklungs- und Staging-Bereitstellungen überspringen, d. h. für die Entwicklungsumgebung, das Trennen und Anfügen von Schritten in beiden Nicht-Produktions-Pipelines sowie für die Staging-Umgebung in der Produktions-Pipeline.

   ![Load Balancer überspringen](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Diese Funktion wird voraussichtlich hauptsächlich von 1-1-1-Kunden verwendet.

1. Jedes AEM-Artefakt wird über Package Manager-APIs in jeder AEM-Instanz bereitgestellt, wobei Paketabhängigkeiten die Implementierungsreihenfolge bestimmen.

   * Weitere Informationen dazu, wie Sie Pakete verwenden können, um neue Funktionen zu installieren, Inhalte zwischen Instanzen zu übertragen und Repository-Inhalte zu sichern, finden Sie im Dokument . [Package Manager.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager.html)
   >[!NOTE]
   >
   >Alle AEM-Artefakte werden für Autor und Publisher bereitgestellt. Wenn knotenspezifische Konfigurationen erforderlich sind, sollten Ausführungsmodi genutzt werden. Weitere Informationen dazu, wie Sie mit Ausführungsmodi Ihre AEM-Instanz für einen bestimmten Zweck anpassen können, finden Sie im Abschnitt [Abschnitt &quot;Ausführungsmodi&quot;des Dokuments, das auf AEM as a Cloud Service bereitgestellt wird.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/overview.html?lang=de#runmodes)

1. Das Dispatcher-Artefakt wird wie folgt für jeden Dispatcher bereitgestellt:

   1. Aktuelle Konfigurationen werden gesichert und an einen temporären Speicherort kopiert.
   1. Alle Konfigurationen werden mit Ausnahme der unveränderlichen Dateien gelöscht. Siehe Dokument . [Dispatcher-Konfigurationen](/help/getting-started/dispatcher-configurations.md) für weitere Details. Mit diesem Schritt werden die Verzeichnisse gelöscht, damit keine verwaisten Dateien übrig bleiben.
   1. Das Artefakt wird in das `httpd`-Verzeichnis extrahiert. Unveränderliche Dateien werden nicht überschrieben. Alle Änderungen an unveränderlichen Dateien in Ihrem Git-Repository werden bei der Implementierung ignoriert. Diese Dateien bilden den Kern des AMS-Dispatcher-Frameworks und können nicht geändert werden.
   1. Apache führt einen Konfigurationstest durch. Wenn keine Fehler gefunden werden, wird der Service neu geladen. Wenn ein Fehler auftritt, werden die Konfigurationen aus der Sicherung wiederhergestellt, der Dienst wird neu geladen und der Fehler wird zurück an Cloud Manager gemeldet.
   1. Jeder in der Pipelinekonfiguration angegebene Pfad wird ungültig oder aus dem Dispatcher-Cache entfernt.

   >[!NOTE]
   >
   >Cloud Manager geht davon aus, dass das Dispatcher-Artefakt alle Dateien enthält. Alle Dispatcher-Konfigurationsdateien müssen im Git-Repository vorhanden sein. Fehlende Dateien oder Ordner führen zu Implementierungsfehlern.

1. Nach der erfolgreichen Implementierung aller AEM- und Dispatcher-Pakete auf allen Knoten werden die Dispatcher wieder zum Lastenausgleich hinzugefügt und die Implementierung wird abgeschlossen.

   >[!NOTE]
   >
   >Sie können Änderungen am Load-Balancer in Entwicklungs- und Staging-Bereitstellungen überspringen, d. h. für die Entwicklungsumgebung, das Trennen und Anfügen in beiden Nicht-Produktions-Pipelines sowie für die Staging-Umgebung in der Produktions-Pipeline.

### Implementierung in der Produktionsphase {#deployment-production-phase}

Der Bereitstellungsprozess für Produktions-Topologien unterscheidet sich geringfügig, um die Auswirkungen auf AEM Site-Besucher zu minimieren.

Produktionsimplementierungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise:

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. AEM-Pakete werden in publish1 und das Dispatcher-Paket parallel in dispatcher1 bereitgestellt, der Dispatcher-Cache wird geleert
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. AEM-Pakete werden in publish2 und das Dispatcher-Paket parallel in dispatcher2 bereitgestellt, der Dispatcher-Cache wird geleert
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt


Dieser Vorgang wird fortgesetzt, bis die Implementierung alle Publisher und Dispatcher in der Topologie erreicht hat.

## Notfall-Pipeline-Ausführungsmodus {#emergency-pipeline}

In kritischen Situationen müssen Adobe Managed Services-Kunden möglicherweise Code-Änderungen in ihrer Staging- und Produktionsumgebung bereitstellen, ohne auf die Ausführung eines vollständigen Cloud Manager-Testzyklus zu warten.

Um diese Situationen zu beheben, kann die Cloud Manager-Produktions-Pipeline in einem Notfall-Modus ausgeführt werden. Wenn dieser Modus verwendet wird, werden die Sicherheits- und Leistungstestschritte nicht ausgeführt. Alle anderen Schritte, einschließlich aller konfigurierten Validierungsschritte, werden wie im normalen Pipeline-Ausführungsmodus ausgeführt.

>[!NOTE]
>
>Die Notfallfunktion des Pipeline-Ausführungsmodus wird von den Customer Success Engineers für jedes Programm aktiviert.

### Verwenden des Notfall-Pipeline-Ausführungsmodus {#using-emergency-pipeline}

Wenn beim Starten der Ausführung einer Produktions-Pipeline die Funktion zur Ausführung der Notfallpipeline für das Programm aktiviert wurde, können Sie die Ausführung im normalen oder im Notfall über ein Dialogfeld starten.

![Pipeline-Optionen ausführen](/help/assets/execution-emergency1.png)

Wenn Sie sich die Seite mit Details zur Pipeline-Ausführung für einen Ausführungsablauf im Notfallmodus ansehen, zeigen die Breadcrumbs oben im Bildschirm einen Hinweis darauf, dass die Pipeline im Notfallmodus ausgeführt wird.

![Breadcrumbs im Notfallmodus](/help/assets/execution-emergency2.png)

Die Ausführung einer Pipeline im Notfallmodus kann auch über die Cloud Manager-API oder die CLI erfolgen. Um eine Ausführung im Notfallmodus zu starten, senden Sie eine `PUT` Anfrage an den Ausführungs-Endpunkt der Pipeline mit dem Abfrageparameter `?pipelineExecutionMode=EMERGENCY` oder bei Verwendung der CLI:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Produktionsbereitstellung erneut ausführen {#re-execute-deployment}

Die Neuausführung des Produktionsbereitstellungsschritts ist für Ausführungen verfügbar, bei denen der Schritt zur Produktionsbereitstellung abgeschlossen ist. Die Art der Fertigstellung ist nicht wichtig. Die Bereitstellung konnte erfolgreich sein (nur für AMS-Programme), abgebrochen oder nicht erfolgreich sein. Der primäre Anwendungsfall besteht darin, dass der Produktionsbereitstellungsschritt aus Verlaufsgründen fehlgeschlagen ist. Bei der erneuten Ausführung wird eine neue Ausführung mit derselben Pipeline erstellt. Diese neue Ausführung besteht aus drei Schritten:

1. **Der Validierungsschritt** - Dies ist im Wesentlichen die gleiche Validierung, die während einer normalen Pipeline-Ausführung erfolgt.
1. **Der Build-Schritt** - Im Kontext einer erneuten Ausführung kopiert der Build-Schritt Artefakte und führt keinen neuen Build-Prozess aus.
1. **Schritt zur Produktionsbereitstellung** - Hierbei werden dieselben Konfigurationen und Optionen wie beim Produktionsbereitstellungsschritt in einer normalen Pipeline-Ausführung verwendet.

Der Build-Schritt wird in der Benutzeroberfläche möglicherweise anders beschriftet, um anzuzeigen, dass er Artefakte kopiert und nicht neu erstellt.

![Erneutes Ausführen](/help/assets/Re-deploy.png)

### Beschränkungen {#limitations}

* Die erneute Ausführung des Produktionsbereitstellungsschritts ist nur für die letzte Ausführung verfügbar.
* Die Neuausführung ist nicht für Rollback-Ausführungen oder Push-Update-Ausführungen verfügbar.
* Wenn die letzte Ausführung vor dem Produktionsbereitstellungsschritt fehlschlug, ist eine erneute Ausführung nicht möglich.

### Ermitteln einer erneuten Ausführung {#identifying}

Um festzustellen, ob es sich bei einer Ausführung um eine erneute Ausführung handelt, wird die `trigger` -Feld geprüft werden. Ihr Wert lautet `RE_EXECUTE`.

### Auslösen einer erneuten Ausführung {#triggering}

Um eine erneute Ausführung Trigger, wird eine `PUT` -Anfrage an den HAL-Link `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` im Status der Produktionsbereitstellungsschritte. Wenn dieser Link vorhanden ist, kann die Ausführung von diesem Schritt an neu gestartet werden. Wenn dies nicht der Fall ist, kann die Ausführung von diesem Schritt an nicht erneut gestartet werden. Dieser Link wird nur im Produktionsbereitstellungsschritt vorhanden sein.

```Javascript
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

Die Syntax des HAL-Links `href` -Wert nicht als Bezugspunkt verwendet werden soll. Der tatsächliche Wert sollte immer aus dem HAL-Link gelesen und nicht generiert werden.

Das Senden einer `PUT`-Anfrage an diesen Endpunkt führt zu einer `201`-Antwort bei Erfolg, wobei der Antworttext die Darstellung der neuen Ausführung ist. Dies ähnelt dem Starten einer regulären Ausführung über die API.
