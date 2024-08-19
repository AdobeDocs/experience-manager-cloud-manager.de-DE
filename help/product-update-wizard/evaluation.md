---
title: Testphase
seo-title: Evaluation Phase
description: Erfahren Sie, wie die Bewertungsphase des Assistenten für Produktaktualisierungen die Komplexität der Aktualisierung mit dem Musterdetektor bewertet.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: 11a6a53d8cbfb689810a9a8e7d82293a49863084
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 17%

---


# Testphase {#evaluation}

Die erste Phase im Assistenten für Produktaktualisierungen ist die Phase **[!UICONTROL Evaluierung]**, in der die Aktualisierungskomplexität mit dem Musterdetektor direkt im Assistenten bewertet wird. Am Ende dieses Schritts können Sie auf den Bewertungsbericht zugreifen.

Mit dem generierten Bericht können Sie die Berechtigung der Autoreninstanz auf ein Upgrade überprüfen, indem Sie die folgenden Muster erkennen:

* Verstoßen Sie bestimmte Regeln in Bezug auf Bereiche, die von der Aktualisierung betroffen oder überschrieben werden.

* Verwenden Sie eine AEM 6.x-Funktion oder eine API, die nicht abwärtskompatibel mit der neuen Version von AEM ist und nach einem Upgrade möglicherweise beschädigt werden kann.

Dieser Bericht dient als Bewertungsgrundlage für den erforderlichen Entwicklungsaufwand beim Upgrade auf Adobe Experience Manager (AEM) 6.5.

>[!NOTE]
>
>Weitere Informationen zum Musterdetektor finden Sie unter [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/upgrading/pattern-detector).

## Testbericht ausführen {#running}

Der Musterdetektor kann in jeder Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und Verlangsamungen bei geschäftskritischen Instanzen zu vermeiden, führt Cloud Manager sie in der Staging-Umgebung der Autoreninstanz aus.

**So führen Sie den Bewertungsbericht aus:**

1. Starten Sie den Assistenten wie im Dokument [Assistent für Produktaktualisierungen](/help/product-update-wizard/overview.md) beschrieben.

1. Klicken Sie auf **[!UICONTROL Test ausführen]**.

   ![Bewertung ausführen](/help/assets/Run-Evaluation.png)

1. Über den Assistenten werden Sie über den Status Ihrer Aktion informiert. Beachten Sie bei der Erstellung des Auswertungsberichts den Wert **Gestartet** oder **Abgeschlossen**.

1. Nachdem der Bericht generiert wurde, können Sie auf **[!UICONTROL Bericht herunterladen]** klicken, um eine Kopie zu speichern.

   ![Erstellter Bericht](/help/assets/Evaluation-1.png)

Die aktuelle Version des Assistenten für Produktaktualisierungen in Cloud Manager unterstützt nur die Phase **Evaluierung** . Die anderen vier Phasen **Behebung**, **Ausführung**, **Validierung** und **Abschluss** folgen bald.
