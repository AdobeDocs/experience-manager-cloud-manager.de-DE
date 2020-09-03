---
title: Verwenden des Assistenten
description: Auf dieser Seite erfahren Sie, wie Sie mit dem Assistenten ein AEM Application Project erstellen
translation-type: tm+mt
source-git-commit: 7146a41d64365c9de03d32f4fc4c33f9e366c244
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 93%

---


# Verwenden des Assistenten {#using-wizard-to-create-an-aem-application-project}

Wenn Kunden Cloud Manager erstmals verwenden, erhalten sie ein leeres Git-Repository. Kunden, die bereits Adobe Managed Services (AMS) verwenden (oder ihre lokale AEM-Lösung zu AMS migrieren), verfügen im Allgemeinen bereits über Projektcode in Git (oder einem anderen Versionskontrollsystem) und importieren ihr Projekt in das Cloud Manager-Repository. Neue Kunden verfügen jedoch nicht über vorhandene Projekte.

Um neuen Kunden die ersten Schritte zu erleichtern, kann Cloud Manager jetzt als Ausgangspunkt ein minimales AEM-Projekt erstellen. Dieser Vorgang basiert auf dem [**AEM-Projektarchetyp**](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).


Gehen Sie wie folgt vor, um ein AEM-Anwendungsprojekt in Cloud Manager zu erstellen:

1. Wenn Sie sich bei Cloud Manager anmelden und die grundlegende Programmeinrichtung abgeschlossen haben und das Repository zu diesem Zeitpunkt leer ist, wird im Bildschirm **Überblick** eine spezielle Aktionskarte angezeigt.

   ![](assets/image2018-10-3_14-29-44.png)

1. Klicken Sie auf **Erstellen**, um einen Dialogfeld zu öffnen, in dem Sie die für den AEM-Projektarchetyp erforderlichen Parameter angeben. Der Dialogfeld fragt standardmäßig zwei Werte ab:

   * **Titel**: Hier ist standardmäßig der *Programmname* angegeben.

   * **Neuer Verzweigungsname**: Hier ist standardmäßig *Master* angegeben.

   ![](assets/screen_shot_2018-10-08at55825am.png)

   Sie können den Dialogfeld über einen Ziehpunkt am unteren Rand des Dialogfelds erweitern. Der erweiterte Dialogfeld zeigt alle Konfigurationsparameter für den Archetyp an. Viele dieser Parameter verfügen über Standardwerte, die basierend auf dem **Titel** erstellt werden.

   ![](assets/screen_shot_2018-10-08at60032am.png)

   >[!NOTE]
   >
   >Wenn der **Titel** beispielsweise ***We.Finance*** lautet, wird der Parameter „Base Maven Artifact ID“ als ***com.wefinance*** generiert. Diese Werte können bei Bedarf geändert werden.
   >
   >
   >Den generierten Wert ***com.wefinance*** können Sie zum Beispiel in ***net.wefinance*** ändern.

1. Klicken Sie im vorherigen Schritt auf **Erstellen**, um das Starterprojekt mit dem Archetyp zu erstellen und in die benannte Git-Verzweigung zu übertragen. Anschließend können Sie die Pipeline einrichten.