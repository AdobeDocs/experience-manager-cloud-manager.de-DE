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
workflow-type: tm+mt
source-wordcount: '1842'
ht-degree: 56%

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

### Hinzufügen einer neuen Produktions-Pipeline über die Pipelines-Karte {#adding-production-pipeline}

Sobald Sie Ihr Programm eingerichtet haben und mindestens eine Umgebung mit [!UICONTROL Cloud Manager] -Benutzeroberfläche können Sie eine Produktions-Pipeline hinzufügen.

Führen Sie die folgenden Schritte aus, um das Verhalten und die Voreinstellungen für Ihre Produktions-Pipeline zu konfigurieren:

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen**.

   ![](/help/using/assets/configure-pipelines/add-prod1.png)

1. **Produktions-Pipeline hinzufügen** angezeigt.

   1. Geben Sie die **Pipeline-Name**. Sie können die **Repository** und **Git-Verzweigung**.

      ![](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Sie können **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** von **Bereitstellungsoptionen**.

      ![](/help/using/assets/configure-pipelines/add-prod3.png)


      Sie können die folgenden Bereitstellungs-Trigger zuweisen, um die Pipeline zu starten:

      * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
      * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

      Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

      Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:

      * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
      * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler genehmigt.
   1. Wählen Sie die **Bereitstellungsoptionen**.

      ![](/help/using/assets/configure-pipelines/add-prod4.png)

      * **Nach Staging-Implementierung genehmigen** funktioniert ähnlich wie die Genehmigung vor der Produktionsbereitstellung, findet aber unmittelbar nach dem Schritt der Staging-Bereitstellung statt (d. h. bevor Tests durchgeführt werden). Das unterscheidet sich von der Genehmigung vor der Produktionsbereitstellung, die nach Abschluss aller Tests erfolgt.

      * **Änderungen am Lastenausgleich überspringen** überspringt die Änderungen.
   1. Wählen Sie die **Dispatcher-Konfiguration** für die Staging-Umgebung. Geben Sie den Pfad ein und wählen Sie die Aktion aus **Typ** und klicken Sie auf **Pfad hinzufügen**. Sie können bis zu 100 Pfade pro Umgebung angeben.

      ![](/help/using/assets/configure-pipelines/dispatcher-stage.png)

   1. Wählen Sie die **Bereitstellungsoptionen** für die Produktion. Jetzt definieren Sie die Parameter zur Steuerung der Produktionsbereitstellung.

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
   1. Richten Sie die **Dispatcher-Konfigurationen** für die Produktion. Geben Sie den Pfad ein und wählen Sie die Aktion aus **Typ** und klicken Sie auf **Pfad hinzufügen**. Sie können bis zu 100 Pfade pro Umgebung angeben.

      ![](/help/using/assets/configure-pipelines/dispatcher-prod.png)

      Als Bereitstellungs-Manager haben Sie die Möglichkeit, eine Reihe von Inhaltspfaden zu konfigurieren, die entweder **ungültig gemacht** oder aus dem AEM Dispatcher-Cache für Veröffentlichungsinstanzen **entfernt** werden, wenn Sie die Pipeline einrichten oder bearbeiten.

      Sie können verschiedene Pfade für die Bereitstellung in der Staging- und Produktionsumgebung konfigurieren. Wenn diese Cache-Aktionen konfiguriert sind, werden sie im Rahmen der Einrichtung der Bereitstellungspipeline direkt nach der Bereitstellung etwaiger Inhaltspakete durchgeführt. Diese Einstellungen verwenden standardmäßiges AEM Dispatcher-Verhalten: Ungültiges Verhalten führt zu einer Ungültigmachung des Caches, vergleichbar mit einer Aktivierung von Autoreninhalten zur Veröffentlichung. Beim „Leeren“ wird der Cache-Inhalt gelöscht.

      Generell ist die Ungültigmachung vorzuziehen. In einigen Fällen ist jedoch eine Leerung erforderlich, insbesondere bei Verwendung von AEM-HTML-Client-Bibliotheken.

      >[!NOTE]
      >
      >Weitere Informationen zum Dispatcher-Cache finden Sie unter [Dispatcher – Übersicht](dispatcher-configurations.md).





1. Klicken Sie auf **Weiter** nach Auswahl aller Optionen.

1. Wählen Sie Ihre Optionen aus dem **Staging-Tests** Schritt. Je nachdem, welche Produkte Sie lizenziert haben, können Sie Leistungstests für *AEM Sites* und *AEM Assets* konfigurieren. Weitere Informationen finden Sie unter [Leistungstests](understand-your-test-results.md#performance-testing).

   1. Wählen Sie Ihre Optionen aus **Sites Content Delivery/Distributed Load Weight**. Siehe [AEM Sites beim Leistungstest](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-sites) für weitere Details.

      ![](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Wählen Sie Ihre Optionen aus **Asset-Leistungstestverteilung**. Siehe [AEM Assets beim Leistungstest](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/how-to-use/understand-your-test-results.html?lang=en#aem-assets) für weitere Details.

      ![](/help/using/assets/configure-pipelines/add-prod6.png)

1. Klicken Sie auf **Speichern** , um das Hinzufügen der Produktions-Pipeline abzuschließen.

### Bearbeiten einer Produktions-Pipeline {#editing-prod-pipeline}

Sie können die Pipeline-Konfigurationen über die **Programmübersicht** Seite.

Gehen Sie wie folgt vor, um die konfigurierte Pipeline zu bearbeiten:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/edit-prod1.png)

1. Die **Produktions-Pipeline bearbeiten** angezeigt.

   1. Die **Konfiguration** -Tab können Sie die **Pipeline-Name**, **Repository**, **Git-Verzweigung**, **Deployment Trigger**, **Verhalten bei wichtigen Metriken mit Fehlern**, **Bereitstellungsoptionen** und **Dispatcher-Konfigurationen**.

      >[!NOTE]
      >Siehe [Hinzufügen und Verwalten von Repositorys](/help/using/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.


   1. Die **Staging-Tests** bietet Ihnen die Möglichkeit, Ihre Optionen erneut auszuwählen unter **Sites Content Delivery/Distributed Load Weight** und **Asset-Leistungstestverteilung**.

1. Klicken Sie auf **Aktualisieren** nachdem Sie die Pipeline bearbeitet haben.

### Zusätzliche Produktions-Pipeline-Aktionen {#additional-prod-actions}

#### Ausführen einer Produktions-Pipeline {#run-prod}

Sie können die Produktions-Pipeline über die Pipelines-Karte ausführen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Löschen einer Produktions-Pipeline {#delete-prod}

Sie können die Produktions-Pipeline aus der Pipelines-Karte löschen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann die Produktions-Pipeline jetzt auf Self-Service-Weise über die **Löschen** -Option auf der Pipeline-Karte aus.

## Produktionsfremde Pipelines und Pipelines für Tests der Code-Qualität

Zusätzlich zur Haupt-Pipeline, die für die Staging- und Produktionsumgebung bereitgestellt wird, können Kunden weitere Pipelines einrichten, die als **Produktionsfremde Pipelines** bezeichnet werden. Diese Pipelines führen immer die Schritte Build-Erstellung und Tests der Code-Qualität aus. Sie können optional auch für die Adobe Managed Services-Umgebung bereitgestellt werden.

## Video-Tutorial {#video-tutorial-two}

### Nicht-Produktions- und Nur-Code-Qualität-Pipelines in Cloud Manager {#non-prod-video}

CI/CD-Produktionsfremde Pipelines sind in zwei Kategorien unterteilt: Code-Qualitäts-Pipelines und Bereitstellungs-Pipelines. Code-Qualitäts-Pipelines leiten den gesamten Code aus einer Git-Verzweigung, der erstellt und anhand der Code-Qualitätsprüfung von Cloud Manager geprüft werden soll.

>[!VIDEO](https://video.tv.adobe.com/v/26316/)

### Hinzufügen einer produktionsfremden Pipeline {#add-non-production-pipeline}

Auf dem Startbildschirm werden diese Pipelines in einer neuen Karte aufgeführt:

1. Zugriff auf **Pipelines** -Karte vom Cloud Manager-Startbildschirm aus. Klicken Sie auf **+Hinzufügen** und wählen Sie **Hinzufügen einer produktionsfremden Pipeline**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add1.png)

1. **Hinzufügen einer produktionsfremden Pipeline**  angezeigt. Wählen Sie den Pipeline-Typ aus, den Sie erstellen möchten, entweder **Code-Qualitäts-Pipeline** oder **Bereitstellungs-Pipeline**.

   Darüber hinaus können Sie auch **Deployment Trigger** und **Verhalten bei wichtigen Metrikfehlern** von **Bereitstellungsoptionen**. Klicken Sie auf **Weiter**.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add2.png)


1. Die neu erstellte Nicht-Produktions-Pipeline wird jetzt im **Pipelines** Karte.

   ![](/help/using/assets/configure-pipelines/nonprod-pipeline-add4.png)


   Die Pipeline wird auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt, wie unten dargestellt:

   * **Hinzufügen** - ermöglicht das Hinzufügen einer neuen Pipeline.
   * **Auf Repository-Informationen zugreifen**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.
   * **Weitere Informationen**: Führt zu weiteren Informationen über die Dokumentation zur CI/CD-Pipeline.

### Bearbeiten einer produktionsfremden Pipeline {#editing-nonprod-pipeline}

Sie können die Pipeline-Konfigurationen über die **Pipelines-Karte** von **Programmübersicht** Seite.

Gehen Sie wie folgt vor, um die konfigurierte Nicht-Produktions-Pipeline zu bearbeiten:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Wählen Sie die produktionsfremde Pipeline aus und klicken Sie auf **...**. Klicken Sie auf **Bearbeiten**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit1.png)

1. Die **Produktions-Pipeline bearbeiten** wird ein Dialogfeld angezeigt, in dem Sie die **Pipeline-Name**, **Repository**, **Git-Verzweigung**, **Deployment Trigger** und **Verhalten bei wichtigen Metriken mit Fehlern**.

   ![](/help/using/assets/configure-pipelines/non-prod-pipeline-edit2.png)

   >[!NOTE]
   >Siehe [Hinzufügen und Verwalten von Repositorys](/help/using/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   Sie können die folgenden Bereitstellungs-Trigger zuweisen, um die Pipeline zu starten:

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Bei Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

   Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt. Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler genehmigt.


1. Klicken Sie auf **Aktualisieren** nach Abschluss der Bearbeitung der produktionsfremden Pipeline.

### Zusätzliche produktionsfremde Pipelineaktionen {#additional-nonprod-actions}

#### Ausführen einer produktionsfremden Pipeline {#run-nonprod}

Sie können die Produktions-Pipeline über die Pipelines-Karte ausführen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/nonprod-run1.png)

#### Löschen einer produktionsfremden Pipeline {#delete-nonprod}

Sie können die Produktions-Pipeline aus der Pipelines-Karte löschen:

1. Navigieren Sie zu **Pipelines** der Karte **Programmübersicht** Seite.

1. Klicken Sie auf **...** von **Pipelines** Karte und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/nonprod-delete.png)


## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Weitere Informationen finden Sie unter [Bereitstellen Ihres Codes](deploying-code.md).
