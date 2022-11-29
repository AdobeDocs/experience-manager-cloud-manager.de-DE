---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 39b38da17ed1cadf4f2e9633a9e76b537325316f
workflow-type: tm+mt
source-wordcount: '1302'
ht-degree: 98%

---


# Konfigurieren von Produktions-Pipelines {#configuring-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie sich zunächst einen konzeptionellen Überblick über die Funktionsweise von Pipelines in Cloud Manager verschaffen möchten, lesen Sie die das Dokument [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md).

## Übersicht {#overview}

Über die Kachel **Pipeline-Einstellungen** in [!UICONTROL Cloud Manager] können Sie zwei verschiedene Arten von Pipelines erstellen.

* **Produktions-Pipelines**: Eine Produktions-Pipeline ist eine speziell entwickelte Pipeline, die eine Reihe orchestrierter Schritte umfasst, um Quell-Code aus dem Git-Repository bis hin in die Produktionsumgebung zu bringen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf Produktions-Pipelines. Weitere Informationen zur Konfiguration von produktionsfremden Pipelines finden Sie unter [Konfigurieren von produktionsfremden Pipelines](/help/using/non-production-pipelines.md).

Die Rolle **Implementierungs-Manager** ist für die Einrichtung der Pipeline verantwortlich. Die Pipeline-Konfiguration besteht aus folgenden Schritten:

1. Definition des Auslösers, der die Pipeline startet
1. Definition der Parameter zur Steuerung der Produktionsbereitstellung
1. Konfiguration der Leistungstestparameter

>[!NOTE]
>
>Die Pipeline kann erst eingerichtet werden, wenn das zugehörige Git-Repository mindestens eine Verzweigung hat und die [Programmeinrichtung](/help/getting-started/program-setup.md) abgeschlossen ist.

