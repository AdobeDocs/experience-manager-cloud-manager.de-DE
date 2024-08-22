---
title: Code-Bereitstellung
description: Erfahren Sie, wie Sie Code bereitstellen und was dabei in Cloud Manager passiert.
exl-id: 3d6610e5-24c2-4431-ad54-903d37f4cdb6
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '1637'
ht-degree: 53%

---


# Codebereitstellung {#code-deployment}

Erfahren Sie, wie Sie Code bereitstellen und was dabei in Cloud Manager passiert.

## Bereitstellen von Code mit Cloud Manager {#deploying-code-with-cloud-manager}

Sobald Sie Ihre Produktions-Pipeline einschließlich des erforderlichen Repositorys und der erforderlichen Umgebungen konfiguriert haben, können Sie Ihren Code bereitstellen.

1. Klicken Sie in Cloud Manager auf **Bereitstellen**, um den Bereitstellungsprozess zu starten.

   ![Schaltfläche „Bereitstellen“](/help/assets/Deploy1.png)

1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt. Klicken Sie auf **Build**, um den Prozess zu starten.

   ![Schaltfläche „Erstellen“](/help/assets/Deploy2.png)

Der Build-Prozess startet den Code-Bereitstellungsprozess einschließlich der folgenden Schritte:

* Staging-Bereitstellung
* Staging-Tests
* Produktionsbereitstellung

Sie können die Schritte aus verschiedenen Bereitstellungsprozessen überprüfen, indem Sie Protokolle anzeigen oder die Ergebnisse für die Testkriterien überprüfen.

## Implementierungsschritte {#deployment-steps}

