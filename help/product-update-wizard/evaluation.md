---
title: Testphase
seo-title: Evaluation Phase
description: Erfahren Sie, wie die Bewertungsphase des Assistenten für Produktaktualisierungen die Komplexität des Upgrades mit dem Musterdetektor bewertet.
exl-id: 1ffcbc21-dc36-435d-b83b-0209f81a15e7
source-git-commit: ce2145da3b9e605e8a41bac28df520f14e255557
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 28%

---


# Testphase {#evaluation}

Die erste Phase im Assistenten für Produktaktualisierungen ist **[!UICONTROL Auswertung]** Phase, die die Komplexität der Aktualisierung mit dem Musterdetektor direkt im Assistenten bewertet. Am Ende dieses Schritts haben Sie Zugriff auf einen Bewertungsbericht.

Der generierte Bericht ermöglicht es Ihnen, die Berechtigung der Autoreninstanz auf ein Upgrade zu überprüfen, indem Sie Muster erkennen, die:

* Verstöße gegen bestimmte Regeln in Bereichen, die von dem Upgrade betroffen oder überschrieben werden.

* Verwenden Sie eine AEM 6.x-Funktion oder eine API, die nicht abwärtskompatibel mit der neuen Version von AEM ist und nach der Aktualisierung möglicherweise beschädigt werden kann.

Der Bericht dient als Bewertung der Entwicklungsbemühungen, die bei der Aktualisierung auf Adobe Experience Manager (AEM) 6.5 erforderlich sind.

>[!NOTE]
>
>Weitere Informationen zum Musterdetektor finden Sie im Dokument . [Bewertung der Komplexität der Aktualisierung mit dem Musterdetektor.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/upgrading/pattern-detector.html?lang=en)

## Ausführen der Auswertung {#running}

Der Musterdetektor kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und Verlangsamungen bei geschäftskritischen Instanzen zu vermeiden, führt Cloud Manager sie in der Staging-Umgebung der Autoreninstanz aus.

Führen Sie diese Schritte aus, um den Bewertungsbericht zu erstellen.

1. Starten Sie den Assistenten wie im Dokument beschrieben. [Assistent für Produktaktualisierungen.](/help/product-update-wizard/overview.md)

1. Klicken Sie auf **[!UICONTROL Test ausführen]**.

   ![Ausführen einer Evaluierung](/help/assets/Run-Evaluation.png)

1. Über den Assistenten werden Sie über den Status Ihrer Aktion informiert. Während der Erstellung des Testberichts wird **In Bearbeitung** oder **Abgeschlossen** angezeigt.

1. Sobald der Bericht generiert wurde, können Sie auf **[!UICONTROL Bericht herunterladen]** klicken, um eine Kopie zu speichern.

   ![Bericht erstellt](/help/assets/Evaluation-1.png)

Die aktuelle Version des Assistenten für Produktaktualisierungen in Cloud Manager unterstützt nur die **Testphase**. Die anderen vier Phasen **Behebung**, **Ausführung**, **Validierung** und **Abschluss** folgen bald.
