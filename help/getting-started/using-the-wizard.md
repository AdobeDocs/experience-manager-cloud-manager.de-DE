---
title: Verwenden des Assistenten für neue Projekte
description: Auf dieser Seite erfahren Sie, wie Sie mit dem Assistenten ein AEM-Anwendungsprojekt erstellen.
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
TQID: https://experienceleague.adobe.com/zoiHL1lNC2XN-T9g0dh3pQyL4Yw3uYgFpHs8d6hkj3M
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
source-git-commit: fa6be369b979682cebf68852603725d8754605ab
workflow-type: tm+mt
source-wordcount: 317
ht-degree: 54%

---

# Verwenden des Assistenten für neue Projekte {#using-the-wizard}

Wenn Sie als Neukunde ein Onboarding für Cloud Manager durchführen, erhalten Sie ein leeres Git-Repository. Cloud Manager bietet einen Assistenten zum Erstellen eines AEM-Projekts auf der Grundlage des [AEM-Projektarchetyps](https://github.com/adobe/aem-project-archetype) als Ausgangspunkt.

**So verwenden Sie den Assistenten für neue Projekte:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Sofern noch nicht geschehen, [erstellen Sie Ihr Programm](program-setup.md). Beim Erstellen des Programms erkennt Cloud Manager, dass das Repository nicht eingerichtet ist. Auf dem Bildschirm **Übersicht** wird dann eine spezielle Eingabeaufforderungskarte angezeigt.

   ![Erstellen des Projekt-CTA](/help/assets/image2018-10-3_14-29-44.png)

1. Klicken Sie auf **Erstellen**, um den Assistenten zu starten und wichtige Informationen anzugeben.

   * **Titel**: Der Titel des Projekts. Standardmäßig ist dieser auf den Namen des Programms gesetzt.
   * **Neuer Verzweigungsname** - Die erste Verzweigung Ihres Git-Repositorys. Standardmäßig ist dies `main`.

   ![Projektwerte](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Das Dialogfeld enthält einen Abschnitt, den Sie durch Klicken auf das Symbol unten anzeigen können. Das erweiterte Dialogfeld zeigt alle Konfigurationsparameter für den AEM-Projektarchetyp an. Diese Parameter haben Standardwerte, die auf Grundlage des von Ihnen bereits angegebenen **Titels** generiert werden und nicht geändert werden müssen. Sie werden hier zu Ihrer Information erläutert.

   ![Detaillierte Archetypparameter](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klicken Sie auf **Erstellen**, um das Starterprojekt unter Verwendung des Archetyps zu erstellen und in die benannte Git-Verzweigung zu übertragen.

Sie verfügen nun über ein Basisprojekt. Sie können jetzt Ihre Pipelines konfigurieren.

## Bestehende oder migrierende Kundinnen und Kunden {#existing-migrating}

Wenn Sie ein aktueller Kunde von Adobe Managed Services (AMS) oder ein lokaler Kunde von AEM sind, der migriert, befindet sich der Projekt-Code bereits in Git oder einem anderen Versionskontrollsystem.

In solchen Fällen ist es möglich, das Projekt in das Git-Repository von Cloud Manager zu importieren.