## Video-Tutorial {#video-tutorial-one}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie mit der [!UICONTROL Cloud Manager]-Benutzeroberfläche Ihr Programm eingerichtet haben und über mindestens eine Umgebung verfügen, können Sie eine Produktions-Pipeline hinzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** zur Karte **Pipelines** und klicken Sie auf **Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen** aus.

   ![Produktions-Pipeline hinzufügen](/help/assets/configure-pipelines/add-prod1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** wird geöffnet, wobei die Registerkarte **Konfiguration** geöffnet ist, auf eine einige Optionen für die Pipeline festgelegt werden müssen. Diese Optionen sind in ausklappbaren Abschnitten gruppiert und werden in den folgenden Schritten beschrieben.

   1. Geben Sie in das Feld **Name der Pipeline** einen beschreibenden Namen für die Pipeline ein.

   1. Im Abschnitt **Quell-Code** definieren Sie, wo die Pipeline den Code abruft, den sie verarbeitet.

      * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.
      >[!TIP]
      >
      >Im Dokument [Einrichten von Programmen](/help/getting-started/program-setup.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten können.

      * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welchem Zweig in der ausgewählten Pipeline der Code abgerufen werden soll.
      * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.

      ![Repos für die Pipeline definieren](/help/assets/configure-pipelines/add-prod2.png)

   1. Im Abschnitt **Umgebungen** legen Sie fest, wodurch eine Bereitstellung ausgelöst wird und wie sie in den einzelnen Umgebungen ausgeführt werden soll.

      1. Im Abschnitt **STAGE** können Sie festlegen, wie die Pipeline in Ihrer Staging-Umgebung eingesetzt wird.

         * **Bereitstellungsauslöser**: Sie haben die folgenden Optionen, um die Bereitstellungsauslöser für den Start der Pipeline zu definieren.

            * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell über die Cloud Manager-Benutzeroberfläche zu starten.
            * **Bei Git-Änderungen**: Diese Option startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.
         * **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungs-Manager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

            * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
            * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler ablehnt.
            * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.

         ![Bereitstellungsauslöser](/help/assets/configure-pipelines/add-prod3.png)

         * **Bereitstellungsoptionen**: Sie können bestimmte Bereitstellungsaufgaben beschleunigen.

            * **Nach Staging-Bereitstellung genehmigen**: Diese Genehmigung erfolgt nach der Bereitstellung in der Staging-Umgebung, bevor irgendwelche Tests durchgeführt werden. Andernfalls erfolgt die Genehmigung vor der Produktionsbereitstellung, die nach Abschluss aller Tests erfolgt.

            * **Änderungen am Load-Balancer überspringen**: Änderungen am Load-Balancer werden nicht vorgenommen.

         ![Staging-Bereitstellungsoptionen](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcherkonfiguration**: Die Rolle **Implementierungs-Manager** kann eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM-Dispatcher-Cache gelöscht werden, wenn eine Pipeline ausgeführt wird. Wenn diese Cache-Aktionen konfiguriert sind, werden sie im Rahmen der Einrichtung der Bereitstellungs-Pipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Konfigurieren:

            1. Geben Sie unter **PATH** einen Pfad für den Inhalt an.
            1. Wählen Sie unter **TYPE** die Aktion aus, die mit dem Pfad durchgeführt werden soll.

               * **Leeren** - Führen Sie einen Cache-Löschvorgang durch.
               * **Ungültigmachen** - Führen Sie eine Cache-Invalidierung durch, ähnlich wie bei der Aktivierung von Inhalten von einer Authoring-Instanz zu einer Publishing-Instanz.
            1. Klicken Sie auf **Pfad hinzufügen**, um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.

         ![Dispatcherkonfiguration](/help/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >Generell ist die Aktion „Invalidieren“ vorzuziehen. In einigen Fällen ist jedoch eine Leerung erforderlich, insbesondere bei Verwendung von AEM-HTML-Client-Bibliotheken.

      1. Im Abschnitt **PRODUCTION** können Sie festlegen, wie die Pipeline in der Produktionsumgebung eingesetzt werden soll.

         * **Bereitstellungsoptionen**: Sie können die Parameter zur Steuerung der Produktionsbereitstellung definieren.

            * **GoLive-Genehmigung verwenden**: Für die Bereitstellung ist eine manuelle Genehmigung durch eine Anwenderin oder einen Anwender mit der Rolle **Geschäftsinhaber**, **Projekt-Manager** oder **Implementierungs-Manager** über die Benutzeroberfläche von [!UICONTROL Cloud Manager] erforderlich.
            * **Geplant**: Mit dieser Option wird die Pipeline vor der Produktionsbereitstellung angehalten, sodass sie geplant werden kann. Wenn diese Option ausgewählt ist, wird die Pipeline nach der Bereitstellung in der Staging-Umgebung angehalten und die Anwenderin bzw. der Anwender wird aufgefordert, die entsprechenden Maßnahmen zu ergreifen.
               * **Jetzt**: Bei Auswahl dieser Option erfolgt sofort die Bereitstellung in der Produktion und die Pipeline wird damit abgeschlossen.
               * **Datum**: Mit dieser Option kann die Anwenderin oder der Anwender einen Zeitpunkt festlegen, zu dem die Bereitstellung abgeschlossen sein soll.
               * **Ausführung stoppen**: Mit dieser Option wird die Bereitstellung in der Produktionsumgebung abgebrochen.

            >[!TIP]
            >
            >Weitere Informationen dazu, wie Sie den Bereitstellungsplan festlegen oder die Pipeline sofort ausführen können, finden Sie im Dokument [Bereitstellen des Codes](/help/using/code-deployment.md).

            * **CSE-Überwachung nutzen**: Bei Auswahl dieser Option wird ein CSE eingeschaltet, um die Bereitstellung tatsächlich zu starten. Wenn diese Option aktiviert ist, während eine Pipeline erstellt oder bearbeitet wird, hat die Rolle **Implementierungs-Manager** folgende Optionen.

               * **Beliebiger CSE**: Bei Auswahl dieser Option kann jeder verfügbare CSE die Bereitstellung starten.
               * **Mein CSE**: Bei Auswahl dieser Option kann nur der dem Kunden zugewiesene CSE die Bereitstellung starten. Dies gilt auch für den designierten CSE-Backup, wenn der CSE nicht verfügbar ist.

            ![Optionen für die Produktionsbereitstellung](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcherkonfiguration**: Definiert die Dispatcher-Konfiguration für die Produktionsumgebung. Es sind die gleichen Optionen wie für die Staging-Umgebung verfügbar.










1. Klicken Sie auf **Weiter**, um zur Registerkarte **Staging-Test** zu gelangen, auf der Sie Leistungstests für AEM Sites und AEM Assets konfigurieren können, je nachdem, welche Produkte Sie lizenziert haben.

   >[!TIP]
   >
   >Im Dokument [Testen der Code-Qualität](/help/using/code-quality-testing.md#performance-testing) finden Sie weitere Informationen zu den Optionen, die auf der Registerkarte **Staging-Tests** verfügbar sind.

   1. Im Abschnitt **Site-Inhaltsbereitstellung/verteilte Lastgewichtung** legen Sie fest, wie die Leistungstests für Sites konfiguriert werden, basierend auf der Gewichtung der Seitenanfragen zwischen den drei Seitensätzen, die aktiviert oder deaktiviert werden können.

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

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen. Weitere Einzelheiten finden Sie in dem Dokument [Code-Bereitstellung](/help/using/code-deployment.md).
