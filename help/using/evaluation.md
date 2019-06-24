---
title: Test
seo-title: Test
description: 'Diese Seite dient als Ausgangspunkt für die Lernphase im Produkt-Update-Assistenten. '
seo-description: Diese Seite dient als Ausgangspunkt für die Lernphase im Produkt-Update-Assistenten.
uuid: 62d68e79-c2ba-4d8b-ba7d-33709014d5b6
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
discoiquuid: ebcc91a5-be9e-4684-8146-d88f4013d4d1
translation-type: tm+mt
source-git-commit: 2ac4a59f1af46cfb1cae8cda3c24e217620cec70

---


# Evaluation Phase {#evaluation}

Once you click **[!UICONTROL Start Update]**, the first phase in Product Update Wizard is the Evaluation phase. In dieser Phase können Sie die Komplexität der Aktualisierung mit dem Mustererkennungsprogramm bewerten, auf das Sie direkt über den Assistenten zugreifen können. Am Ende dieses Schrittes haben Sie Zugriff auf den Bewertungsbericht.

Der generierte Bericht ermöglicht es Ihnen, die Autoreninstanz zur Upgradbarkeit zu prüfen, indem Muster erkannt werden, die:

* Verletzen Sie bestimmte Regeln und werden sie in Bereichen durchgeführt, die durch die Aktualisierung betroffen oder überschrieben werden.

* Verwenden Sie eine AEM 6. x-Funktion oder eine API, die nicht auf dem neuen AEM abwärtskompatibel ist und möglicherweise nach der Aktualisierung umgebrochen wird.


Dies dient als Beurteilung des Entwicklungsaufwands, der bei der Aktualisierung auf Adobe Experience Manager (AEM) 6.5 beteiligt ist.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Führen Sie die folgenden Schritte aus, um den Bewertungsfaktor auszuführen:

1. Select **[!UICONTROL Run Evaluation]** to run the pattern detector.

   >[!NOTE]
   >Der Musterbildschirm kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und zu vermeiden, dass wichtige Geschäftskritische Instanzen auftreten, führt Cloud Manager diese in der Staging-Umgebung auf der Autoreninstanz aus.

   ![](assets/Run-Evaluation.png)

1. Der Assistent informiert Sie über den Status Ihrer Aktion. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

   Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy of the evaluation report.

   ![](assets/Evaluation-1.png)

   Sie können die aktualisierten Pulse-Benachrichtigungen als Statusaktualisierungen anzeigen.

   ![](assets/Evaluation-pulse-notification.png)

>[!NOTE]
>The other four phases succeeding **Evaluation** namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon and are not available in the current release.
