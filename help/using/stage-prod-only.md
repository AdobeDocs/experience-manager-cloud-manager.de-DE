---
title: Reine Staging- und Produktions-Pipelines
description: Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufteilen können.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: 03f7429fd2c4a6dd4c8ae3228eff9c8cdab1ded8
workflow-type: tm+mt
source-wordcount: '932'
ht-degree: 42%

---

# Reine Staging- und Produktions-Pipelines {#stage-prod-only}

Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufteilen können.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/release-notes/current.md#early-adoption) verfügbar.

## Überblick {#overview}

Staging- und Produktionsumgebungen sind eng miteinander verbunden. Standardmäßig sind die damit verknüpften Bereitstellungen mit einer einzelnen Pipeline verknüpft. Das heißt, eine Bereitstellungs-Pipeline wird sowohl für die Staging- als auch für die Produktionsumgebung in diesem Programm bereitgestellt. Diese Kopplung ist zwar in der Regel geeignet, es gibt jedoch einige Anwendungsfälle, in denen Nachteile vorliegen:

* Wenn Sie eine Bereitstellung nur für Staging durchführen möchten, lehnen Sie den Schritt **Weiterleiten an Produktion** in der Pipeline ab. Die Ausführung wird jedoch als abgebrochen markiert.
* Wenn Sie den neuesten Code in einer Staging-Umgebung für die Produktion bereitstellen möchten, müssen Sie die gesamte Pipeline einschließlich der Staging-Bereitstellung erneut bereitstellen, selbst wenn dort kein Code geändert wurde.
* Umgebungen können während der Bereitstellung nicht aktualisiert werden. Wenn Sie den Test in der Staging-Umgebung mehrere Tage lang anhalten, bevor Sie die Promotion zur Produktion durchführen, bleibt die Produktionsumgebung gesperrt und kann nicht aktualisiert werden. Dieses Szenario macht nicht-abhängige Aufgaben wie das Aktualisieren von [Umgebungsvariablen](/help/getting-started/build-environment.md#environment-variables) unmöglich.

Reine Staging- und Produktions-Pipelines bieten Lösungen für diese Anwendungsfälle, indem sie dedizierte Bereitstellungsoptionen bieten.

* **Bereitstellungs-Pipelines für die Staging-Umgebung:** Wird nur in einer Staging-Umgebung bereitgestellt, während die Ausführung abgeschlossen ist, sobald die Bereitstellung und die Tests abgeschlossen sind. Eine reine Staging-Pipeline verhält sich genauso wie die standardmäßig gekoppelte Full-Stack-Produktions-Pipeline, jedoch ohne die Schritte der Produktionsbereitstellung (Genehmigung, Zeitplan, Bereitstellung).
* **Produktionsgeschützte Bereitstellungs-Pipelines:** Wird nur für die Produktion bereitgestellt, indem die zuletzt erfolgreiche Staging-Ausführung ausgewählt wird. Bereitstellen der Artefakte dann für die Produktion. Nur-Prod-Pipelines verwenden die Staging-Bereitstellungsartefakte erneut, wobei die Build-Phase umgangen wird.

Staging- und reine Produktions-Pipelines werden nicht ausgeführt, während eine Produktions-Pipeline für den vollständigen Stapel ausgeführt wird, und umgekehrt. Wenn sowohl bei der reinen Staging- als auch bei der Full-Stack-Produktions-Pipeline der Trigger **Bei Git-Änderungen** konfiguriert wurde und auf dieselbe Verzweigung und dasselbe Repository verweist, wird nur die reine Staging-Pipeline automatisch gestartet. Nur-Prod-Pipelines starten nicht &quot;**`On Git Changes`**&quot;, da sie nicht direkt mit einem Repository verknüpft sind.

Nur-Prod-Pipelines werden manuell ausgelöst, da sie nicht direkt mit einem Repository für **On-Git-Änderungen** verknüpft sind.

Diese dedizierten Pipelines bieten mehr Flexibilität. Beachten Sie jedoch die folgenden Details zum Betrieb und Empfehlungen.

>[!NOTE]
>
>Nur-Produkt-Pipelines verwenden immer Artefakte aus der schreibgeschützten Pipeline. Dieser Prozess bleibt auch dann wahr, wenn die standardmäßige gekoppelte Produktions-Pipeline in der Zwischenzeit etwas Anderes für die Staging-Umgebung bereitgestellt hat.
>
>* Ein Beispiel hierfür könnte zu unerwünschten Code-Rollbacks führen.
>* Adobe empfiehlt, die standardmäßig gekoppelte Produktions-Pipeline nicht mehr zu verwenden, wenn Sie mit der Verwendung der reinen Produktions- und Staging-Pipelines beginnen.
>* Wenn Sie weiterhin die standardmäßigen gekoppelten Pipelines und die reinen Staging-/Produktions-Pipelines ausführen möchten, sollten Sie die Wiederverwendung von Artefakten nicht vergessen, um Code-Rollbacks zu vermeiden.

## Pipeline-Erstellung {#pipeline-creation}

Die Erstellung von reinen Produktions- und Staging-Pipelines erfolgt auf ähnliche Weise wie bei den standardmäßig gekoppelten [Produktions-Pipelines](/help/using/production-pipelines.md) und [produktionsfremden Pipelines](/help/using/non-production-pipelines.md). Weitere Informationen finden Sie in den zugehörigen Dokumenten.

1. Klicken Sie im Fenster **Pipelines** auf **Pipeline hinzufügen**.

   * Wählen Sie **Produktionsfremde Pipeline hinzufügen**, um eine reine Staging-Pipeline zu erstellen.
   * Wählen Sie **Reine Produktions-Pipeline hinzufügen**, um eine reine Produktions-Pipeline zu erstellen.

   ![Erstellen einer reinen Produktions-/Staging-Pipeline](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Bestimmte Optionen können ausgegraut sein, wenn die entsprechenden Pipelines bereits vorhanden sind.
>
>* **Reine Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn noch keine reine Staging-Pipeline existiert.
>* **Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn bereits eine standardmäßige gekoppelte Pipeline vorhanden ist.
>* Pro Programm ist nur je eine reine Produktions-Pipeline und eine reine Staging-Pipeline zulässig.

### Reine Staging-Pipelines {#stage-only}

1. Nachdem Sie die Option **Nicht-Produktions-Pipeline hinzufügen** ausgewählt haben, wird das Dialogfeld **Nicht-Produktions-Pipeline hinzufügen** geöffnet.
1. Um eine Staging-Pipeline zu erstellen, wählen Sie die Staging-Umgebung im Feld **Für Ihre Pipeline geeignete Bereitstellungsumgebungen** aus.
1. Füllen Sie die übrigen Felder aus.
1. Klicken Sie auf **Weiter**.

   ![Erstellen einer reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only.png)

1. Definieren Sie auf der Registerkarte **Staging-Tests** die Tests, die in der Staging-Umgebung durchgeführt werden sollen.
1. Klicken Sie auf **Speichern**.

   ![Testparameter für eine reine Staging-Pipeline](/help/assets/configure-pipelines/stage-only-test.png)

### Reine Produktions-Pipelines {#prod-only}

1. Nachdem Sie die Option **Nur Produktions-Pipeline hinzufügen** ausgewählt haben, wird das Dialogfeld **Nur Produktions-Pipeline hinzufügen** geöffnet.
1. Geben Sie im Feld **Pipeline-Name** den gewünschten Namen ein. Die übrigen Optionen und Funktionen des Dialogfelds entsprechen den Optionen im Dialogfeld zur Erstellung der standardmäßig gekoppelten Pipeline.
1. Klicken Sie in der rechten unteren Ecke des Dialogfelds auf **Speichern**.

   ![Erstellen einer reinen Produktions-Pipeline](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ausführen von reinen Produktions- und Staging-Pipelines {#running}

Nur-Prod- und Nur-Staging-Pipelines werden größtenteils auf dieselbe Weise ausgeführt wie [alle anderen Pipelines werden ausgeführt](/help/using/managing-pipelines.md#running-pipelines). Weitere Informationen finden Sie in dieser Dokumentation . Es gibt jedoch zwei neue Funktionen dieser Pipelines.

* Nur-Staging- und reine Produktleitungen bieten einen neuen [Notfallmodus](#emergency-mode), in dem Tests übersprungen werden können.
* Der reine Prod-Pipelineablauf kann direkt aus den Ausführungsdetails einer [Nur-Staging-Pipeline](#stage-only-run) ausgelöst werden.

### Notfallmodus {#emergency-mode}

Beim Starten von reine Produktions- und Staging-Online-Pipelines werden Sie aufgefordert, den Start und dessen Start zu bestätigen.

* **Normaler Modus** ist ein Standardablauf und umfasst Schritte zum Testen von Phasen.
* **Notfallmodus** überspringt die Schritte zum Testen der Bühne.

![Notfallmodus](/help/assets/configure-pipelines/emergency-mode.png)

### Reine Staging-Pipelines {#stage-only-run}

Eine reine Staging-Pipeline wird fast genauso ausgeführt wie eine standardmäßige gekoppelte Pipeline. Am Ende der Ausführung wird jedoch nach den Testschritten eine Schaltfläche **Build bewerben** angezeigt. Mit dieser Schaltfläche können Sie eine reine Pipelineausführung mit den Artefakten starten, die auf der Bühne bereitgestellt wurden, und sie für die Produktion bereitstellen.

![Ausführen einer reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Wenn Sie auf **Build bewerben** klicken, werden Sie aufgefordert, die Ausführung der zugehörigen reinen Staging-Pipeline entweder normal oder im [Notfallmodus](#emergency-mode) zu bestätigen.

Wenn keine reine Pipeline vorhanden ist, werden Sie aufgefordert, eine zu erstellen.

### Reine Produktions-Pipelines {#prod-only-run}

Stellen Sie bei reinen Produktions-Pipelines sicher, dass Sie die Quellartefakte identifizieren, die in der Produktion bereitgestellt werden sollen. Diese Details finden Sie im Schritt **Artefaktvorbereitung** . Sie können zu diesen Ausführungen navigieren, um weitere Details und Protokolle zu erhalten.

![Artefaktdetails](/help/assets/configure-pipelines/prod-only-pipeline-run.png)
