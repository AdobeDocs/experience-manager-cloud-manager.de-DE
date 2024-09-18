---
title: Verwenden des Assistenten für neue Projekte
description: Auf dieser Seite erfahren Sie, wie Sie mit dem Assistenten ein AEM-Anwendungsprojekt erstellen.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: 7bc874a8dd14544c22201ef2c470faab84d31f8b
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---


# Verwenden des Assistenten für neue Projekte {#using-the-wizard}

Beim Neukunden-Onboarding für Cloud Manager haben Sie ein leeres Git-Repository erhalten. Um Ihnen die ersten Schritte zu erleichtern, bietet Cloud Manger einen Assistenten zum Erstellen eines minimalen AEM-Projekts auf der Grundlage des [AEM-Projektarchetypen](https://github.com/adobe/aem-project-archetype) als Startpunkt.

Führen Sie diese Schritte aus, um mithilfe des Assistenten ein AEM-Projekt zu erstellen.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Sofern noch nicht geschehen, [erstellen Sie Ihr Programm](program-setup.md). Wenn das Programm erstellt wird, erkennt Cloud Manager, dass die Repositorys noch nicht eingerichtet sind. Auf dem Bildschirm **Übersicht** wird dann eine spezielle Karte mit einem Aktionsaufruf angezeigt.

   ![Erstellen des Projekt-CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Klicken Sie auf **Erstellen**, um den Assistenten zu starten und wichtige Informationen anzugeben.

   * **Titel**: Der Titel des Projekts. Standardmäßig ist dieser auf den Namen des Programms gesetzt.
   * **Neuer Verzweigungsname**: Die erste Verzweigung Ihrer Git-Repositorys. Standardmäßig ist dies `main`.

   ![Projektwerte](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Sie können das Dialogfeld über einen Ziehpunkt am unteren Rand des Dialogfelds erweitern. Das erweiterte Dialogfeld zeigt alle Konfigurationsparameter für den AEM-Projektarchetyp an. Diese Parameter haben Standardwerte, die auf Grundlage des von Ihnen bereits angegebenen **Titels** generiert werden und nicht geändert werden müssen. Sie werden hier zu Ihrer Information erläutert.

   ![Detaillierte Archetypparameter](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klicken Sie auf **Erstellen**, um das Starterprojekt unter Verwendung des Archetyps zu erstellen und in die benannte Git-Verzweigung zu übertragen.

Sie verfügen nun über ein Basisprojekt. Jetzt ist es an Zeit, Ihre Pipelines einzurichten.

## Bestehende oder migrierende Kundinnen und Kunden {#existing-migrating}

Aktuelle Kundinnen oder Kunden von Adobe Managed Services (AMS) oder von AEM On-Premise, die zu AMS migrieren, haben wahrscheinlich bereits Projekt-Code in Git oder einem anderen Versionskontrollsystem.

In solchen Fällen ist es möglich, das Projekt in das Git-Repository von Cloud Manager zu importieren.
