---
title: Hinzufügen einer Produktions-Pipeline
description: Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
TQID: https://experienceleague.adobe.com/WH6W8bZNCWo0BAGLwnMOPpB3bk5P6Fd7c5b-dRT5Vc0
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377
source-git-commit: 4c73ab16ff7eab406c31a6d26cdd09360a94b3ea
workflow-type: tm+mt
source-wordcount: 2101
ht-degree: 60%

---

# Hinzufügen einer Produktions-Pipeline {#configuring-production-pipelines}

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

## Hinzufügen einer Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie mit der [!UICONTROL Cloud Manager]-Benutzeroberfläche Ihr Programm eingerichtet haben und über mindestens eine Umgebung verfügen, können Sie eine Produktions-Pipeline hinzufügen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Navigieren Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen** aus.

   ![Produktions-Pipeline hinzufügen](/help/assets/configure-pipelines/add-prod7.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** wird geöffnet, wobei die Registerkarte **Konfiguration** geöffnet ist, auf eine einige Optionen für die Pipeline festgelegt werden müssen. Diese Optionen sind in ausklappbaren Abschnitten gruppiert und werden in den folgenden Schritten beschrieben.

   1. Geben Sie in das Feld **Name der Pipeline** einen beschreibenden Namen für die Pipeline ein.

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

1. Klicken Sie **Weiter**, um zur Registerkarte **Source-Code** zu gelangen, auf der Sie den Code-Typ auswählen, der bereitgestellt und das Quell-Repository konfiguriert werden soll.

   1. Wählen **unter „Code für Bereitstellung**&quot; den Bereitstellungstyp aus:

      * **[Full-Stack-Code](#full-stack-code)** - Code für Ihre gesamte AEM-Anwendung.
      * **[Web-Stufen-](#web-tier-config)**: Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client.

      Weitere [&#x200B; zu diesen Bereitstellungstypen finden &#x200B;](/help/overview/ci-cd-pipelines.md#code-sources) unter CI/CD-Pipelines . Die restlichen Schritte zum Abschließen der Pipeline-Konfiguration hängen vom ausgewählten Typ ab. Folgen Sie den obigen Links, um zum entsprechenden Abschnitt dieses Dokuments zu springen.

1. Klicken Sie auf **Weiter**, um zur Registerkarte **Staging-Tests** zu gelangen. Dort können Sie abhängig von den von Ihnen lizenzierten Produkten Leistungstests für AEM Sites und AEM Assets konfigurieren. {#stage-testing}

   >[!TIP]
   >
   >Weitere Informationen zu den verfügbaren Optionen auf der Registerkarte **Staging-Tests** finden Sie unter [Testen der Code-Qualität](/help/using/code-quality-testing.md#performance-testing).

   1. Im Abschnitt **Site-Inhaltsbereitstellung/verteilte Lastgewichtung** konfigurieren Sie die Site-Leistungstests anhand der Gewichtung von Seitenanfragen zwischen drei Seitensätzen. Sie können die Seitensätze nach Bedarf aktivieren oder deaktivieren.

      * **Beliebte Live-Seiten**
      * **Andere Live-Seiten**
      * **Neue Seiten**

      ![Sites-Lastgewichtung](/help/assets/configure-pipelines/add-prod8.png)

   1. Im Abschnitt **Asset-Leistungstestverteilung** definieren Sie sowohl die Testverteilung von Bildern und PDFs als auch eigene Test-Assets.

      * **Bilder**: Stellen Sie den Schieberegler ein, um die Aufteilung des Tests zwischen Bildern und PDFs anzupassen.
      * **PDFs**: Stellen Sie den Schieberegler ein, um die Aufteilung des Tests zwischen Bildern und PDFs anzupassen.

      * Definieren Sie eigene benutzerdefinierte Assets, indem Sie sie hochladen.

         1. **FORMAT**: Wählen Sie aus, ob das benutzerdefinierte Asset eine PDF-Datei eines Bilds ist.
         1. **DATEINAME**: Verwenden Sie die Schaltfläche „Datei-Browser“, um ein Bild auf Ihrem lokalen Computer auszuwählen.
         1. **Testdatei hinzufügen**: Klicken Sie darauf, um das ausgewählte Asset hochzuladen.

      ![Assets-Testverteilung](/help/assets/configure-pipelines/add-prod6.png)

1. Klicken Sie auf **Speichern**, um das Hinzufügen der Produktions-Pipeline abzuschließen.

### Full-Stack-Code {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt Backend- und Frontend-Code-Builds zusammen mit der HTTPD/Dispatcher-Konfiguration bereit.

>[!NOTE]
>
>Wenn bereits eine Produktions-Pipeline mit vollem Stapel vorhanden ist, ist diese Auswahl deaktiviert.

**So konfigurieren Sie eine Produktions-Pipeline mit Full-Stack-Code:**

1. Definieren Sie auf der Registerkarte **Quell-Code** die folgenden Optionen:

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   >
   >Im Dokument [Einrichten von Programmen](/help/getting-started/program-setup.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten können.

   * **Git-Verzweigung** - Definiert, aus welcher Verzweigung die Pipeline den Code abrufen soll.
   * **Konfiguration der Web-Stufe ignorieren**: Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Web-Stufenkonfiguration nicht bereit. Wenn für dieselbe Umgebung bereits eine Web-Stufen-Konfigurations-Pipeline vorhanden ist, wird dieses Kontrollkästchen automatisch aktiviert und deaktiviert, da die Web-Stufen-Konfiguration stattdessen von dieser Pipeline verwaltet wird. Wenn keine Web-Stufen-Konfigurations-Pipeline vorhanden ist, können Sie diese Option aktivieren oder deaktivieren, um zu steuern, ob die Full-Stack-Pipeline die Dispatcher-Konfiguration bereitstellt.

   ![Full-Stack-Code-Quelle](/help/assets/configure-pipelines/add-prod-fullstack-source.png)

1. Klicken Sie **Weiter**, um zur Registerkarte **Staging-Tests** zu gelangen. Weitere Informationen finden [&#x200B; unter &#x200B;](#stage-testing) .

### Web-Stufen-Konfiguration {#web-tier-config}

Eine Web-Stufen-Konfigurations-Pipeline stellt nur die HTTPD-/Dispatcher-Konfiguration bereit. Weitere [&#x200B; zu diesem Pipeline-Typ finden &#x200B;](/help/overview/ci-cd-pipelines.md#deployment-types) unter CI/CD-Pipelines .

>[!NOTE]
>
>Wenn bereits eine Web-Stufen-Konfigurations-Produktions-Pipeline vorhanden ist, ist diese Auswahl deaktiviert.

Wenn Sie eine Konfigurations-Pipeline auf Web-Ebene für eine Umgebung mit einer vorhandenen Full-Stack-Pipeline erstellen, wird die Konfiguration auf Web-Ebene in der Full-Stack-Pipeline ignoriert. Diese Änderung betrifft nur die Web-Stufen-Konfiguration in dieser Umgebung.

**So konfigurieren Sie eine Web-Stufen-Konfigurations-Produktions-Pipeline:**

1. Definieren Sie auf der Registerkarte **Quell-Code** die folgenden Optionen:

   * **Repository** - Wählen Sie in der Dropdown-Liste das Git-Repository aus, das die Web-Stufen-Konfiguration enthält.
   * **Git-Verzweigung** - Wählen Sie die Verzweigung im ausgewählten Repository aus, die Cloud Manager für die Bereitstellung verwendet.
   * **Code-Speicherort** - Geben Sie den Pfad in das ausgewählte Repository ein, das die bereitzustellende Web-Stufen-Konfiguration enthält. Der Standardspeicherort ist der Repository-Stamm (`/`).

   >[!NOTE]
   >
   >Wenn der Code-Speicherort nicht auf den Dispatcher-Code-Speicherort verweist, kann zusätzlicher Anwendungs-Code in das Artefaktpaket gezogen und im Dispatcher bereitgestellt werden, was dazu führt, dass Apache beim Neustart fehlschlägt und die Pipeline fehlschlägt. Stellen Sie sicher, dass Sie den richtigen Pfad zu den Dispatcher-Dateien im Repository festlegen.

   ![Web-Stufen-Konfigurationsquelle](/help/assets/configure-pipelines/add-prod-webtier-source.png)

1. Klicken Sie **Weiter**, um zur Registerkarte **Staging-Tests** zu gelangen. Weitere Informationen finden [&#x200B; unter &#x200B;](#stage-testing) .


## Über die Verwendung von Smart Build in einer Produktions-Pipeline{#about-smart-build}

**Smart Build** in Cloud Manager ist eine optimierte Build-Strategie für Produktions-Pipelines. Smartes Erstellen reduziert Build-Zeiten, indem Module zwischengespeichert und nur die Module neu erstellt werden, die seit der letzten erfolgreichen Ausführung geändert wurden. Unveränderte Module werden aus dem Cache wiederverwendet, während nur geänderte Module und ihre Abhängigkeiten neu erstellt werden, was die Effizienz für Workflows für die iterative Entwicklung verbessert.

Smart Build ist derzeit für Folgendes verfügbar:

* Code-Qualitäts-Pipelines
* Implementierungs-Pipelines für Entwicklung, Staging und Produktion mit Full-Stack.

>[!NOTE]
>
>Die erste Ausführung nach der Aktivierung von Smart Build verhält sich wie ein vollständiger Build, da der Cache leer ist.

Smartes Erstellen wird empfohlen, wenn Folgendes zutrifft:

* Sie entwickeln aktiv und nehmen häufige inkrementelle Änderungen vor.
* Ihr Projekt enthält mehrere Maven-Module.
* Vollständige Builds beanspruchen viel Zeit.

Smartes Erstellen ist nicht immer ideal, wenn Folgendes zutrifft:

* Ihr Build beruht in hohem Maße auf Plug-ins, die Vorgänge außerhalb des Abhängigkeitsdiagramms von Maven durchführen.
* Sie benötigen bei jeder Ausführung eine vollständige Neuaufbauvalidierung.

### Grundlegendes zur Build-Leistung{#smart-build-performance}

Der Leistungsgewinn durch die Verwendung von Smart Build hängt von mehreren Faktoren ab, darunter den folgenden:

* Die Anzahl der Module im Projekt.
* Häufigkeit und Umfang von Code-Änderungen.
* Die Verteilung von Abhängigkeiten über Module hinweg.

Im Allgemeinen können Projekte mit vielen unabhängigen Modulen die größte Verbesserung verzeichnen.

### Opt-out aus dem Cache pro Modul{#smart-build-cache-optout}

Smart Build bietet eine differenzierte Steuerung, mit der Sie das Caching für bestimmte Module deaktivieren können. Diese Funktion ist nützlich, wenn bestimmte Module:

* Verwenden Sie Plug-ins wie `exec-maven-plugin` oder `maven-antrun-plugin`.
* Führen Sie Dateivorgänge aus, die nicht von Maven-Abhängigkeiten verfolgt werden.
* Erzeugt im Cache inkonsistente Ergebnisse.

### Deaktivieren der Zwischenspeicherung für ein Modul{#smart-build-disable-caching}

Sie können die folgende Eigenschaft zum `pom.xml` des betroffenen Moduls hinzufügen:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Diese Syntax zwingt das Modul bei jeder Pipeline-Ausführung neu zu erstellen, während andere Module weiterhin vom Caching profitieren.

### Einschränkungen und Überlegungen bei der Verwendung von Smart Build{#smart-build-limitations}

Beachten Sie bei der Verwendung von Smart Build Folgendes:

* Smarter Build beruht auf Maven-Abhängigkeitsanalyse.
* Bei Änderungen außerhalb des Abhängigkeitsdiagramms werden Trigger-Neuaufbauten möglicherweise nicht unterstützt.
* Einige Plug-ins sind möglicherweise nicht vollständig mit der Zwischenspeicherung kompatibel.
* Sie können jederzeit wieder zu **Vollständiger Build** wechseln, indem Sie die produktionsfremde Pipeline bearbeiten.

Wenn Sie auf unerwartetes Build-Verhalten stoßen, sollten Sie das Caching für bestimmte Module deaktivieren oder Ihre Build-Strategie vorübergehend auf **Vollständiger Build** umstellen.

### Fehlerbehebung bei Problemen mit Smart Build{#smart-build-troubleshoot}

| Problem | Lösungsvorschläge |
| --- | --- |
| Buildergebnisse sind inkonsistent | ・ Deaktivierung der Zwischenspeicherung für betroffene Module.<br>・ Überprüfen des Plug-in-Verhaltens (insbesondere `exec`/`antrun`-Plug-ins). |
| Keine Leistungsverbesserung | ・ Stellen Sie sicher, dass mehrere Durchgänge stattgefunden haben (Aufwärmen des Cache).<br>・ Prüfen Sie, ob die meisten Module häufig wechseln. |
| Unerwartete Artefakte oder fehlende Änderungen | ・ Überprüfen, ob Änderungen außerhalb des Maven-Abhängigkeits-Trackings liegen<br>・ Verwenden Sie **Vollständiger Build** zur Überprüfung. |

Siehe [Hinzufügen einer Produktions-Pipeline](#adding-production-pipeline) Aktivieren des Smart Builds.


## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen. Weitere Informationen finden Sie unter [Bereitstellung von Code](/help/using/code-deployment.md).

## Video-Tutorial {#video-tutorial-one}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/327785?captions=ger)
