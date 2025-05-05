---
title: Hinzufügen einer produktionsfremden Pipeline
description: Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: 1209faf71edbd74cd87acfe24ec438b98ddd4a3a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Hinzufügen einer produktionsfremden Pipeline {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie sich zunächst einen konzeptionellen Überblick über die Funktionsweise von Pipelines in Cloud Manager verschaffen möchten, finden Sie unter [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md) entsprechende Informationen.

## Überblick {#overview}

Über die Kachel **Pipelines** in [!UICONTROL Cloud Manager] kann der **Bereitstellungs-Manager** zwei verschiedene Arten von Pipelines erstellen.

* **Produktions-Pipelines**: Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die eine Reihe aufeinander abgestimmter Schritte umfasst, um Quell-Code vollständig in die Produktion zu übernehmen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf produktionsfremde Pipelines. Weitere Informationen zur Konfiguration von Produktions-Pipelines finden Sie unter [Konfigurieren von Produktions-Pipelines](/help/using/production-pipelines.md).

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Code-Qualitäts-Pipelines**: Diese Pipelines führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und die Build- und Code-Qualitätsschritte aus.
* **Bereitstellungs-Pipelines**: Diese Pipelines führen nicht nur wie die Code-Qualitäts-Pipelines die Build- und Code-Qualitätsschritte aus, sondern stellen den Code auch in einer produktionsfremden Umgebung bereit.

>[!NOTE]
>
>Die Pipeline kann erst eingerichtet werden, wenn das zugehörige Git-Repository mindestens eine Verzweigung hat und die [Programmeinrichtung](/help/getting-started/program-setup.md) abgeschlossen ist. Informationen zum Hinzufügen und Verwalten von Repositorys in Cloud Manager finden Sie unter [Cloud Manager-Repositorys](/help/managing-code/managing-repositories.md).

## Hinzufügen einer neuen produktionsfremden Pipeline {#add-non-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von Cloud Manager Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte „Pipelines“ über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Wählen Sie auf der Registerkarte **Konfiguration** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** den zu erstellenden Pipeline-Typ aus: entweder **Codequalitäts-Pipeline** oder **Bereitstellungspipeline**.

   ![Pipeline-Typ wählen](/help/assets/configure-pipelines/add-non-production-pipeline.png)

1. Geben Sie im Feld **Name der produktionsfremden Pipeline** eine Beschreibung für die Pipeline an.

1. Wenn Sie eine **Bereitstellungs-Pipeline** erstellen möchten, wählen Sie im Dropdown-Menü **Berechtigte Bereitstellungsumgebungen** die Ziel-Bereitstellungsumgebung aus.

1. Geben Sie das Repository an, aus dem die Pipeline den Code abrufen soll.

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   * **Git-Verzweigung**: Diese Option legt fest, von welcher Git-Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.

1. Definieren Sie die Bereitstellungsoptionen.

   1. Definieren Sie unter **Bereitstellungsauslöser**, durch welches Ereignis die Pipeline aktiviert werden soll.

      * **Manuell**: Die Option ermöglicht es Ihnen, die Pipeline manuell zu starten.
      * **Bei Git-Änderungen**: Diese Option startet die Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Damit können Sie die Pipeline bei Bedarf immer noch manuell starten.

   1. Für Bereitstellungs-Pipelines definieren Sie unter **Verhalten bei wichtigen Metrikfehlern** das Verhalten der Pipeline, wenn ein wichtiger Fehler in einem der Quality Gates auftritt.

      * **Jedes Mal fragen**: Dies ist die Standardeinstellung, die ein manuelles Eingreifen bei jedem bedeutenden Fehler verlangt.
      * **Sofortiger Ausfall**: Die Pipeline wird bei einem bedeutenden Fehler abgebrochen. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler ablehnen.
      * **Sofort fortsetzen**: Die Pipeline wird bei einem bedeutenden Fehler automatisch fortgesetzt. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler genehmigen.

   1. **Dispatcher-Konfiguration**: Die Rolle **Bereitstellungs-Manager** kann eine Reihe von Inhaltspfaden konfigurieren, die beim Ausführen einer Pipeline entweder invalidiert oder aus dem AEM Dispatcher-Cache gelöscht werden. Diese Cache-Aktionen werden im Rahmen der Einrichtung der Bereitstellungs-Pipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Konfigurieren:

      1. Geben Sie unter **PATH** einen Pfad für den Inhalt an.
      1. Wählen Sie unter **TYPE** die Aktion aus, die mit dem Pfad durchgeführt werden soll.

         * **Leeren**: Löschen des Cache-Inhalts.
         * **Invalidieren**: Eine Cache-Invalidierung durchführen, ähnlich wie bei der Aktivierung von Inhalten von einer Autoreninstanz auf einer Veröffentlichungsinstanz.

      1. Klicken Sie auf **Pfad hinzufügen**, um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.

1. Klicken Sie auf **Speichern**.

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Pipeline konfiguriert haben, können Sie Ihren Code bereitstellen. Weitere Informationen finden Sie unter [Bereitstellung von Code](/help/using/code-deployment.md).

## Video-Tutorial {#video-tutorial}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/327615?captions=ger)
