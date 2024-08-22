---
title: Verwenden des Assistenten für neue Projekte
description: Auf dieser Seite erfahren Sie, wie Sie mit dem Assistenten ein AEM-Programmprojekt erstellen
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 28%

---


# Verwenden des Assistenten für neue Projekte {#using-the-wizard}

Als Sie als neuer Kunde in Cloud Manager integriert wurden, wurde Ihnen ein leeres Git-Repository bereitgestellt. Um Ihnen die ersten Schritte zu erleichtern, bietet Cloud Manger einen Assistenten zum Erstellen eines minimalen AEM-Projekts auf der Grundlage des [AEM-Projektarchetypen](https://github.com/adobe/aem-project-archetype) als Startpunkt.

Führen Sie diese Schritte aus, um mithilfe des Assistenten ein AEM-Projekt zu erstellen.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Falls noch nicht geschehen, erstellen Sie [Ihr Programm](program-setup.md). Wenn das Programm erstellt wird, erkennt Cloud Manager, dass die Repositorys noch nicht eingerichtet sind. Eine spezielle Aktionsaufruffunktion wird dann auf dem Bildschirm **Überblick** angezeigt.

   ![Erstellen des Projekt-CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Klicken Sie auf **Erstellen**, um den Assistenten zu starten und wichtige Informationen anzugeben.

   * **Titel** - Der Titel des Projekts. Standardmäßig ist er auf den Namen des Programms gesetzt.
   * **Neuer Verzweigungsname** - Die erste Verzweigung Ihrer Git-Repositorys. Standardmäßig ist dies `main`.

   ![Projektwerte](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Das Dialogfeld verfügt über eine Schublade, die durch Klicken auf den Ziehpunkt am unteren Rand geöffnet werden kann. Im erweiterten Formular werden im Dialogfeld alle Konfigurationsparameter für den AEM Projektarchetyp angezeigt. Diese Parameter verfügen über Standardwerte, die basierend auf dem bereits bereitgestellten **Titel** generiert werden und keine Änderungen erfordern. Sie werden hier zu Ihrer Information erläutert.

   ![Detaillierte Archetypparameter](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klicken Sie auf **Erstellen** , um das Starterprojekt mithilfe des Archetyps zu erstellen und in die benannte Git-Verzweigung zu übertragen.

Sie haben jetzt ein Basisprojekt. Es ist Zeit, Ihre Pipelines einzurichten.

## Bestehende oder migrierende Kunden {#existing-migrating}

Wenn Sie aktuell Adobe Managed Services (AMS)-Kunde oder On-Premise-AEM-Kunde sind, der zu migriert, verfügen Sie wahrscheinlich bereits über Projektcode in Git oder einem anderen Versionskontrollsystem.

In solchen Fällen können Sie Ihr Projekt in das Cloud Manager-Git-Repository importieren.
