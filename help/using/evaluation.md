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
source-git-commit: 9e33b90818c686f0b7aacaf0955c3f2eba05488f

---


# Evaluation Phase {#evaluation}

The first phase in the Product Update wizard is **[!UICONTROL Evaluation]** phase.
Hier können Sie die Komplexität der Aktualisierung mit dem Mustererkennungsprogramm bewerten, auf das Sie direkt über den Assistenten zugreifen können. Am Ende dieses Schrittes haben Sie Zugriff auf den Bewertungsbericht.

Der generierte Bericht ermöglicht es Ihnen, die Autoreninstanz zur Upgradbarkeit zu prüfen, indem Muster erkannt werden, die:

* Verletzen Sie bestimmte Regeln und werden sie in Bereichen durchgeführt, die durch die Aktualisierung betroffen oder überschrieben werden.

* Verwenden Sie eine AEM 6. x-Funktion oder eine API, die nicht auf dem neuen AEM abwärtskompatibel ist und möglicherweise nach der Aktualisierung umgebrochen wird.

Dies dient als Beurteilung des Entwicklungsaufwands, der bei der Aktualisierung auf Adobe Experience Manager (AEM) 6.5 beteiligt ist.

>[!NOTE]
>To learn more about pattern detector, refer to [Assessing the Upgrade Complexity with the Pattern Detector](https://helpx.adobe.com/experience-manager/6-4/sites/deploying/using/pattern-detector.html)

## Running the Evaluator {#running-evaluator}

Gehen Sie wie folgt vor, um Bewertungsberichte zu erstellen:

1. Click on **[!UICONTROL Run Evaluation]**.

   >[!NOTE]
   >Der Musterbildschirm kann in einer beliebigen Umgebung ausgeführt werden. Um jedoch die Erkennungsrate zu erhöhen und zu vermeiden, dass wichtige Geschäftskritische Instanzen auftreten, führt Cloud Manager diese in der Staging-Umgebung auf der Autoreninstanz aus.

   ![](assets/Run-Evaluation.png)

1. Der Assistent informiert Sie über den Status Ihrer Aktion. You will notice **In progress** or **completed** as applicable when the evaluation report is being generated.

   Once the report is generated, you can click on **[!UICONTROL Download report]** to save a copy.

   ![](assets/Evaluation-1.png)


>[!NOTE]
>The current release of Product Update wizard in Cloud Manager supports the **Evaluation** phase only. The other four phases namely **Remediation**, **Execution**, **Validation**, and **Completion** are coming soon.
