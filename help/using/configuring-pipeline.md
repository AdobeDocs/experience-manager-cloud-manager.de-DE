---
title: Konfigurieren Ihrer CI/CD-Pipeline
seo-title: Configure your CI/CD Pipeline
description: Auf dieser Seite erfahren Sie, wie Sie Ihre Pipeline-Einstellungen in Cloud Manager konfigurieren.
seo-description: Before you start to deploy your code, you must configure your pipeline settings from the AEM Cloud Manager.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 2be8f290b58fff2991f876c37dd1b499bc6c5352
workflow-type: ht
source-wordcount: '1842'
ht-degree: 100%

---

# Konfigurieren Ihrer CI/CD-Pipeline {#configure-your-ci-cd-pipeline}

>[!NOTE]
>Informationen zum Konfigurieren der CI/CD-Pipeline für Cloud Manager in AEM as a Cloud Service finden Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html?lang=de#using-cloud-manager).

Auf der folgenden Seite wird beschrieben, wie Sie die **Pipeline** konfigurieren. Weitere grundlegende Informationen zur Funktionsweise der Pipeline finden Sie unter [Übersicht zur CI/CD-Pipeline](ci-cd-pipeline.md).


## Wissenswertes zum Ablauf {#understanding-the-flow}

Sie können Ihre Pipeline über die Kachel **Pipeline-Einstellungen** in der [!UICONTROL Cloud Manager]-Benutzeroberfläche konfigurieren.

Der Implementierungs-Manager ist für die Einrichtung der Pipeline verantwortlich. Wählen Sie hierfür zunächst eine Verzweigung im **Git-Repository** aus. Die Pipelinekonfiguration besteht aus folgenden Schritten:

* Definition des Auslösers, der die Pipeline startet
* Definition der Parameter zur Steuerung der Produktionsbereitstellung
* Konfiguration der Leistungstestparameter

## Video-Tutorial {#video-tutorial-one}

### Konfigurieren von Pipelines in Cloud Manager {#config-pipeline-video}

Die Konfiguration der CI/CD-Produktions-Pipeline definiert den Auslöser, der die Pipeline initiiert, sowie Parameter zur Steuerung der Produktionsbereitstellung und Leistungstestparameter.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Einrichten der Pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>Die Pipeline kann erst eingerichtet werden, wenn das Git-Repository mindestens eine Verzweigung hat und die [Programmeinrichtung](setting-up-program.md) abgeschlossen ist.

Bevor Sie Code bereitstellen, müssen Sie Ihre Pipelineeinstellungen über [!UICONTROL Cloud Manager] konfigurieren.

>[!NOTE]
>
>Sie können die Pipelineeinstellungen nach der Ersteinrichtung ändern.

### Hinzufügen einer neuen Produktions-Pipeline über die Karte „Pipelines“ {#adding-production-pipeline}

Sobald Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der [!UICONTROL Cloud Manager]-Benutzeroberfläche verfügen, können Sie Ihre Produktions-Pipeline einrichten.

Führen Sie folgende Schritte aus, um das Verhalten und die Voreinstellungen für Ihre Pipeline zu konfigurieren:

