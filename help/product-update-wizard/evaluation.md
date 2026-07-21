---
title: Testphase
seo-title: Evaluation Phase
description: Erfahren Sie, wie die Bewertungsphase des Assistenten für Produktaktualisierungen mithilfe der Mustererkennung die Komplexität des Upgrades bewertet.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
TQID: https://experienceleague.adobe.com/dj-Wnq9FagNI3mzzVHcUH-sOufzb02D0juHqhtgpon0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
feature_v2:
  - id: a01bfd36-4ab8-4bf8-9dc0-5b45b890552e
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: 1b146c2a01d3371ed2fe014a15a84ddee2cd9b6c
workflow-type: tm+mt
source-wordcount: 270
ht-degree: 40%

---

# Auswertungsphase {#evaluation}

Die erste Phase des Assistenten für Produktaktualisierungen ist die **[!UICONTROL Test]**-Phase. Sie führt die Mustererkennung im Assistenten aus, um die Komplexität des Upgrades zu bewerten. Am Ende dieses Schritts können Sie den Bewertungsbericht anzeigen.

Der Bericht überprüft die Autoreninstanz auf die Bereitschaft für ein Upgrade, indem Muster für Folgendes erkannt werden:

* Regelverletzungen in Bereichen, die von dem Upgrade betroffen oder überschrieben werden.
* Es erkennt AEM 6.x-Funktionen oder APIs, die nicht abwärtskompatibel sind und nach dem Upgrade fehlschlagen können.

Dieser Bericht hilft bei der Schätzung des Entwicklungsaufwands, der für das Upgrade auf Adobe Experience Manager (AEM) 6.5 erforderlich ist.

>[!NOTE]
>
>Weitere Informationen zur Mustererkennung finden Sie unter [Bewertung der Komplexität des Upgrades mit der Mustererkennung](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Ausführen des Auswertungsberichts {#running}

Die Mustererkennung kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und Leistungseinbußen bei kritischen Instanzen zu vermeiden, wird sie von Cloud Manager in der Staging-Umgebung der Autoreninstanz ausgeführt.

**So führen Sie den Auswertungsbericht aus:**

1. Starten Sie den Assistenten, wie unter [Assistent für Produktaktualisierungen](/help/product-update-wizard/overview.md) beschrieben.

1. Klicken Sie auf **[!UICONTROL Auswertung durchführen]**.

   ![Bewertung ausführen](/help/assets/Run-Evaluation.png)

1. Über den Assistenten werden Sie über den Status Ihrer Aktion informiert. Hinweis **In Bearbeitung** oder **Abgeschlossen** während der Erstellung des Bewertungsberichts.

1. Nachdem der Bericht generiert wurde, können Sie auf **[!UICONTROL Bericht herunterladen]** klicken, um eine Kopie zu speichern.

   ![Erstellter Bericht](/help/assets/Evaluation-1.png)

Der aktuelle Assistent für Produktaktualisierungen in Cloud Manager unterstützt nur die **Test**-Phase. Die anderen vier Phasen, nämlich **Behebung**, **Ausführung**, **Validierung** und **Abschluss**, kommen in Kürze.
