---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 8e2c57d2594691e7fb18d8a538caa9b54a26b6bb
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 49%

---


# Produktions-Pipelines konfigurieren {#configuring-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen. Wenn Sie zunächst einen konzeptionellen Überblick darüber erhalten möchten, wie Pipelines in Cloud Manager funktionieren, finden Sie weitere Informationen unter [CI/CD-Pipelines](/help/overview/ci-cd-pipelines.md).

## Übersicht {#overview}

Über die Kachel **Pipeline-Einstellungen** in [!UICONTROL Cloud Manager] können Sie zwei verschiedene Arten von Pipelines erstellen.

* **Produktions-Pipelines** - Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die aus einer Reihe aufeinander abgestimmter Schritte besteht, um Quellcode aus Ihrem Git-Repository bis zur Produktion zu übernehmen.
* **Produktionsfremde Pipelines**: Eine produktionsfremde Pipeline dient dazu, Code-Qualitätsprüfungen durchzuführen oder Quell-Code in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf Produktions-Pipelines. Weitere Informationen zum Konfigurieren von Nicht-Produktions-Pipelines finden Sie im Dokument [Konfigurieren von Nicht-Produktions-Pipelines](/help/using/non-production-pipelines.md) .

Die Rolle **Bereitstellungs-Manager** ist für die Einrichtung der Pipeline verantwortlich. Die Pipeline-Konfiguration besteht aus folgenden Schritten:

1. Definieren des Triggers, der die Pipeline startet.
1. Definition der Parameter zur Steuerung der Produktionsbereitstellung
1. Konfiguration der Leistungstestparameter

>[!NOTE]
>
>Eine Pipeline kann erst eingerichtet werden, wenn das zugehörige Git-Repository mindestens eine Verzweigung aufweist und die [Programmeinrichtung](/help/getting-started/program-setup.md) abgeschlossen ist.

## Neue Produktions-Pipeline hinzufügen {#adding-production-pipeline}

