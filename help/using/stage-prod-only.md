---
title: Reine Staging- und Produktions-Pipelines
description: Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufteilen können.
badge: label="Early Adopter" type="Positive" url="/help/release-notes/current.md
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
source-git-commit: b830c30bb6b2b99ef442577325a30de6b9953ec8
workflow-type: tm+mt
source-wordcount: '937'
ht-degree: 99%

---

# Reine Staging- und Produktions-Pipelines {#stage-prod-only}

Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufteilen können.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/release-notes/current.md#staging-production-only-pipelines) verfügbar.

## Übersicht {#overview}

Staging- und Produktionsumgebungen sind eng miteinander verbunden. Standardmäßig sind die damit verknüpften Bereitstellungen mit einer einzelnen Pipeline verknüpft. Hierbei handelt es sich um eine Bereitstellungs-Pipeline, die sowohl für die Staging- als auch für die Produktionsumgebung in diesem Programm bereitgestellt wird. Diese Kopplung ist zwar in der Regel geeignet, es gibt jedoch einige Anwendungsfälle, in denen Nachteile entstehen:

* Wenn Sie die Bereitstellung nur für die Staging-Umgebung durchführen möchten, lehnen Sie den Schritt **Zur Produktion weiterleiten** in der Pipeline ab. Die Ausführung wird jedoch als abgebrochen markiert.
* Wenn Sie den neuesten Code in einer Staging-Umgebung für die Produktion bereitstellen möchten, müssen Sie die gesamte Pipeline einschließlich der Staging-Bereitstellung erneut bereitstellen, selbst wenn dort kein Code geändert wurde.
* Während einer Bereitstellung können Umgebungen nicht aktualisiert werden. Wenn Sie mehrere Tage in der Staging-Umgebung pausieren und testen möchten, bevor Sie sie zur Produktion weiterleiten, bleibt die Produktionsumgebung gesperrt und kann nicht aktualisiert werden. Dieses Szenario macht nicht abhängige Aufgaben wie die Aktualisierung von [Umgebungsvariablen](/help/getting-started/build-environment.md#environment-variables) unmöglich.

Reine Staging- und Produktions-Pipelines bieten Lösungen für diese Anwendungsfälle, indem sie dedizierte Bereitstellungsoptionen bieten.

* **Bereitstellungs-Pipelines für reine Staging-Umgebungen** stellen nur in einer Staging-Umgebung bereit und beenden ihre Ausführung, sobald die Bereitstellung und die Tests abgeschlossen sind. Eine reine Staging-Pipeline verhält sich genauso wie die standardmäßig gekoppelte Full-Stack-Produktions-Pipeline, jedoch ohne die Schritte der Produktionsbereitstellung (Genehmigung, Zeitplan, Bereitstellung).
* **Bereitstellungs-Pipelines für reine Produktionsumgebungen:** Wird nur in einer Produktionsumgebung bereitgestellt, indem die letzte erfolgreiche Staging-Ausführung ausgewählt wird. Anschließend stellen sie ihre Artefakte für die Produktion bereit. Reine Produktions-Pipelines verwenden die Artefakte aus den Staging-Bereitstellungen erneut und überspringen die Erstellungsphase.

Reine Staging- und reine Produktions-Pipelines werden nicht ausgeführt, während eine Full-Stack-Produktions-Pipeline ausgeführt wird und umgekehrt. Wenn sowohl bei der reinen Staging- als auch bei der Full-Stack-Produktions-Pipeline der Trigger **Bei Git-Änderungen** konfiguriert wurde und auf dieselbe Verzweigung und dasselbe Repository verweist, wird nur die reine Staging-Pipeline automatisch gestartet. Reine Produktions-Pipelines werden nicht mit **`On Git Changes`** gestartet, da sie nicht direkt mit einem Repository verknüpft sind.

Reine Produktions-Pipelines werden nicht manuell ausgelöst, da sie nicht direkt mit einem Repository für **Bei Git-Änderungen** verknüpft sind.

Diese dedizierten Pipelines bieten mehr Flexibilität. Beachten Sie jedoch die folgenden Details zum Betrieb und Empfehlungen.

>[!NOTE]
>
>Reine Produktions-Pipelines verwenden immer die Artefakte aus der reinen Staging-Pipeline. Dieser Prozess wird auch dann eingehalten, wenn die standardmäßige gekoppelte Produktions-Pipeline in der Zwischenzeit etwas Anderes für die Staging-Umgebung bereitgestellt hat.
>
>* Ein solches Szenario könnte zu unerwünschten Code-Rollbacks führen.
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

1. Sobald Sie die Option **Produktionsfremde Pipeline hinzufügen** ausgewählt haben, wird das Dialogfeld **Produktionsfremde Pipeline hinzufügen** geöffnet.
1. Um eine reine Staging-Pipeline zu erstellen, wählen Sie die Staging-Umgebung im Feld **Zulässige Bereitstellungsumgebungen** für Ihre Pipeline aus. 
1. Füllen Sie die übrigen Felder aus.
1. Klicken Sie auf **Weiter**.

   ![Erstellen einer reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only.png)

1. Definieren Sie auf der Registerkarte **Staging-Tests** die Tests, die in der Staging-Umgebung durchgeführt werden sollen. 
1. Klicken Sie auf **Speichern**.

   ![Testparameter für eine reine Staging-Pipeline](/help/assets/configure-pipelines/stage-only-test.png)

### Reine Produktions-Pipelines {#prod-only}

1. Sobald Sie die Option **Reine Produktions-Pipeline hinzufügen** gewählt haben, öffnet sich das Dialogfeld **Reine Produktions-Pipeline hinzufügen**.
1. Geben Sie im Feld **Pipeline-Name** den gewünschten Namen ein. Die verbleibenden Optionen und Funktionen des Dialogfelds funktionieren genauso wie die Optionen im Dialogfeld zur Erstellung der standardmäßig gekoppelten Pipeline. 
1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

   ![Erstellen einer reinen Produktions-Pipeline](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ausführen von reinen Produktions- und Staging-Pipelines {#running}

Reine Produktions- und reine Staging-Pipelines werden auf die gleiche Weise ausgeführt wie [alle anderen Pipelines](/help/using/managing-pipelines.md#running-pipelines). Weitere Informationen finden Sie in der zugehörigen Dokumentation. Es gibt jedoch zwei neue Funktionen dieser Pipelines.

* Reine Staging- und reine Produktions-Pipelines bieten einen neuen [Notfallmodus](#emergency-mode) zum Überspringen von Tests.
* Die Ausführung einer reinen Produktions-Pipeline kann direkt aus den Ausführungsdetails einer [reinen Staging-Pipeline](#stage-only-run) ausgelöst werden.

### Notfallmodus {#emergency-mode}

Beim Starten von reinen Produktions- und reinen Staging-Online-Pipelines werden Sie aufgefordert, den Start sowie die Art des Starts zu bestätigen.

* **Normaler Modus** ist ein Standardablauf und umfasst Schritte zum Testen von Staging-Umgebungen.
* **Notfallmodus** überspringt die Schritte zum Testen der Staging-Umgebung.

![Notfallmodus](/help/assets/configure-pipelines/emergency-mode.png)

### Reine Staging-Pipelines {#stage-only-run}

Eine reine Staging-Pipeline wird fast genauso ausgeführt wie eine standardmäßige gekoppelte Pipeline. Am Ende des Laufs wird jedoch nach den Testschritten eine Schaltfläche **Build weiterleiten** angezeigt. Mit dieser Schaltfläche können Sie eine reine Produktions-Pipeline-Ausführung starten, die die Artefakte, die während dieses Durchlaufs in der Staging-Umgebung bereitgestellt wurden, verwendet und in der Produktion bereitstellt.

![Ausführen einer reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Wenn Sie auf **Build weiterleiten** klicken, werden Sie aufgefordert, die Ausführung der zugehörigen reinen Staging-Pipeline entweder normal oder im [Notfallmodus](#emergency-mode) zu bestätigen.

Wenn keine reine Produktions-Pipeline existiert, werden Sie dazu aufgefordert, eine zu erstellen.

### Reine Produktions-Pipelines {#prod-only-run}

Achten Sie bei reinen Produktions-Pipelines darauf, die Quellartefakte zu identifizieren, die für die Produktion bereitgestellt werden sollen. Diese Details finden Sie im Schritt **Artefaktvorbereitung**. Sie können zu diesen Ausführungen navigieren, um weitere Details und Protokolle zu erhalten.

![Artefaktdetails](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

