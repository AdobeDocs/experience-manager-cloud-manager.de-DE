---
title: Aufspalten in reine Staging- und reine Produktions-Pipelines
description: Erfahren Sie, wie Sie mithilfe von dedizierten Pipelines in Staging- und Produktionsbereitstellungen aufteilen können.
exl-id: b7dd0021-d346-464a-a49e-72864b01cce3
TQID: https://experienceleague.adobe.com/whq-Hkwp3mjTr0iftoKZHKdsi0xaKtVXazXjUENoaLk
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: cd2426f1-5719-4006-b8c2-738e5969754b
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 6b0075d2405e89dce1c883a2b5fc0bd952a3fddd
workflow-type: tm+mt
source-wordcount: 975
ht-degree: 56%

---

# Aufspalten in reine Staging- und reine Produktions-Pipelines {#stage-prod-only}

Sie können Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufspalten.

## Überblick {#overview}

Staging- und Produktionsumgebungen sind eng miteinander verbunden. Standardmäßig sind die damit verknüpften Bereitstellungen mit einer einzelnen Pipeline verknüpft. Eine Bereitstellungs-Pipeline wird sowohl in der Staging- als auch in der Produktionsumgebung dieses Programms bereitgestellt. Diese Kopplung ist zwar in der Regel geeignet, es gibt aber bestimmte Anwendungsfälle, in denen Nachteile auftreten:

