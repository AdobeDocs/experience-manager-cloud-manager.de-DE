---
title: Verwenden des Assistenten für neue Projekte
description: Auf dieser Seite erfahren Sie, wie Sie mit dem Assistenten ein AEM-Anwendungsprojekt erstellen
exl-id: 9d7c6f4c-9379-471c-8dad-772a7099da54
source-git-commit: cb791a4f148ba394687b5e824b75fe1386d83c18
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 9%

---


# Verwenden des Assistenten für neue Projekte {#using-the-wizard}

Wenn Sie Cloud Manager als neuer Kunde integrieren, erhalten Sie ein leeres Git-Repository. Um Ihnen die ersten Schritte zu erleichtern, bietet Cloud Manager einen Assistenten, mit dem Sie ein AEM Projekt erstellen können, das auf der [AEM Projektarchetyp](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype) als Ausgangspunkt.

Führen Sie diese Schritte aus, um ein AEM Projekt mithilfe des Assistenten zu erstellen.

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Falls noch nicht geschehen, [Erstellen Sie Ihr Programm.](program-setup.md) Nachdem das Programm erstellt wurde, erkennt Cloud Manager, dass die Repositorys noch nicht eingerichtet sind, und eine spezielle Aktionsaufruftkarte wird auf der Seite **Übersicht** angezeigt.

   ![Projekt-CTA erstellen](/help/assets/image2018-10-3_14-29-44.png)

1. Klicken **Erstellen** um den Assistenten zu starten und wichtige Werte anzugeben.

   * **Titel** - Dies ist der Titel des Projekts und standardmäßig auf den Namen des Programms festgelegt.
   * **Neuer Verzweigungsname** - Dies ist die erste Verzweigung Ihrer Git-Repositorys und standardmäßig wird `main`.

   ![Projektwerte](/help/assets/screen_shot_2018-10-08at55825am.png)

1. Das Dialogfeld verfügt über eine Schublade, die durch Klicken auf den Ziehpunkt am unteren Rand geöffnet werden kann. In seiner erweiterten Form zeigt das Dialogfeld alle Konfigurationsparameter für den AEM Projektarchetyp an. Diese Parameter verfügen über Standardwerte, die basierend auf der Variablen **Titel** Sie haben bereits bereitgestellt und müssen nicht geändert werden. Sie werden hier für Ihre Informationen erklärt.

   ![Detaillierte Archetypparameter](/help/assets/screen_shot_2018-10-08at60032am.png)

1. Klicken **Erstellen** , um das Starterprojekt mithilfe des Archetyps zu erstellen und in die benannte Git-Verzweigung zu übertragen.

Sie haben jetzt ein Basisprojekt! Jetzt können Sie Ihre Pipelines einrichten.

## Bestehende oder migrierende Kunden {#existing-migrating}

Wenn Sie aktuell Adobe Managed Services (AMS)-Kunde oder On-Premise-AEM-Kunde sind, der zu migriert, verfügen Sie wahrscheinlich bereits über Projektcode in Git oder einem anderen Versionskontrollsystem.

In solchen Fällen importieren Sie Ihr Projekt in das Git-Repository von Cloud Manager.
