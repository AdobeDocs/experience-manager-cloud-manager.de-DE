---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Ausführen, Bearbeiten und Löschen.
exl-id: e36420d2-57c5-4375-99fb-dd47c1c8bffd
source-git-commit: d4a7d9ab72947b97b0dabb2f822ef268e4972685
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 61%

---


# Verwalten von Pipelines {#managing-pipelines}

Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Ausführen, Bearbeiten und Löschen.

## Pipeline-Karte {#pipeline-card}

Die Karte **Pipelines** auf der Seite **Programmübersicht** in Cloud Manager bietet Ihnen einen Überblick über alle Ihre Pipelines und deren aktuellen Status.

![Pipelines-Karte in Cloud Manager](/help/assets/configure-pipelines/pipelines-card.png)

Durch Klicken auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Auslassungspunkte neben jeder Pipeline können Sie die folgenden Aktionen ausführen:

* [Ausführen der Pipeline](#running-pipelines) 
* [Bearbeiten der Pipeline](#editing-pipelines)
* [Löschen der Pipeline](#deleting-pipelines)
* [Anzeigen von Details](#view-details)

Am Ende der Pipeline-Liste befinden sich die folgenden allgemeinen Optionen:

* **Hinzufügen**: Dient zum [Hinzufügen einer neuen Produktions-Pipeline](/help/using/production-pipelines.md) oder [Hinzufügen einer neuen produktionsfremden Pipeline](/help/using/non-production-pipelines.md).
* **Alle anzeigen**: Leitet weiter zum Bildschirm **Pipelines**, wo alle Pipelines in einer detaillierteren Tabelle angezeigt werden.
* **Auf Repository-Informationen zugreifen**: Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind.
* **Weitere Infos**: Navigiert zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Seite „Pipelines“ {#pipelines}

Die Seite **Pipelines** zeigt eine vollständige Liste aller Pipelines für das ausgewählte Programm an. Dies ist nützlich, da es umfassendere Informationen enthält als der Abschnitt [Pipeline-Karte](#pipeline-card).

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Pipelines**, um zur Seite **Pipelines** zu wechseln.

1. Hier können Sie eine Liste aller Pipelines für das Programm sehen und die Ausführung von Pipelines starten und stoppen, wie Sie es in der **Pipelines-Karte** tun würden.

Durch Klicken auf das Symbol `i` erhalten Sie Details über die letzte oder aktuelle Ausführung der Pipeline.

![Details zur Pipeline-Ausführung](/help/assets/configure-pipelines/pipeline-status.png)

Klicken Sie auf **Details anzeigen**, um zu den [Details zur Pipeline-Ausführung](#view-details) zu gelangen.

## Seite „Aktivität“ {#activity}

Die Seite **Aktivität** zeigt eine vollständige Liste aller Pipeline-Ausführungen für das ausgewählte Programm an.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Aktivität**, um zur Seite **Aktivität** zu wechseln.

1. Hier sehen Sie eine Liste aller Pipeline-Ausführungen für das Programm, einschließlich aktueller und vorheriger Ausführungen.

Durch Klicken auf das Symbol `i` werden Details zur Ausführung des ausgewählten Pipeline-Laufs angezeigt.

![Details zur Pipeline-Ausführung](/help/assets/configure-pipelines/pipeline-activity.png)

Klicken Sie auf **Details anzeigen**, um die [Details zur Pipeline-Ausführung](#view-details) zu überprüfen.

## Ausführen einer Pipeline {#run-one-pipeline}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.
1. Klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Auslassungszeichen neben der Pipeline, die Sie ausführen, und dann auf **Ausführen**.

   Die Statusspalte gibt an, wann die Pipeline-Ausführung beginnt.

   Sie können die Details der Ausführung sehen, indem Sie erneut auf ![Mehr-Symbol, ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)) und auf **[Details anzeigen](#view-details)** klicken.

   Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf ![Mehr-Symbol, ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und auf **Abbrechen** klicken.

## Mehrere Pipelines ausführen {#run-multiple-pipelines}

Mit Cloud Manager können Sie mehrere Pipelines gleichzeitig ausführen, was die Bereitstellungseffizienz für Adobe Managed Services (AMS)-Kunden verbessert. Mit **Funktion „Ausgewählte** ausführen“ können Sie mehrere Pipelines auswählen und Trigger für ihre gleichzeitige Ausführung einrichten. Dies reduziert den manuellen Aufwand, der mit der individuellen Ausführung von Pipelines verbunden ist, und optimiert Build- und Bereitstellungs-Workflows.

**So führen Sie mehrere Pipelines aus:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Klicken Sie im Menü links auf ![Workflow-Symbol ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg)Pipelines ****.
1. Aktivieren Sie in der Tabelle auf **Seite**Pipeline) die Kontrollkästchen neben den Pipelines, die Sie ausführen möchten.
Klicken Sie bei Bedarf auf ![Filtersymbol, ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Filter_18_N.svg)**Filter**, um Pipelines nach Name, Umgebung oder bereitgestelltem Code-Typ oder einer Kombination aus allen drei Typen zu sortieren.
1. Klicken Sie oben rechts auf der Seite auf **Ausgewählte ausführen (x)**.
1. Klicken **im Dialogfeld „Ausgewählte Pipelines ausführen (x** auf **Ausführen (x)**.

   Die Schaltfläche **Ausführen** gibt die Anzahl der Pipelines an, die fortgesetzt werden können. Sie haben beispielsweise vier Pipelines ausgewählt, von denen jedoch eine bereits ausgeführt wird. Oder es existiert keine mit einer ausgewählten Pipeline verknüpfte Umgebung mehr. In solchen Fällen passt sich das System entsprechend an. Die Schaltfläche wird in „Ausführen (3)“ aktualisiert, um anzugeben, dass drei Pipelines fortgesetzt werden können.

1. Pipelines werden ausgeführt und ihr Status wird in der Liste **Pipelines** aktualisiert.

## Bearbeiten von Pipelines {#editing-pipelines}

Eine Pipeline, die ausgeführt wird, können Sie nicht bearbeiten.

**So bearbeiten Sie Pipelines:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der **Programmübersicht** zur Karte **Pipelines**.

1. Klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Auslassungszeichen neben der Pipeline, die Sie bearbeiten möchten, und dann auf **Bearbeiten**.

1. Im Dialogfeld **Produktions-Pipeline bearbeiten** oder **Produktionsfremde Pipeline bearbeiten** können Sie die Details bearbeiten, die Sie bei der Pipeline-Erstellung eingegeben haben.

   Weitere Informationen zu den Feldern und Konfigurationsoptionen für Pipelines finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md) und [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

1. Wenn Sie fertig sind, klicken Sie **Aktualisieren**.

## Löschen von Pipelines {#deleting-pipelines}

Pipelines, die gerade ausgeführt werden, können nicht gelöscht werden.

**So löschen Sie Pipelines:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der **Programmübersicht** zur Karte **Pipelines**.

1. Klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Auslassungszeichen neben der Pipeline, die Sie ausführen, und dann auf **Löschen**.


## Pipeline-Details anzeigen {#view-details}

Sie können nur Details einer Pipeline anzeigen, die gerade ausgeführt wird oder schon mindestens einmal ausgeführt worden ist.

**So zeigen Sie Pipeline-Details an:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie auf der **Programmübersicht** zur Karte **Pipelines**.

1. Klicken Sie auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) Auslassungszeichen neben der Pipeline, die Sie ausführen, und dann auf **Details anzeigen**.

1. Sie gelangen zur Detailseite der Pipeline, die gerade ausgeführt wird.

![Pipeline-Details](/help/assets/configure-pipelines/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline einsehen und Build-Protokolle zu Diagnosezwecken abrufen. Weitere Informationen finden Sie im Dokument [Bereitstellung von Code](/help/using/code-deployment.md).

Es werden alle Schritte einer Pipeline-Ausführung angezeigt, wobei die Schritte, die noch nicht gestartet wurden, ausgegraut sind. Die abgeschlossenen Schritte werden mit ihrer jeweiligen Dauer angezeigt.

Wenn ein Pipeline-Schritt abgeschlossen ist, wird eine Zusammenfassung angezeigt.

![Schrittzusammenfassung](/help/assets/configure-pipelines/pipeline-step.png)

Klicken Sie auf den Link **Details anzeigen**, um den Abschnitt **Dauer** anzuzeigen. Dieser Abschnitt umfasst die durchschnittliche Dauer der Pipeline basierend auf dem Verlaufs-Trend für dieses Programm.

![Dauer](/help/assets/configure-pipelines/duration.png)

Wenn Ihre Pipeline einen Schritt **Code-Überprüfung** enthält, der Probleme verursacht hat, können Sie auf **Details herunterladen** klicken, um eine Liste der [Code-Qualitätstests](/help/using/code-quality-testing.md) anzuzeigen, die nicht bestanden wurden.

![Fehler bei der Code-Qualität](assets/managing-pipelines-code-quality-issues.png)

In der CSV-Datei ist eine Spalte **Speicherort der Projektdatei** verfügbar, die den Speicherort des fehlerhaften Codes angibt. Diese Spalte ist der projektrelative Pfad, während die Spalte **Dateispeicherort** von Maven generiert wird.

![Details zu Problemen beim Scannen des Projekt-Codes](assets/managing-pipelines-code-quality-details.png)
