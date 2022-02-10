---
title: Verwalten von Pipelines
description: Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.
index: true
source-git-commit: 099a4490e3a8578b9f3485fd1514d1e97db977ab
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 4%

---


# Verwalten von Pipelines {#managing-pipelines}

Erfahren Sie, wie Sie Ihre vorhandenen Pipelines verwalten, einschließlich Bearbeiten, Ausführen und Löschen.

## Pipeline-Karte {#pipeline-card}

Die **Pipelines** auf der Karte **Programmübersicht** -Seite in Cloud Manager bietet Ihnen einen Überblick über alle Ihre Pipelines und ihren aktuellen Status.

![Pipelines-Karte in Cloud Manager](/help/using/assets/configure-pipelines/pipelines-card.png)

Wenn Sie auf die Suchschaltfläche neben jeder Pipeline klicken, können Sie die folgenden Aktionen ausführen.

* [Pipeline ausführen](#running-pipelines)
* [Pipeline bearbeiten](#editing-pipelines)
* [Pipeline löschen](#deleting-pipelines)
* [Details anzeigen](#view-details)

Am unteren Rand der Pipelineliste befinden sich allgemeine Optionen.

* **Hinzufügen** - nach [Hinzufügen einer neuen Produktions-Pipeline](configuring-production-pipelines.md) oder [Neue produktionsfremde Pipeline hinzufügen](configuring-non-production-pipelines.md)
* **Alle anzeigen** - Leitet den Benutzer zum **Pipelines** angezeigt, um alle Pipelines in einer detaillierteren Tabelle anzuzeigen.
* **Zugriff auf Repo Info** - Zeigt die Informationen an, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlich sind
* **Weitere Infos** - Navigieren Sie zu den Dokumentationsressourcen zur CI/CD-Pipeline.

## Laufende Pipelines {#running-pipelines}

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie ausführen, und wählen Sie **Ausführen** aus dem Menü.

1. Der Pipeline-Lauf beginnt und wird durch die Variable **Status** Spalte.

Sie können die Details der Ausführung sehen, indem Sie erneut auf die Suchschaltfläche klicken und **[Details anzeigen.](#view-details)**

Je nach Pipeline-Typ können Sie die Ausführung möglicherweise abbrechen, indem Sie erneut auf die Suchschaltfläche klicken und auswählen **Abbrechen**.

## Bearbeiten von Pipelines {#editing-pipelines}

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie bearbeiten möchten, und wählen Sie **Bearbeiten** aus dem Menü.

1. Die **Produktions-Pipeline bearbeiten** oder **Bearbeiten von produktionsfremden Pipelines** angezeigt, sodass Sie dieselben Details bearbeiten können, die Sie beim Erstellen der Pipeline eingegeben haben.

   * Auf den folgenden Seiten finden Sie Details zu allen Feldern und Konfigurationsoptionen, die für Pipelines verfügbar sind.
      * [Konfigurieren von Produktions-Pipelines](configuring-production-pipelines.md)
      * [Konfigurieren von Nicht-Produktions-Pipelines](configuring-non-production-pipelines.md)

1. Klicken Sie auf **Aktualisieren**, nachdem Sie die Pipeline bearbeitet haben.

>[!NOTE]
>
>Eine laufende Pipeline kann nicht bearbeitet werden.

## Löschen von Pipelines {#deleting-pipelines}

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie ausführen, und wählen Sie **Löschen** aus dem Menü.

>[!NOTE]
>
>Eine laufende Pipeline kann nicht gelöscht werden.

## Details anzeigen {#view-details}

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** und klicken Sie auf die Suchschaltfläche neben der Pipeline, die Sie ausführen, und wählen Sie **Details anzeigen** aus dem Menü.

1. Sie gelangen zur Detailseite der laufenden Pipeline.

![Pipeline-Details](/help/using/assets/configure-pipelines/pipeline-running-details.png)

Von hier aus können Sie den Status der verschiedenen Schritte der Pipeline sehen und Build-Protokolle zu Diagnosezwecken abrufen. Siehe Dokument . [Bereitstellen des Codes](deploying-code.md) für weitere Informationen.

>[!NOTE]
>
>Sie können nur Details einer Pipeline anzeigen, die ausgeführt wird oder mindestens einmal ausgeführt wurde.