In jedem Schritt der Implementierung werden verschiedene Aktionen ausgeführt, die in diesem Abschnitt beschrieben werden. Technische Details dazu, wie der Code selbst hinter den Kulissen bereitgestellt wird, finden Sie unter [Details zum Bereitstellungsprozess](#deployment-process) .

### Schritt zur Staging-Bereitstellung {#stage-deployment}

Der Schritt **Staging-Bereitstellung** umfasst die folgenden Aktionen:

* **Validierung**: Dieser Schritt stellt sicher, dass die Pipeline für die Verwendung der derzeit verfügbaren Ressourcen konfiguriert ist. Beispielsweise, dass die konfigurierte Verzweigung vorhanden ist und die Umgebungen verfügbar sind.
* **Build- und Unit-Tests**: Dieser Schritt führt einen containerisierten Build-Prozess aus. Weitere Informationen finden Sie unter [Die Build-Umgebung](/help/getting-started/build-environment.md) .
* **Codescan**: Dieser Schritt bewertet die Qualität des Programm-Codes. Weitere Informationen zum Testprozess finden Sie unter [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) .
* **Staging-Bereitstellung**

![Staging-Bereitstellung](/help/assets/Stage_Deployment1.png)

### Schritt für Staging-Tests {#stage-testing}

Der Schritt **Staging-Tests** umfasst die folgenden Aktionen:

* **Sicherheitstests**: Dieser Schritt bewertet die Auswirkungen des Programm-Codes auf die Sicherheit der AEM-Umgebung. Einzelheiten zum Testverfahren finden Sie im Dokument [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md).
   * **Leistungstests**: Dieser Schritt bewertet die Leistung des Codes. Weitere Informationen zum Testprozess finden Sie unter [Grundlegendes zu Testergebnissen](/help/using/code-quality-testing.md) .

### Schritt zur Produktionsbereitstellung {#production-deployment}

Der Schritt **Produktionsbereitstellung** umfasst die folgenden Aktionen:

* **Genehmigungsantrag**
   * Diese Option ist beim Konfigurieren der Pipeline aktiviert.
   * Mit dieser Option können Sie die Produktionsbereitstellung planen. Oder klicken Sie auf **Jetzt**, um die Produktionsbereitstellung sofort auszuführen.
* **Planen der Bereitstellung für die Produktion**
   * Diese Option ist beim Konfigurieren der Pipeline aktiviert.
   * Das geplante Datum und die Uhrzeit werden in Bezug auf die Zeitzone des Benutzers angegeben.
     ![Bereitstellung planen](/help/assets/Production_Deployment1.png)
* **CSE-Unterstützung** (sofern aktiviert)
* **Bereitstellung für Produktion**

![Produktionsbereitstellung](/help/assets/Prod_Deployment1.png)

Sobald die Bereitstellung abgeschlossen ist, befindet sich der Code in der Zielumgebung und Sie können die Protokolle anzeigen.

![Bereitstellung abgeschlossen](/help/assets/Production_Deployment2.png)

## Zeitüberschreitungen {#timeouts}

Die folgenden Schritte zeigen ein Timeout, wenn der Benutzer auf Feedback gewartet hat:

| Schritt | Zeitüberschreitung |
|--- |--- |
| Testen der Code-Qualität | 7 Tage |
| Sicherheitstests | 7 Tage |
| Leistungstests | 7 Tage |
| Genehmigungsantrag (Staging) | 7 Tage |
| Genehmigungsantrag (Produktion) | 14 Tage |
| Planen der Bereitstellung für die Produktion | 14 Tage |
| Verwaltete Produktionsbereitstellung | 14 Tage |

## Details zum Implementierungsprozess {#deployment-process}

Cloud Manager lädt alle beim Build-Prozess generierten target/*.zip-Dateien in einen Speicherort hoch. Diese Artefakte werden in der Pipeline-Bereitstellungsphase von diesem Speicherort abgerufen.

Wenn Cloud Manager in produktionsfremden Topologien bereitgestellt wird, besteht das Ziel darin, die Bereitstellung so schnell wie möglich abzuschließen. Daher werden die Artefakte wie folgt auf allen Knoten gleichzeitig bereitgestellt:

1. Cloud Manager bestimmt, ob jedes Artefakt ein AEM- oder Dispatcher-Paket ist.
1. Cloud Manager entfernt alle Dispatcher aus dem Lastenausgleich, um die Umgebung während der Bereitstellung zu isolieren.

   * Sofern nicht anders konfiguriert, können Sie Änderungen am Load-Balancer in Entwicklungs- und Staging-Bereitstellungen überspringen. Für die Entwicklungsumgebung trennen und hängen Sie die Schritte sowohl in produktionsfremden Pipelines als auch in der Staging-Umgebung in der Produktions-Pipeline ab.

   ![Lastenausgleich überspringen](/help/assets/load_balancer.png)

   >[!NOTE]
   >
   >Es wird erwartet, dass 1-1-1-Kunden diese Funktion verwenden werden.

1. Jedes AEM-Artefakt wird über Package Manager-APIs in jeder AEM-Instanz bereitgestellt, wobei Paketabhängigkeiten die Bereitstellungsreihenfolge bestimmen.

   * Um mehr darüber zu erfahren, wie Sie Pakete verwenden können, um neue Funktionen zu installieren, Inhalte zwischen Instanzen zu übertragen und Repository-Inhalte zu sichern. Siehe [Package Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).

   >[!NOTE]
   >
   >Alle AEM-Artefakte werden für Autor und Veröffentlichung bereitgestellt. Wenn knotenspezifische Konfigurationen erforderlich sind, sollten Ausführungsmodi genutzt werden. Weitere Informationen dazu, wie Sie mit den Ausführungsmodi Ihre AEM-Instanz für einen bestimmten Zweck anpassen können, finden Sie im Abschnitt &quot;[Ausführungsmodi&quot;des Dokuments &quot;In AEM as a Cloud Service bereitstellen&quot;](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/deploying/overview#runmodes).

1. Das Dispatcher-Artefakt wird wie folgt für jede Dispatcher bereitgestellt:

   1. Aktuelle Konfigurationen werden gesichert und in einen temporären Speicherort kopiert.
   1. Alle Konfigurationen (mit Ausnahme der unveränderlichen Dateien) werden gelöscht. Weitere Informationen finden Sie unter [Dispatcher-Konfigurationen](/help/getting-started/dispatcher-configurations.md) . Dieser Ansatz löscht die Verzeichnisse, um sicherzustellen, dass keine verwaisten Dateien zurückgelassen werden.
   1. Das Artefakt wird in das `httpd`-Verzeichnis extrahiert. Unveränderliche Dateien werden nicht überschrieben. Alle Änderungen, die Sie an unveränderlichen Dateien in Ihrem Git-Repository vornehmen, werden zum Zeitpunkt der Bereitstellung ignoriert. Diese Dateien bilden den Kern des AMS Dispatcher-Frameworks und können nicht geändert werden.
   1. Apache führt einen Konfigurationstest durch. Wenn keine Fehler gefunden werden, wird der Service neu geladen. Falls ein Fehler auftritt, werden die Konfigurationen aus der Sicherung wiederhergestellt, der Service wird neu geladen und der Fehler wird an Cloud Manager gemeldet.
   1. Jeder in der Pipeline-Konfiguration angegebene Pfad wird ungültig gemacht oder aus dem Dispatcher-Cache entfernt.

   >[!NOTE]
   >
   >Cloud Manager erwartet, dass das Dispatcher-Artefakt den vollständigen Dateisatz enthält. Alle Dispatcher-Konfigurationsdateien müssen im Git-Repository vorhanden sein. Fehlende Dateien oder Ordner führen zu Implementierungsfehlern.

1. Nach der erfolgreichen Bereitstellung aller AEM- und Dispatcher-Pakete auf allen Knoten werden die Dispatcher wieder zum Lastenausgleich hinzugefügt und die Bereitstellung ist abgeschlossen.

   >[!NOTE]
   >
   >Sie können Änderungen am Load-Balancer in Entwicklungs- und Staging-Bereitstellungen überspringen. Das heißt, für die Entwicklungsumgebung trennen und anhängen Sie Schritte in beiden produktionsfremden Pipelines und für die Staging-Umgebung in der Produktions-Pipeline.

### Implementierung in die Produktionsphase {#deployment-production-phase}

Der Bereitstellungsprozess für Produktions-Topologien unterscheidet sich geringfügig, um die Auswirkungen auf AEM Site-Besucher zu minimieren.

Produktionsbereitstellungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise:

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. Stellen Sie AEM Pakete parallel in publish1 und das Dispatcher-Paket in dispatcher1 bereit und leeren Sie den Dispatcher-Cache.
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. Stellen Sie AEM Pakete parallel in publish2 und das Dispatcher-Paket in dispatcher2 bereit und leeren Sie den Dispatcher-Cache.
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt.

Dieser Vorgang wird fortgesetzt, bis die Bereitstellung alle Publisher und Dispatcher in der Topologie erreicht hat.

## Ausführungsmodus der Notfallpipeline {#emergency-pipeline}

In kritischen Situationen müssen Adobe Managed Services-Kunden möglicherweise Code-Änderungen sofort in ihrer Staging- und Produktionsumgebung bereitstellen. Durch diese Fähigkeit können sie den gesamten Cloud Manager-Testzyklus umgehen.

Um diese Situationen zu beheben, kann die Cloud Manager-Produktions-Pipeline in einem Notfall-Modus ausgeführt werden. Wenn dieser Modus verwendet wird, werden die Sicherheits- und Leistungstestschritte nicht ausgeführt. Alle anderen Schritte, einschließlich aller konfigurierten Genehmigungsschritte, werden wie im normalen Pipeline-Ausführungsmodus ausgeführt.

>[!NOTE]
>
>Die Funktion des Ausführungsmodus der Notfallpipeline wird für jedes Programm aktiviert. Die Aktivierung erfolgt durch Customer Success Engineers.

### Verwenden des Ausführungsmodus der Notfallpipeline {#using-emergency-pipeline}

Beim Starten einer Produktions-Pipeline können Sie in einem Dialogfeld zwischen dem normalen Modus und dem Notmodus wählen. Diese Option ist verfügbar, wenn die Funktion für den Ausführungsmodus der Notfallpipeline für das Programm aktiviert ist. Diese Auswahl ist verfügbar, sobald die Funktion aktiviert wurde.

![Optionen für die Ausführung von Pipelines](/help/assets/execution-emergency1.png)

Wenn Sie die Seite mit den Pipeline-Ausführungsdetails für eine im Notfallmodus ausgeführte Ausführung anzeigen, wird in den Breadcrumbs am oberen Bildschirmrand ein Hinweis darauf angezeigt, dass die Pipeline im Notfallmodus ausgeführt wird.

![Breadcrumbs für den Notfallmodus](/help/assets/execution-emergency2.png)

Die Ausführung einer Pipeline im Notfallmodus kann auch über die Cloud Manager-API oder die CLI erfolgen. Um eine Ausführung im Notfallmodus zu starten, senden Sie mit dem Abfrageparameter `?pipelineExecutionMode=EMERGENCY` eine `PUT`-Anfrage an den Ausführungsendpunkt der Pipeline. Alternativ haben Sie bei Verwendung der CLI folgende Möglichkeit:

```
$ aio cloudmanager:pipeline:create-execution PIPELINE_ID --emergency
```

## Erneutes Ausführen einer Produktionsbereitstellung {#reexecute-deployment}

In seltenen Fällen kann es vorkommen, dass Schritte der Produktionsbereitstellung aus vorübergehenden Gründen fehlschlagen. In diesen Fällen können Sie den Produktionsbereitstellungsschritt erneut ausführen, solange er abgeschlossen ist, unabhängig davon, ob er erfolgreich, abgebrochen oder nicht erfolgreich war. Die Neuausführung wird unterstützt, indem dieselbe Pipeline verwendet wird, die aus den folgenden drei Schritten besteht:

1. **Der Validierungsschritt** - Die gleiche Validierung, die während einer normalen Pipeline-Ausführung erfolgt.
1. **Der Build-Schritt** – Im Rahmen einer erneuten Ausführung kopiert der Build-Schritt Artefakte und führt keinen wirklich neuen Build-Prozess aus.
1. **Der Schritt zur Produktionsbereitstellung** - Verwendet dieselbe Konfiguration und dieselben Optionen wie der Schritt zur Produktionsbereitstellung in einer normalen Pipeline-Ausführung.

In solchen Fällen, in denen eine erneute Ausführung möglich ist, bietet die Statusseite der Produktions-Pipeline neben der üblichen Option **Build-Protokoll herunterladen** auch die Option **Erneut ausführen**.

![Die Option „Erneut ausführen“ im Pipeline-Übersichtsfenster](/help/assets/re-execute.png)

>[!NOTE]
>
>Bei einer erneuten Ausführung wird der Build-Schritt in der Benutzeroberfläche mit dem Hinweis versehen, dass er Artefakte kopiert und nicht neu erstellt.

### Einschränkungen {#limitations}

* Das erneute Ausführen des Produktionsbereitstellungsschritts ist nur für die letzte Ausführung verfügbar.
* Die Neuausführung ist nicht für Rollback-Ausführungen oder &quot;Push-Update&quot;-Ausführungen verfügbar.
* Wenn die letzte Ausführung vor dem Produktionsbereitstellungsschritt fehlschlug, ist eine erneute Ausführung nicht möglich.


### API erneut ausführen {#reexecute-api}

Zusätzlich zur Verfügbarkeit in der Benutzeroberfläche können Sie [die Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) verwenden, um erneute Ausführungen auszulösen und Ausführungen zu identifizieren, die als erneute Ausführungen ausgelöst wurden.

#### Trigger einer erneuten Ausführung {#triggering}

Um eine erneute Ausführung auszulösen, muss eine `PUT`-Anfrage an die HAL-Verknüpfung `http://ns.adobe.com/adobecloud/rel/pipeline/reExecute` im Status des Schritts der Produktionsbereitstellung erfolgen.

* Wenn diese Verknüpfung vorhanden ist, kann die Ausführung von diesem Schritt aus neu gestartet werden.
* Wenn dies nicht der Fall ist, kann die Ausführung von diesem Schritt an nicht erneut gestartet werden.

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

Wenn eine `PUT` -Anfrage an diesen Endpunkt gesendet wird, wird eine `201` -Antwort angezeigt, wenn sie erfolgreich ist. Der Antworttext stellt die Darstellung der neuen Ausführung dar. Diese Funktion ähnelt dem Starten einer regulären Ausführung über die API.

#### Ermitteln einer erneut ausgeführten Ausführung {#identifying}

Das System identifiziert erneut ausgeführte Ausführungen anhand des Werts `RE_EXECUTE` im Feld Trigger .