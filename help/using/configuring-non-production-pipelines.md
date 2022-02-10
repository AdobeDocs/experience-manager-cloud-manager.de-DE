---
title: Konfigurieren von Nicht-Produktions-Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager Nicht-Produktions-Pipelines erstellen und konfigurieren können, um Ihren Code bereitzustellen.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 12%

---


# Konfigurieren von Nicht-Produktions-Pipelines {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager Nicht-Produktions-Pipelines erstellen und konfigurieren können, um Ihren Code bereitzustellen. Wenn Sie zunächst einen konzeptionellen Überblick darüber erhalten möchten, wie Pipelines in Cloud Manager funktionieren, finden Sie im Abschnitt [Dokumentation zur CI/CD-Pipeline](ci-cd-pipeline.md)

>[!NOTE]
>
>Informationen zum Konfigurieren von CI/CD-Pipelines für Cloud Manager in AEM as a Cloud Service finden Sie unter [die AEMaaCS-Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Übersicht {#understanding-the-flow}

Die **Bereitstellungsmanager** ist für die Einrichtung der Pipeline mithilfe der **Pipelines** -Kachel im [!UICONTROL Cloud Manager] Benutzeroberfläche.

Sie können zwei verschiedene Pipelinetypen erstellen.

* **Produktions-Pipelines** - Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die aus einer Reihe aufeinander abgestimmter Schritte besteht, um Quellcode vollständig in die Produktion zu übernehmen.
* **Nicht-Produktions-Pipelines** - Eine Nicht-Produktions-Pipeline dient hauptsächlich dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf produktionsfremde Pipelines. Weitere Informationen zum Konfigurieren von produktionsfremden Pipelines finden Sie im Dokument [Konfigurieren von Nicht-Produktions-Pipelines.](configuring-non-production-pipelines.md)

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Code-Qualitäts-Pipelines** - Diese führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und führen die Build- und Codequalitätsschritte aus.
* **Implementierungs-Pipelines** - Neben der Ausführung der Build- und Codequalitätsschritte wie der Code-Qualitäts-Pipelines stellen diese Pipelines den Code in einer Nicht-Produktionsumgebung bereit.

>[!NOTE]
>
>Eine Pipeline kann erst eingerichtet werden, wenn ihr verknüpftes Git-Repository mindestens eine Verzweigung aufweist und [Programmeinrichtung](setting-up-program.md) ist abgeschlossen. Siehe [Hinzufügen und Verwalten von Repositorys](cloud-manager-repositories.md), um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

## Video-Tutorial {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Hinzufügen einer produktionsfremden Pipeline {#add-non-production-pipeline}

Nachdem Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der Cloud Manager-Benutzeroberfläche verfügen, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie diese Schritte ausführen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte Pipelines über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **Hinzufügen** und wählen Sie **Hinzufügen einer produktionsfremden Pipeline**.

   ![Nicht-Produktions-Pipeline hinzufügen](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Im **Konfiguration** des **Hinzufügen einer produktionsfremden Pipeline** wählen Sie den Pipeline-Typ aus, den Sie erstellen möchten, entweder eine **Code-Qualitäts-Pipeline** oder **Bereitstellungs-Pipeline**.


   ![Pipeline-Typ auswählen](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. Geben Sie eine Beschreibung für Ihre Pipeline im **Name der produktionsfremden Pipeline** -Feld.

1. Wenn Sie eine **Bereitstellungs-Pipeline**, wählen Sie die Zielbereitstellungsumgebung aus dem **Förderfähige Bereitstellungsumgebungen** Dropdown-Liste.

1. Geben Sie das Repository an, aus dem die Pipeline den Code abrufen soll.

   * **Repository** - Diese Optionen definieren, aus welchem Git-Repo die Pipeline den Code abrufen soll.
   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.

1. Definieren Sie Ihre Bereitstellungsoptionen.

   1. under **Deployment Trigger** festlegen, welches Ereignis die Pipeline aktiviert.

      * **Manuell** - Verwenden Sie diese Option, um die Pipeline manuell zu starten.
      * **Bei Git-Änderungen** - Diese Optionen starten die Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline nach Bedarf weiterhin manuell starten.
   1. under **Verhalten bei wichtigen Metrikfehlern** festlegen, definieren Sie das Verhalten der Pipeline, wenn in einem der Quality Gates ein wichtiger Fehler auftritt.

      * **Jedes Mal fragen** - Dies ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
      * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Klicken **Speichern** , um die Pipeline zu speichern.

## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Lesen Sie das Dokument [Bereitstellen Ihres Codes](deploying-code.md) für weitere Details.
