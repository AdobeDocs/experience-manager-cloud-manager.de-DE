---
title: Testphase
seo-title: Evaluation Phase
description: Erfahren Sie, wie die Bewertungsphase des Assistenten für Produktaktualisierungen mit der Mustererkennung die Komplexität des Upgrades bewertet.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: f855fa91656e4b3806a617d61ea313a51fae13b4
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 75%

---


# Testphase {#evaluation}

Die erste Phase im Assistenten für Produktaktualisierungen ist die **[!UICONTROL Bewertungs]**-Phase, die mit dem Mustererkennung direkt im Assistenten die Komplexität der Aktualisierung bewertet. Nach diesem Schritt haben Sie Zugriff auf den Berwertungsbericht.

Im generierten Bericht können Sie die Autoreninstanz auf die Berechtigung für ein Upgrade überprüfen. Suchen Sie nach Mustern, die:

* gegen bestimmte Regeln verstoßen und Bereiche betreffen, die durch das Upgrade überschrieben werden.

* eine AEM 6.x-Funktion oder eine API verwenden, die mit der neuen Version von AEM nicht abwärtskompatibel ist und nach dem Upgrade möglicherweise beeinträchtigt sein kann.

Dieser Bericht dient als Bewertungsgrundlage für den erforderlichen Entwicklungsaufwand beim Upgrade auf Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Weitere Informationen zum Musterdetektor finden Sie unter [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=de).

## Testbericht ausführen {#running}

Die Mustererkennung kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und zu vermeiden, dass in geschäftskritischen Instanzen Verzögerungen auftreten, wird sie von Cloud Manager auf der Autoreninstanz in der Staging-Umgebung ausgeführt.

**So führen Sie den Bewertungsbericht aus:**

1. Starten Sie den Assistenten wie im Dokument [Assistent für Produktaktualisierungen](/help/product-update-wizard/overview.md) beschrieben.

1. Klicken Sie auf **[!UICONTROL Test ausführen]**.

   ![Bewertung ausführen](/help/assets/Run-Evaluation.png)

1. Über den Assistenten werden Sie über den Status Ihrer Aktion informiert. Beachten Sie bei der Erstellung des Auswertungsberichts den Wert **Gestartet** oder **Abgeschlossen**.

1. Nachdem der Bericht generiert wurde, können Sie auf **[!UICONTROL Bericht herunterladen]** klicken, um eine Kopie zu speichern.

   ![Erstellter Bericht](/help/assets/Evaluation-1.png)

Die aktuelle Version des Assistenten für Produktaktualisierungen in Cloud Manager unterstützt nur die **Testphase**. Die anderen vier Phasen **Behebung**, **Ausführung**, **Validierung** und **Abschluss** folgen bald.
