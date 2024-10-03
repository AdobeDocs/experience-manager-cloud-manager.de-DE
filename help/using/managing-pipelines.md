---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Ausführen, Bearbeiten und Löschen.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: 9d910e1b1a4aad000a8389ddc22ce380bbccd4ef
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 89%

---


# Verwalten von Pipelines {#managing-pipelines}

Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Ausführen, Bearbeiten und Löschen.

## Pipeline-Karte {#pipeline-card}

Die Karte **Pipelines** auf der Seite **Programmübersicht** in Cloud Manager bietet Ihnen einen Überblick über alle Ihre Pipelines und deren aktuellen Status.

![Pipelines-Karte in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Wenn Sie auf die Schaltfläche mit den Auslassungspunkten neben den einzelnen Pipelines klicken, können Sie die folgenden Aktionen ausführen:

* [Ausführen der Pipeline](#running-pipelines) 
* [Bearbeiten der Pipeline](#editing-pipelines)
* [Löschen der Pipeline](#deleting-pipelines)
* [Anzeigen von Details](#view-details)

Am Ende der Pipeline-Liste befinden sich die folgenden allgemeinen Optionen:

* **Hinzufügen**: Dient zum [Hinzufügen einer neuen Produktions-Pipeline](/help/using/production-pipelines.md) oder [Hinzufügen einer neuen produktionsfremden Pipeline](/help/using/non-production-pipelines.md).
* **Alle anzeigen**: Leitet weiter zum Bildschirm **Pipelines**, wo alle Pipelines in einer detaillierteren Tabelle angezeigt werden.
* **Auf Repository-Informationen zugreifen**: Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind.
* **Weitere Infos**: Navigiert zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Pipelines-Seite {#pipelines}

Auf der Seite **Pipelines** wird eine vollständige Liste aller Pipelines für das ausgewählte Programm angezeigt. Dies ist nützlich, da es umfassendere Informationen enthält als der Abschnitt [Pipeline-Karte](#pipeline-card).

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Pipelines** , um zur Seite **Pipelines** zu wechseln.

1. Hier können Sie eine Liste aller Pipelines für das Programm sehen und die Ausführung von Pipelines starten und stoppen, wie Sie es in der **Pipelines-Karte** tun würden.

Durch Klicken auf das Symbol `i` erhalten Sie Details über die letzte oder aktuelle Ausführung der Pipeline.

![Details zur Pipeline-Ausführung](/help/assets/configure-pipelines/pipeline-status.png)

Klicken Sie auf **Details anzeigen**, um zu den [Details zur Pipeline-Ausführung](#view-details) zu gelangen.

## Aktivitätsseite {#activity}

Die Seite **Aktivitäten** enthält eine vollständige Liste aller Pipelines, die für das ausgewählte Programm ausgeführt werden.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Aktivität** , um zur Seite **Aktivität** zu wechseln.

1. Hier sehen Sie eine Liste aller Pipeline-Ausführungen für das Programm, einschließlich aktueller und vorheriger Ausführungen.

Durch Klicken auf das Symbol `i` werden Details zur Ausführung des ausgewählten Pipeline-Laufs angezeigt.

![Details zur Pipeline-Ausführung](/help/assets/configure-pipelines/pipeline-activity.png)

Klicken Sie auf **Details anzeigen**, um die [Details zur Pipeline-Ausführung](#view-details) zu überprüfen.

## Ausführen von Pipelines {#running-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.
1. Klicken Sie auf die auf die Schaltfläche mit den Auslassungspunkten neben der von Ihnen ausgeführten Pipeline und wählen Sie dann im Menü die Option **Ausführen** aus.

   Die Statusspalte gibt an, wann die Pipeline-Ausführung beginnt.

   Sie können die Details der Ausführung sehen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **[Details anzeigen](#view-details)** auswählen.

   Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf die Schaltfläche mit den Auslassungspunkten klicken und **Abbrechen** auswählen.

## Bearbeiten von Pipelines {#editing-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der Pipeline, die Sie bearbeiten möchten, und wählen Sie dann im Menü die Option **Bearbeiten** aus.

1. Das Dialogfeld **Produktions-Pipeline bearbeiten** oder **Nicht-Produktions-Pipeline bearbeiten** wird angezeigt. Sie können dieselben Details bearbeiten, die Sie während der Pipeline-Erstellung eingegeben haben.

   Weitere Informationen zu den Feldern und Konfigurationsoptionen für Pipelines finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

1. Klicken Sie auf **Aktualisieren**, wenn Sie fertig sind.

>[!NOTE]
>
>Pipelines, die gerade ausgeführt werden, können nicht bearbeitet werden.

## Löschen von Pipelines {#deleting-pipelines}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der von Ihnen ausgeführten Pipeline und wählen Sie dann im Menü die Option **Löschen** aus.

>[!NOTE]
>
>Pipelines, die gerade ausgeführt werden, können nicht gelöscht werden.

## Anzeigen von Details {#view-details}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der von Ihnen ausgeführten Pipeline und wählen Sie dann im Menü die Option **Anzeigen** aus.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

![Pipeline-Details](/help/assets/configure-pipelines/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Weitere Informationen finden Sie im Dokument [Bereitstellung von Code](/help/using/code-deployment.md).

Es werden alle Schritte einer Pipeline-Ausführung angezeigt, wobei die Schritte, die noch nicht gestartet wurden, ausgegraut sind. Die abgeschlossenen Schritte werden mit ihrer jeweiligen Dauer angezeigt.

Wenn ein Pipeline-Schritt abgeschlossen ist, wird eine Zusammenfassung angezeigt.

![Schrittzusammenfassung](/help/assets/configure-pipelines/pipeline-step.png)

Klicken Sie auf den Link **Details anzeigen**, um den Abschnitt **Dauer** anzuzeigen. Dieser Abschnitt umfasst die durchschnittliche Dauer der Pipeline basierend auf dem Verlaufs-Trend für dieses Programm.

![Dauer](/help/assets/configure-pipelines/duration.png)

Wenn Ihre Pipeline den Schritt **Code-Scan** umfasst hat, durch den Probleme aufgetreten sind, können Sie auf die Schaltfläche **Details herunterladen** klicken, um eine Liste von [Code-Qualitätstests](/help/using/code-quality-testing.md) anzuzeigen, die nicht bestanden wurden.

![Fehler bei der Code-Qualität](assets/managing-pipelines-code-quality-issues.png)

In der CSV-Datei ist eine Spalte **Speicherort der Projektdatei** verfügbar, die den Speicherort des fehlerhaften Codes angibt. Diese Spalte ist der projektrelative Pfad, während die Spalte **Dateispeicherort** von Maven generiert wird.

![Details zu Problemen beim Scannen des Projekt-Codes](assets/managing-pipelines-code-quality-details.png)


>[!NOTE]
>
>Sie können nur Details einer Pipeline anzeigen, die gerade ausgeführt wird oder schon mindestens einmal ausgeführt worden ist.
