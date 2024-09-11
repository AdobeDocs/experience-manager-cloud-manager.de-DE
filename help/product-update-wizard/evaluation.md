---
title: Testphase
seo-title: Evaluation Phase
description: Erfahren Sie, wie die Bewertungsphase des Assistenten für Produktaktualisierungen mithilfe der Mustererkennung die Komplexität des Upgrades bewertet.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: ht
source-wordcount: '279'
ht-degree: 100%

---


# Auswertungsphase {#evaluation}

Die erste Phase im Assistenten für Produktaktualisierungen ist die **[!UICONTROL Bewertungsphase]**, die mit der Mustererkennung direkt im Assistenten die Komplexität der Aktualisierung bewertet. Nach diesem Schritt haben Sie Zugriff auf den Auswertungsbericht.

Im generierten Bericht können Sie die Autoreninstanz auf die Berechtigung für ein Upgrade überprüfen. Suchen Sie nach den folgenden Mustern, die:

* gegen bestimmte Regeln verstoßen, die Bereiche betreffen, die durch das Upgrade beeinträchtigt oder überschrieben werden.

* eine AEM 6.x-Funktion oder eine API verwenden, die mit der neuen Version von AEM nicht abwärtskompatibel ist und nach dem Upgrade möglicherweise beeinträchtigt sein könnte.

Dieser Bericht dient als Bewertungsgrundlage für den erforderlichen Entwicklungsaufwand beim Upgrade auf Adobe Experience Manager (AEM) 6.5.

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

Die aktuelle Version des Assistenten für Produktaktualisierungen in Cloud Manager unterstützt nur die **Auswertungsphase**. Die anderen vier Phasen **Behebung**, **Ausführung**, **Validierung** und **Abschluss** folgen bald.
