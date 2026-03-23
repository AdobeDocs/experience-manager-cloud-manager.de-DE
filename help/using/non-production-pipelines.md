---
title: Hinzufügen einer produktionsfremden Pipeline
description: Erfahren Sie, wie Sie mit Cloud Manager produktionsfremde Pipelines erstellen und konfigurieren, um Code bereitzustellen.
exl-id: ccf4b4a2-6e29-4ede-821c-36318b568e5c
source-git-commit: eaf3db69bd3cc0a06aafd1b415c5bdb467019c1b
workflow-type: tm+mt
source-wordcount: '1992'
ht-degree: 27%

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

Nachdem Sie ein Programm und mindestens eine Umgebung in der Cloud Manager-Benutzeroberfläche eingerichtet haben, können Sie produktionsfremde Pipelines hinzufügen. Verwenden Sie diese Pipelines, um Ihre Code-Qualität zu testen, bevor Sie sie in Produktionsumgebungen bereitstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte „Pipelines“ über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Wählen Sie auf **Registerkarte** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** den zu erstellenden Pipeline-Typ aus:

   * **Code-Qualitäts-Pipeline**: Erstellt eine Pipeline, die den Code erstellt, Komponententests durchführt und die Code-Qualität auswertet, ohne in einer Umgebung bereitgestellt zu werden.
   * **Bereitstellungs-Pipeline**: Erstellt eine Pipeline, die den Code erstellt, Komponententests durchführt, die Code-Qualität auswertet und in einer Umgebung implementiert.

   ![Pipeline-Typ wählen](/help/using/assets/add-non-production-pipeline-cm-ams.png)

>[!BEGINTABS]

>[!TAB Code-Qualitäts-Pipeline - Registerkarte „Konfiguration“]

| Abschnitt | Option | Beschreibung |
| --- | --- | --- |
| **Pipeline-Konfiguration** | **Name der produktionsfremden Pipeline** | Geben Sie im Feld **Name der produktionsfremden Pipeline** eine Beschreibung für die Pipeline an. |
|  | **Testen** | Nur beim Bearbeiten einer produktionsfremden Pipeline sichtbar.<br>Die Benutzeroberfläche zeigt die Testkategorien an, die die Pipeline im Rahmen der Validierung der Code-Qualität ausführt.<ul><li>**Statische Code-**: Analysiert den Code auf Qualitäts- und Korrektheitsprobleme.<li>**Belastungs-/Leistungstests** : Evaluiert leistungsbezogenes Verhalten im Rahmen von Pipeline-Tests.<li>**Sicherheitstests**: Überprüft den Code und die Pipeline-Ausgabe auf sicherheitsbezogene Probleme. |
| **Bereitstellungsoptionen** | **Bereitstellungs-Trigger** | <ul><li>**Manuell**: Die Option ermöglicht es Ihnen, die Pipeline manuell zu starten.<li>**Bei Git-Änderungen**: Diese Option startet die Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Damit können Sie die Pipeline bei Bedarf immer noch manuell starten. |
|  | **Verhalten bei bedeutenden Metrikfehlern** | <ul><li>**Jedes Mal fragen**: Dieses Verhalten ist die Standardeinstellung und erfordert ein manuelles Eingreifen bei einem bedeutenden Fehler.<li>**Sofort fehlschlagen** - Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Im Wesentlichen wird damit ein Benutzer simuliert, der manuell jeden Fehler ablehnt.<li>**Sofort fortfahren** - Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Im Wesentlichen wird damit eine Benutzerin oder ein Benutzer simuliert, die bzw. der manuell jeden Fehler genehmigt.</li></ul> |
|  | Kontrollkästchen **Nach Staging-Bereitstellung genehmigen** | Nur beim Bearbeiten einer produktionsfremden Pipeline sichtbar.<br>Wählen Sie diese Option, um nach der Bereitstellung in der Staging-Umgebung eine Genehmigung einzuholen, bevor die Pipeline fortgesetzt werden kann. Wenn diese Option nicht ausgewählt ist, wird die Pipeline basierend auf dem konfigurierten Verhalten fortgesetzt. |

