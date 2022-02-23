---
title: Konfigurieren von produktionsfremden Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen.
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: ht
source-wordcount: '626'
ht-degree: 100%

---


# Konfigurieren von produktionsfremden Pipelines {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie sich zunächst einen konzeptionellen Überblick über die Funktionsweise von Pipelines in Cloud Manager verschaffen möchten, lesen Sie die Dokumentation [CI/CD-Pipeline-Übersicht](ci-cd-pipeline.md).

>[!NOTE]
>
>Informationen zum Konfigurieren der CI/CD-Pipeline für Cloud Manager in AEM as a Cloud Service finden Sie in der [AEMaaCS-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=de#using-cloud-manager).

## Übersicht {#understanding-the-flow}

Die Rolle **Bereitstellungs-Manager** ist dafür verantwortlich, die Pipeline mithilfe der Kachel **Pipelines** in der Benutzeroberfläche von [!UICONTROL Cloud Manager] einzurichten.

Sie können zwei Arten von Pipelines erstellen.

* **Produktions-Pipelines**: Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quell-Code vollständig in die Produktion zu übernehmen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf produktionsfremde Pipelines. Informationen zum Konfigurieren von produktionsfremden Pipelines finden Sie unter [Konfigurieren von produktionsfremden Pipelines](configuring-non-production-pipelines.md).

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Code-Qualitäts-Pipelines**: Diese Pipelines führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und sie führen die Build- und Code-Qualitätsschritte aus.
* **Bereitstellungs-Pipelines**: Diese Pipelines führen nicht nur wie die Code-Qualitäts-Pipelines die Build- und Code-Qualitätsschritte aus, sondern stellen den Code auch in einer produktionsfremden Umgebung bereit.

>[!NOTE]
>
>Die Pipeline kann erst eingerichtet werden, wenn das zugehörige Git-Repository mindestens eine Verzweigung hat und die [Programmeinrichtung](setting-up-program.md) abgeschlossen ist. Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](cloud-manager-repositories.md).

## Video-Tutorial {#video-tutorial-two}

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

## Hinzufügen einer produktionsfremden Pipeline {#add-non-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von Cloud Manager Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte „Pipelines“ über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Wählen Sie auf der Registerkarte **Konfiguration** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** den zu erstellenden Pipeline-Typ aus: entweder **Codequalitätspipeline** oder **Bereitstellungspipeline**.


   ![Pipeline-Typ wählen](/help/using/assets/configure-pipelines/add-non-production-pipeline.png)

1. Geben Sie im Feld **Name der produktionsfremden Pipeline** eine Beschreibung für die Pipeline an.

1. Wenn Sie eine **Implementierungs-Pipeline** erstellen möchten, wählen Sie im Dropdown-Menü **Berechtigte Implementierungsumgebungen** die Zielimplementierungsumgebung aus.

1. Geben Sie das Repository an, aus dem die Pipeline den Code abrufen soll.

   * **Repository**: Diese Option definiert, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   * **Git-Verzweigung**: Diese Option definiert, aus welcher Verzweigung des ausgewählten Repositorys die Pipeline den Code abrufen soll.

1. Definieren Sie die Implementierungsoptionen.

   1. Definieren Sie unter **Implementierungsauslöser**, durch welches Ereignis die Pipeline aktiviert werden soll.

      * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell zu starten.
      * **Bei Git-Änderungen**: Bei Auswahl dieser Option wird die Pipeline immer dann gestartet, wenn der konfigurierten Git-Verzweigung Übertragungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.
   1. Definieren Sie unter **Verhalten bei wichtigen Metrikfehlern** das Verhalten der Pipeline, wenn in einer der Qualitätsstufen ein wichtiger Fehler auftritt.

      * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofort fehlschlagen**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler ablehnt.
      * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Weitere Informationen finden Sie unter [Bereitstellen Ihres Codes](deploying-code.md).
