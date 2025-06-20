---
title: Testphase
seo-title: Evaluation Phase
description: Erfahren Sie, wie die Bewertungsphase des Assistenten für Produktaktualisierungen mithilfe der Mustererkennung die Komplexität des Upgrades bewertet.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: fb3c2b3450cfbbd402e9e0635b7ae1bd71ce0501
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 57%

---


# Auswertungsphase {#evaluation}

Die erste Phase des Assistenten für Produktaktualisierungen ist die **[!UICONTROL Test]**-Phase. Sie führt die Mustererkennung im Assistenten aus, um die Komplexität des Upgrades zu bewerten. Am Ende dieses Schritts können Sie den Bewertungsbericht anzeigen.

Der Bericht überprüft die Autoreninstanz auf die Bereitschaft für ein Upgrade, indem Muster für Folgendes erkannt werden:

* Regelverletzungen in Bereichen, die von dem Upgrade betroffen oder überschrieben werden.
* Sie verwendet AEM 6.x-Funktionen oder -APIs, die nicht abwärtskompatibel sind und nach dem Upgrade beschädigt werden können.

Dieser Bericht hilft bei der Schätzung des Entwicklungsaufwands, der für das Upgrade auf Adobe Experience Manager (AEM) 6.5 erforderlich ist.

>[!NOTE]
>
>Weitere Informationen zur Mustererkennung finden Sie unter [Bewertung der Komplexität des Upgrades mit der Mustererkennung](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Ausführen des Auswertungsberichts {#running}

Die Mustererkennung kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und zu vermeiden, dass in geschäftskritischen Instanzen Verzögerungen auftreten, wird sie von Cloud Manager auf der Autoreninstanz in der Staging-Umgebung ausgeführt.

**So führen Sie den Auswertungsbericht aus:**

1. Starten Sie den Assistenten, wie unter [Assistent für Produktaktualisierungen](/help/product-update-wizard/overview.md) beschrieben.

1. Klicken Sie auf **[!UICONTROL Auswertung durchführen]**.

   ![Bewertung ausführen](/help/assets/Run-Evaluation.png)

1. Über den Assistenten werden Sie über den Status Ihrer Aktion informiert. Während der Erstellung des Auswertungsberichts wird **In Bearbeitung** oder **Abgeschlossen** angezeigt.

1. Nachdem der Bericht generiert wurde, können Sie auf **[!UICONTROL Bericht herunterladen]** klicken, um eine Kopie zu speichern.

   ![Erstellter Bericht](/help/assets/Evaluation-1.png)

Der aktuelle Assistent für Produktaktualisierungen in Cloud Manager unterstützt nur die **Test**-Phase. Die anderen vier Phasen **Behebung**, **Ausführung**, **Validierung** und **Abschluss** folgen bald.