1. Gehen Sie von Ihrer Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** wird angezeigt.

   1. Geben Sie den **Name der Pipeline** an. Sie können das **Repository** und die **Git-Verzweigung** auswählen.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Sie können den **Bereitstellungsauslöser** und das **Verhalten bei bedeutenden Metrikfehlern** in den **Bereitstellungsoptionen** festlegen.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Sie können die folgenden Bereitstellungsauslöser zuweisen, um die Pipeline zu starten:

      * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
      * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

      Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

      Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:

      * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofort fehlschlagen**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
      * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler genehmigt.
   1. Wählen Sie die **Bereitstellungsoptionen** aus.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **Nach Staging-Bereitstellung genehmigen** funktioniert ähnlich wie die Genehmigung vor der Produktionsimplementierung, findet aber unmittelbar nach dem Schritt der Staging-Implementierung statt (d. h. bevor Tests durchgeführt werden). Das unterscheidet sich von der Genehmigung vor der Produktionsimplementierung, die nach Abschluss aller Tests erfolgt.

      * **Änderungen am Load-Balancer überspringen** überspringen die Änderungen.
   1. Wählen Sie die **Dispatcher-Konfiguration** für die Staging-Umgebung aus. Geben Sie den Pfad ein, wählen Sie im Menü **Typ** die Aktion aus und klicken Sie auf **Pfad hinzufügen**. Sie können bis zu 100 Pfade pro Umgebung angeben.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Wählen Sie die **Bereitstellungsoptionen** für die Produktionsumgebung aus. Jetzt definieren Sie die Parameter zur Steuerung der Produktionsbereitstellung.

      ![](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

      Die drei verfügbaren Optionen sind:

      * **GoLive-Genehmigung verwenden**: Für die Bereitstellung ist eine manuelle Genehmigung durch einen Business Owner, einen Projektmanager oder Implementierungs-Manager über die [!UICONTROL Cloud Manager]-Benutzeroberfläche erforderlich.

      * **Geplant**: Mit dieser Option kann der Benutzer die geplante Bereitstellung in der Produktionsumgebung aktivieren.

         >[!NOTE]
         >Wenn die Option **Geplant** ausgewählt ist, können Sie Ihre Produktionsbereitstellung für die Pipeline **nach** der Staging-Bereitstellung (und nach der **GoLive-Genehmigung verwenden**, sofern diese Option aktiviert ist) planen, um auf einen Zeitplan zu warten. Der Benutzer kann die Produktionsbereitstellung aber auch sofort ausführen.
         >
         >Unter [Bereitstellen Ihres Codes](deploying-code.md) erfahren Sie, wie Sie den Bereitstellungsplan festlegen oder den Code sofort in der Produktionsumgebung ausführen.

         * **CSE-Überwachung nutzen**: Ein CSE ist involviert, der die eigentliche Bereitstellung startet. Während der Einrichtung oder Bearbeitung der Pipeline wurde die CSE-Überwachung aktiviert. In diesem Fall kann der Implementierungs-Manager Folgendes auswählen:

            * **Beliebiger CSE**: Schließt alle verfügbaren CSE ein.
            * **Mein CSE**: Bezieht sich auf einen bestimmten CSE, der dem Kunden zugewiesen wurde, bzw. auf dessen Backup, falls der zugewiesene CSE nicht im Hause ist.
   1. Richten Sie die **Dispatcher-Konfigurationen** für die Produktionsumgebung ein. Geben Sie den Pfad ein, wählen Sie im Menü **Typ** die Aktion aus und klicken Sie auf **Pfad hinzufügen**. Sie können bis zu 100 Pfade pro Umgebung angeben.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      Als Bereitstellungs-Manager haben Sie die Möglichkeit, eine Reihe von Inhaltspfaden zu konfigurieren, die entweder **ungültig gemacht** oder aus dem AEM Dispatcher-Cache für Veröffentlichungsinstanzen **entfernt** werden, wenn Sie die Pipeline einrichten oder bearbeiten.

      Sie können verschiedene Pfade für die Bereitstellung in der Staging- und Produktionsumgebung konfigurieren. Wenn diese Cache-Aktionen konfiguriert sind, werden sie im Rahmen der Einrichtung der Bereitstellungspipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden standardmäßiges AEM Dispatcher-Verhalten: Ungültiges Verhalten führt zu einer Ungültigmachung des Caches, vergleichbar mit einer Aktivierung von Autoreninhalten zur Veröffentlichung. Beim „Leeren“ wird der Cache-Inhalt gelöscht.

      Generell ist die Ungültigmachung vorzuziehen. In einigen Fällen ist jedoch eine Leerung erforderlich, insbesondere bei Verwendung von AEM-HTML-Client-Bibliotheken.

      >[!NOTE]
      >
      >Weitere Informationen zum Dispatcher-Cache finden Sie unter [Dispatcher – Übersicht](dispatcher-configurations.md).





1. Klicken Sie nach Auswahl aller Optionen auf **Weiter**.

1. Wählen Sie Ihre Optionen aus dem Schritt **Staging-Tests**. Je nachdem, welche Produkte Sie lizenziert haben, können Sie Leistungstests für *AEM Sites* und *AEM Assets* konfigurieren. Weitere Informationen finden Sie unter [Leistungstests](understand-your-test-results.md#performance-testing).

   1. Wählen Sie Ihre Optionen aus **Site-Inhaltsbereitstellung/Verteilte Lastgewichtung**. Weitere Informationen dazu finden Sie unter [AEM Sites beim Leistungstest](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#aem-sites).

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Wählen Sie Ihre Optionen aus **Assets-Leistungstestverteilung** aus. Weitere Informationen dazu finden Sie unter [AEM Assets beim Leistungstest](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=de#aem-assets).

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Klicken Sie auf **Speichern**, um das Hinzufügen der Produktions-Pipeline abzuschließen.

### Bearbeiten einer Produktions-Pipeline {#editing-prod-pipeline}

Sie können die Pipeline-Konfigurationen über die Seite **Programmübersicht** bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte Pipeline zu bearbeiten:

1. Gehen Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. Das Dialogfeld **Produktions-Pipeline bearbeiten** wird angezeigt.

   1. Auf der Registerkarte **Konfiguration** können Sie den **Name der Pipeline**, das **Repository**, die **Git-Verzweigung**, den **Bereitstellungsauslöser**, das **Verhalten bei bedeutenden Metrikfehlern**, die **Bereitstellungsoptionen** und die **Dispatcher-Konfigurationen** ändern.

      >[!NOTE]
      >Unter [Hinzufügen und Verwalten von Repositorys](/help/using/cloud-manager-repositories.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.


   1. Die Registerkarte **Staging-Tests** bietet Ihnen die Möglichkeit, Ihre Optionen unter **Sites-Inhaltsbereitstellung/Verteilte Lastgewichtung** und **Assets-Leistungstestverteilung** erneut auszuwählen.

1. Klicken Sie auf **Aktualisieren**, nachdem Sie die Pipeline bearbeitet haben.

### Zusätzliche Produktions-Pipeline-Aktionen {#additional-prod-actions}

#### Ausführen einer Produktions-Pipeline {#run-prod}

Sie können die Produktions-Pipeline über die Karte „Pipelines“ ausführen:

1. Gehen Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Löschen einer Produktions-Pipeline {#delete-prod}

Sie können die Produktions-Pipeline aus der Karte „Pipelines“ löschen:

1. Gehen Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann die Produktions-Pipeline jetzt im Self-Service über die Option **Löschen** von der Karte „Pipeline“ löschen.

## Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität

Zusätzlich zur Haupt-Pipeline, die für die Staging- und Produktionsumgebung bereitgestellt wird, können Kunden weitere Pipelines einrichten, die als **Produktionsfremde Pipelines** bezeichnet werden. Diese Pipelines führen immer die Schritte Build-Erstellung und Tests der Code-Qualität aus. Sie können optional auch für die Adobe Managed Services-Umgebung bereitgestellt werden.

## Video-Tutorial {#video-tutorial-two}

### Nicht-Produktions- und Nur-Code-Qualität-Pipelines in Cloud Manager {#non-prod-video}

CI/CD-Produktionsfremde Pipelines sind in zwei Kategorien unterteilt: Codequalitätspipelines und Bereitstellungs-Pipelines. Codequalitätspipelines leiten den gesamten Code aus einer Git-Verzweigung, der erstellt und anhand der Code-Qualitätsprüfung von Cloud Manager geprüft werden soll.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Hinzufügen einer produktionsfremden Pipeline {#add-non-production-pipeline}

Auf dem Startbildschirm werden diese Pipelines in einer neuen Karte aufgeführt:

1. Rufen Sie im Cloud Manager-Startbildschirm die Karte **Pipelines** auf. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. Das Dialogfeld **Hinzufügen einer produktionsfremden Pipeline** wird angezeigt. Wählen Sie den Pipeline-Typ aus, den Sie erstellen möchten, entweder **Codequalitätspipeline** oder **Bereitstellungspipeline**.

   Zusätzlich können Sie den **Bereitstellungsauslöser** und das **Verhalten bei bedeutenden Metrikfehlern** in den **Bereitstellungsoptionen** festlegen. Klicken Sie auf **Weiter**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. Die neu erstellte produktionsfremde Pipeline wird jetzt in der Karte **Pipelines** angezeigt.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   Die Pipeline wird auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen**: ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.

### Bearbeiten einer produktionsfremden Pipeline {#editing-nonprod-pipeline}

Sie können die Pipeline-Konfigurationen über die Karte **Pipelines** von der Seite **Programmübersicht** aus bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte produktionsfremde Pipeline zu bearbeiten:

1. Gehen Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Wählen Sie die produktionsfremde Pipeline aus und klicken Sie auf **...**. Klicken Sie auf **Bearbeiten**, wie in der Abbildung unten gezeigt.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. Das Dialogfeld **Produktions-Pipeline bearbeiten** wird angezeigt. Darin können Sie den **Name der Pipeline**, das **Repository**, die **Git-Verzweigung**, den **Bereitstellungsauslöser** und das **Verhalten bei bedeutenden Metrikfehlern** ändern.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Unter [Hinzufügen und Verwalten von Repositorys](/help/using/cloud-manager-repositories.md) erfahren Sie, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   Sie können die folgenden Bereitstellungsauslöser zuweisen, um die Pipeline zu starten:

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

   Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungs-Manager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt. Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort fehlschlagen**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler genehmigt.


1. Klicken Sie nach Abschluss der Bearbeitung der produktionsfremden Pipeline auf **Aktualisieren**.

### Zusätzliche Aktionen für produktionsfremde Pipelines {#additional-nonprod-actions}

#### Ausführen einer produktionsfremden Pipeline {#run-nonprod}

Sie können die Produktions-Pipeline über die Karte „Pipelines“ ausführen:

1. Gehen Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### Löschen einer produktionsfremden Pipeline {#delete-nonprod}

Sie können die Produktions-Pipeline aus der Karte „Pipelines“ löschen:

1. Gehen Sie von der Seite **Programmübersicht** aus zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Weitere Informationen finden Sie unter [Bereitstellen Ihres Codes](deploying-code.md).
