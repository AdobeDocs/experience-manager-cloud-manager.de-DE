---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 984269e5fe70913644d26e759fa21ccea0536bf4
workflow-type: ht
source-wordcount: '1247'
ht-degree: 100%

---


# Konfigurieren von Produktions-Pipelines {#configuring-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie sich zunächst einen konzeptionellen Überblick über die Funktionsweise von Pipelines in Cloud Manager verschaffen möchten, finden Sie unter [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md) entsprechende Informationen.

## Überblick {#overview}

Über die Kachel **Pipeline-Einstellungen** in [!UICONTROL Cloud Manager] können Sie zwei verschiedene Arten von Pipelines erstellen.

* **Produktions-Pipelines**: Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe orchestrierter Schritte umfasst, um Quell-Code aus dem Git-Repository bis in die Produktionsumgebung zu bringen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf Produktions-Pipelines. Weitere Informationen zur Konfiguration von produktionsfremden Pipelines finden Sie unter [Konfigurieren produktionsfremder Pipelines](/help/using/non-production-pipelines.md).

Die Rolle **Bereitstellungs-Manager** ist für die Einrichtung der Pipeline verantwortlich. Die Pipeline-Konfiguration besteht aus folgenden Schritten:

1. Definition des Auslösers, der die Pipeline startet
1. Definition der Parameter zur Steuerung der Produktionsbereitstellung
1. Konfiguration der Leistungstestparameter

