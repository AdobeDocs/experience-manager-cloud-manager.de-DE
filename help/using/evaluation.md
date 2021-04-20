---
title: Test
seo-title: Test
description: 'Diese Seite dient als Ausgangspunkt für weitere Informationen zur Testphase des Assistenten für Produktaktualisierungen. '
seo-description: Diese Seite dient als Ausgangspunkt für weitere Informationen zur Testphase des Assistenten für Produktaktualisierungen.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
feature: Getting Started
translation-type: tm+mt
source-git-commit: fb10d775c930b5bb475b497aac2fd59b053a9a00
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 100%

---


# Testphase {#evaluation}

Die erste Phase im Assistenten für Produktaktualisierungen ist die **[!UICONTROL Testphase]**.
Hier können Sie die Komplexität des Upgrades beurteilen, und zwar mithilfe des Musterdetektors, den Sie direkt über den Assistenten aufrufen können. Nach diesem Schritt haben Sie Zugriff auf den Testbericht.

Im generierten Bericht können Sie die Autoreninstanz auf ein Uggrade überprüfen. Suchen Sie nach Mustern, die:

* gegen bestimmte Regeln verstoßen und Bereiche betreffen, die durch das Upgrade überschrieben werden.

* eine AEM 6.x-Funktion oder eine API verwenden, die im neuen AEM nicht abwärtskompatibel ist und nach dem Upgrade möglicherweise beeinträchtigt sein kann.

Dies dient als Bewertungsgrundlage für den erforderlichen Entwicklungsaufwand beim Upgrade auf Adobe Experience Manager AEM 6.5.

>[!NOTE]
>
>Weitere Informationen zum Musterdetektor finden Sie unter [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor](https://helpx.adobe.com/de/experience-manager/6-4/sites/deploying/using/pattern-detector.html).

## Ausführen des Auswerters {#running-evaluator}

Gehen Sie wie folgt vor, um Testberichte zu erstellen:

1. Klicken Sie auf **[!UICONTROL Test ausführen]**.

   >[!NOTE]
   >
   >Der Musterdetektor kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und zu vermeiden, dass in geschäftskritischen Instanzen Verzögerungen auftreten, wird er von Cloud Manager auf der Autoreninstanz in der Staging-Umgebung ausgeführt.

   ![](assets/Run-Evaluation.png)

1. Über den Assistenten werden Sie über den Status Ihrer Aktion informiert. Während der Erstellung des Testberichts wird **In Bearbeitung** oder **Abgeschlossen** angezeigt.

   Sobald der Bericht generiert wurde, können Sie auf **[!UICONTROL Bericht herunterladen]** klicken, um eine Kopie zu speichern.

   ![](assets/Evaluation-1.png)


   >[!NOTE]
   >
   >Die aktuelle Version des Assistenten für Produktaktualisierungen in Cloud Manager unterstützt nur die **Testphase**. Die anderen vier Phasen **Behebung**, **Ausführung**, **Validierung** und **Abschluss** folgen bald.
