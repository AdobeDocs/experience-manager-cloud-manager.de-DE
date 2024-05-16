---
title: Nur-Staging- und Nur-Produktion-Pipelines
description: Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe dedizierter Pipelines aufteilen können.
source-git-commit: c09fbf30270523018a36b128d43cbf10e65daf54
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 2%

---


# Nur-Staging- und reine Produktions-Pipelines {#stage-prod-only}

Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe dedizierter Pipelines aufteilen können.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/release-notes/current.md#early-adoption) verfügbar.

## Überblick {#overview}

Staging- und Produktionsumgebungen sind eng miteinander verbunden. Standardmäßig sind damit verknüpfte Bereitstellungen mit einer einzelnen Pipeline verknüpft. Hierbei handelt es sich um eine Bereitstellungs-Pipeline, die sowohl für die Staging- als auch für die Produktionsumgebung in diesem Programm bereitgestellt wird. Diese Kopplung ist zwar in der Regel geeignet, es gibt jedoch einige Anwendungsfälle, in denen Nachteile vorliegen:

* Wenn Sie eine Bereitstellung nur für Staging durchführen möchten, können Sie dies nur tun, indem Sie die **Weiterleiten an Produktion** Schritt in der Pipeline. Die Ausführung wird jedoch als abgebrochen markiert.
* Wenn Sie den neuesten Code in einer Staging-Umgebung für die Produktion bereitstellen möchten, müssen Sie die gesamte Pipeline einschließlich der Staging-Bereitstellung erneut bereitstellen, auch wenn dort kein Code geändert wurde.
* Da Umgebungen während Bereitstellungen nicht aktualisiert werden können und Sie die Produktionsumgebung nicht aktualisieren können, wenn Sie sie mehrere Tage lang anhalten und in der Staging-Umgebung testen möchten, bevor Sie sie zur Produktion weiterleiten. Dies führt zu nicht abhängigen Aufgaben, z. B. zum Aktualisieren [Umgebungsvariablen](/help/getting-started/build-environment.md#environment-variables) unmöglich.

Staging- und reine Produktleitungen bieten Lösungen für diese Anwendungsfälle durch Bereitstellung dedizierter Bereitstellungsoptionen.

* **Implementierungs-Pipelines für die Staging-Umgebung** nur in einer Staging-Umgebung bereitstellen, deren Ausführung abgeschlossen ist, sobald die Implementierung und die Tests abgeschlossen sind.
   * Eine reine Staging-Pipeline verhält sich identisch mit der standardmäßigen gekoppelten vollständigen Stackprod-Pipeline, jedoch ohne die Produktionsbereitstellungsschritte (Genehmigung, Zeitplan, Bereitstellung).
* **Bereitstellungs-Pipelines für &quot;Nur Produktion&quot;** Bereitstellung nur in einer Produktionsumgebung mit der Option, eine Ausführung auszuwählen, die erfolgreich abgeschlossen und in der Staging-Phase validiert wurde, und Bereitstellung der Artefakte für die Produktion.
   * Reine Produktebene Pipelines verwenden die Artefakte aus den Staging-Implementierungen erneut und überspringen die Erstellungsphase.

Weder stage-only- noch prod-only-Pipelines werden ausgeführt, während eine Full-Stack-Produktions-Pipeline ausgeführt wird und umgekehrt.

Diese dedizierten Pipelines bieten mehr Flexibilität. Beachten Sie jedoch die folgenden Details zu Betrieb und Empfehlungen.

>[!NOTE]
>
>Nur-Produkt-Pipelines verwenden immer die Artefakte aus der Nur-Staging-Pipeline, unabhängig davon, was in der Zwischenzeit über die standardmäßige gekoppelte Produktions-Pipeline auf der Bühne bereitgestellt wurde.
>
>* Dies könnte zu unerwünschten Code-Rollbacks führen.
>* Adobe empfiehlt, die standardmäßig gekoppelte Produktions-Pipeline nicht mehr zu verwenden, wenn Sie mit der Verwendung der reinen Produktions- und Staging-Pipelines beginnen.
>* Wenn Sie weiterhin die standardmäßigen gekoppelten Pipelines und die Nur-Staging-/Prod-Pipelines ausführen möchten, sollten Sie die Wiederverwendung von Artefakten beachten, um Code-Rollbacks zu vermeiden.

## Pipeline-Erstellung {#pipeline-creation}

Nur-Prod- und Nur-Staging-Pipelines werden ähnlich wie die standardmäßigen gekoppelten Pipelines erstellt [Produktions-Pipelines](/help/using/production-pipelines.md) und [produktionsfremde Pipelines.](/help/using/non-production-pipelines.md) Weitere Informationen finden Sie in diesen Dokumenten.

1. Im **Pipelines** Fenster, tippen oder klicken **Pipeline hinzufügen**.

   * Auswählen **Hinzufügen einer produktionsfremden Pipeline** , um eine reine Staging-Pipeline zu erstellen.
   * Auswählen **Hinzufügen der Pipeline &quot;Nur Produktion&quot;** , um eine reine Prod-Pipeline zu erstellen.

   ![Erstellen einer reinen Produktions-/Staging-Pipeline](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Bestimmte Optionen können ausgegraut werden, wenn die entsprechenden Pipelines bereits vorhanden sind.
>
>* **Hinzufügen der Pipeline &quot;Nur Produktion&quot;** nicht verfügbar, wenn noch keine schreibgeschützte Pipeline vorhanden ist.
>* **Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn bereits eine Standard-gekoppelte Pipeline vorhanden ist.
>* Pro Programm ist nur eine Produktions- und eine Nur-Staging-Pipeline zulässig.

### Nur-Staging-Pipelines {#stage-only}

1. Nachdem Sie die **Hinzufügen einer produktionsfremden Pipeline** die Option **Hinzufügen einer produktionsfremden Pipeline** wird geöffnet.
1. Um eine schreibgeschützte Pipeline zu erstellen, wählen Sie die Staging-Umgebung im **Förderfähige Bereitstellungsumgebungen** -Feld für Ihre Pipeline. Füllen Sie die übrigen Felder aus und tippen oder klicken Sie auf **Weiter**.

   ![Erstellen einer reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only.png)

1. Im **Staging-Tests** -Registerkarte können Sie dann Tests definieren, die in der Staging-Umgebung durchgeführt werden sollen. Tippen oder klicken **Speichern** , um Ihre neue Pipeline zu speichern.

   ![Testparameter für eine schreibgeschützte Pipeline](/help/assets/configure-pipelines/stage-only-test.png)

### Reine Produktanleitungen {#prod-only}

1. Nachdem Sie die **Hinzufügen der Pipeline &quot;Nur Produktion&quot;** die Option **Hinzufügen der Pipeline &quot;Nur Produktion&quot;** wird geöffnet.
1. Stellen Sie eine **Pipeline-Name**. Die verbleibenden Optionen und Funktionen des Dialogfelds funktionieren genauso wie im Dialogfeld zur Erstellung der standardmäßig gekoppelten Pipeline. Tippen oder klicken Sie auf **Speichern**, um die Pipeline zu speichern.

   ![Erstellen einer reinen Produktions-Pipeline](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ausführen von reinen Produktions- und Nur-Staging-Pipelines {#running}

Nur-Prod- und Nur-Staging-Pipelines werden auf dieselbe Weise ausgeführt wie [alle anderen Pipelines ausgeführt werden.](/help/using/managing-pipelines.md#running-pipelines) Weitere Informationen finden Sie in dieser Dokumentation .

Darüber hinaus kann ein reiner Pipeline-Lauf direkt aus den Ausführungsdetails einer reinen Staging-Pipeline ausgelöst werden.

### Nur-Staging-Pipelines {#stage-only-run}

Eine Nur-Staging-Pipeline läuft fast genauso wie eine standardmäßige gekoppelte Pipeline. Am Ende der Ausführung wird nach den Testschritten jedoch ein **Build bewerben** -Schaltfläche können Sie eine reine Pipeline-Ausführung starten, die die von dieser Ausführung auf der Bühne bereitgestellten Artefakte verwendet und in der Produktion bereitstellt.

![Ausführung der reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Die **Build bewerben** -Schaltfläche wird nur angezeigt, wenn Sie die neueste erfolgreiche Ausführung der reinen Staging-Pipeline verwenden. Nachdem Sie auf getippt oder geklickt haben, werden Sie aufgefordert, die Ausführung der reinen Produktepipeline zu bestätigen oder eine reine Prod-only-Pipeline zu erstellen, falls noch keine Pipeline vorhanden ist.

### Reine Produktanleitungen {#prod-only-run}

Bei reinen Produktleitungen ist es wichtig, die Quellartefakte zu identifizieren, die für die Produktion bereitgestellt werden sollen. Diese Details finden Sie im **Artefaktvorbereitung** Schritt. Sie können zu diesen Ausführungen navigieren, um weitere Details und Protokolle zu erhalten.

![Artefaktdetails](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
