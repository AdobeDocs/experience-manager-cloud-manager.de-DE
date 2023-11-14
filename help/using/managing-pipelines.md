---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 28ab641ec85335d8330aeb465c07bf0264218fe4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 67%

---


# Verwalten von Pipelines {#managing-pipelines}

Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.

## Pipeline-Karte {#pipeline-card}

Die Karte **Pipelines** auf der Seite **Programmübersicht** in Cloud Manager bietet Ihnen einen Überblick über alle Ihre Pipelines und deren aktuellen Status.

![Pipelines-Karte in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Wenn Sie auf die Schaltfläche mit den Auslassungspunkten neben jeder Pipeline klicken, können Sie die folgenden Aktionen ausführen.

* [Pipeline ausführen](#running-pipelines)
* [Pipeline bearbeiten](#editing-pipelines)
* [Pipeline löschen](#deleting-pipelines)
* [Details anzeigen](#view-details)

Am Ende der Pipeline-Liste befinden sich allgemeine Optionen.

* **Hinzufügen**: Dient zum [Hinzufügen einer neuen Produktions-Pipeline](/help/using/production-pipelines.md) oder [Hinzufügen einer neuen produktionsfremden Pipeline](/help/using/non-production-pipelines.md)
* **Alle anzeigen**: Leitet den Anwender zum Bildschirm **Pipelines**, wo alle Pipelines in einer detaillierteren Tabelle angezeigt werden
* **Zugriff auf Repo Info**: Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind
* **Weitere Infos**: Navigiert zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Pipelines Window {#pipelines}

Die **Pipelines** zeigt eine vollständige Liste aller Pipelines für das ausgewählte Programm an. Dies ist nützlich, da es umfassendere Informationen enthält, als im Abschnitt [Pipeline-Karte.](#pipeline-card)

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Aus dem **Programmübersicht** Seite, tippen oder klicken Sie auf **Pipelines** Registerkarte, um zu der **Pipelines** Fenster.

1. Hier sehen Sie eine Liste aller Pipelines für das Programm sowie die Ausführung der Pipeline wie im **Pipelines Card**.

Wenn eine Pipeline ausgeführt wird, bewegen Sie den Mauszeiger über die **Status** enthält Details zur Ausführung.

![Details zur Pipelineausführung](/help/assets/configure-pipelines/pipeline-status.png)

Tippen oder Klicken **Details anzeigen** bringt Sie zu [Details zur Pipelineausführung.](#view-details)

## Aktivitätsfenster {#activity}

Die **Tätigkeiten** zeigt eine vollständige Liste aller Pipelines-Ausführungen für das ausgewählte Programm an.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Aus dem **Programmübersicht** Seite, tippen oder klicken Sie auf **Aktivität** Registerkarte, um zu der **Aktivität** Fenster.

1. Hier sehen Sie eine Liste aller Pipeline-Ausführungen für das Programm, einschließlich aktueller und historischer Ausführungen.

Wenn eine Pipeline ausgeführt wird, bewegen Sie den Mauszeiger über die **Status** enthält Details zur Ausführung.

![Details zur Pipelineausführung](/help/assets/configure-pipelines/pipeline-activity.png)

Tippen oder Klicken **Details anzeigen** bringt Sie zu [Details zur Pipelineausführung.](#view-details)

## Ausführen von Pipelines {#running-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie ausführen, und wählen Sie im Menü **Ausführen** aus.

1. Der Pipeline-Ausführung beginnt und wird durch die Spalte **Status** angezeigt.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **[Details anzeigen](#view-details)** auswählen.

Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **Abbrechen** auswählen.

## Bearbeiten von Pipelines {#editing-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie bearbeiten möchten, und wählen Sie im Menü **Bearbeiten** aus.

1. Daraufhin wird das Dialogfeld **Produktions-Pipeline bearbeiten** oder **Produktionsfremde Pipeline bearbeiten** angezeigt, sodass Sie die Details bearbeiten können, die Sie beim Erstellen der Pipeline eingegeben haben.

   * Auf den folgenden Seiten finden Sie Details zu allen Feldern und Konfigurationsoptionen, die für Pipelines verfügbar sind.
      * [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md)
      * [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md)

1. Klicken Sie auf **Aktualisieren**, nachdem Sie die Pipeline bearbeitet haben.

>[!NOTE]
>
>Pipelines, die gerade ausgeführt werden, können nicht bearbeitet werden.

## Löschen von Pipelines {#deleting-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie löschen möchten, und wählen Sie im Menü **Löschen** aus.

>[!NOTE]
>
>Pipelines, die gerade ausgeführt werden, können nicht gelöscht werden.

## Details anzeigen {#view-details}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie ausführen, und wählen Sie **Details anzeigen** aus dem Menü.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

![Pipeline-Details](/help/assets/configure-pipelines/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Weitere Informationen finden Sie im Dokument [Bereitstellung von Code](/help/using/code-deployment.md).

Alle Schritte in einer Pipeline-Ausführung werden angezeigt, wobei die Schritte, die noch nicht gestartet wurden, ausgegraut sind. Die abgeschlossenen Schritte zeigen ihre Dauer an.

Sobald ein Pipeline-Schritt abgeschlossen ist, wird eine Zusammenfassung angezeigt.

![Schrittzusammenfassung](/help/assets/configure-pipelines/pipeline-step.png)

Tippen oder klicken Sie auf **Details anzeigen** -Link, um die **Dauer** Abschnitt. Dies umfasst die durchschnittliche Dauer der Pipeline basierend auf dem historischen Trend für dieses Programm.

![Dauer](/help/assets/configure-pipelines/duration.png)

>[!NOTE]
>
>Sie können nur Details einer Pipeline anzeigen, die gerade ausgeführt wird oder mindestens einmal ausgeführt worden ist.