>[!TAB Bereitstellungs-Pipeline - Registerkarte „Konfiguration“]

| Abschnitt | Option | Beschreibung |
| --- | --- | --- |
| **Pipeline-Konfiguration** | **Name der produktionsfremden Pipeline** | Geben Sie im Feld **Name der produktionsfremden Pipeline** eine Beschreibung für die Pipeline an. |
|   | **Mögliche Bereitstellungsumgebung** | Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welchen Umgebungen Cloud Manager den Code bereitstellt. |
|   | **Testen** | Nur beim Bearbeiten einer produktionsfremden Pipeline sichtbar.<br>Die Benutzeroberfläche zeigt die Testkategorien an, die die Pipeline im Rahmen der Validierung der Code-Qualität ausführt.<ul><li>**Statische Code-**: Analysiert den Code auf Qualitäts- und Korrektheitsprobleme.<li>**Belastungs-/Leistungstests** : Evaluiert leistungsbezogenes Verhalten im Rahmen von Pipeline-Tests.<li>**Sicherheitstests**: Überprüft den Code und die Pipeline-Ausgabe auf sicherheitsbezogene Probleme.</li></ul> |
| **Bereitstellungsoptionen** | **Bereitstellungs-Trigger** | <ul><li>**Manuell**: Die Option ermöglicht es Ihnen, die Pipeline manuell zu starten.<li>**Bei Git-Änderungen**: Diese Option startet die Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Damit können Sie die Pipeline bei Bedarf immer noch manuell starten. |
|   | **Verhalten bei bedeutenden Metrikfehlern** | <ul><li>**Jedes Mal fragen** - Die Standardeinstellung, bei der der Benutzer aufgefordert wird, zu entscheiden, wie er vorgehen soll, wenn eine wichtige Metrik fehlschlägt.<li>**Sofort fehlschlagen**: Die Pipeline wird abgebrochen, wenn eine wichtige Metrik fehlschlägt. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler ablehnen.<li>**Sofort fortfahren**: Die Pipeline wird automatisch fortgesetzt, wenn eine wichtige Metrik fehlschlägt. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler genehmigen.</li></ul> |
|  | Kontrollkästchen **Nach Staging-Bereitstellung genehmigen** | Nur beim Bearbeiten einer produktionsfremden Pipeline sichtbar.<br>Wählen Sie diese Option, um nach der Bereitstellung in der Staging-Umgebung eine Genehmigung einzuholen, bevor die Pipeline fortgesetzt werden kann. Wenn diese Option nicht ausgewählt ist, wird die Pipeline basierend auf dem konfigurierten Verhalten fortgesetzt. |
|  | Kontrollkästchen **Änderungen am Load-Balancer**&#x200B;überspringen) | Wählen Sie diese Option aus, um zu verhindern, dass die Pipeline während der Bereitstellung Änderungen am Lastenausgleich vornimmt. |
|  | **Dispatcher-Konfiguration** | Die **Bereitstellungs-Manager**-Rolle kann eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM Dispatcher-Cache gelöscht werden, wenn eine Pipeline ausgeführt wird. Diese Cache-Aktionen werden im Rahmen der Einrichtung der Bereitstellungs-Pipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden das Standardverhalten von AEM Dispatcher. Gehen Sie wie folgt vor, um `Dispatcher` zu konfigurieren:<ul><li>Geben **unter** einen Inhaltspfad an, den die Pipeline leeren oder ungültig machen soll.<li>Wählen Sie unter **TYPE** die Aktion aus, die mit dem Pfad durchgeführt werden soll.<ul><li>**Flush**: Löschen des Cache-Inhalts unter dem angegebenen Pfad.</li><li>**Invalidieren**: Eine Cache-Invalidierung durchführen, ähnlich wie bei der Aktivierung von Inhalten von einer Autoreninstanz auf einer Veröffentlichungsinstanz.</li><li>Klicken Sie auf **Pfad hinzufügen**, um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.</li></ul> |
| **Pipeline** | **Experience Audit**-Kontrollkästchen | Wählen Sie diese Option aus, um einen Experience Audit-Schritt in die Pipeline aufzunehmen. Nach der Aktivierung umfasst die Pipeline den Experience Audit-Schritt nach der Registerkarte &quot;Source-Code“. |