* Wenn Sie eine Bereitstellung im Staging durchführen möchten, überspringen Sie den Schritt **Zur Produktion** Hochstufen“ in der Pipeline. Die Ausführung wird jedoch als abgebrochen markiert.
* Wenn Sie den neuesten Code aus einer Staging-Umgebung in der Produktion bereitstellen möchten, müssen Sie die gesamte Pipeline einschließlich der Staging-Bereitstellung erneut bereitstellen, obwohl dort kein Code geändert wurde.
* Während einer Bereitstellung können Umgebungen nicht aktualisiert werden. Wenn Sie Tests in der Staging-Umgebung mehrere Tage verzögern, bevor Sie zur Produktion weitergeleitet werden, bleibt die Produktionsumgebung gesperrt und kann nicht aktualisiert werden. Dieses Szenario macht nicht abhängige Aufgaben wie die Aktualisierung von [Umgebungsvariablen](/help/getting-started/build-environment.md#environment-variables) unmöglich.

Staging- und Nur-Produktions-Pipelines bieten Lösungen für diese Anwendungsfälle, indem spezielle Bereitstellungsoptionen bereitgestellt werden.

* **Nur-Staging-Bereitstellungs-Pipelines** Stellen Sie nur in einer Staging-Umgebung bereit, wobei die Ausführung nach Abschluss der Bereitstellung und der Tests abgeschlossen ist. Eine reine Staging-Pipeline verhält sich genauso wie die standardmäßig gekoppelte Full-Stack-Produktions-Pipeline, jedoch ohne die Schritte der Produktionsbereitstellung (Genehmigung, Zeitplan, Bereitstellung).
* **Nur-Produktion-Bereitstellungs-Pipelines** Stellen Sie nur für die Produktion bereit, indem Sie die neueste erfolgreiche Staging-Ausführung auswählen. Stellen Sie dann die Artefakte in der Produktion bereit. Reine Produktions-Pipelines verwenden Artefakte zur Staging-Bereitstellung wieder, wobei die Build-Phase übersprungen wird.

Reine Staging- und reine Produktions-Pipelines werden nicht ausgeführt, während eine Full-Stack-Produktions-Pipeline ausgeführt wird und umgekehrt. Wenn sowohl bei der reinen Staging- als auch bei der Full-Stack-Produktions-Pipeline der Trigger **Bei Git-Änderungen** konfiguriert wurde und auf dieselbe Verzweigung und dasselbe Repository verweist, wird nur die reine Staging-Pipeline automatisch gestartet. Reine Produktions-Pipelines führen keinen Trigger zu **`On Git Changes`**, da sie nicht direkt mit einem Repository verknüpft sind.

Reine Produktions-Pipelines werden nicht manuell ausgelöst, da sie nicht direkt mit einem Repository für **Bei Git-Änderungen** verknüpft sind.

Diese dedizierten Pipelines bieten mehr Flexibilität, beachten Sie jedoch die folgenden Details zum Betrieb und zu den Empfehlungen:

>[!NOTE]
>
>Reine Produktions-Pipelines verwenden immer die Artefakte aus der reinen Staging-Pipeline. Dieser Prozess bleibt auch dann gültig, wenn die standardmäßige gekoppelte Produktions-Pipeline in der Zwischenzeit etwas Anderes zum Staging bereitgestellt hat.
>
>* Ein solches Szenario führt zu unerwünschten Code-Rollbacks.
>* Adobe empfiehlt, die Verwendung der standardmäßigen gekoppelten Produktions-Pipeline einzustellen, sobald Sie mit der Verwendung der produktionsbezogenen und der Nur-Staging-Pipeline beginnen.
>* Wenn Sie weiterhin die standardmäßigen gekoppelten Pipelines und die reinen Staging-/Produktions-Pipelines ausführen möchten, sollten Sie die Wiederverwendung von Artefakten nicht vergessen, um Code-Rollbacks zu vermeiden.

## Pipeline-Erstellung {#pipeline-creation}

Reine Produktions- und Staging-Pipelines werden auf ähnliche Weise wie die standardmäßigen gekoppelten [Produktions-Pipelines](/help/using/production-pipelines.md) und [produktionsfremden Pipelines](/help/using/non-production-pipelines.md) erstellt. Weitere Informationen finden Sie in den zugehörigen Dokumenten.

1. Klicken Sie im Fenster **Pipelines** auf **Pipeline hinzufügen**.

   * Wählen Sie **Produktionsfremde Pipeline hinzufügen**, um eine reine Staging-Pipeline zu erstellen.
   * Wählen Sie **Produktionsgeschützte Pipeline hinzufügen** aus, um eine produktionsgeschützte Pipeline zu erstellen.

   ![Erstellen einer reinen Produktions-/Staging-Pipeline](/help/assets/configure-pipelines/prod-stage-pipelines.png)

>[!NOTE]
>
>Bestimmte Optionen sind ausgegraut, wenn die entsprechenden Pipelines bereits vorhanden sind.
>
>* **Nur Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn noch keine reine Staging-Pipeline vorhanden ist.
>* **Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn bereits eine standardmäßige gekoppelte Pipeline vorhanden ist.
>* Pro Programm ist nur eine produktbezogene und eine studienbezogene Pipeline zulässig.

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

1. Nachdem Sie auf **Nur Produktions-Pipeline hinzufügen** geklickt haben, wird das zugehörige Dialogfeld geöffnet.
1. Geben Sie im Feld **Pipeline-Name** den gewünschten Namen ein. Die verbleibenden Optionen und Funktionen des Dialogfelds funktionieren genauso wie die Optionen im Dialogfeld zur Erstellung der standardmäßig gekoppelten Pipeline.
1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

   ![Erstellen einer reinen Produktions-Pipeline](/help/assets/configure-pipelines/prod-only-pipeline.png)

## Ausführen von reinen Produktions- und Staging-Pipelines {#running}

Reine Produktions- und reine Staging-Pipelines werden auf die gleiche Weise ausgeführt wie [alle anderen Pipelines](/help/using/managing-pipelines.md#running-pipelines). Weitere Informationen finden Sie in der zugehörigen Dokumentation. Es gibt jedoch zwei neue Funktionen dieser Pipelines.

* Reine Staging- und reine Produktions-Pipelines bieten einen neuen [Notfallmodus](#emergency-mode) zum Überspringen von Tests.
* Eine schreibgeschützte Pipeline-Ausführung kann direkt über die Ausführungsdetails einer (Nur-Staging[-Pipeline ausgelöst &#x200B;](#stage-only-run).

### Notfallmodus {#emergency-mode}

Beim Starten von Pipelines, die nur für die Produktion und Staging vorgesehen sind, werden Sie aufgefordert, den Start zu bestätigen und anzugeben, wie er fortgesetzt wird.

* **Normaler Modus** ist ein Standardablauf und umfasst Schritte zum Testen von Staging-Umgebungen.
* **Notfallmodus** überspringt die Schritte zum Testen der Staging-Umgebung.

![Notfallmodus](/help/assets/configure-pipelines/emergency-mode.png)

### Reine Staging-Pipelines {#stage-only-run}

Eine reine Staging-Pipeline wird fast genauso ausgeführt wie eine standardmäßige gekoppelte Pipeline. Am Ende des Laufs wird jedoch nach den Testschritten eine Schaltfläche **Build weiterleiten** angezeigt. Mit dieser Schaltfläche können Sie eine schreibgeschützte Pipeline-Ausführung starten. Sie verwendet die Artefakte, die für die Staging-Phase der Ausführung bereitgestellt wurden. Anschließend werden sie in der Produktion bereitgestellt.

![Ausführen einer reinen Staging-Pipeline](/help/assets/configure-pipelines/stage-only-pipeline-run.png)

Wenn Sie auf **Build bewerben** klicken, werden Sie aufgefordert, die Ausführung der zugehörigen Nur-Produktions-Pipeline entweder normal oder im [Notfallmodus](#emergency-mode) zu bestätigen.

Wenn keine reine Produktions-Pipeline existiert, werden Sie dazu aufgefordert, eine zu erstellen.

### Reine Produktions-Pipelines {#prod-only-run}

Achten Sie bei reinen Produktions-Pipelines darauf, die Quellartefakte zu identifizieren, die für die Produktion bereitgestellt werden sollen. Diese Details finden Sie im Schritt **Artefaktvorbereitung**. Sie können zu diesen Ausführungen navigieren, um weitere Details und Protokolle zu erhalten.

![Artefaktdetails](/help/assets/configure-pipelines/prod-only-pipeline-run.png)