>[!NOTE]
>
>Die Pipeline kann erst eingerichtet werden, wenn das zugehörige Git-Repository mindestens eine Verzweigung hat und die [Programmeinrichtung](/help/getting-started/program-setup.md) abgeschlossen ist.

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie mit der [!UICONTROL Cloud Manager]-Benutzeroberfläche Ihr Programm eingerichtet haben und über mindestens eine Umgebung verfügen, können Sie eine Produktions-Pipeline hinzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Gehen Sie von Ihrer Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen** aus.

   ![Produktions-Pipeline hinzufügen](/help/assets/configure-pipelines/add-prod1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** wird geöffnet, wobei die Registerkarte **Konfiguration** geöffnet ist, auf eine einige Optionen für die Pipeline festgelegt werden müssen. Diese Optionen sind in ausklappbaren Abschnitten gruppiert und werden in den folgenden Schritten beschrieben.

   1. Geben Sie in das Feld **Name der Pipeline** einen beschreibenden Namen für die Pipeline ein.

   1. Definieren Sie im Abschnitt **Quell-Code**, wo die Pipeline den Code abruft, den sie verarbeitet.

      * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

      >[!TIP]
      >
      >Im Dokument [Einrichten von Programmen](/help/getting-started/program-setup.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten können.

      * **Git-Verzweigung**: Diese Option legt fest, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * **Code-Verzeichnis**: Diese Option legt Pfad in der Verzweigung des ausgewählten Repositorys fest, aus dem die Pipeline den Code abrufen soll.

      ![Repos für die Pipeline definieren](/help/assets/configure-pipelines/add-prod2.png)

   1. Im Abschnitt **Umgebungen** legen Sie fest, wodurch eine Bereitstellung ausgelöst wird und wie sie in den einzelnen Umgebungen ausgeführt werden soll.

      1. Im Abschnitt **STAGE** können Sie festlegen, wie die Pipeline in Ihrer Staging-Umgebung eingesetzt wird.

         * **Bereitstellungsauslöser**: Sie haben die folgenden Optionen, um die Bereitstellungsauslöser für den Start der Pipeline zu definieren.

            * **Manuell**: Diese Option startet die Pipeline manuell über die Cloud Manager-Benutzeroberfläche.
            * **Bei Git-Änderungen**: Diese Option startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

         * **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der Bereitstellungs-Manager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

            * **Jedes Mal fragen**: Dies ist die Standardeinstellung, die ein manuelles Eingreifen bei jedem bedeutenden Fehler verlangt.
            * **Sofortiger Ausfall**: Die Pipeline wird bei einem bedeutenden Fehler abgebrochen. Damit werden Benutzende simuliert, die manuell jeden Fehler ablehnen.
            * **Sofort fortsetzen**: Die Pipeline wird bei einem bedeutenden Fehler automatisch fortgesetzt. Damit werden Benutzende simuliert, die manuell jeden Fehler genehmigen.

         ![Bereitstellungsauslöser](/help/assets/configure-pipelines/add-prod3.png)

         * **Bereitstellungsoptionen**: Sie können bestimmte Bereitstellungsaufgaben beschleunigen.

            * **Nach Staging-Bereitstellung genehmigen**: Diese Genehmigung erfolgt nach der Bereitstellung in der Staging-Umgebung, bevor irgendwelche Tests durchgeführt werden. Andernfalls erfolgt die Genehmigung vor der Produktionsbereitstellung, die nach Abschluss aller Tests erfolgt.

            * **Änderungen am Load-Balancer überspringen**: Änderungen am Load-Balancer werden nicht vorgenommen.

         ![Staging-Bereitstellungsoptionen](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher-Konfiguration**: Die Rolle **Bereitstellungs-Manager** kann eine Reihe von Inhaltspfaden konfigurieren, die beim Ausführen einer Pipeline entweder invalidiert oder aus dem AEM Dispatcher-Cache gelöscht werden. Diese Cache-Aktionen werden im Rahmen der Einrichtung der Bereitstellungs-Pipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Gehen Sie zur Konfiguration wie folgt vor:

            1. Geben Sie unter **PATH** einen Pfad für den Inhalt an.
            1. Wählen Sie unter **TYPE** die Aktion aus, die mit dem Pfad durchgeführt werden soll.

               * **Leeren**: Löschen des Cache-Inhalts.
               * **Invalidieren**: Eine Cache-Invalidierung durchführen, ähnlich wie bei der Aktivierung von Inhalten von einer Autoreninstanz auf einer Veröffentlichungsinstanz.

            1. Klicken Sie auf **Pfad hinzufügen**, um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.

         ![Dispatcherkonfiguration](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >Generell ist die Aktion „Invalidieren“ vorzuziehen. In einigen Fällen ist jedoch eine Leerung erforderlich, insbesondere bei Verwendung von AEM-HTML-Client-Bibliotheken.

      1. Im Abschnitt **PRODUCTION** können Sie festlegen, wie die Pipeline in der Produktionsumgebung eingesetzt werden soll.

         * **Bereitstellungsoptionen**: Sie können die Parameter zur Steuerung der Produktionsbereitstellung definieren.

            * **GoLive-Genehmigung verwenden**: Eine Benutzerin oder ein Benutzer mit der Rolle **Geschäftsinhaber**, **Projekt-Manager** oder **Bereitstellungs-Manager** muss eine Bereitstellung über die [!UICONTROL Cloud Manager]-Benutzeroberfläche manuell genehmigen.
            * **Geplant**: Diese Option hält die Pipeline vor der Produktionsbereitstellung an, sodass sie geplant werden kann. Wenn diese Option ausgewählt ist, wird die Pipeline nach der Bereitstellung in der Staging-Umgebung angehalten und die Benutzerin oder der Benutzer wird aufgefordert, die entsprechenden Maßnahmen zu ergreifen.
               * **`Now`**: Dieser Option sorgt dafür, dass die Bereitstellung in der Produktionsumgebung sofort erfolgt. Die Pipeline wird damit abgeschlossen.
               * **Datum**: Diese Option ermöglicht es Benutzenden, einen Zeitpunkt festzulegen, zu dem die Bereitstellung abgeschlossen sein soll.
               * **Ausführung stoppen**: Diese Option bricht die Bereitstellung in der Produktionsumgebung ab.

           >[!TIP]
           >
           >Weitere Informationen dazu, wie Sie einen Bereitstellungsplan festlegen oder die Pipeline sofort ausführen können, finden Sie unter [Bereitstellung von Code](/help/using/code-deployment.md).

            * **CSE-Überwachung nutzen**: Bei Auswahl dieser Option wird ein Mitglied des Customer Success Engineer(CSE)-Teams eingeschaltet, um die tatsächliche Bereitstellung zu starten. Wenn diese Option aktiviert ist, während eine Pipeline erstellt oder bearbeitet wird, hat die Rolle **Bereitstellungs-Manager** folgende Optionen.

               * **Beliebiger CSE**: Diese Option ermöglicht es, dass jedes verfügbare Mitglied des CSE-Teams die Bereitstellung starten kann.
               * **Mein CSE**: Diese Option sorgt dafür, dass nur das der Kundin oder dem Kunden zugewiesene Mitglied des CSE-Teams die Bereitstellung starten kann. Diese Option gilt auch für die vorgesehene CSE-Backup-Person, wenn das zugewiesene Mitglied des CSE-Teams nicht verfügbar ist.

           ![Optionen für die Produktionsbereitstellung](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher-Konfiguration**: Definieren Sie die Dispatcher-Konfiguration für die Produktionsumgebung. Es sind die gleichen Optionen wie für die Staging-Umgebung verfügbar.

1. Klicken Sie auf **Weiter**, um zur Registerkarte **Staging-Tests** zu gelangen. Dort können Sie abhängig von den von Ihnen lizenzierten Produkten Leistungstests für AEM Sites und AEM Assets konfigurieren.

   >[!TIP]
   >
   >Weitere Informationen zu den verfügbaren Optionen auf der Registerkarte **Staging-Tests** finden Sie unter [Testen der Code-Qualität](/help/using/code-quality-testing.md#performance-testing).

   1. Im Abschnitt **Site-Inhaltsbereitstellung/verteilte Lastgewichtung** konfigurieren Sie die Site-Leistungstests anhand der Gewichtung von Seitenanfragen zwischen drei Seitensätzen. Sie können die Seitensätze nach Bedarf aktivieren oder deaktivieren.

      * **Beliebte Live-Seiten**
      * **Andere Live-Seiten**
      * **Neue Seiten**

      ![Sites-Lastgewichtung](/help/assets/configure-pipelines/add-prod5.png)

   1. Im Abschnitt **Asset-Leistungstestverteilung** definieren Sie sowohl die Testverteilung von Bildern und PDFs als auch eigene Test-Assets.

      * **Bilder**: Stellen Sie den Schieberegler ein, um die Aufteilung des Tests zwischen Bildern und PDFs anzupassen.
      * **PDFs**: Stellen Sie den Schieberegler ein, um die Aufteilung des Tests zwischen Bildern und PDFs anzupassen.

      * Definieren Sie eigene benutzerdefinierte Assets, indem Sie sie hochladen.

         1. **FORMAT**: Wählen Sie aus, ob das benutzerdefinierte Asset eine PDF-Datei eines Bilds ist.
         1. **DATEINAME**: Verwenden Sie die Schaltfläche „Datei-Browser“, um ein Bild auf Ihrem lokalen Computer auszuwählen.
         1. **Testdatei hinzufügen**: Klicken Sie darauf, um das ausgewählte Asset hochzuladen.

      ![Assets-Testverteilung](/help/assets/configure-pipelines/add-prod6.png)

1. Klicken Sie auf **Speichern**, um das Hinzufügen der Produktions-Pipeline abzuschließen.

## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen. Weitere Informationen finden Sie unter [Bereitstellung von Code](/help/using/code-deployment.md).

## Video-Tutorial {#video-tutorial-one}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