>[!ENDTABS]

1. Klicken Sie unten rechts im Dialogfeld **Produktionsfremde Pipeline hinzufügen** auf **Weiter**.
1. Wählen Sie den Code-Typ aus, den die Pipeline erstellen und bereitstellen soll.

>[!BEGINTABS]

>[!TAB Registerkarte &quot;Source-Code“ - Full-Stack-Code]

Stellt die gesamte AEM-Anwendung bereit, einschließlich Anwendungs-Code und standardmäßig der Web-Stufen-Konfiguration.

| Abschnitt | Option | Beschreibung |
| --- | --- | --- |
| **Source-Code** | **Repository** | Wählen Sie aus der Dropdown-Liste das Git-Repository aus, das die Pipeline als Quelle verwendet. Cloud Manager erstellt Code aus dem Repository, das Sie hier auswählen. |
|   | **Git-Verzweigung** | Wählen Sie aus der Dropdown-Liste die Verzweigung im ausgewählten Repository aus, aus der die Pipeline erstellen soll. Der Standardwert lautet `main`. Die Pipeline verwendet die ausgewählte Verzweigung als Quelle für die Erstellung und Bereitstellung. Klicken Sie bei Bedarf auf **Aktualisieren**, um die Liste der verfügbaren Verzweigungen für das ausgewählte Repository zu aktualisieren. Verwenden Sie diese Option, wenn eine kürzlich erstellte Verzweigung nicht in der Liste angezeigt wird. |
|   | **Strategie erstellen** | <ul><li>**Vollständiger Build**: Erstellt jedes Mal alle Module im Repository.<li>BETA **Smart Build** - Erstellt nur Module, die sich seit dem letzten Commit geändert haben.<br>Weitere Informationen [Verwenden von Smart Build in einer produktionsfremden Pipeline](#about-smart-build).</li></ol>**Wichtig**: Smarter Build ist nur für Code-Qualitäts-Pipelines und Bereitstellungs-Pipelines für Entwicklungs-Full-Stack-Code verfügbar. |
|   | Kontrollkästchen **Konfiguration der Web-Stufe** ignorieren) | Wählen Sie diese Option, um die Bereitstellung der Web-Stufen-Konfiguration in einer Full-Stack-Code-Pipeline zu überspringen. Lassen Sie die Option deaktiviert, um die Web-Stufen-Konfiguration zusammen mit dem Code der Pipeline bereitzustellen. |
| **Pipeline** | **Experience Audit**-Kontrollkästchen | Wählen Sie diese Option aus, um einen Experience Audit-Schritt in die Pipeline aufzunehmen. Nach der Aktivierung umfasst die Pipeline den Experience Audit-Schritt nach der Registerkarte &quot;Source-Code“. |

>[!TAB Source-Code - Web-Stufen-Konfiguration]

Stellt nur Web-Stufen-Konfigurationen bereit, z. B. Dispatcher-Eigenschaften, die zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client verwendet werden. Wenn Sie **Web-Stufen-Konfiguration** auswählen, erstellt Cloud Manager eine Pipeline für die Bereitstellung der Web-Stufen-Konfiguration.

Wenn bereits eine Full-Stack-Pipeline vorhanden ist, zeigt Cloud Manager einen Hinweis an, dass die vorhandene Full-Stack-Pipeline durch das Erstellen einer Web-Stufen-Konfigurations-Pipeline die Web-Stufen-Konfiguration ignoriert. Nachdem Sie die Web-Stufen-Konfigurations-Pipeline erstellt haben, verwaltet Cloud Manager Web-Stufen-Konfigurationsbereitstellungen über diese Pipeline anstelle der Full-Stack-Pipeline.