Nachdem Sie die Benutzeroberfläche von [!UICONTROL Cloud Manager] zum Einrichten Ihres Programms verwendet haben und über mindestens eine Umgebung verfügen, können Sie eine Produktions-Pipeline hinzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Gehen Sie von Ihrer Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie auf **+Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Produktions-Pipeline hinzufügen](/help/assets/configure-pipelines/add-prod1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** wird geöffnet, wobei die Registerkarte **Konfiguration** geöffnet ist, auf eine einige Optionen für die Pipeline festgelegt werden müssen. Diese Optionen sind in ausklappbaren Abschnitten gruppiert und werden in den folgenden Schritten beschrieben.

   1. Geben Sie in das Feld **Name der Pipeline** einen beschreibenden Namen für die Pipeline ein.

   1. Im Abschnitt **Source-Code** definieren Sie, wo die Pipeline den von ihr verarbeiteten Code abruft.

      * **Repository** - Definiert, welches Git-Repository die Pipeline abrufen soll.

      >[!TIP]
      >
      >Im Dokument [Einrichten von Programmen](/help/getting-started/program-setup.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten können.

      * **Git-Verzweigung** - Definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * **Codeposition** - Definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.

      ![Repos für die Pipeline definieren](/help/assets/configure-pipelines/add-prod2.png)

   1. Im Abschnitt **Umgebungen** legen Sie fest, wodurch eine Bereitstellung ausgelöst wird und wie sie in den einzelnen Umgebungen ausgeführt werden soll.

      1. Im Abschnitt **STAGE** können Sie festlegen, wie die Pipeline in Ihrer Staging-Umgebung eingesetzt wird.

         * **Bereitstellungsauslöser**: Sie haben die folgenden Optionen, um die Bereitstellungsauslöser für den Start der Pipeline zu definieren.

            * **Manuell** - Starten Sie die Pipeline manuell über die Cloud Manager-Benutzeroberfläche.
            * **Bei Git-Änderungen** - Starten Sie die CI/CD-Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

         * **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der Bereitstellungs-Manager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

            * **Jedes Mal fragen** - Die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
            * **Sofort fehlschlagen** - Die Pipeline wird abgebrochen, sobald ein wichtiger Fehler auftritt. Es emuliert einen Benutzer, der jeden Fehler manuell ablehnt.
            * **Sofort fortfahren** - Die Pipeline wird automatisch fortgesetzt, wenn ein wichtiger Fehler auftritt. Es emuliert einen Benutzer, der manuell jeden Fehler genehmigt.

         ![Bereitstellungsauslöser](/help/assets/configure-pipelines/add-prod3.png)

         * **Bereitstellungsoptionen**: Sie können bestimmte Bereitstellungsaufgaben beschleunigen.

            * **Nach Staging-Bereitstellung genehmigen**: Diese Genehmigung erfolgt nach der Bereitstellung in der Staging-Umgebung, bevor irgendwelche Tests durchgeführt werden. Andernfalls erfolgt die Genehmigung vor der Produktionsbereitstellung, die nach Abschluss aller Tests erfolgt.

            * **Änderungen am Load-Balancer überspringen**: Änderungen am Load-Balancer werden nicht vorgenommen.

         ![Staging-Bereitstellungsoptionen](/help/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher-Konfiguration** - Die Rolle **Bereitstellungsmanager** kann eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM Dispatcher-Cache entfernt werden, wenn eine Pipeline ausgeführt wird. Diese Cache-Aktionen werden im Rahmen des Implementierungs-Pipeline-Schritts ausgeführt, unmittelbar nachdem alle Inhaltspakete bereitgestellt wurden. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Gehen Sie zur Konfiguration wie folgt vor:

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

            * **GoLive-Genehmigung verwenden** - Ein Benutzer mit der Rolle **Business Owner**, **Project Manager** oder **Deployment Manager** über die Benutzeroberfläche von [!UICONTROL Cloud Manager] muss eine Bereitstellung manuell genehmigen.
            * **Geplant** - Hält die Pipeline vor der Produktionsbereitstellung, damit sie geplant werden kann. Wenn diese Option ausgewählt ist, wird die Pipeline nach der Bereitstellung in der Staging-Umgebung angehalten und die Anwenderin bzw. der Anwender wird aufgefordert, die entsprechenden Maßnahmen zu ergreifen.
               * **`Now`** - Wird sofort für die Produktion bereitgestellt und schließt die Pipeline effektiv ab.
               * **Datum** - Hiermit kann der Benutzer einen Zeitpunkt planen, zu dem die Bereitstellung abgeschlossen werden soll.
               * **Ausführung stoppen** - Bricht die Bereitstellung für die Produktion ab.

           >[!TIP]
           >
           >Unter [Code-Bereitstellung](/help/using/code-deployment.md) erfahren Sie, wie Sie den Bereitstellungsplan festlegen oder die Pipeline sofort ausführen.

            * **CSE-Überwachung verwenden** - Wenn diese Option ausgewählt ist, ist ein CSE (Customer Success Engineer) damit beauftragt, die eigentliche Bereitstellung zu starten. Wenn diese Option aktiviert ist, während eine Pipeline erstellt oder bearbeitet wird, hat die Rolle **Bereitstellungs-Manager** folgende Optionen.

               * **Beliebiger CSE** - Ermöglicht jedem verfügbaren CSE, die Bereitstellung zu starten.
               * **My CSE** - Ermöglicht nur den dem Kunden zugewiesenen CSE, die Bereitstellung zu starten. Diese Option gilt auch für die vorgesehene Sicherung des CSE, wenn der zugewiesene CSE nicht verfügbar ist.

           ![Optionen für die Produktionsbereitstellung](/help/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher-Konfiguration** - Definieren Sie die Dispatcher-Konfiguration für Ihre Produktionsumgebung. Die Optionen entsprechen den Optionen für die Staging-Umgebung.

1. Klicken Sie auf **Weiter** , um zur Registerkarte **Staging-Tests** zu wechseln, wo Sie je nachdem, welche Produkte Sie lizenziert haben, Leistungstests für AEM Sites und AEM Assets konfigurieren können.

   >[!TIP]
   >
   >Weitere Informationen zu den auf der Registerkarte **Staging-Tests** verfügbaren Optionen finden Sie unter [Tests der Codequalität](/help/using/code-quality-testing.md#performance-testing) .

   1. Im Abschnitt **Sites Content Delivery/Distributed Load Weight** konfigurieren Sie die Site-Leistungstests anhand der Gewichtung von Seitenanfragen zwischen drei Seitensätzen. Sie können die Seitensätze nach Bedarf aktivieren oder deaktivieren.

      * **Beliebte Live-Seiten**
      * **Andere Live-Seiten**
      * **Neue Seiten**

      ![Sites-Lastgewichtung](/help/assets/configure-pipelines/add-prod5.png)

   1. Im Abschnitt **Assets-Leistungstestverteilung** definieren Sie die Testverteilung von Bildern und PDF und definieren Ihre eigenen Testassets.

      * **Bilder**: Stellen Sie den Schieberegler ein, um die Aufteilung des Tests zwischen Bildern und PDFs anzupassen.
      * **PDFs**: Stellen Sie den Schieberegler ein, um die Aufteilung des Tests zwischen Bildern und PDFs anzupassen.

      * Definieren Sie eigene benutzerdefinierte Assets, indem Sie sie hochladen.

         1. **FORMAT**: Wählen Sie aus, ob das benutzerdefinierte Asset eine PDF-Datei eines Bilds ist.
         1. **DATEINAME**: Verwenden Sie die Schaltfläche „Datei-Browser“, um ein Bild auf Ihrem lokalen Computer auszuwählen.
         1. **Testdatei hinzufügen**: Klicken Sie darauf, um das ausgewählte Asset hochzuladen.

      ![Assets-Testverteilung](/help/assets/configure-pipelines/add-prod6.png)

1. Klicken Sie auf **Speichern**, um das Hinzufügen der Produktions-Pipeline abzuschließen.

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Pipeline konfiguriert haben, stellen Sie Ihren Code bereit. Weitere Informationen finden Sie unter [Codebereitstellung](/help/using/code-deployment.md) .

## Video-Tutorial {#video-tutorial-one}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)
