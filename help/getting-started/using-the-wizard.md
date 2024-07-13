---
title: Verwenden des Assistenten für neue Projekte
description: Auf dieser Seite erfahren Sie, wie Sie mit dem Assistenten ein AEM-Programmprojekt erstellen
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 100%

---


# Verwenden des Assistenten für neue Projekte {#using-the-wizard}

Wenn Sie als neuer Kunde ein Onboarding für Cloud Manager durchlaufen, erhalten Sie ein leeres Git-Repository. Um Ihnen die ersten Schritte zu erleichtern, bietet Cloud Manger einen Assistenten zum Erstellen eines minimalen AEM-Projekts auf der Grundlage des [AEM-Projektarchetypen](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) als Startpunkt.

Führen Sie diese Schritte aus, um mithilfe des Assistenten ein AEM-Projekt zu erstellen.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Falls noch nicht geschehen, [erstellen Sie Ihr Programm.](program-setup.md) Nachdem das Programm erstellt wurde, erkennt Cloud Manager, dass die Repositorys noch nicht eingerichtet sind, und eine spezielle Karte mit einer Handlungsaufforderung wird auf dem Bildschirm **Übersicht** angezeigt.

   ![Erstellen des Projekt-CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Klicken Sie auf **Erstellen**, um den Assistenten zu starten und wichtige Informationen anzugeben.

   * **Titel**: Dies ist der Titel des Projekts und standardmäßig auf den Namen des Programms festgelegt.
   * **Neuer Verzweigungsname**: Dies ist die erste Verzweigung Ihrer Git-Repositorys und sie ist standardmäßig auf `main` festgelegt.

   ![Projektwerte](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Sie können den Dialogfeld über einen Ziehpunkt am unteren Rand des Dialogfelds erweitern. Der erweiterte Dialogfeld zeigt alle Konfigurationsparameter für den AEM-Projektarchetyp an. Diese Parameter haben Standardwerte, die auf der Grundlage des von Ihnen bereits angegebenen **Titels** generiert werden und nicht geändert werden müssen. Sie werden hier zu Ihrer Information erläutert.

   ![Detaillierte Archetypparameter](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klicken Sie auf **Erstellen**, um das Starterprojekt unter Verwendung des Archetyps zu erstellen und in die benannte Git-Verzweigung zu übertragen.

Sie haben jetzt ein Basisprojekt! Jetzt können Sie Ihre Pipelines einrichten.

## Bestehende oder migrierende Kunden {#existing-migrating}

Wenn Sie ein aktueller Kunde von Adobe Managed Services (AMS) oder ein On-Premise-Kunde von AEM sind, der zu AMS migriert, haben Sie wahrscheinlich bereits Projekt-Code in Git oder einem anderen Versionskontrollsystem.

In solchen Fällen importieren Sie Ihr Projekt in das Git-Repository von Cloud Manager.
