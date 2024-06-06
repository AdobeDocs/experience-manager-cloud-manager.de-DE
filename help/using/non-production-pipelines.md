---
title: Konfigurieren von produktionsfremden Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 85c1e22609dc5646d3de0ccc71e9423d4243e13a
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 100%

---

# Konfigurieren von produktionsfremden Pipelines {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie sich zunächst einen konzeptionellen Überblick über die Funktionsweise von Pipelines in Cloud Manager verschaffen möchten, lesen Sie die das Dokument [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md).

## Übersicht {#overview}

Über die Kachel **Pipelines** in [!UICONTROL Cloud Manager] kann der **Bereitstellungs-Manager** zwei verschiedene Arten von Pipelines erstellen.

* **Produktions-Pipelines**: Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quell-Code vollständig in die Produktion zu übernehmen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf produktionsfremde Pipelines. Informationen zur Konfiguration von Produktions-Pipelines finden Sie im Dokument [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md).

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Code-Qualitäts-Pipelines**: Diese Pipelines führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und sie führen die Build- und Code-Qualitätsschritte aus.
* **Bereitstellungs-Pipelines**: Diese Pipelines führen nicht nur wie die Code-Qualitäts-Pipelines die Build- und Code-Qualitätsschritte aus, sondern stellen den Code auch in einer produktionsfremden Umgebung bereit.

>[!NOTE]
>
>Die Pipeline kann erst eingerichtet werden, wenn das zugehörige Git-Repository mindestens eine Verzweigung hat und die [Programmeinrichtung](/help/getting-started/program-setup.md) abgeschlossen ist. Im Dokument [Cloud Manager Repositorys](/help/managing-code/managing-repositories.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten können.

## Hinzufügen einer produktionsfremden Pipeline {#add-non-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von Cloud Manager Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte „Pipelines“ über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Wählen Sie auf der Registerkarte **Konfiguration** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** den zu erstellenden Pipeline-Typ aus: entweder **Codequalitäts-Pipeline** oder **Bereitstellungspipeline**.

   ![Pipeline-Typ wählen](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Geben Sie im Feld **Name der produktionsfremden Pipeline** eine Beschreibung für die Pipeline an.

1. Wenn Sie eine **Bereitstellungs-Pipeline** erstellen möchten, wählen Sie im Dropdown-Menü **Berechtigte Bereitstellungsumgebungen** die Ziel-Bereitstellungsumgebung aus.

1. Geben Sie das Repository an, aus dem die Pipeline den Code abrufen soll.

   * **Repository**: Diese Option definiert, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   * **Git-Verzweigung**: Diese Option definiert, aus welcher Verzweigung des ausgewählten Repositorys die Pipeline den Code abrufen soll.

1. Definieren Sie die Bereitstellungsoptionen.

   1. Definieren Sie unter **Bereitstellungsauslöser**, durch welches Ereignis die Pipeline aktiviert werden soll.

      * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell zu starten.
      * **Bei Git-Änderungen**: Bei Auswahl dieser Option wird die Pipeline immer dann gestartet, wenn der konfigurierten Git-Verzweigung Übertragungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   1. Für Bereitstellungs-Pipelines definieren Sie unter **Verhalten bei wichtigen Metrikfehlern** das Verhalten der Pipeline, wenn ein wichtiger Fehler in einem der Quality Gates auftritt.

      * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler ablehnt.
      * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.

   1. **Dispatcherkonfiguration**: Die Rolle **Bereitstellungs-Manager** kann eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM-Dispatcher-Cache gelöscht werden, wenn eine Pipeline ausgeführt wird. Wenn diese Cache-Aktionen konfiguriert sind, werden sie im Rahmen der Einrichtung der Bereitstellungs-Pipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Konfigurieren:

      1. Geben Sie unter **PATH** einen Pfad für den Inhalt an.
      1. Wählen Sie unter **TYPE** die Aktion aus, die mit dem Pfad durchgeführt werden soll.

         * **Leeren**: Löschen des Cache-Inhalts.
         * **Invalidieren**: Eine Cache-Invalidierung durchführen, ähnlich wie bei der Aktivierung von Inhalten von einer Autoreninstanz auf einer Veröffentlichungsinstanz.
      1. Klicken Sie auf **Pfad hinzufügen**, um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen. Weitere Einzelheiten finden Sie in dem Dokument [Code-Bereitstellung](/help/using/code-deployment.md).

## Video-Tutorial {#video-tutorial}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