| Abschnitt | Option | Beschreibung |
| --- | --- | --- |
| **Source-Code** | **Repository** | Wählen Sie aus der Dropdown-Liste das Git-Repository aus, das die Web-Stufen-Konfiguration enthält. |
|   | **Git-Verzweigung** | Wählen Sie die Verzweigung im ausgewählten Repository aus, die Cloud Manager für die Bereitstellung verwendet. Klicken Sie bei Bedarf auf **Aktualisieren**, um die Liste der verfügbaren Verzweigungen für das ausgewählte Repository zu aktualisieren. Verwenden Sie diese Option, wenn eine kürzlich erstellte Verzweigung nicht in der Liste angezeigt wird. |
|   | **Code-Speicherort** | Geben Sie den Pfad in das ausgewählte Repository ein, das die bereitzustellende Web-Stufen-Konfiguration enthält. Der Standardspeicherort ist der Repository-Stamm (`/`). |

>[!ENDTABS]

1. Klicken Sie auf **Speichern**.

## Über die Verwendung von Smart Build in einer produktionsfremden Pipeline{#about-smart-build}

**Smart Build** in Cloud Manager ist eine optimierte Build-Strategie für produktionsfremde Pipelines. Smartes Erstellen reduziert Build-Zeiten, indem Module zwischengespeichert und nur die Module neu erstellt werden, die seit der letzten erfolgreichen Ausführung geändert wurden. Unveränderte Module werden aus dem Cache wiederverwendet, während nur geänderte Module und ihre Abhängigkeiten neu erstellt werden, was die Effizienz für Workflows für die iterative Entwicklung verbessert.

Smart Build ist derzeit nur für Folgendes verfügbar:

* Code-Qualitäts-Pipelines
* Entwickeln Sie Full-Stack-Bereitstellungs-Pipelines.

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

Im Allgemeinen weisen Projekte mit vielen unabhängigen Modulen die größten Verbesserungen auf.

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

Siehe [Hinzufügen einer produktionsfremden Pipeline](#add-non-production-pipeline) Aktivieren von Smart Build.



<!-- 
1. If you chose to add a **Deployment Pipeline**, select the target deployment environment from the **Eligible Deployment Environments** dropdown.

1. Provide the repository where the pipeline should retrieve the code.

   * **Repository** - Defines from which Git repo that the pipeline should retrieve the code.
   * **Git Branch** - Defines from which branch in Git that the selected pipeline should retrieve the code.

1. Define your deployment options.

   1. Under **Deployment Trigger**, define what event activates the pipeline.

      * **Manual** - Lets you manually start the pipeline.
      * **On Git Changes** - Starts the pipeline when commits are added to the configured Git branch. With this option, you can still start the pipeline manually, as required.

   1. For deployment pipelines, under **Important Metric Failures Behavior**, define the behavior of the pipeline when an important failure is encountered in any of the quality gates.

       * **Ask every time** - The default setting and requires manual intervention on any important failure.
       * **Fail Immediately** - The pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
       * **Continue Immediately** - The pipeline proceeds automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

   1. **Dispatcher Configuration** - The **Deployment Manager** role can configure a set of content paths that are either invalidated or flushed from the AEM Dispatcher cache when a pipeline is run. These cache actions are performed as part of the deployment pipeline step, just after any content packages are deployed. These settings use standard AEM Dispatcher behavior. To configure:

      1. Under **PATH** provide a content path.
      1. Under **TYPE**, select the action to be taken on that path.

         * **Flush** - Perform a cache deletion.
         * **Invalidate** - Perform a cache invalidation, similar to when content is activated from an authoring instance to a publishing instance.
         
      1. Click **Add Path** to add your specified path. You can add up to 100 paths per environment.

1. Click **Save**.
-->

## Die nächsten Schritte {#the-next-steps}

Nachdem Sie die Pipeline konfiguriert haben, können Sie Ihren Code bereitstellen. Weitere Informationen finden Sie unter [Bereitstellung von Code](/help/using/code-deployment.md).

## Video-Tutorial {#video-tutorial}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess, der in diesem Dokument beschrieben wird.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)
