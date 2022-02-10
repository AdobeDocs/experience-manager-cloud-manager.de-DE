---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren können, um Code bereitzustellen.
uuid: 35fd56ac-dc9c-4aca-8ad6-36c29c4ec497
products: SG_EXPERIENCEMANAGER/CLOUDMANAGER
topic-tags: using
content-type: reference
discoiquuid: ba6c763a-b78a-439e-8c40-367203a719b3
feature: CI-CD Pipeline
exl-id: d489fa3c-df1e-480b-82d0-ac8cce78a710
source-git-commit: 205113735cc743e11e140b1161413002844f5b79
workflow-type: tm+mt
source-wordcount: '1557'
ht-degree: 18%

---

# Konfigurieren von Produktions-Pipelines {#configuring-production-pipelines}

Erfahren Sie, wie Sie mit Cloud Manager Produktions-Pipelines erstellen und konfigurieren können, um Code bereitzustellen. Wenn Sie zunächst einen konzeptionellen Überblick darüber erhalten möchten, wie Pipelines in Cloud Manager funktionieren, finden Sie im Abschnitt [Dokumentation zur CI/CD-Pipeline](ci-cd-pipeline.md)

>[!NOTE]
>
>Informationen zum Konfigurieren von CI/CD-Pipelines für Cloud Manager in AEM as a Cloud Service finden Sie unter [die AEMaaCS-Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/configure-pipeline.html#using-cloud-manager)

## Übersicht {#understanding-the-flow}

Sie konfigurieren Pipelines mit dem **Pipeline-Einstellungen** -Kachel im [!UICONTROL Cloud Manager] Benutzeroberfläche.

Sie können zwei verschiedene Pipelinetypen erstellen.

* **Produktions-Pipelines** - Eine Produktions-Pipelines ist eine speziell entwickelte Pipeline, die aus einer Reihe aufeinander abgestimmter Schritte besteht, um Quellcode vollständig in die Produktion zu übernehmen.
* **Nicht-Produktions-Pipelines** - Eine Nicht-Produktions-Pipeline dient hauptsächlich dazu, Code-Qualitätsprüfungen durchzuführen oder Quellcode in einer Entwicklungsumgebung bereitzustellen.

Dieses Dokument konzentriert sich auf Produktions-Pipelines. Weitere Informationen zum Konfigurieren von produktionsfremden Pipelines finden Sie im Dokument [Konfigurieren von Nicht-Produktions-Pipelines.](configuring-non-production-pipelines.md)

Die **Bereitstellungsmanager** ist für die Einrichtung der Pipeline verantwortlich. Die Pipelinekonfiguration besteht aus folgenden Schritten:

1. Definieren des Triggers, der die Pipeline startet.
1. Definieren der Parameter zur Steuerung der Produktionsbereitstellung.
1. Konfiguration der Leistungstestparameter.

>[!NOTE]
>
>Eine Pipeline kann erst eingerichtet werden, wenn ihr verknüpftes Git-Repository mindestens eine Verzweigung aufweist und [Programmeinrichtung](setting-up-program.md) ist abgeschlossen.

>[!NOTE]
>
>Sie können die Pipelineeinstellungen nach der Ersteinrichtung ändern.

## Video-Tutorial {#video-tutorial-one}

In diesem Video erhalten Sie einen Überblick über den Pipeline-Erstellungsprozess.

>[!VIDEO](https://video.tv.adobe.com/v/26314/)

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie die [!UICONTROL Cloud Manager] -Benutzeroberfläche, um Ihr Programm einzurichten und über mindestens eine Umgebung zu verfügen, können Sie eine Produktions-Pipeline hinzufügen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** Seite und klicken Sie auf **+Hinzufügen** und wählen Sie **Produktions-Pipeline hinzufügen**.

   ![Hinzufügen einer Produktions-Pipeline](/help/using/assets/configure-pipelines/add-prod1.png)

1. Die **Produktions-Pipeline hinzufügen** Das Dialogfeld wird geöffnet. **Konfiguration** Registerkarte, auf der eine Reihe von Optionen für Ihre Pipeline definiert werden müssen. Diese Optionen sind in ausblendbare Abschnitte unterteilt und werden in den folgenden Schritten beschrieben.

   1. Geben Sie einen beschreibenden Namen für Ihre Pipeline im **Pipeline-Name** -Feld.

   1. Unter dem **Quellcode** -Abschnitt definieren, legen Sie fest, wo die Pipeline den Code abruft, den sie verarbeiten wird.

      * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.
      >[!TIP]
      >
      >Siehe Dokument . [Einrichten des Programms](setting-up-program.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

      * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * **Code-Speicherort** - Diese Option definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.

      ![Definieren von Repositorys für die Pipeline](/help/using/assets/configure-pipelines/add-prod2.png)

   1. Unter dem **Umgebungen** festlegen, welche Trigger eine Bereitstellung durchführen und wie sie pro Umgebung eingeführt werden soll.

      1. Im **STUFE** können Sie definieren, wie die Pipeline in Ihre Staging-Umgebung ausgeführt wird.

         * **Deployment Trigger** - Sie haben die folgenden Optionen, um die Bereitstellungs-Trigger zum Starten der Pipeline zu definieren.

            * **Manuell** - Verwenden Sie diese Option, um die Pipeline mithilfe der Cloud Manager-Benutzeroberfläche manuell zu starten.
            * **Bei Git-Änderungen** - Diese Optionen starten die CI/CD-Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline nach Bedarf weiterhin manuell starten.
         * **Verhalten bei wichtigen Metrikfehlern** - Während der Einrichtung oder Bearbeitung der Pipeline kann der Bereitstellungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Die verfügbaren Optionen sind:

            * **Jedes Mal fragen** - Dies ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
            * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
            * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.

         ![Deployment Trigger](/help/using/assets/configure-pipelines/add-prod3.png)

         * **Bereitstellungsoptionen** - Sie können bestimmte Bereitstellungsaufgaben beschleunigen.

            * **Nach der Staging-Bereitstellung genehmigen** - Diese Genehmigung erfolgt nach der Bereitstellung in der Staging-Umgebung, bevor Tests durchgeführt werden. Andernfalls erfolgt die Genehmigung vor der Produktionsbereitstellung, die nach Abschluss aller Tests erfolgt.

            * **Änderungen am Lastenausgleich überspringen** - Änderungen am Lastenausgleich werden nicht vorgenommen.

         ![Bereitstellungsoptionen für Staging](/help/using/assets/configure-pipelines/add-prod4.png)

         * **Dispatcher-Konfiguration** - die **Bereitstellungsmanager** -Rolle kann eine Reihe von Inhaltspfaden konfigurieren, die entweder ungültig gemacht oder aus dem AEM Dispatcher-Cache entfernt werden, wenn eine Pipeline ausgeführt wird. Diese Cache-Aktionen werden im Rahmen des Implementierungs-Pipeline-Schritts ausgeführt, unmittelbar nachdem alle Inhaltspakete bereitgestellt wurden. Diese Einstellungen verwenden das standardmäßige AEM Dispatcher-Verhalten. So konfigurieren Sie:

            1. under **PFAD** einen Inhaltspfad angeben.
            1. under **TYP** auswählen, die Aktion, die auf diesem Pfad ausgeführt werden soll.
            * **Leeren** - Führen Sie eine Cache-Invalidierung durch, ähnlich wie bei der Aktivierung von Inhalten von einer Authoring-Instanz zu einer Publishing-Instanz.
            * **Ungültigmachen** - Führt einen Cache-Löschvorgang durch.
            1. Klicken **Pfad hinzufügen** , um den angegebenen Pfad hinzuzufügen. Sie können bis zu 100 Pfade pro Umgebung hinzufügen.

         ![Dispatcher-Konfiguration](/help/using/assets/configure-pipelines/dispatcher-stage.png)

         >[!TIP]
         >
         >Im Allgemeinen ist die Verwendung der Invalidierungs-Aktion vorzuziehen. Es kann jedoch vorkommen, dass eine Leerung erforderlich ist, insbesondere bei der Verwendung AEM HTML Client-Bibliotheken.

      1. Im **PRODUKTION** können Sie definieren, wie die Pipeline in Ihre Produktionsumgebung ausgeführt wird.

         * **Bereitstellungsoptionen** - Sie können die Parameter definieren, die die Produktionsbereitstellung steuern.

            * **Go-Live-Genehmigung verwenden** - Eine Bereitstellung muss von einem Benutzer manuell mit der **Business Owner**, **Projektmanager** oder **Bereitstellungsmanager** Rolle über die [!UICONTROL Cloud Manager] Benutzeroberfläche.
            * **Geplant** - Diese Option stoppt die Pipeline vor der Produktionsbereitstellung, damit sie geplant werden kann. Wenn diese Option aktiviert ist, wird die Pipeline nach der Bereitstellung in der Staging-Umgebung angehalten und der Benutzer wird aufgefordert, die Aktion durchzuführen.
               * **Jetzt** - Diese Option wird sofort in der Produktion bereitgestellt und schließt die Pipeline effektiv ab.
               * **Datum** - Mit dieser Option kann der Benutzer einen Zeitpunkt planen, zu dem die Bereitstellung abgeschlossen sein soll.
               * **Ausführung stoppen** - Mit dieser Option wird die Bereitstellung für die Produktion abgebrochen.

            >[!TIP]
            >
            >Weitere Informationen finden Sie im Dokument . [Bereitstellen Ihres Codes,](deploying-code.md) , um zu erfahren, wie Sie den Bereitstellungsplan festlegen oder die Pipeline sofort ausführen.

            * **CSE-Überwachung verwenden** - Wenn diese Option aktiviert ist, ist ein CSE damit beauftragt, die Bereitstellung tatsächlich zu starten. Wenn diese Option aktiviert ist, wird beim Erstellen oder Bearbeiten einer Pipeline der **Bereitstellungsmanager** -Rolle hat die folgenden Optionen.

               * **Jeglicher CSE** - Mit dieser Option kann jeder verfügbare CSE die Implementierung starten.
               * **My CSE** - Diese Option ermöglicht es nur dem Kunden zugewiesenen CSE, die Bereitstellung zu starten. Dies gilt auch für die vorgesehene Sicherung des CSE, wenn der zugewiesene CSE nicht verfügbar ist.

            ![Produktionsbereitstellungsoptionen](/help/using/assets/configure-pipelines/prod-deploymentoptions.png)

         * **Dispatcher-Konfiguration** - Definieren Sie die Dispatcher-Konfiguration für Ihre Produktionsumgebung. Die Optionen entsprechen denen der Staging-Umgebung.











1. Klicken Sie auf **Weiter** , um **Staging-Tests** Registerkarte, auf der Sie je nach lizenzierten Produkten Leistungstests für AEM Sites und AEM Assets konfigurieren können.

   >[!TIP]
   >
   >Siehe Dokument . [Grundlegendes zu Testergebnissen](understand-your-test-results.md#performance-testing) Weitere Informationen zu den verfügbaren Optionen finden Sie unter **Staging-Tests** Registerkarte.

   1. Unter dem **Sites Content Delivery/Distributed Load Weight** festlegen, wie Sites-Leistungstests basierend auf der Gewichtung von Seitenanforderungen zwischen den drei Seitensätzen konfiguriert werden, die aktiviert oder deaktiviert werden können.

      * **Beliebte Live-Seiten**
      * **Andere Live-Seiten**
      * **Neue Seiten**

      ![Sites-Ladegewicht](/help/using/assets/configure-pipelines/add-prod5.png)

   1. Unter dem **Asset-Leistungstestverteilung** -Abschnitt definieren Sie die Testverteilung von Bildern und PDF und definieren Sie Ihre eigenen Test-Assets.

      * **Bilder** - Passen Sie den Schieberegler an, um die Testaufteilung zwischen Bildern und PDF anzupassen.
      * **PDF** - Passen Sie den Schieberegler an, um die Testaufteilung zwischen Bildern und PDF anzupassen.

      * Definieren Sie Ihre eigenen benutzerdefinierten Assets, indem Sie sie hochladen.

         1. **FORMAT** - Wählen Sie aus, ob Ihr benutzerdefiniertes Asset eine PDF eines Bildes ist.
         1. **DATEINAME** - Verwenden Sie die Schaltfläche Dateibrowser , um ein Bild von Ihrem lokalen Computer auszuwählen.
         1. **Testdatei hinzufügen** - Klicken Sie auf , um das ausgewählte Asset hochzuladen.

      ![Asset-Testverteilung](/help/using/assets/configure-pipelines/add-prod6.png)



1. Klicken **Speichern** , um das Hinzufügen Ihrer Produktions-Pipeline abzuschließen.














### Bearbeiten einer Produktions-Pipeline {#editing-prod-pipeline}

Sie können die Pipeline-Konfigurationen über die Seite **Programm-Überblick** bearbeiten.

Gehen Sie wie folgt vor, um die konfigurierte Pipeline zu bearbeiten:

1. Gehen Sie von der Seite **Programm-Überblick** zur Karte **Pipelines**.

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

1. Gehen Sie von der Seite **Programm-Überblick** zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Ausführen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/prod-run.png)

#### Löschen einer Produktions-Pipeline {#delete-prod}

Sie können die Produktions-Pipeline von der Karte „Pipelines“ aus löschen:

1. Gehen Sie von der Seite **Programm-Überblick** zur Karte **Pipelines**.

1. Klicken Sie von der Karte **Pipelines** aus auf **...** und klicken Sie auf **Löschen**, wie in der folgenden Abbildung dargestellt.

   ![](/help/using/assets/configure-pipelines/prod-delete.png)

   >[!NOTE]
   >Ein Benutzer in der Rolle des Implementierungs-Managers kann die Produktions-Pipeline jetzt im Selbstbedienungsmodus über die Option **Löschen** auf der Karte „Pipeline“ löschen.

